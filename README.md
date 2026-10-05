# Prome

> 흩어져 있는 프롬프트를 한 곳에서


<img width="2545" height="1270" alt="image" src="https://github.com/user-attachments/assets/e724d4e3-4f33-4bc9-a03f-02d795bd64d5" />


<br>

## 📌 개요

| 항목 | 내용 |
|---|---|
| 프로젝트 | 한국외국어대학교 멋쟁이사자처럼 13기 팀 프로젝트 |
| 개발 기간 | 2025.09~2025.11 |
| 팀 구성 | Frontend 2명, Backend 4명 |
| 내 역할 | **Frontend** |

<br>

## 💡 서비스 소개

좋은 AI 프롬프트는 블로그, SNS, 커뮤니티에 흩어져 있어서 찾기 어렵습니다.
Prome는 사용자들이 프롬프트를 공유하고 평가하며, 원하는 프롬프트를 카테고리와 검색으로 빠르게 찾아 쓸 수 있는 프롬프트 커뮤니티입니다.
하나의 프롬프트를 ChatGPT, Gemini, Claude 각 모델에 맞게 확인할 수 있고, 티켓 시스템과 프리미엄 구독으로 서비스를 운영하는 구조까지 기획했습니다.

<!-- 서비스 기획 의도에 맞게 자유롭게 고쳐 주세요 -->

<br>

## ✨ 주요 기능

<!-- 기획서를 기준으로 정리했어요. 실제로 구현된 기능에 맞게 고쳐 주세요 -->

**회원**
- 일반 회원가입 : 아이디·닉네임 실시간 중복 검사, 비밀번호 유효성 안내
- 카카오 소셜 로그인
- 마이페이지 : 프로필 관리, 티켓 현황, 내가 쓴 글·댓글, 구독 관리

**프롬프트**
- 목록 조회 : 카테고리 필터, 정렬(최신순, 좋아요순, 조회순, 관련도순)
- 검색 : 헤더 검색창에서 키워드로 검색
- 상세 조회 : ChatGPT / Gemini / Claude 모델별 프롬프트 탭, 복사하기

**커뮤니티**
- 좋아요 / 싫어요 (싫어요가 일정 수 이상 누적되면 자동 블라인드)
- 댓글 작성, 조회, 댓글 좋아요
- 게시글·댓글 신고

**티켓 / 구독 모델**
- 블루 티켓, 그린 티켓을 매일 자동 충전
- 티켓 소진 시 안내 팝업과 구독 유도
- 광고 시청으로 티켓 충전
- 프리미엄 구독 : 티켓 제한 해제, 광고 제거, 북마크, 프리미엄 전용 콘텐츠

<br>

## 🖼 화면

<!-- 본인이 맡은 화면을 캡처해서 넣으세요 -->

<table>
  <tr>
    <td width="50%">
      <img src="https://github.com/user-attachments/assets/5040abe3-bce0-499b-aff9-640f32d95487" alt="메인" width="100%" />
      <br /><sub><b>메인</b></sub>
    </td>
    <td width="50%">
      <img src="https://github.com/user-attachments/assets/6b5d6a18-c614-4eeb-9705-ca8c14a1c72a" alt="상세" width="100%" />
      <br /><sub><b>요금제</b></sub>
    </td>
  </tr>
  <tr>
    <td width="50%">
      <img src="https://github.com/user-attachments/assets/e117f1e6-d882-4437-ae9c-0fe2ba41cbae" alt="{화면 이름}" width="100%" />
      <br /><sub><b>상세</b></sub>
    </td>
    <td width="50%">
      <img src="https://github.com/user-attachments/assets/0c9219ab-a52e-42f1-8917-5b5b7d4e6910" alt="{화면 이름}" width="100%" />
      <br /><sub><b>회원가입</b></sub>
    </td>
  </tr>
</table>
<br>

## 🛠 기술 스택

| 구분 | 사용 기술 |
|---|---|
| Frontend | React, Vite, JavaScript |
| 라우팅 / 통신 | React Router, Axios |
| 스타일링 | styled-components |
| 배포 | Vercel |
| 협업 | Git, GitHub, Notion |

<!-- package.json의 dependencies를 확인해서 쓰지 않는 항목은 지우고, 더 쓴 라이브러리는 추가하세요 -->

<br>

## 🏗 프로젝트 구조

```
src/
├── api/          # API 호출
├── app/          # 앱 설정
├── assets/       # 정적 자원
├── components/   # 공통 컴포넌트
├── features/
│   └── auth/     # 인증 기능
├── pages/        # 화면(페이지)
├── shared/
│   └── api/      # 공통 API 설정
├── App.jsx
└── main.jsx
```

<!-- 폴더 설명은 일반적인 구성 기준이에요. 실제 역할과 다르면 고쳐 주세요 -->

<br>

## 🔗 API 명세 요약

모든 API는 `/api/v1` 경로를 사용합니다.

| 분류 | 주요 엔드포인트 |
|---|---|
| 계정 | `POST /auth/signup`, `GET /auth/check-id`, `GET /auth/check-nickname`, `POST /auth/login`, `POST /auth/logout`, `GET /auth/kakao/callback` |
| 사용자 | `GET /users/me`, `PUT /users/me/profile`, `PUT /users/me/password`, `GET /users/me/posts`, `GET /users/me/comments`, `GET /users/me/subscription` |
| 프롬프트 | `GET /posts`, `GET /posts/premium`, `GET /posts/{postId}`, `POST /posts`, `GET /posts/search`, `PUT·DELETE /posts/{postId}` |
| 상호작용 | `POST /posts/{postId}/copy`, `POST /posts/{postId}/reaction`, `POST /posts/{postId}/bookmark`, `GET /users/me/bookmarks` |
| 댓글 | `GET·POST /posts/{postId}/comments`, `PUT·DELETE /comments/{commentId}`, `POST /comments/{commentId}/like` |
| 결제 / 광고 | `GET /ads`, `POST /ads/watch-reward`, `POST /payments/subscribe`, `GET /payments/products`, `POST /payments/cancel` |

<!-- API 명세는 계획 기준이라 실제 연동과 다를 수 있어요. 우선순위가 낮았던 카카오 로그인, 광고, 결제는 구현 여부를 확인해 주세요 -->

<br>

## 🙋 내가 한 일

Frontend 개발을 담당했습니다.

- 서버 API 연동 전체 담당 : Axios로 백엔드 API를 연동하고, 화면별 요청과 응답 처리를 구현
- 광고 시청 기능 구현 : 광고를 시청하면 티켓이 충전되는 기능을 구현하고 광고 관련 API 연동

<!-- 구체적으로 해결한 문제나 구현 포인트를 한두 줄 추가하면 훨씬 좋아요 -->

<br>
