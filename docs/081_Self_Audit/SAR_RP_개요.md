# Self_Audit_Report (SAR) 작성 규칙

> **문서 목적:** Self Check & Self Test 단계에서 발견된 오류 및 수정 사항을 체계적으로 기록하고 관리하는 규칙

**버전:** 1.0  
**작성일:** 2026-04-08  
**작성자:** PJT_2026_010 팀

---

## 📋 목차

1. [개요](#개요)
2. [SAR 작성 시기](#sar-작성-시기)
3. [SAR 파일 구조](#sar-파일-구조)
4. [메타정보 작성 규칙](#메타정보-작성-규칙)
5. [본문 작성 규칙](#본문-작성-규칙)
6. [개정 이력 기록](#개정-이력-기록)
7. [파일 명명 규칙](#파일-명명-규칙)
8. [예시](#예시)

---

## 개요

### 정의

**Self_Audit_Report (SAR):**
- Self Check 또는 Self Test 단계에서 발견된 오류/결함을 기록하는 감사 보고서
- 오류의 현상, 원인, 조치 방법을 상세히 문서화
- 동일 오류의 재발 방지를 위한 Check List 업데이트 트리거

### 목표

```
1. 오류 추적성: 모든 오류가 기록되고 추적 가능
2. 재발 방지: 동일 오류가 다시 발생하지 않도록 개선
3. 팀 학습: 오류 경험을 팀 전체가 학습
4. 프로세스 개선: Check List 지속적 개선
```

### 대상

```
✅ SAR 작성 대상:
  ├─ Self Check에서 "미통과" 항목 발견
  ├─ Self Test에서 테스트 실패 발견
  ├─ 커버리지 부족 (80% 미달)
  ├─ 보안 검증 실패
  └─ ZEN_A4 자동 리뷰 오류

❌ SAR 불필요:
  ├─ 설계 재검토만 필요한 경우 (SAR 대신 설계 수정)
  ├─ 단순 오타 (커밋 메시지에만 기록)
  └─ 경미한 스타일 이슈
```

---

## SAR 작성 시기

### Timeline

```
Step 1: 오류 발견
  └─ Self Check/Self Test 수행 중

Step 2: 즉시 기록
  └─ 오류 발생 직후 SAR 작성 시작

Step 3: 조치 수행
  └─ 코드 수정, 테스트 재실행

Step 4: SAR 완성 및 Check List 업데이트
  └─ 오류 조치 완료 후 SAR 최종 작성

Step 5: Check List 업데이트
  └─ 동일 오류 재발 방지를 위한 체크 항목 추가
```

### 예시 Timeline

```
14:00 - Self Test 실행
        npm test → 3개 테스트 실패

14:05 - 오류 분석
        "refreshToken() 함수에서 null reference error"
        → SAR 생성 시작

14:15 - 원인 분석
        "토큰 만료 시간 초과 후 접근 시 null 체크 누락"

14:30 - 코드 수정 및 테스트
        null 체크 추가 → npm test 재실행 → 통과

14:45 - SAR 최종 작성
        현상, 원인, 조치 상세 기록

15:00 - Check List 업데이트
        "토큰 만료 후 상태 확인" 체크 항목 추가
```

---

## SAR 파일 구조

### 디렉토리 구조

```
docs/081_Self_Audit/
├─ SAR_RP_개요.md (이 파일)
├─ 000_SAR_README.md (SAR 인덱스)
│
└─ SAR_reports/
   ├─ SAR_2026-04-08_001_RefreshToken_NullReference.md
   ├─ SAR_2026-04-09_002_PasswordValidation_EdgeCase.md
   ├─ SAR_2026-04-10_003_DatabaseQuery_Performance.md
   └─ ... (시간순 저장)
```

### 파일 명명 규칙

```
SAR_YYYY-MM-DD_NNN_문제_분류.md

예시:
SAR_2026-04-08_001_RefreshToken_NullReference.md
    └─ 날짜: 2026-04-08
    └─ 번호: 001 (일일 번호, 001부터 시작)
    └─ 문제: RefreshToken (오류 관련 기능)
    └─ 분류: NullReference (오류 유형)
```

### 파일 구성

```
SAR 파일 (1개 오류 = 1개 파일)
├─ 메타정보 섹션 (상단)
│  ├─ 버전
│  ├─ 작성일 / 수정일
│  ├─ 작성자 / 수정자
│  └─ 개요
│
├─ 본문 섹션 (중간)
│  ├─ 1. 현상 (What)
│  ├─ 2. 원인 (Why)
│  ├─ 3. 조치 (How)
│  ├─ 4. 검증 (Verification)
│  └─ 5. 예방 (Prevention)
│
└─ 개정 이력 섹션 (하단)
   ├─ 2026-04-08 (작성)
   ├─ 2026-04-09 (수정)
   └─ ...
```

---

## 메타정보 작성 규칙

### 메타정보 템플릿

```markdown
# SAR-2026-04-08-001: RefreshToken 함수 NullReference 오류

**버전:** 1.0  
**작성일:** 2026-04-08 14:45  
**수정일:** -  
**작성자:** Edward Kwon  
**수정자:** -  

## 개요

| 항목 | 내용 |
| --- | --- |
| **현상** | Self Test 수행 시 refreshToken() 함수에서 null reference 오류 발생 |
| **원인** | 토큰 만료 시간 초과 후 접근 시 null 체크 누락 |
| **조치** | null 체크 추가 + 테스트 케이스 추가 |
| **영향도** | 높음 (로그인 기능 핵심) |
| **상태** | ✅ 해결 (2026-04-08 14:45) |
```

### 각 필드 설명

```
버전: 문서 버전
  초판: 1.0
  수정: 1.1, 1.2, ... (마이너 변경)
  대개정: 2.0, 3.0, ... (주요 변경)

작성일: 첫 작성 날짜 (변경 금지)
  형식: YYYY-MM-DD HH:MM

수정일: 최종 수정 날짜 (수정할 때마다 업데이트)
  형식: YYYY-MM-DD HH:MM
  미수정: "-"

작성자/수정자:
  형식: 이름 (예: Edward Kwon)
  수정자는 최종 수정자 이름

개요: 표 형식으로 현상/원인/조치/영향도/상태 요약
  현상: What (무엇이 일어났는가)
  원인: Why (왜 일어났는가)
  조치: How (어떻게 해결했는가)
  영향도: Low/Medium/High (프로젝트에 미치는 영향)
  상태: ✅ 해결 / ⚠️ 진행중 / ❌ 차단
```

---

## 본문 작성 규칙

### 1. 현상 (What)

```markdown
## 1. 현상

**Self Test 단계:** Phase 2 - Self Test (Step 1: 단위 테스트)  
**발견 시간:** 2026-04-08 14:05  
**발견자:** Edward Kwon  

### 에러 메시지

```
Test Suites: 1 failed, 0 passed, 1 total
Tests:       3 failed, 2 passed, 5 total

FAIL src/auth/service.test.ts
  AuthService
    ✓ should register user (50ms)
    ✓ should login user (45ms)
    ✗ should refresh token with valid refresh_token (120ms)
    ✗ should return error with expired refresh_token (105ms)
    ✗ should return error with invalid refresh_token (98ms)

Error: Cannot read property 'expiresAt' of undefined
  at AuthService.refreshToken (src/auth/service.ts:67:15)
```

### 재현 방법

1. `npm test` 실행
2. refreshToken 테스트 케이스 실행
3. 만료된 토큰으로 refresh 시도
4. null reference 에러 발생
```

**작성 팁:**
- 에러 메시지 전체 복사
- 재현 방법 단계별 기록
- 스크린샷 (필요시) 첨부
- 발생 빈도 기록 (100% 재현 vs 간헐적)

### 2. 원인 (Why)

```markdown
## 2. 원인

### 근본 원인 분석

#### 코드 검토

```typescript
// src/auth/service.ts, Line 67
async refreshToken(refreshToken: string) {
  const stored = await redis.get(`refresh:${refreshToken}`);
  
  // ❌ 문제: stored가 null인 경우 체크 없음
  const token = JSON.parse(stored); // null일 때 에러 발생
  
  if (token.expiresAt < Date.now()) { // 여기서 null reference 에러
    return { error: 'Token expired' };
  }
  
  return { accessToken: generateToken() };
}
```

#### 원인

1. **직접 원인:** null 체크 누락
   - Redis에서 토큰을 찾지 못한 경우 (null)
   - JSON.parse(null) 실행 후 token이 undefined
   - token.expiresAt 접근 시 에러

2. **근본 원인:** 불완전한 테스트 커버리지
   - 토큰 만료 후 refresh 시도하는 엣지 케이스 미테스트
   - 만료 시간 로직 재검토 필요

3. **설계 이슈:** 토큰 저장소 에러 처리 부재
   - Redis 오류 시 처리 방법 미정의
   - 토큰 조회 실패 시나리오 미고려

### 영향 범위

- AuthService.refreshToken() 함수
- 로그인 유지 기능
- 사용자 세션 관리
```

**작성 팁:**
- 코드 라인 번호 명시
- 직접 원인 vs 근본 원인 구분
- 테스트 케이스 부족 부분 명시
- 설계 결함 여부 검토

### 3. 조치 (How)

```markdown
## 3. 조치

### 적용한 수정 사항

#### 수정 1: Null 체크 추가

```typescript
// src/auth/service.ts, Line 67 (수정)
async refreshToken(refreshToken: string) {
  const stored = await redis.get(`refresh:${refreshToken}`);
  
  // ✅ 수정: null 체크 추가
  if (!stored) {
    return { error: 'Refresh token not found or expired', code: 'INVALID_TOKEN' };
  }
  
  const token = JSON.parse(stored);
  
  if (token.expiresAt < Date.now()) {
    return { error: 'Token expired', code: 'TOKEN_EXPIRED' };
  }
  
  return { accessToken: generateToken() };
}
```

#### 수정 2: 테스트 케이스 추가

```typescript
// src/auth/service.test.ts
describe('AuthService - refreshToken', () => {
  // ... 기존 테스트 ...
  
  // ✅ 추가: 만료된 토큰 테스트
  it('should return error with expired refresh_token', async () => {
    const expiredToken = 'expired-token';
    const pastTime = Date.now() - 1000; // 1초 전
    await redis.set(`refresh:${expiredToken}`, 
      JSON.stringify({ expiresAt: pastTime }));
    
    const result = await authService.refreshToken(expiredToken);
    
    expect(result.error).toBe('Token expired');
    expect(result.code).toBe('TOKEN_EXPIRED');
  });
  
  // ✅ 추가: 존재하지 않는 토큰 테스트
  it('should return error with invalid refresh_token', async () => {
    const invalidToken = 'non-existent-token';
    
    const result = await authService.refreshToken(invalidToken);
    
    expect(result.error).toBe('Refresh token not found or expired');
    expect(result.code).toBe('INVALID_TOKEN');
  });
});
```

### 수정 검증

1. `npm test` 재실행
   ```
   Test Suites: 1 passed, 1 total
   Tests:       5 passed, 5 total
   ```

2. 커버리지 확인
   ```
   AuthService: 92% (이전 87%)
   ```

3. 수동 테스트
   - 만료된 토큰으로 refresh 시도 → 적절한 에러 반환 ✓
   - 존재하지 않는 토큰으로 refresh 시도 → 적절한 에러 반환 ✓
```

**작성 팁:**
- 수정 전/후 코드 명시 (```typescript 블록 사용)
- 각 수정의 목적 설명
- 검증 결과 기록 (테스트 통과 확인)
- 성능 영향 평가

### 4. 검증 (Verification)

```markdown
## 4. 검증

### 테스트 결과

| 테스트 | 이전 | 수정 후 | 상태 |
| --- | --- | --- | --- |
| npm test | ❌ 3/5 실패 | ✅ 5/5 통과 | PASS |
| 커버리지 | 87% | 92% | PASS |
| 수동 테스트 | - | 만료/무효 토큰 처리 정상 | PASS |
| ZEN_A4 검증 | - | 통과 | PASS |

### 검증 체크리스트

- ✅ 모든 단위 테스트 통과
- ✅ 커버리지 80% 이상
- ✅ 에러 메시지 명확
- ✅ 엣지 케이스 처리
- ✅ 코드 리뷰 피드백 반영
- ✅ 보안 이슈 없음
```

### 5. 예방 (Prevention)

```markdown
## 5. 예방 방안

### Check List에 추가할 항목

```
☐ Null/Undefined 체크
  ☐ 외부 입력값 null 체크
  ☐ DB/Cache 조회 결과 null 체크
  ☐ 옵셔널 필드 접근 안전성 확인

☐ 토큰/세션 로직
  ☐ 토큰 만료 시간 검증
  ☐ 토큰 갱신 실패 시나리오
  ☐ 토큰 저장소 오류 처리
  ☐ 동시성 이슈 (race condition)

☐ 테스트 케이스
  ☐ Happy Path만 테스트
  ☐ Edge Case: 만료된 데이터
  ☐ Error Case: 없는 데이터
  ☐ Security Case: 잘못된 데이터
```

### 향후 개선

1. **코드 리뷰 강화**
   - Null 체크 필수 항목으로 지정
   - Code reviewer 자동 검사 규칙 추가

2. **테스트 전략 개선**
   - 엣지 케이스 테스트 템플릿 제공
   - 커버리지 레포트 의무화

3. **설계 문서화**
   - 토큰 생명주기 문서화
   - 에러 처리 전략 명시
```

---

## 개정 이력 기록

### 형식

```markdown
## 개정 이력

| 버전 | 날짜 | 작성자 | 수정자 | 변경 내용 |
| --- | --- | --- | --- | --- |
| 1.0 | 2026-04-08 | Edward Kwon | - | 초판 작성 |
| 1.1 | 2026-04-09 | Edward Kwon | Manager | 추가 테스트 케이스 결과 반영 |
| 1.2 | 2026-04-10 | Edward Kwon | Reviewer | 코드 리뷰 피드백 적용 |
```

### 기록 규칙

- 모든 수정 사항 기록 (타이핑 오류도 포함)
- 수정자는 승인자 또는 코드 리뷰어
- 변경 내용은 간결하게 (1-2줄)

---

## 파일 명명 규칙

### 규칙

```
SAR_YYYY-MM-DD_NNN_문제_분류.md

YYYY-MM-DD: 발견 날짜
NNN: 일일 일련번호 (001부터 시작)
문제: 오류와 관련된 기능명
분류: 오류 유형 (분류는 아래 참조)
```

### 오류 분류 (분류 코드)

```
NullReference: Null/Undefined 체크 누락
TypeError: 타입 불일치
LogicError: 로직 오류
PerformanceIssue: 성능 문제
SecurityIssue: 보안 취약점
EdgeCase: 엣지 케이스 미처리
ConcurrencyIssue: 동시성 문제
ConfigError: 설정 오류
DependencyIssue: 의존성 문제
UnexpectedBehavior: 예상치 못한 동작
```

### 파일명 예시

```
SAR_2026-04-08_001_RefreshToken_NullReference.md
SAR_2026-04-08_002_PasswordValidation_EdgeCase.md
SAR_2026-04-09_001_DatabaseConnection_PerformanceIssue.md
SAR_2026-04-09_002_LoginFlow_ConcurrencyIssue.md
SAR_2026-04-10_001_APIResponse_TypeError.md
```

---

## 예시

### 완전한 SAR 문서 예시

```markdown
# SAR-2026-04-08-001: RefreshToken 함수 NullReference 오류

**버전:** 1.1  
**작성일:** 2026-04-08 14:45  
**수정일:** 2026-04-09 10:30  
**작성자:** Edward Kwon  
**수정자:** Code Reviewer  

## 개요

| 항목 | 내용 |
| --- | --- |
| **현상** | Self Test 수행 시 refreshToken() 함수에서 null reference 오류 |
| **원인** | 토큰 만료 시간 초과 후 접근 시 null 체크 누락 |
| **조치** | null 체크 추가, 테스트 케이스 추가, 에러 처리 강화 |
| **영향도** | 높음 |
| **상태** | ✅ 해결 |

---

## 1. 현상

**Self Test 단계:** Phase 2 - Self Test (Step 1: 단위 테스트)  
**발견 시간:** 2026-04-08 14:05  

### 에러 메시지

```
FAIL src/auth/service.test.ts
Tests: 3 failed, 2 passed, 5 total
Error: Cannot read property 'expiresAt' of undefined
  at AuthService.refreshToken (src/auth/service.ts:67:15)
```

---

## 2. 원인

### 근본 원인

코드의 67번 라인에서 Redis에서 조회한 값이 null인 경우 null 체크 없이 바로 JSON.parse() 실행  
→ token이 undefined로 설정  
→ token.expiresAt 접근 시 에러

---

## 3. 조치

### 수정 내용

```typescript
// 수정 전
const stored = await redis.get(`refresh:${refreshToken}`);
const token = JSON.parse(stored); // null일 때 에러

// 수정 후
const stored = await redis.get(`refresh:${refreshToken}`);
if (!stored) {
  return { error: 'Token not found' };
}
const token = JSON.parse(stored);
```

### 테스트 추가

엣지 케이스 테스트 2개 추가 (만료된 토큰, 존재하지 않는 토큰)

---

## 4. 검증

모든 테스트 통과: 5/5 ✓  
커버리지: 92% (목표 80% 달성)

---

## 5. 예방

Check List에 다음 항목 추가:
- ☐ 외부 입력값 null 체크
- ☐ 토큰 만료 시간 검증
- ☐ 엣지 케이스 테스트

---

## 개정 이력

| 버전 | 날짜 | 작성자 | 수정자 | 변경 내용 |
| --- | --- | --- | --- | --- |
| 1.0 | 2026-04-08 | Edward Kwon | - | 초판 작성 |
| 1.1 | 2026-04-09 | Edward Kwon | Reviewer | 추가 테스트 결과 반영 |
```

---

## 정리

```
이 문서를 따라 SAR을 작성하면:

✅ 모든 오류가 체계적으로 기록됨
✅ 동일 오류의 재발이 방지됨
✅ 팀 전체가 경험을 학습함
✅ Check List가 지속적으로 개선됨
✅ 프로젝트 품질이 향상됨
```
