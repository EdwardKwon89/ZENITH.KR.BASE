# GSD + ZEN_A4 + Claude Code + Ollama 통합 개발 방법론

> 1~5명 팀을 위한 최적화된 개발 워크플로우 가이드  
> **작성일:** 2026-04-08  
> **버전:** 1.0  
> **대상:** PJT_2026_010 및 유사 프로젝트

---

## 📋 목차

1. [Executive Summary](#executive-summary)
2. [방법론 소개](#방법론-소개)
3. [도구 소개](#도구-소개)
4. [통합 아키텍처](#통합-아키텍처)
5. [단계별 워크플로우](#단계별-워크플로우)
6. [실제 예시](#실제-예시)
7. [운영 가이드](#운영-가이드)
8. [체크리스트](#체크리스트)
9. [FAQ](#faq)

---

## Executive Summary

### 핵심 구성

```
┌────────────────────────────────────────┐
│  GSD + ZEN_A4 + Claude + Ollama        │
│  (통합 개발 프레임워크)                 │
└────────────────────────────────────────┘

설계 & 검증    →    자동화 검증    →    자동완성
Claude Code         ZEN_A4            Ollama
(Subscription)    (settings.json)    (로컬 무료)
```

### 기대 효과

| 지표 | 효과 |
|------|------|
| **개발 속도** | +50% (Ollama 자동완성) |
| **코드 품질** | Claude 수준 (자동 리뷰) |
| **팀 협업** | 명확함 (GSD 문서) |
| **비용** | Subscription만 (추가 비용 $0) |
| **자동화** | 80% 이상 (ZEN_A4) |

### 권장 대상

- ✅ 1~5명 팀
- ✅ 3개월 이상 프로젝트
- ✅ Claude Code Subscription 보유
- ✅ 로컬 개발 환경

---

## 방법론 소개

### 1️⃣ GSD (Goal-Driven Software Development)

#### 목적
"무엇을, 왜 하는가"의 명확성을 확보하고, 각 단계를 추적 가능하게 관리

#### 5단계 프로세스

```
Initialize (초기화)
    ↓
Discuss (논의)
    ↓
Plan (계획)  ← Claude Code 주도
    ↓
Execute (실행) ← Ollama + Claude 협력
    ↓
Verify (검증) ← Claude Code + ZEN_A4
```

#### 1~5명 팀용 경량화

| 단계 | 사용 여부 | 대상 |
|------|---------|------|
| Initialize | 선택 | 프로젝트 시작시만 |
| Discuss | 선택 | 팀 회의 있을 때만 |
| Plan | ✅ 필수 | 모든 복잡한 기능 |
| Execute | ✅ 필수 | 모든 개발 |
| Verify | ✅ 필수 | 모든 커밋 전 |

### 2️⃣ ZEN_A4 (A++++)

#### 목적
자동화된 코드 리뷰, 조건부 GSD 트리거, 품질 게이트

#### 3가지 훅 시스템

```
PreToolUse (코드 작성 전)
    ├─ 복잡한 기능 감지 → /gsd-plan-phase 자동 트리거
    ├─ 보안 코드 감지 → security-reviewer 자동 실행
    └─ 아키텍처 변경 감지 → architect 자동 실행

PostToolUse (코드 작성 후)
    ├─ 모든 코드 → code-reviewer 자동 리뷰
    ├─ 보안 관련 코드 → 자동 검증
    └─ 문서 파일 → 자동 품질 검증

Stop (커밋 전)
    ├─ 테스트 커버리지 확인
    ├─ Linting 검증
    ├─ 보안 스캔
    └─ 최종 품질 게이트
```

---

## 도구 소개

### 1️⃣ Claude Code (Subscription 기반)

#### 역할

```
설계 (Plan)
├─ /gsd-plan-phase로 상세 아키텍처 설계
├─ ARCHITECTURE.md 작성
└─ 기술 결정사항 문서화

검증 (Verify)
├─ @codebase "최종 검토해줄래?"
├─ 버그 & 성능 분석
└─ VERIFICATION.md 작성

상담 (Execute 중간)
├─ "이 로직이 맞는가?"
├─ "성능 최적화 방법은?"
└─ 복잡한 문제 해결

자동 리뷰 (ZEN_A4 백그라운드)
└─ PostToolUse 훅으로 자동 실행
```

#### 특징

- ✅ 무제한 사용 (Subscription 내)
- ✅ 응답 시간: 2-5초
- ✅ 컨텍스트: 200K 토큰
- ✅ 모델: Sonnet 4.6 또는 Opus 4.6
- ✅ 비용: 추가 비용 $0

#### 사용 시나리오

```
1. 기능 설계할 때
   → /gsd-plan-phase "기능명"

2. 아키텍처 결정할 때
   → /plan 또는 Claude Code에서 직접

3. 코드 검토할 때
   → VS Code에서 Cmd+K,C (Continue.dev)

4. 복잡한 문제 디버깅할 때
   → 채팅으로 "이 부분이 왜 오류나지?"
```

### 2️⃣ Ollama + Gemma4-9B (로컬 무료)

#### 역할

```
자동완성 (Tab키)
├─ 함수 구현체 자동 생성
├─ 타입 정보 자동 완성
└─ 반복 코드 패턴 인식

코드 초안 (Cmd+K로 선택)
├─ 파일 기본 구조 생성
├─ 함수 시그니처 자동 작성
└─ CRUD 작업 빠르게 작성

테스트 코드 생성
├─ 기본 테스트 구조 생성
├─ Mock 데이터 자동 작성
└─ 테스트 케이스 기본 생성
```

#### 특징

- ✅ 로컬 실행 (인터넷 불필요)
- ✅ 응답 시간: 0.5-2초 (극도로 빠름)
- ✅ 메모리: 3-4GB 사용
- ✅ 지연 없음 (즉각적)
- ✅ 비용: $0 (로컬)

#### 사용 시나리오

```
1. 함수 작성할 때
   함수 선언 후 Tab
   → Ollama가 함수 본체 자동 생성

2. 반복 패턴 작성할 때
   첫 번째 예시 작성 후 Tab
   → 같은 패턴 자동 반복

3. 테스트 코드 작성할 때
   describe() 작성 후 Tab
   → 테스트 케이스 자동 생성

4. 빠른 피드백 필요할 때
   → Ollama의 즉각적인 제안 활용
```

### 3️⃣ ZEN_A4 (설정 기반 자동화)

#### 역할

자동으로 코드 리뷰, 조건부 GSD 트리거, 품질 검증

#### 특징

- ✅ settings.json 기반
- ✅ 자동 실행 (수동 개입 없음)
- ✅ Claude Code 백그라운드에서 실행
- ✅ 비용: 포함됨 (추가 비용 $0)

---

## 통합 아키텍처

### 도구-방법론-역할 맵핑

```
┌──────────────────────────────────────────────────────┐
│ GSD 단계 → 주도 도구 → 지원 도구 → 자동화          │
├──────────────────────────────────────────────────────┤
│                                                      │
│ Plan → Claude Code → ARCHITECTURE.md → (선택적)    │
│        (/gsd-plan-phase)                            │
│                                                      │
│ Execute → Ollama → Claude Code → ZEN_A4 PostUse    │
│           (자동완성)  (상담)        (자동 리뷰)     │
│                                                      │
│ Verify → Claude Code → Tests → ZEN_A4 Stop         │
│          (@codebase)      (실행)   (품질 게이트)    │
│                                                      │
└──────────────────────────────────────────────────────┘
```

### 시간 배분

```
1 기능 개발 (평균 3시간)
├─ 설계 (Plan): 30분 - 1시간
│  └─ Claude Code: 30분 - 1시간
│
├─ 구현 (Execute): 1-2시간
│  ├─ Ollama 자동완성: 70% 시간 (매우 빠름)
│  ├─ 직접 코딩: 20% 시간 (로직만)
│  └─ Claude 상담: 10% 시간 (필요시)
│
└─ 검증 (Verify): 30분
   ├─ ZEN_A4 자동: 투명 (백그라운드)
   └─ Claude 최종 검증: 30분
```

### 비용 구조

```
월 비용:
├─ Claude Code Subscription: [기존 비용]
├─ Ollama: $0 (로컬)
├─ ZEN_A4: $0 (자동화)
└─ 총 추가 비용: $0

대비:
• API 기반: 월 $7-20
• 이 설정: 월 Subscription만
```

---

## 단계별 워크플로우

### Phase 1: 설계 (Plan) - 30분~1시간

#### 1-1. 기능 정의

```bash
# 작업: 새로운 기능 구현 결정
# 도구: 회의 또는 이슈 트래킹
# 산출물: 기능명, 요구사항

예시:
기능: "사용자 인증 시스템"
요구사항:
  ├─ JWT 기반 로그인
  ├─ Refresh Token 지원
  ├─ 2FA 선택적 지원
  └─ 세션 관리
```

#### 1-2. Claude Code로 설계

```bash
# 방법 1: /gsd-plan-phase 명령 (권장)
/gsd-plan-phase

프롬프트:
"PJT_2026_010에서 사용자 인증 시스템을 구현하려고 한다.
 JWT + Refresh Token 패턴으로 설계해줄래?
 아키텍처 다이어그램, 파일 구조, 핵심 인터페이스를 포함해줘."

# 방법 2: Continue.dev에서 직접
Cmd+K,C → 프롬프트 입력

Claude 산출물:
├─ 아키텍처 설계서
├─ 파일 구조
├─ 타입 정의 (TypeScript/Python 등)
├─ 핵심 함수 시그니처
└─ 테스트 전략
```

#### 1-3. 설계서 검토

```bash
# 방법 1: 자가 검증
@codebase "지금 만든 아키텍처에서
 성능 문제나 보안 이슈가 있을까?"

Claude 피드백:
✅ 아키텍처 평가
⚠️ 개선 필요 부분
💡 성능 최적화 제안

# 방법 2: 팀 리뷰 (있으면)
팀원과 설계서 논의
```

#### 1-4. 문서화

```bash
# 파일 작성
docs/ARCHITECTURE.md
├─ 아키텍처 다이어그램
├─ 기술 결정사항
├─ 구현 전략
└─ 테스트 계획

.planning/DECISIONS.md
├─ 왜 JWT를 선택했는가?
├─ 왜 Refresh Token이 필요한가?
├─ 보안 고려사항
└─ 성능 최적화 전략
```

---

### Phase 2: 구현 (Execute) - 1~3시간

#### 2-1. 초기 파일 구조 생성 (Claude)

```bash
# Claude Code에서 요청
"src/auth 폴더 구조를 만들어줄래?
 types.ts, service.ts, controller.ts, middleware.ts 파일을."

Claude 제공:
├─ src/auth/types.ts (인터페이스 & 타입)
├─ src/auth/service.ts (비즈니스 로직)
├─ src/auth/controller.ts (HTTP 핸들러)
├─ src/auth/middleware.ts (검증 미들웨어)
└─ tests/auth.test.ts (테스트 구조)
```

#### 2-2. 함수 구현 (Ollama 주도)

```bash
# VS Code에서 작업

Step 1: 함수 선언 작성
async register(email: string, password: string) {

Step 2: Tab 누르기
→ Ollama 자동완성 시작

Step 3: 제안 검토 및 선택
Ollama 제안:
  const hash = await bcrypt.hash(password, 10)
  await db.users.create({ email, hash })
  return { success: true }

Step 4: 수정 후 계속
다음 함수로 이동

반복: 모든 함수에 적용
```

#### 2-3. 자동 리뷰 (ZEN_A4 PostToolUse - 투명)

```bash
# 자동으로 실행됨 (수동 개입 불필요)

코드 저장 후:
1. code-reviewer 에이전트 자동 실행
   → 함수 길이, 에러 처리, 명명규칙 검증

2. security-reviewer 에이전트 자동 실행
   → 패스워드 저장 방식, 토큰 유출 위험 검증

3. 피드백 자동 적용
   → 문제 있으면 마크업으로 표시
```

#### 2-4. 복잡한 부분만 Claude 상담

```bash
# 필요할 때만 수동으로 Claude에 물어보기

예시 1: 복잡한 로직
"Token refresh 로직에서 race condition이 발생할 수 있을까?
 어떻게 방지하면 좋을까?"

Claude 답변:
✅ 문제 분석
✅ 해결 방법 (mutex, 원자성 등)
✅ 코드 예시

예시 2: 성능 이슈
"이 로직이 너무 느려. 어디서 병목이 나지?"

Claude 답변:
✅ 병목 지점 분석
✅ 최적화 방법
✅ 개선된 코드

이 작업은 전체의 10-20%만
```

#### 2-5. 테스트 작성 (Ollama)

```bash
# describe() 또는 test() 작성 후 Tab

describe("AuthService", () => {
  // Tab 누르기
  
Ollama 제안:
  it("should register user with valid credentials", () => {
    ...
  })
  
  it("should reject weak passwords", () => {
    ...
  })
  
  it("should hash password", () => {
    ...
  })
  
  // 추가로 필요한 테스트 자동 생성
```

---

### Phase 3: 검증 (Verify) - 30분

#### 3-1. 자동 품질 게이트 (ZEN_A4 Stop)

```bash
# 커밋 전에 자동으로 실행됨

확인 사항:
✓ 테스트 커버리지 (80% 이상)
✓ TypeScript 컴파일 (또는 언어별 빌드)
✓ Linting 검증 (ESLint 등)
✓ 보안 스캔 (hardcoded secrets 등)
✓ 문서 완성도 (JSDoc 등)

문제 있으면:
❌ 커밋 불가
→ 문제 해결 후 재시도
```

#### 3-2. Claude 최종 검증

```bash
# 자동 게이트 통과 후, Claude에 최종 검증 요청

@codebase "방금 만든 인증 기능을 검토해줄래?
 아키텍처, 보안, 성능, 테스트 관점에서"

Claude 분석:
✅ 아키텍처 준수 확인
├─ 설계 문서와 일치하는가?
├─ 의존성 순환이 없는가?
└─ 확장성은 좋은가?

⚠️ 보안 검증
├─ JWT 비밀키 관리는 안전한가?
├─ 토큰 만료 처리는 올바른가?
└─ CORS 설정은 필요한가?

💡 성능 최적화
├─ 데이터베이스 쿼리 최적화
├─ 캐싱 기회
└─ 토큰 검증 속도
```

#### 3-3. 피드백 반영

```bash
Claude 제안 사항 구현:
├─ 코드 개선
├─ 테스트 추가
└─ 문서 업데이트

반복:
모든 피드백이 해결될 때까지
```

#### 3-4. VERIFICATION.md 작성

```markdown
# 인증 시스템 검증 결과

## 목표 달성도
- ✅ JWT 기반 로그인: 100%
- ✅ Refresh Token: 100%
- ✅ 테스트 커버리지: 91%

## 성능 지표
- Token 검증: < 1ms
- Password 해싱: < 100ms
- Database 쿼리: < 50ms

## 보안 평가
- ✅ 암호 저장: bcrypt + salt
- ✅ 토큰 관리: 안전함
- ⚠️ CORS: 추가 설정 권장

## 위험도
- 총: Low
- 상태: Production Ready
```

#### 3-5. 커밋 & 병합

```bash
# Git 커밋
git add .
git commit -m "feat: Implement JWT authentication system

- JWT token generation and validation
- Refresh token mechanism
- Password hashing with bcrypt
- Auth middleware
- Comprehensive test coverage (91%)

Fixes: #123
Related: #456"

# PR 생성 및 병합
gh pr create --draft
# 리뷰 후 병합
```

---

## 실제 예시

### 시나리오: 사용자 인증 기능 (실전 예시)

#### Day 1 - 설계 (오전 1시간)

```
09:00 - 회의
└─ "인증 기능을 JWT로 구현하자"
   기술 결정: JWT + Refresh Token + Redis 세션

09:15 - Claude Code로 설계
/gsd-plan-phase "JWT 기반 인증 시스템"

Claude 산출물:
├─ docs/auth/ARCHITECTURE.md
│  ├─ 인증 흐름도 (ASCII 다이어그램)
│  ├─ 파일 구조
│  ├─ 핵심 타입 정의
│  ├─ 시큐리티 체크리스트
│  └─ 테스트 계획
│
└─ 아키텍처 검토 피드백
   ✅ 구조: 좋음
   ⚠️ CORS 설정 필요
   💡 Token 캐싱 권장

10:00 - 설계 문서 정리
.planning/DECISIONS.md에 기록:
└─ "JWT 선택 이유: Stateless, 확장성, 보안"
```

#### Day 1 - 구현 (오전 10시~오후 5시)

```
10:15 - 파일 구조 생성
Claude Code에서:
"src/auth 폴더와 필수 파일 만들어줄래?"

파일 생성:
├─ src/auth/types.ts
├─ src/auth/service.ts
├─ src/auth/controller.ts
├─ src/auth/middleware.ts
└─ tests/auth.test.ts

10:30 - 함수 구현 (반복)
Step 1: async register(email: string, password: string) {
Step 2: Tab 누르기
Step 3: Ollama 제안 확인
Step 4: 수정 및 진행

함수 목록:
├─ register() - 3분
├─ login() - 3분
├─ refreshToken() - 2분
├─ validateToken() - 2분
├─ logout() - 2분
└─ authMiddleware() - 2분

11:00 - ZEN_A4 자동 리뷰 (투명)
PostToolUse가 자동으로:
├─ code-reviewer 실행
└─ security-reviewer 실행

11:15 - 복잡한 부분 Claude 상담
"Token rotation 로직에서 race condition이 있을까?"

Claude 답변: "Mutex 패턴 적용 권장"
구현: 5분

12:00 - 테스트 코드 작성
describe("AuthService", () => { Tab
Ollama 자동완성:
├─ register 테스트 (3분)
├─ login 테스트 (3분)
├─ token rotation 테스트 (3분)
└─ error cases (2분)

13:00-14:00 - 추가 구현 및 개선

14:00 - 테스트 실행
npm test
결과: 87% 커버리지, 3개 실패

14:15-14:45 - 실패 테스트 디버깅
Claude에 물어보기:
"refreshToken에서 expireAt vs expiresIn 혼동"

Claude 분석: 변수 명명 문제
수정: 15분

14:45-15:00 - 재테스트
npm test → 모두 통과 ✓
Coverage: 91%

15:00 - 커밋 & 자동 검증
git add .
git commit ...

ZEN_A4 Stop Hook 자동 실행:
✓ Coverage: 91% (80% 초과)
✓ Linting: 통과
✓ Security: 통과
✓ Build: 성공
→ 커밋 성공
```

#### Day 2 - 검증 (오전 1시간)

```
09:00 - Claude 최종 검증
@codebase "인증 기능 전체 검토해줄래?"

Claude 분석 (5분):
✅ 아키텍처: 설계 준수 ✓
⚠️ CORS: 추가 설정 필요
💡 성능: Token 캐싱 권장

09:15 - 피드백 반영
├─ CORS 설정 추가 (5분)
├─ Redis 캐싱 구현 (10분)
└─ API 문서 업데이트 (5분)

09:40 - VERIFICATION.md 작성
├─ 목표 달성도: 100%
├─ 테스트: 91% 커버리지
├─ 성능: 우수
└─ 상태: Production Ready

10:00 - 최종 커밋 & PR
git push origin feature/auth
gh pr create --ready

팀원 검토 (또는 셀프)
→ 승인 & 병합
```

#### 결과

```
총 소요 시간: 약 2일 (16시간)
└─ 설계: 1시간
└─ 구현: 7시간 (Ollama 자동완성 덕분에 40% 단축)
└─ 테스트: 3시간
└─ 검증: 1시간
└─ 기타: 4시간

코드 품질: A+
└─ 커버리지: 91%
└─ 성능: 우수
└─ 보안: 우수

비용: $0 (Subscription 내)
```

---

## 운영 가이드

### 일일 작업 구조

```
아침 (설계)
  ├─ 오늘 작업할 기능 정의
  ├─ /gsd-plan-phase 실행
  └─ Claude와 설계 검토: 30~60분

낮 (구현)
  ├─ 파일 생성 (Claude)
  ├─ 함수 구현 (Ollama Tab 자동완성)
  ├─ 자동 리뷰 (ZEN_A4 자동)
  └─ 복잡한 부분만 Claude 상담: 4~5시간

오후 (검증)
  ├─ 테스트 코드 작성 (Ollama)
  ├─ 자동 품질 게이트 (ZEN_A4 Stop)
  ├─ Claude 최종 검증
  └─ 커밋: 1시간
```

### 주간 작업 구조

```
월요일: 주간 계획 & 설계
  ├─ .planning/CONTEXT.md 업데이트
  └─ 이주 목표 3-5개 선정

화~목: 일일 작업 반복
  ├─ 위의 일일 구조 반복
  └─ 매일 1-2개 기능 완성

금요일: 검증 & 정리
  ├─ 주간 산출물 검증
  ├─ .planning/DECISIONS.md 정리
  └─ 주간 회고 (있으면)
```

### 월간 작업 구조

```
초반 (1주): 마일스톤 계획
  ├─ /gsd-new-milestone (있으면)
  └─ .planning/CONTEXT.md 상세화

중반 (2-3주): 개발
  └─ 일일 + 주일 작업 반복

말기 (1주): 최종 검증 & 릴리즈
  ├─ 통합 검증
  ├─ 성능 테스트
  └─ Production 배포
```

### 체크리스트: 기능 구현

```
□ 설계 단계
  □ 기능 정의 완료
  □ /gsd-plan-phase 실행
  □ docs/ARCHITECTURE.md 작성
  □ .planning/DECISIONS.md 기록
  □ Claude 최종 검증

□ 구현 단계
  □ 파일 구조 생성 (Claude)
  □ 함수 구현 (Ollama 자동완성)
  □ ZEN_A4 자동 리뷰 확인
  □ 복잡한 부분 Claude 상담
  □ 테스트 코드 작성

□ 검증 단계
  □ npm test 모두 통과
  □ ZEN_A4 Stop 게이트 통과
  □ Claude 최종 검증
  □ VERIFICATION.md 작성
  □ Git 커밋
  □ PR 생성 & 승인 & 병합
```

---

## FAQ

### Q1: Ollama와 Claude를 언제 사용하나?

**A:** 
- **Ollama 사용**: 함수 구현, 반복 패턴, 테스트 기본 구조
  - 특징: 매우 빠름 (0.5-2초), 로컬에서 즉각적
  
- **Claude 사용**: 설계, 검증, 복잡한 문제
  - 특징: 더 정확함, 깊이 있는 분석

### Q2: ZEN_A4가 자동으로 GSD를 트리거한다고?

**A:** 
네. settings.json의 PreToolUse 훅에 설정되어 있습니다.
```
큰 파일 수정 감지 → /gsd-plan-phase 자동 실행
보안 코드 작성 → security-reviewer 자동 실행
```
수동으로 GSD를 실행할 필요가 없습니다.

### Q3: 1명 팀에도 GSD가 필요한가?

**A:** 
선택적입니다.
- 복잡한 기능: GSD Plan 필수
- 간단한 기능: GSD 생략 가능
- 버그 수정: GSD 생략

조건부 적용이 핵심입니다.

### Q4: Subscription이 없으면 어떻게 하나?

**A:**
Claude API를 직접 사용하거나 다른 LLM을 사용할 수 있습니다.
```
옵션 1: Anthropic API 직접 사용 (~$7/월)
옵션 2: 오픈소스 LLM만 사용 (Ollama + vLLM)
옵션 3: 다른 클라우드 LLM (GPT-4, Gemini)
```

### Q5: 팀이 5명이 되면?

**A:**
이 설정은 그대로 유지됩니다.
```
추가 변화:
├─ GSD 비중 증가 (30% → 50%)
├─ 팀 회의 시간 증가
├─ .planning/CONTEXT.md 상세화
└─ 주간 동기화 강화
```

### Q6: API 비용은 정말 안 드나?

**A:**
네, 다음을 사용하는 한:
```
비용 $0인 이유:
├─ Claude Code: Subscription (이미 있음)
├─ Ollama: 로컬 (무료)
├─ ZEN_A4: 설정 기반 (무료)
└─ 추가 API 호출: 없음
```

### Q7: Ollama 대신 vLLM을 사용하면?

**A:**
vLLM이 더 좋습니다:
```
vLLM 장점:
├─ 처리량: +200-400% (2-4배)
├─ 동시 요청: 3-5개
├─ 메모리 효율: PagedAttention

vLLM 단점:
├─ 설정 복잡도: 약간 높음
├─ Windows: Docker 필요
└─ 팀 환경: 추가 설정

권장: 팀이 3명 이상이면 vLLM 고려
```

### Q8: Sonnet과 Opus 중 어떤 걸 쓰나?

**A:**
Subscription에 포함되면 둘 다 사용하세요:
```
Sonnet 사용: 대부분의 작업 (80-90%)
├─ 설계
├─ 코드 검증
├─ 일반적인 상담

Opus 사용: 복잡한 문제 (10-20%)
├─ 극도로 복잡한 알고리즘
├─ 아키텍처 재설계
├─ 깊은 분석 필요시
```

### Q9: 이 방법론이 XP나 Scrum과 충돌하나?

**A:**
아니오. 오히려 보완합니다:
```
Scrum과의 관계:
├─ Sprint Planning → GSD Initialize/Plan
├─ Daily Standup → 진행 상황 공유
├─ Sprint Review → Verify 단계
└─ Retrospective → 프로세스 개선

XP와의 관계:
├─ Pair Programming → Claude Code와 협력
├─ TDD → Ollama로 테스트 자동화
└─ Continuous Integration → ZEN_A4로 자동화
```

---

## 체크리스트: 초기 설정

```
□ Claude Code
  □ Subscription 활성화 확인
  □ VS Code 또는 CLI 준비

□ Ollama
  □ 설치 완료
  □ Gemma4-9B 모델 다운로드
    ollama pull gemma4-9b
  □ 서비스 실행 확인
    ollama serve

□ Continue.dev (VS Code)
  □ 확장 설치
  □ Claude Code 연결
  □ Ollama 설정
    - apiBase: http://localhost:11434
    - model: gemma4-9b

□ ZEN_A4
  □ .claude/settings.json 검토
  □ 훅 활성화 확인
  □ 테스트 실행

□ 프로젝트
  □ .planning/ 폴더 생성
  □ CONTEXT.md 작성 (30줄)
  □ DECISIONS.md 초기화
  □ docs/ARCHITECTURE.md 템플릿 준비
  □ CLAUDE.md 업데이트

□ 팀 문서
  □ 이 가이드 모두에게 공유
  □ 초기 교육 (선택)
  □ 첫 기능은 함께 진행 (선택)
```

---

## 참고 자료

### 외부 링크

- [Claude Code 가이드](https://claude.ai/code)
- [Ollama 공식 사이트](https://ollama.ai)
- [Continue.dev 문서](https://continue.dev)
- [GSD 공식 문서](https://gsd.dev) (있으면)

### 프로젝트 내 문서

- [SMALL_TEAM_SETUP-EVALUATION.md](./SMALL_TEAM_SETUP-EVALUATION.md)
- [README.md](./README.md)
- [CLAUDE.md](../../CLAUDE.md)

---

## 최종 확인

이 가이드는:

✅ 1~5명 팀 최적화  
✅ 3개월 이상 프로젝트 대상  
✅ Claude Code Subscription 기반  
✅ 로컬 개발 환경 상정  
✅ 실전에서 검증된 워크플로우  

**다음 단계:**
1. 체크리스트의 초기 설정 완료
2. 첫 기능 구현 시 이 가이드 참조
3. 경험하면서 팀에 맞게 커스터마이징

---

**버전 히스토리**

| 버전 | 날짜 | 변경사항 |
|------|------|---------|
| 1.0 | 2026-04-08 | 초기 작성 |

**마지막 업데이트:** 2026-04-08  
**담당자:** Edward Kwon  
**라이선스:** 프로젝트 내부용
