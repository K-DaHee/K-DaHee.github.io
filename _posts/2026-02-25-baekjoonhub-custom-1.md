---
title: "백준허브(BaekjoonHub) 커스텀 (1) - 백준허브란? 설치 방법"
date: 2026-02-25 16:00:00 +0900
categories: [Dev, Tools]
tags: [baekjoonhub, chrome-extension, github, 알고리즘]
image:
  path: /assets/images/baekjoonhub-custom/thumbnails/1.png
  alt: 백준허브 커스텀 썸네일
---

## 목적

알고리즘 문제를 풀고 GitHub에 올리는 과정, 생각보다 번거롭다.

백준이나 프로그래머스 문제를 푼 뒤 수동으로 Commit하는 작업을 자주 잊어버렸고,

그런 날들이 쌓이다보니 어떤 문제를 안올렸는지 기억 안나게 되고,

결국 듬성듬성 비어가는 안쓰러운 나의 깃허브,,,

![진짜 말도 안돼.](/assets/images/baekjoonhub-custom/image1.png)
_진짜 말도 안돼._

이런 번거로움을 한번에 해결해주는 것이 바로 **백준 허브!!!**

정답 코드는 물론, 성능, 메모리, 문제 내용까지 알아서 커밋해줘서 관리하기 정말 편하지만

한 가지 아쉬웠던 점! **커밋되는 경로가 내가 기존에 올리던 Repository와 일치하지 않는다는 것**.

관련 정보를 찾아봤지만 생각보다 많지 않았고, 이왕 시작한 김에 원하는 대로 커스텀하기로 했다.

**이 글은 백준 허브를 커스터마이징 하고 싶은 분들을 위해 그 과정을 공유하고자 작성되었다.**

---

## 백준 허브?

백준, 프로그래머스, SWEA 같은 코딩 테스트 사이트에서 문제를 풀었을 때
**정답 코드를 자동으로 GitHub에 Commit 해주는 Chrome 확장 프로그램**이다.

### 설치

1. [**백준 허브**](https://chromewebstore.google.com/detail/%EB%B0%B1%EC%A4%80%ED%97%88%EB%B8%8Cbaekjoonhub/ccammcjdkpgjmcpijpahlehmapgmphmk?hl=ko) 링크를 통해 확장 프로그램을 설치한다.
2. 설치가 완료되면 브라우저 오른쪽 상단의 퍼즐 모양에서 확장 프로그램 확인 가능하다.

   ![확장 프로그램 확인](/assets/images/baekjoonhub-custom/image2.png)

3. 아이콘을 눌러 `Authenticate` 버튼을 통해 GitHub Repository와 연동.
   - 새로운 Repository를 생성하고 싶다면 Pick an Option에서 `Create a new Private Repository`
   - 이미 있는 Repository를 연결해 사용하고 싶다면 `Link an Existing Repository`를 선택하면 된다.

   ![연결 화면 1](/assets/images/baekjoonhub-custom/image3.png)

   ![연결 화면 2](/assets/images/baekjoonhub-custom/image4.png)

4. Repository가 연동되면 아래와 같은 화면이 된다.

   ![Repository 연동 완료](/assets/images/baekjoonhub-custom/image5.png)

이 과정을 마치면 백준, 프로그래머스, SWEA에서 문제를 맞췄을 경우,
설정한 Repository로 자동 업로드 된다.

---

다음 편에서는 백준허브의 **파일명, 경로, 커밋 메시지를 원하는 대로 커스텀하는 방법**을 다루겠다.

📌 **다음 글:** [백준허브(BaekjoonHub) 커스텀 (2) - 기본 커스텀](/posts/baekjoonhub-custom-2/)
