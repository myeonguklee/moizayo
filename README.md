# 모이자요 (Moizayo)

함께하는 모임으로 건강하고 활기찬 직장생활을 만들어보세요.

![모이자요 온보딩](https://github.com/user-attachments/assets/2394fe4d-37e4-48d1-9c17-8241fb5548a3)

배포 주소: https://moizayo.vercel.app

### [프로젝트 전체 리드미](https://github.com/FESI-10th-team6/moizayo)

## 목차

1. [프로젝트 소개](#-프로젝트-소개)

2. [개발 사항](#-개발-사항)
3. [Core Web Vitals 개선](#-Core-Web-Vitals-개선)
4. [API 아키텍처 설계 및 구축](#-API-아키텍처-설계-및-구축)
5. [개발 생산성 및 코드 품질 향상](#-개발-생산성-및-코드-품질-향상)
6. [글로벌 서비스를 위한 다국어 지원](-글로벌-서비스를-위한-다국어-지원)
7. [기술 스택](#-기술-스택)
8. [기술 상세 설명](#-기술-상세-설명)

## 📋 프로젝트 소개

**모이자요(Moizayo)** 는 직장인들을 위한 **모임 플랫폼**입니다.

### 🎯 주요 기능

- **모임 생성 및 관리**: 다양한 주제의 모임을 만들고 관리
- **모임 참여**: 관심 있는 모임에 참여하여 마음 힐링 및 소통
- **찜한 모임**: 마음에 드는 모임을 찜한 목록에 추가
- **리뷰**: 참여한 모임에 대한 후기 작성 및 공유
- **사용자 프로필**: 개인 정보 관리 및 참여/개설 모임 히스토리

### 🌟 핵심 가치

직장인들이 다양한 모임을 만들고 참여하여 더욱 풍요롭고 활기찬 직장생활을 할 수 있도록 돕습니다.

## 🖥️ 개발 사항

1. 메인 페이지 성능 최적화

- 웹 워커를 활용하여 메인 스레드 차단 없이 이미지 리사이징 및 webp 변환
- 이미지 리사이징으로 폼 전송 속도 개선, 2mb 이미지 기준 서버 저장 용량 90% 감소
- API 병렬 처리 및 번들 사이즈 최적화로 LCP 12% 개선, 메인 페이지 서버 응답 시간 30% 단축

2. 개발 생산성 및 코드 품질 향상

- Git husky, lint-staged 기반 커밋 단계 코드 검증으로 배포 오류 사전 방지
- Github actions CI/CD 파이프라인 구축으로 배포 자동화
- Frontend API 아키텍처 설계로 중앙화된 에러 처리, 에러 모니터링(sentry) 통합 관리
- 테스트 피라미드 전략에 따라 Jest, RTL을 이용한 단위 테스트, Cypress를 이용한 E2E 테스트 설계 및 테스트 자동화 구현

3. 사용자 포용성 확보

- next-intl을 활용한 다국어(i18n) 지원으로 언어적 제약 해소
- 'Switch to DOM Tree View' 를 활용하여 스크린 리더 호환성 개선
- 색상 대비 점검을 통해 저시력자를 위한 색상 대비와 텍스트 크기 조정
- 라이트 하우스 기준 접근성 86점 -> 96점, SEO 92점 -> 100점 개선

4. 모임 찾기(목록) 페이지, 마이 페이지 구현

<details>
<summary><strong>기능 gif</strong></summary>

|                                       필터링- 타입                                        |                                   필터링-지역/날짜/정렬                                   |
| :---------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: |
| ![Image](https://github.com/user-attachments/assets/3377c2a7-a3e3-425e-bef5-fb1d599bd89e) | ![Image](https://github.com/user-attachments/assets/cfcf53cf-29be-470a-a0a8-631e49e0d7d5) |

|                                        무한스크롤                                         |                                       모임생성하기                                        |
| :---------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: |
| ![Image](https://github.com/user-attachments/assets/743926bc-a305-4c28-a307-b34a498536bd) | ![Image](https://github.com/user-attachments/assets/620b2be8-0132-4d9f-b215-7d522b8fded7) |

|                                      마이페이지 조회                                      |                                        프로필 변경                                        |
| :---------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: |
| ![Image](https://github.com/user-attachments/assets/8870eca7-7ae8-4824-9c5a-c65d3a44bb74) | ![Image](https://github.com/user-attachments/assets/3b8f5944-37d4-48c3-86b9-da6ab668bfb6) |

|                                         리뷰 등록                                         |                                       모임생성하기                                        |
| :---------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: |
| ![Image](https://github.com/user-attachments/assets/8d568fc6-ff56-4364-8757-b76c9c9970b6) | ![Image](https://github.com/user-attachments/assets/620b2be8-0132-4d9f-b215-7d522b8fded7) |

</details>

<details>
<summary><strong>모바일</strong></summary>

|                                           온보딩                                           |                                           모임 찾기                                           |
| :----------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------: |
| ![온보딩](https://github.com/user-attachments/assets/e16f91f1-84ad-49c0-af7f-bcf6303f1f81) | ![모임 찾기](https://github.com/user-attachments/assets/2b0f967f-0fa2-419b-b8ce-87270b92a292) |

|                                           모임 만들기                                           |                                           모임 상세                                           |
| :---------------------------------------------------------------------------------------------: | :-------------------------------------------------------------------------------------------: |
| ![모임 만들기](https://github.com/user-attachments/assets/0763054d-646f-4e04-8140-79cc64ca50c1) | ![모임 상세](https://github.com/user-attachments/assets/3fc38fdd-2257-4b8e-b2ad-829b2e7ef9d1) |

|                                           모든 리뷰                                           |                                           마이 페이지                                           |
| :-------------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------------: |
| ![모든 리뷰](https://github.com/user-attachments/assets/80a9f69b-6417-4c1b-80ff-b4ac4b6a67b5) | ![마이 페이지](https://github.com/user-attachments/assets/5b0e15b8-c18f-4a4b-adde-10b85831b10d) |

|                                           로그인                                           |                                           회원가입                                           |
| :----------------------------------------------------------------------------------------: | :------------------------------------------------------------------------------------------: |
| ![로그인](https://github.com/user-attachments/assets/ea2e913a-8146-4339-9d7f-c3fbcf383caf) | ![회원가입](https://github.com/user-attachments/assets/9e670963-9cb1-40a4-a1b5-b40185f42682) |

</details>

## 🚀 Core Web Vitals 개선

|                                         초기 배포(7월 29일)                                          |                                         최근 배포(8월 11일)                                          |
| :--------------------------------------------------------------------------------------------------: | :--------------------------------------------------------------------------------------------------: |
| ![라이트하우스(전)](https://github.com/user-attachments/assets/79457f12-3069-4d5e-a88f-748ccc84fd56) | ![라이트하우스(후)](https://github.com/user-attachments/assets/b621fbcf-17bf-49ab-9114-60b8fb6b5c76) |

#### Performance 87점 -> 89점 (2점 상승)

- 웹워커를 활용하여 메인스레드 차단없이 이미지 리사이징 및 Webp 변환
- ~~가상화 적용~~ <- 렌더링 최적화에는 효과적이지만 복잡한 js구조로 Performance 점수 하락, 롤백 결정
  ![가상화](https://github.com/user-attachments/assets/b5dd70de-2236-4e99-9452-01655d0ad043)
- 번들 분석 결과 초기 로드에 포함된 react-day-picker 라이브러리 다이내믹 임포트
  ![번들분석](https://github.com/user-attachments/assets/4b2c17d9-76c7-4396-9edf-7dbd46f37f0b)
- `Promise.all()` 을 활용하여 api요청 병렬 처리

#### Accessibility 86점 -> 96점 (10점 상승)

- 개발자 도구의 'Switch to DOM Tree view' 기능을 활용
- 실제 스크린 리더 사용자 입장에서 콘텐츠의 계층 구조 개선
- 시맨틱 태그, ARIA 속성을 활용한 동적 콘텐츠 상태 전달 및 키보드 네비게이션 지원
- WCAG 기준 색상 대비율 점검 저시력자를 위한 충분한 색상 차이와 텍스트 크기 조정

#### SEO 92점 -> 100점 (8점 상승)

- 다국어 지원을 고려한 메타 데이터 및 Open Graph 설정
  ![open graph](https://github.com/user-attachments/assets/044ebdb7-cadf-41a2-b78f-4803564fe806)

- [사이트맵 설정](https://moizayo.vercel.app/sitemap.xml)과 robots.txt을 통한 검색 엔진 접근 최적화

## 📡 API 아키텍처 설계 및 구축

![API아키텍처](https://github.com/user-attachments/assets/0ae55fd8-ee97-42c0-a8ca-057df9b9b4ab)

### 중앙 집중식 API 에러 처리 시스템 설계

Axios Interceptor와 Tanstack Query의 전역 설정 기능을 통해 **모든 API 에러를 한 곳에서 체계적으로 관리**하는 시스템을 구축했습니다.

- Intercepter를 통해 **공통 에러**(네트워크, 타임아웃, 인증)에 대한 처리
- Intercepter에서 처리 되지 않은 에러를 API 에러를 커스텀 ApiError 클래스로 래핑하여 전파
- Production 환경일 경우 Sentry를 통한 에러 로깅
- Tanstack Query 전역 onError 핸들러를 통해 서버에서 받은 **사용자 친화적 에러 메세지**를 토스트 알림으로 안내

**개별 API 호출부의 에러 처리 코드 최소화**하여 개발 생산성을 향상시켰고, **사용자들에게 일관된 에러 피드백**을 제공할 수 있었습니다. 동시에, Tanstack query가 제공하는 유연한 오버라이딩 기능을 활용하여 특정 비지니스 로직에서는 개별적인 에러 처리가 가능하도록 확장성 높은 구조를 채택하였습니다.

### SSR/CSR 환경을 모두 고려한 통신 모듈 설계

- 서버에서는 요청마다 QueryClient 인스턴스 생성하여 사용자 간 **데이터가 공유되는 문제를 차단**
- 클라이언트에서는 useState를 통해 인스턴스가 한 번만 생성되도록 하여 상태를 안정적으로 유지
- React Query Hydration 패턴을 적용하여 서버에서 API를 통해 미리 가져온 데이터를 클라이언트에 안전하게 주입(Hydrate)
- 이를 통해 **클라이언트에서 불필요한 중복 API 호출을 방지**하고, **초기 페이지 로딩 속도를 향상**시켰습니다.
- 클라이언트 환경에서만 suspense, error boundary, toast 관련 옵션을 활성화하여 **하이드레이션 오류를 방지**

## ✅ 개발 생산성 및 코드 품질 향상

### 테스트 커버리지 전략

- Jest + React Testing Library를 활용한 단위 테스트
- Cypress E2E 테스트를 통한 사용자 시나리오 테스트

![테스트 피라미드](https://github.com/user-attachments/assets/c48d5c9d-8bc4-4d06-ab04-da1fd23ea3db)

### 테스트 자동화

#### pre-push 훅을 통한 품질 저하 방지

- Feature branch 에서 작업한 내용을 원격 저장소로 push 하기 전 유닛 테스트를 실행
- 코드 품질을 사전에 검증하고 테스트 실패 시 push를 차단
- **프로덕션 환경으로의 오류 코드 전파를 방지**

#### GitHub Actions를 통한 Pull Request시 테스트 실행

- PR 생성시 자동으로 유닛, E2E 테스트를 실행
- 팀원 간 코드 병합 시 생길 수 있는 **잠재적 문제를 최소화**

### E2E 테스트 도입 및 전략

실제 브라우저 환경에서 사용자 플로우를 검증하여 **유닛, 통합 테스트의 한계를 보완**하고자 하였습니다.

**테스트 비용 효율성을 고려**하여 서비스의 **핵심 비지니스 로직**인 모임 생성, 참여에 대한 E2E 테스트를 설계, 구현하였습니다. 이때 필요한 로그인 관련 테스트의 중복을 최소화 하였습니다.

- 모임 참여 : (비로그인) → 모임 참가 → 로그인 안내 → 로그인 → 모임 상세 페이지 → 모임 참가
- 모임 생성: 로그인 → 모임 생성 → 모임 관련 폼 작성 → 모임 생성 완료

폼 검증 및 에러 처리 등은 단위/통합 테스트로 위임하여 **테스트 피라미드 구조를 유지**했습니다. 또한 MSW를 활용한 API 응답 모킹으로 **서버 의존성을 제거**하고 **테스트 안정성을 확보**하였습니다.

### CI/CD

#### 코드 품질 관리
![로컬](https://github.com/user-attachments/assets/19653227-8338-4dd9-95a5-d37493511a28)
- Husky + lint-staged를 통한 커밋 전 코드 품질 검사
- ESLint, Prettier 자동 실행으로 배포 에러 사전 예방
- 일관된 코드 스타일과 규칙 강제

#### 자동화된 배포 파이프라인
![ci-cd](https://github.com/user-attachments/assets/38bf0c85-4600-4d2f-9411-f0d2eef347fb)
- GitHub Actions를 통한 자동화된 배포
- 코드 품질 검사 및 테스트 자동화
- Vercel을 통한 무중단 배포

## 🌎 글로벌 서비스를 위한 다국어 지원

![next-intl](https://github.com/user-attachments/assets/b5794bd1-f8a1-4f0e-b5a1-ec33168d73f2)

#### next-intl 라이브러리 선택 이유

- 타입 안정성
- app-router와 호환성
- 성능 최적화(트리 쉐이킹)

![다국어 지원](https://github.com/user-attachments/assets/d485c06f-cbb3-4f39-84e6-0cbfffbeed41)

#### SSR 환경에서의 동적 언어 전환 문제

- 초기 렌더링 이후 언어 변경 시 서버 컴포넌트들이 번역되지 않는 문제
- **해결**: URL params 기반 locale 전달로 서버 컴포넌트 번역 동기화 구현

#### 다국어 구현 과정에서의 시행착오와 개선

- 초기 설계: next-intl 최신 버전 공식문서의 권장대로 locale, message(번역 json) 자동 주입 방식으로 구성
- next-intl의 `useLocale()` 훅이 올바른 locale을 반환하지 않는 문제 발생
- **임시 해결**: `usePathname()`으로 URL에서 locale 추출하여 활용하는 안티패턴 사용
- 팀원들의 Next.js `Link`와 next-intl `Link` 혼용으로 라우팅 불일치 및 locale prefix 누락
- 코드 복잡성 증가와 유지보수성 저하 문제 인식
- **해결**: 다국어 지원 설정 전면 점검 및 구조 개선 [(관련 PR)](https://github.com/FESI-10th-team6/moizayo/pull/80), locale, message 직접 주입 설정으로 변경하여 locale context 문제 해결
- next-intl의 `Link` 및 `useLocale()` 사용으로 컴포넌트 통일
- 불필요한 안티패턴 제거 및 코드 간소화 일관된 다국어 지원 패턴 유지

#### 구조화된 번역 파일 관리

- `ui`, `pages` 등 도메인별 번역 키 분리로 네임스페이스 기반 선택적 사용 및 로드
- 431개의 번역 키를 계층적 구조로 관리하여 유지보수성 향상(ko.json, en.json)

<details>
<summary><strong>다국어 지원 구현 사항</strong></summary>

|                                          랜딩-en                                          |                                          랜딩-ko                                          |
| :---------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: |
| ![Image](https://github.com/user-attachments/assets/c82ea5c9-0ab1-4f63-aa62-a2e47c95f27e) | ![Image](https://github.com/user-attachments/assets/5b1b4047-4fd0-4370-9be5-6826609ec593) |

|                                        회원가입-en                                        |                                        회원가입-ko                                        |
| :---------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: |
| ![Image](https://github.com/user-attachments/assets/fa9987dc-b54f-49a9-b58a-95a2e7c8c672) | ![Image](https://github.com/user-attachments/assets/bf1fc3de-27df-4a63-98c6-39ae6e5f2337) |

|                                     회원가입-에러-en                                      |                                     회원가입-에러-ko                                      |
| :---------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: |
| ![Image](https://github.com/user-attachments/assets/9c887d31-1d23-4c0a-a9a0-47178bcc8ce5) | ![Image](https://github.com/user-attachments/assets/12bdaf42-7349-490b-9c66-b08bc07e443a) |

|                                         로그인-en                                         |                                         로그인-ko                                         |
| :---------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: |
| ![Image](https://github.com/user-attachments/assets/92f197d6-7266-4a9e-a84d-f5330ae39316) | ![Image](https://github.com/user-attachments/assets/cb4820be-5a70-4d2d-a9b7-5b12d82374b7) |

|                                        모임찾기-en                                        |                                        모임찾기-ko                                        |
| :---------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: |
| ![Image](https://github.com/user-attachments/assets/72b0ab25-2efd-4496-9835-979ec5c08d67) | ![Image](https://github.com/user-attachments/assets/af2f0c54-4d12-42bd-8de1-15dc2b0d4f65) |

|                                       모임만들기-en                                       |                                       모임만들기-ko                                       |
| :---------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: |
| ![Image](https://github.com/user-attachments/assets/95f1e721-b9f9-4047-b51a-c0584b938dad) | ![Image](https://github.com/user-attachments/assets/6c1e7854-5a1b-407d-a539-6115a1281b6c) |

|                                    모임만들기-에러-en                                     |                                    모임만들기-에러-ko                                     |
| :---------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: |
| ![Image](https://github.com/user-attachments/assets/44656d94-d48d-4b2e-8b0e-d14f07b22454) | ![Image](https://github.com/user-attachments/assets/8decfbb1-2b23-4935-9fa0-f9ea0cd1458d) |

|                                        모임상세-en                                        |                                        모임상세-ko                                        |
| :---------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: |
| ![Image](https://github.com/user-attachments/assets/d14568e5-fb98-442a-b967-4869b674a84f) | ![Image](https://github.com/user-attachments/assets/1cb1a95a-714b-4dbc-bbf4-e9be147d7fe1) |

|                                        모든리뷰-en                                        |                                        모든리뷰-ko                                        |
| :---------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: |
| ![Image](https://github.com/user-attachments/assets/081d513a-e9e3-489d-9fae-59382dbd1efb) | ![Image](https://github.com/user-attachments/assets/8976be00-4925-4890-871a-4c731bf6e2c2) |

|                                       마이페이지-en                                       |                                       마이페이지-ko                                       |
| :---------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: |
| ![Image](https://github.com/user-attachments/assets/9151bc01-9371-4e75-9dfe-41cc41c28a77) | ![Image](https://github.com/user-attachments/assets/a9544c5a-eebf-4687-b4e3-dee13b08e065) |

|                                    모바일-모임찾기-en                                     |                                    모바일-모임찾기-ko                                     |                                   모바일-마이페이지-en                                    |                                   모바일-마이페이지-ko                                    |
| :---------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: | :---------------------------------------------------------------------------------------: |
| ![Image](https://github.com/user-attachments/assets/5b056ae3-af93-45f4-9675-3889a535d76e) | ![Image](https://github.com/user-attachments/assets/1f15ae27-bdb9-45cd-97d7-4b45b2280f4a) | ![Image](https://github.com/user-attachments/assets/aad6fa71-315a-4772-9eea-6efc8f3db5f0) | ![Image](https://github.com/user-attachments/assets/ca2b9af9-8f12-4be6-b12c-a18e2b8403f5) |

</details>

## 🛠 기술 스택

### Frontend

- **Framework**: Next.js 15.3.5 (App Router)
- **Language**: TypeScript 5
- **Styling**: Tailwind CSS 4
- **State Management**: TanStack React Query 5.81.5
- **Authentication**: Next Auth 4.24.11
- **Form**: React Hook Form 7.59.0 + Zod 3.25.73
- **UI Components**: Storybook 9.0.15 + 디자인 시스템 지향적인 컴포넌트
- **Internationalization**: next-intl 4.3.4 (다국어 지원)
- **Image Optimization**: Next.js Image 컴포넌트 + 웹워커 활용한 이미지 리사이징

### Development Tools

- **Pakage Manager**: pnpm
- **Node.js**: 22.16.0
- **Linting & Formatting**: ESLint 9 + Prettier 3.6.2
- **Testing**: Jest 30.0.4 + React Testing Library 16.3.0 + MSW 2.10.3 (API Mocking)
- **Git Hooks**: Husky 9.1.7 + lint-staged 16.1.2
- **Commit Convention**: Commitlint 19.8.1 (Conventional Commits)
- **Type Checking**: TypeScript 5 strict mode
- **Code Quality**: ESLint rules + Prettier formatting

### Architecture & Patterns

- **Feature-Sliced Design (FSD)**: 도메인 중심의 폴더 구조
- **Component Architecture**: 재사용 가능한 UI 컴포넌트 설계
- **Error Handling**: 전역 에러 바운더리 및 사용자 친화적 에러 처리(토스트 메시지)

## 🛠 기술 상세 설명

<details>
<summary><strong>📦 pnpm 패키지 매니저</strong></summary>

![pnpm](https://github.com/user-attachments/assets/7ba2d0be-1372-4420-a2f1-b941bf72de8e)

#### 테스트 결과(모이자요 프로젝트, 의존성 수: 1,405 패키지)

|                                          설치 시간                                           |                                          디스크 사용량                                           |
| :------------------------------------------------------------------------------------------: | :----------------------------------------------------------------------------------------------: |
| ![설치시간](https://github.com/user-attachments/assets/6a768366-2bd3-4621-9a7f-433ddb7cbfce) | ![디스크사용량](https://github.com/user-attachments/assets/e1267e61-df1d-4921-92d9-1dc96b86d8d3) |

#### pnpm의 장점

- 빠른 설치: npm 대비 2.4배 빠름
- 효율적인 공간 사용: yarn 대비 79MB 절약
- 안정성: 스트릭트 의존성 관리

#### pnpm의 단점

- 호환성 이슈: 일부 레거시 패키지에서 symlink 관련 문제 발생 가능
- 생태계: npm/yarn 대비 상대적으로 작은 커뮤니티

=> 프로젝트 규모가 커질수록 속도와 공간 측면에서 장점이 더 커질 것이라고 예상

</details>

<details>
<summary><strong>📚 Feature-Sliced Design (FSD)</strong></summary>

![fsd](https://github.com/user-attachments/assets/4955916f-cdbd-4f65-9593-aea68e66be2c)

#### 도입 배경

- 프로젝트 기획 단계에서 **기능 확장성**과 **팀원 4명의 동시 작업 효율성**을 고려해, 적절한 아키텍처의 필요성을 느낌
- 기존의 단순 컴포넌트 폴더 구조는 프로젝트 규모가 커질수록 **의존성 얽힘**과 **유지보수 어려움**을 유발할 가능성이 있음

=> **도메인 중심 설계**와 **관심사 분리**를 체계적으로 적용할 수 있는 `Feature-Sliced Design(FSD)` 아키텍처를 **초기부터 도입**

⚡ **핵심 원칙 — 단방향 의존성**

> 상위 레이어는 하위 레이어에만 의존할 수 있다.  
> 이를 통해 코드 흐름이 예측 가능해지고, 의도치 않은 사이드 이펙트를 원천 차단.

```plaintext
app → entities → features → widgets → shared
```

#### FSD 도입을 통해 얻은 효과

- **개발 생산성 향상 및 병렬 작업 용이성**
  ```plaintext
  entities/
    ├─ gathering/   # 모임 페이지 관련
    └─ user/        # 로그인·회원가입 관련
  ```
  **`entities/gathering`** 와 **`entities/user`** 는 서로 다른 **슬라이스(slice)** 에 속함 <br>
  **각 슬라이스는 기능별로 완전히 독립**되어 있어, 팀원들이 **각자 맡은 기능에 집중** 가능 <br>
  → `코드 충돌(merge conflict) 최소화 및 개발 속도 향상`
- **유지보수 비용 감소 및 높은 응집도**<br>
  변경이 필요할 경우 해당 도메인 폴더만 확인하면 됨 <br>
  관련된 UI·API 호출·상태 로직이 하나의 슬라이스에 모여 있어 변경 범위 예측이 명확하고,
  그 결과 유지보수 비용 감소

</details>

<details>
<summary><strong>📁 프로젝트 구조</strong></summary>
  
```
📦src/
├── 📂app/                    # Next.js App Router
│   ├── 📂[locale]/          # 다국어 지원 (한국어/영어)
│   │   ├── 📂(auth)/        # 인증 관련 페이지 (signin, signup)
│   │   ├── 📂gathering/     # 모임 관련 페이지
│   │   ├── 📂favorites/     # 찜한 모임 페이지
│   │   ├── 📂reviews/       # 리뷰 페이지
│   │   ├── 📂my-page/       # 마이페이지 (프로필, 참여/개설 모임, 리뷰)
│   │   └── 📜layout.tsx     # 로케일별 레이아웃
│   ├── 📂api/               # API 라우트 (NextAuth 등)
│   ├── 📂fonts/             # 폰트 설정 (Pretendard)
│   ├── 📜global-error.tsx   # 전역 에러 처리
│   ├── 📜not-found.tsx      # 404 페이지
│   ├── 📜providers.tsx      # React Query, NextAuth 등 프로바이더
│   └── 📜layout.tsx         # 루트 레이아웃
├── 📂entities/              # 도메인 엔티티 (비즈니스 모델)
│   ├── 📂gathering/         # 모임 엔티티 (생성, 수정, 삭제)
│   ├── 📂gathering-detail/  # 모임 상세 정보 엔티티
│   ├── 📂participant/       # 참여자 엔티티
│   ├── 📂review/            # 리뷰 엔티티
│   ├── 📂favorites/         # 찜한 모임 엔티티
│   ├── 📂auth/              # 인증 엔티티
│   └── 📂user/              # 사용자 엔티티
├── 📂features/              # 비즈니스 기능 (사용자 시나리오)
│   ├── 📂gathering/         # 모임 관련 기능 (생성, 수정, 삭제)
│   ├── 📂signin/            # 로그인 기능
│   ├── 📂signup/            # 회원가입 기능
│   ├── 📂favorites/         # 찜한 모임 관리 기능
│   ├── 📂review/            # 리뷰 작성/관리 기능
│   ├── 📂my-page/           # 마이페이지 기능
│   └── 📂filters/           # 필터링 기능
├── 📂widgets/               # UI 위젯 (페이지 구성 요소)
│   ├── 📂Header/            # 헤더 위젯
│   ├── 📂GatheringCard/     # 모임 카드 위젯
│   ├── 📂GatheringList/     # 모임 목록 위젯
│   ├── 📂ReviewList/        # 리뷰 목록 위젯
│   ├── 📂AuthForm/          # 인증 폼 위젯
│   ├── 📂MyPageSkeleton/    # 마이페이지 스켈레톤
│   ├── 📂FavoritesSkeleton/ # 찜한 모임 스켈레톤
│   ├── 📂ContainerInformation/ # 컨테이너 정보 위젯
│   ├── 📂BottomFloatingBar/ # 하단 플로팅 바
│   └── 📂AllReviewRating/   # 전체 리뷰 평점 위젯
├── 📂shared/                # 공유 리소스
│   ├── 📂api/               # API 관련 (HTTP 클라이언트, React Query)
│   ├── 📂config/            # 설정 (라우트, API 엔드포인트)
│   ├── 📂lib/               # 유틸리티 라이브러리 (날짜, 이미지, 테스트 등)
│   ├── 📂hooks/             # 커스텀 훅
│   ├── 📂types/             # 공통 타입 정의
│   └── 📂ui/                # 공통 UI 컴포넌트 (Button, Input, Modal 등)
├── 📂i18n/                  # 국제화 설정
└── 📂messages/              # 다국어 메시지 (ko.json, en.json)
```
  
</details>

<details>
<summary><strong>🎨 디자인 시스템 + 스토리북</strong></summary>

### 📖 스토리북

![스토리북](https://user-images.githubusercontent.com/263385/199832481-bbbf5961-6a26-481d-8224-51258cce9b33.png)

#### 도입 이유

- 특정 상태에 따른 다양한 공통컴포넌트 UI를 자동으로 문서화하여 개발 환경을 개선
- 프로젝트 전반에 걸쳐 일관된 디자인 시스템 구축 및 유지

#### 적용 범위

- FSD 구조 중 `shared/ui` 디렉토리에 포함된 **공통 UI 컴포넌트**를 대상으로 스토리 작성
- Button, Input, Modal 등 **여러 페이지에서 재사용되는 UI 요소** 위주로 문서화
- 각 컴포넌트는 **props**에 따른 상태 변화를 시각적으로 확인할 수 있도록 `args`와 `controls`를 구성

#### Storybook 도입으로 얻은 이점

- 공통 컴포넌트의 디자인과 상태를 빠르게 확인하고 사용법을 쉽게 제공하여 개발 속도 향상
- 의존성을 제거한 독립적인 컴포넌트를 설계 및 구현

![스토리북사용](https://github.com/user-attachments/assets/6dad6f12-b15e-4568-a884-b1a94ebe2821)

### 🎨 디자인 토큰 (Style Dictionary + Tokens Studio + Tailwind)

#### 목적(Use-case)

- 디자이너(Figma) ↔ 개발자(코드) 간 공통 언어 확립
- 팀/레포 전반의 스타일 수치의 단일 출처(SSOT) 유지

#### 스택 개요

- Tokens Studio(Figma): 디자인 소스의 변수/토큰 관리·내보내기
- Style Dictionary v5: 토큰 변환·빌드 파이프라인(플랫폼별 산출물 생성)
- Node.js 스크립트: 사전/사후 처리(검증, 정렬, 포맷)
- Tailwind(유틸리티): CSS 변수와 함께 사용하는 런타임 프레임워크

#### 디렉토리 구조(예시)

```
src
├─ app/
│   ├─ _variables.css      # Style Dictionary가 생성 (CSS Custom Properties)
│   └─ global.css          # Tailwind 엔트리, variables import
├─ designTokens.json       # Tokens Studio에서 자동 push되는 원천(SSOT)
├─ style-dictionary.config.json # 빌드 파이프라인 설정
└─ package.json             # 스크립트
```

#### 사용 방법

1. 디자이너

- Figma의 Tokens Studio에서 팀 규칙(네이밍/그룹)을 지켜 변수 편집

- Export 자동화가 저장소로 push → tokens/designTokens.json 갱신

2. 개발자

- 토큰 빌드

```bash
# 토큰 빌드
pnpm style:tokens
```

- 사용: Tailwind 엔트리(global.css)에서 variables를 import 후 클래스/임의값으로 사용

```ts
/* src/app/global.css */
@import './_variables.css'; /* Style Dictionary 산출물: CSS 변수들 */

// _variables.css 의 css 변수들 사용 가능
```

협업용 디자인 토큰. Tailwind v4의 @theme 영역을 사용해 브레이크포인트와 z-index 레이어를 단일 출처(SSOT)로 관리함.

```
/* global.css (발췌) */
@theme {
  /* Breakpoints */
  --breakpoint-mobile: 23.4375rem;  /* 375px */
  --breakpoint-tablet: 46.5rem;     /* 744px */
  --breakpoint-web: 75rem;          /* 1200px */
  --breakpoint-desktop: 120rem;     /* 1920px */

  /* Z-index 레이어(의미 토큰) */
  --z-base: 0;
  --z-dropdown: 100;
  --z-sticky: 200;
  --z-backdrop: 300;
  --z-modal: 400;
  --z-drawer: 450;
  --z-toast: 500;
  --z-tooltip: 600;
}

```

> 반응형 기준·레이어링 정책처럼 “디자인 결정을 수치로 표준화한 값 전부”가 토큰의 범주에 들어갑니다.
> 다만 이 문서의 토큰은 **개발 협업 중심(런타임 토큰)**입니다.

#### 사용 목적

- 일관성: 팀 전체가 동일한 레이어/브레이크포인트를 사용합니다.
- 가시성: 숫자 하드코딩 대신 의미 이름으로 의도를 드러냅니다.
- 유연성: 재정렬·값 변경 시 토큰만 바꾸면 대규모 수정이 안전합니다.

#### 운영원칙

1. 브레이크포인트
   이름은 디바이스 가설(mobile/tablet/web/desktop)로 두되, 실제 기준은 콘텐츠 기반으로 기획합니다.
   - Tailwind 반응형 프리픽스(mobile:, tablet:, web:, desktop:)와 연동

2. Z-Index
   숫자 직접 사용 금지. 의미 토큰만 사용합니다.

- 숫자 z-index가 가끔 필요한데요?
  - 허용하지 않습니다. 새로운 구간이 필요하면 예약 스케일에 슬롯을 추가하고 의미 토큰을 함께 정의하세요.
  </details>

<details>
<summary><strong>📝 유닛 테스트</strong></summary>

![유닛테스트](https://github.com/user-attachments/assets/86567307-26cf-48a1-a07f-dea7e54c480d)

#### 테스트 커버리지

- **Entity, Feature, Shared 레이어 중심의 jest, rtl 활용한 유닛 테스트**
- **Statements**: 91.03% (1,330/1,461)
- **Branches**: 82.39% (543/659)
- **Functions**: 83.58% (275/329)
- **Lines**: 92.68% (1,178/1,271)

#### 테스트를 통해 얻은 이점

- **리팩토링 안정성**: 코드 리팩토링 시 기존 기능 보장
- **엣지케이스 발견**: 예외 상황 및 경계값 처리 개선
- **코드 품질 향상**: 컴포넌트, 의존성 분리하여 재사용 가능한 코드 작성

</details>
