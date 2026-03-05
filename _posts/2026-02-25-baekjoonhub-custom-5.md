---
title: "백준허브(BaekjoonHub) 커스텀 (5) - 수정 완료한 코드 연결"
date: 2026-03-05 16:00:00 +0900
categories: [Dev, Tools]
tags: [baekjoonhub, chrome-extension, github, 알고리즘]
image:
  path: /assets/images/baekjoonhub-custom/thumbnails/5.png
  alt: 백준허브 커스텀 (5) 썸네일
---

> 이전 글: [백준허브(BaekjoonHub) 커스텀 (4) - PR 자동화](/posts/baekjoonhub-custom-4/)

이전 편에서 README 대신 PR을 자동 생성하는 방법을 다뤘다.

이번 편에서는 **수정한 코드를 확장 프로그램으로 연결하는 방법**과 **커스텀 코드 공유**를 다룬다.

---

## 수정 완료한 코드 연결

> ※ 크롬이 아닌 엣지에서도 연결 가능

1. 확장 프로그램 관리에서 오른쪽 상단, **개발자 모드**를 켠다.

   ![개발자 모드 켜기](/assets/images/baekjoonhub-custom/image10.png)

2. **압축해제된 확장 프로그램 로드**

   ![압축해제된 확장프로그램 로드](/assets/images/baekjoonhub-custom/image11.png)

   개발자 모드를 켜면 이미지 처럼 **압축해제된 확장프로그램**을 로드할 수 있다.

   여기서 커스텀 시작 시 압축을 해제했던 경로의 폴더를 선택해주면 된다.

   이때, 프로그램의 루트 폴더인 `BaekjoonHub-1.2.8`을 선택한다.

   로드가 됐다면 아래와 같이 프로그램이 뜰 것 이다.

   ![확장프로그램 로드 완료](/assets/images/baekjoonhub-custom/image12.png)

3. 만약 로드 후 코드를 수정했다면!

   확장 프로그램을 삭제했다가 재업로드 할 필요 없이, 프로그램 **새로고침**만 해주면 된다.

4. 문제를 푼 후 아래와 같이 **초록색 체크 표시**가 뜬다면 제대로 연결된 것이다.

   ![초록색 체크 표시](/assets/images/baekjoonhub-custom/image13.png)

---

## 커스텀 코드 공유

별도의 수정 없이 내가 위에서 수정한 코드 그대로 이용하고 싶다면, 아래의 레포를 clone 하여 확장프로그램으로 로드하여 이용하길 바란다.

👉 [백준허브 커스텀 코드 공유](https://github.com/K-DaHee/BaekjoonHubCustom_for_Personal)

이렇게 하면 루트 폴더는 `BaekjoonHubCustom_for_Personal`이다.

---

다음 편부터는 개발 과정에서 마주친 **트러블슈팅 및 추가 개발 사항**을 다루겠다.
