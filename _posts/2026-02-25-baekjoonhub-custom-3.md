---
title: "백준허브(BaekjoonHub) 커스텀 (3) - Java 코드 자동 수정 (클래스명, 패키지)"
date: 2026-03-03 16:00:00 +0900
categories: [Dev, Tools]
tags: [baekjoonhub, chrome-extension, github, 알고리즘, java]
image:
  path: /assets/images/baekjoonhub-custom/thumbnails/3.png
  alt: 백준허브 커스텀 썸네일
---

> 이전 글: [백준허브(BaekjoonHub) 커스텀 (2) - 기본 커스텀](/posts/baekjoonhub-custom-2/)

이전 편에서 파일명, 경로, 커밋 메시지를 수정하는 기본 커스텀을 다뤘다.

이번 편과 다음 편은 **이 커스텀의 꽃🌸🌷🌺🌻🌼🪷🏵️🌹🪻💮💐🥀**

이번 편에서는 **Java 코드의 클래스명과 패키지를 자동으로 수정하는 방법**을, 다음 편에서는 이 시리즈의 **메인 이벤트인 PR 자동화**를 다룬다.

---

## 코드 내부 수정하기 (클래스명, 패키지 추가)

나는 내 레포를 클론해서 받으면 바로 IDE에서도 오류 없이 사용하고 싶었다.

백준허브로 업로드되는 클래스 명(Main, Solution, …), 패키지 지정 안된 구조는 위에서 설정한 경로로 업로드 되었을때 오류가 발생한다.

> **※중요※**
> Java 코드 기준으로 작성했기 때문에 패키지 추가, 클래스명 수정을 진행한 것이다.
> 수정된 코드도 자바일때만 수정/추가 되도록 해뒀기 때문에 신경쓰지 않아도 된다.
{: .prompt-warning }


### 백준

**수정할 파일 경로 : `BaekjoonHub-1.2.8\scripts\baekjoon\parsing.js`**

`makeDetailMessageAndReadme` 메서드 내부 내용 추가

~~~javascript
/*
기존 구조 : 백준에서 업로드할 때 사용되는 코드 그대로 업로드 됨
클래스 이름 Main, 패키지 없음
*/
/*
수정 구조
  package BOJ.레벨.레벨랭크
  Main => BOJ_문제번호
  (예) package BOJ.bronze.bronze02
       class BOJ_1000
*/

let modifiedCode = code;

// Java 파일일 경우, 파일명에 맞춰 클래스명 변경
const extension = languages[language];
if (extension === 'java') {
  const newClassName = `BOJ_${problemId}`;
  modifiedCode = code.replace(
    /public\s+class\s+([A-Za-z_][A-Za-z0-9_]*)/,
    `public class ${newClassName}`
  );
}

// 패키지 추가
let finalCode = modifiedCode;
if (extension === 'java') {
  const packageName = `package BOJ.${tier}.${tierWithRank};`;
  finalCode = `${packageName}\n\n${modifiedCode}`;
}
~~~

### 프로그래머스

**수정할 파일 경로 : `BaekjoonHub-1.2.8\scripts\programmers\parsing.js`**

`makeData` 메서드 내부 내용 추가

프로그래머스는 조금 특별하다. `Solution` 클래스를 감싸는 실행용 `public` 클래스를 새로 만들어야 한다.

~~~javascript
/*
기존 구조
클래스 이름 Solution, 패키지 없음
*/
/*
수정 구조
public 클래스명 PRO_문제번호, 그 안에 main 메서드 추가
main 메서드 안에 Solution_문제번호 s = new Solution_문제번호(); 작성
프로그래머스에서 실행하는 Solution 클래스는 Solution_문제번호로 이름 변경
*/
let finalCode = code;

// Java 파일일 경우, 실행 가능한 main 클래스를 생성하고 기존 Solution 클래스를 래핑
if (language_extension === 'java') {
  const solutionClassName = `Solution_${problemId}`; // 내부 풀이 클래스 이름
  const mainClassName = `PRO_${problemId}`;          // 실행용 public 클래스 이름

  // 기존 코드의 'public class Solution'을 'class Solution_문제번호'로 변경
  const modifiedSolutionClass = code.replace(
    /public\s+class\s+([A-Za-z_][A-Za-z0-9_]*)/,
    `class ${solutionClassName}`
  );

  // main 메서드를 포함하는 새로운 public 클래스 생성
  const mainClass = `
    public class ${mainClassName} {
        public static void main(String[] args) {
            ${solutionClassName} s = new ${solutionClassName}();
            // 테스트케이스를 활용해 코드를 실행코드 작성하시오.
        }
    }
  `;

  // 패키지 선언문
  const packageName = `package PRO.Lv${level};`;

  // 최종 코드를 조합: 패키지 선언부 + 실행용 클래스 + 풀이 클래스
  finalCode = `${packageName}\n\n${mainClass}\n\n${modifiedSolutionClass}`;
}
~~~

### SWEA

**수정할 파일 경로 : `BaekjoonHub-1.2.8\scripts\swexpertacademy\parsing.js`**

`makeData` 메서드 내부 내용 추가

~~~javascript
/*
기존 구조 : SWEA에서 업로드할 때 사용되는 코드 그대로 업로드 됨
클래스 이름 Solution, 패키지 없음
*/
/*
수정 구조
  package SWEA.레벨
  Solution => SWEA_문제번호
  (예) package SWEA.D1
       class SWEA_1000
*/
let modifiedCode = code;

// Java 파일일 경우, 파일명에 맞춰 클래스명 변경
if (extension === 'java') {
  let newClassName = `SWEA_${problemId}`;
  modifiedCode = code.replace(
    /public\s+class\s+([A-Za-z_][A-Za-z0-9_]*)/,
    `public class ${newClassName}`
  );
}

// 패키지 추가
let finalCode = modifiedCode;
if (extension === 'java') {
  const packageName = `package SWEA.${level};`;
  finalCode = `${packageName}\n\n${modifiedCode}`;
}
~~~

---

여기까지가 코드 내부 수정이다!

클래스명과 패키지가 자동으로 추가되기 때문에, 레포를 클론해서 IDE에서 바로 열어도 오류 없이 사용할 수 있다.

다음 편에서는 **README 대신 PR을 자동 생성하는 방법**을 다루겠다.

📌 **다음 글:** [백준허브(BaekjoonHub) 커스텀 (4) - PR 자동화](/posts/baekjoonhub-custom-4/)
