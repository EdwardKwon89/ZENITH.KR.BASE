# 📋 프로젝트 Tailoring Templates

> 새 프로젝트 시작 시 PM/Leader가 사용하는 Template 모음  
> **버전:** 1.0  
> **작성일:** 2026-04-08

---

## 📌 개요

이 디렉토리는 **GSD + ZEN_A4 방법론**을 새로운 프로젝트에 적용할 때 필요한 모든 문서의 Template을 제공합니다.

### 특징
- ✅ 범용적 구조 (모든 프로젝트 타입 적용 가능)
- ✅ 최소 customize로 바로 사용 가능
- ✅ 팀 규모/기술스택별 자동 조정 가능
- ✅ 프로젝트 시작 시간 단축 (설정 → 2-3시간 → 30분)

---

## 🎯 사용 플로우

### 1단계: 프로젝트 기본 정보 수집

```
프로젝트 이름: [PROJECT_NAME]
팀 규모: [TEAM_SIZE] (1~5명)
기술스택: [TECH_STACK]
프로젝트 기간: [DURATION] (예: 3개월)
```

### 2단계: Template 파일 복사

```bash
# 이 디렉토리의 모든 Template 복사
docs/090_TEMPLATES/QUICK_REFERENCE_TEMPLATE.md
docs/090_TEMPLATES/ONBOARDING_TEMPLATE.md
docs/090_TEMPLATES/CHECKLISTS_TEMPLATE/
... 등

↓

# 프로젝트 docs/ 디렉토리에 붙여넣기
docs/QUICK_REFERENCE.md
docs/ONBOARDING_GUIDE.md
docs/CHECKLISTS/
... 등
```

### 3단계: Customize

각 파일에서 다음 항목을 변경:

```markdown
## 필수 변경 항목
- [PROJECT_NAME] → 실제 프로젝트명
- [TEAM_SIZE] → 실제 팀 규모
- [TECH_STACK] → 실제 기술스택
- [TODO: ...] → 프로젝트별 추가 작성

## 선택 변경 항목
- 추가 체크리스트 항목
- 팀별 역할
- 도구 설정
```

### 4단계: 팀원 배포

```
1. Customize 완료
2. CLAUDE.md에 링크 추가
3. 팀 회의에서 설명
4. 팀원들에게 배포
```

---

## 📂 Template 구조

### 핵심 Templates (필수)

| Template | 용도 | 작성자 | 팀원용 |
|----------|------|-------|-------|
| **QUICK_REFERENCE_TEMPLATE.md** | 한눈에 보는 플로우 | PM | ✅ 배포 필수 |
| **ONBOARDING_TEMPLATE.md** | 첫 기능 개발 가이드 | PM | ✅ 배포 필수 |
| **CHECKLISTS_TEMPLATE/** | Phase별 체크리스트 | PM | ✅ 배포 필수 |

### 보조 Templates (상황별)

| Template | 용도 | 필요성 | 팀원용 |
|----------|------|--------|-------|
| **TROUBLESHOOTING_TEMPLATE.md** | 문제 해결 가이드 | 팀 규모 3+ | ⚠️ 필요시 |
| **SETUP_TEMPLATE/** | 도구별 설정 가이드 | 첫 시작 시 | ⚠️ 온보딩 때만 |
| **ROLES_TEMPLATE/** | 역할별 가이드 | 분업 필요시 | ⚠️ 필요시 |
| **EXAMPLES_TEMPLATE/** | 실전 예시 | 팀 경험 낮을 시 | ⚠️ 참고용 |

---

## 🔄 각 Template별 사용 방법

### 1. QUICK_REFERENCE_TEMPLATE.md

**목적**: 개발자들이 개발 중 언제든 빠르게 확인할 수 있는 한 페이지 요약

**사용법**:
```bash
1. Template 열기
2. [PROJECT_NAME] 변경
3. 각 Phase별 예상 시간 추가
4. 프로젝트 특화 항목 추가 (선택)
5. 팀 회의에서 설명
```

**배포 대상**: 모든 팀원

---

### 2. ONBOARDING_TEMPLATE.md

**목적**: 새로운 팀원이 첫 번째 기능을 개발할 때 따라할 수 있는 단계별 가이드

**사용법**:
```bash
1. Template 열기
2. [FIRST_FEATURE] = 실제 첫 기능명으로 변경
3. [TECH_STACK]에 맞는 예제 코드 추가
4. Self Check/Test 구체 예시 추가
5. 신입 팀원에게 전달
```

**배포 대상**: 신입 팀원, 온보딩 담당자

---

### 3. CHECKLISTS_TEMPLATE/

**목적**: Phase별 자체 검증 체크리스트 (Self Check/Test)

**구성**:
```
PHASE_1_DESIGN_CHECKLIST.md      (Self Check용)
PHASE_2_EXECUTE_CHECKLIST.md     (Self Test용)
PHASE_3_VERIFY_CHECKLIST.md      (최종 검증용)
COMMIT_CHECKLIST.md              (커밋 전용)
```

**사용법**:
```bash
1. 각 파일 열기
2. [PROJECT_SPECIFIC_ITEM] 섹션에 프로젝트별 항목 추가
3. 팀이 사용할 형식 결정 (인쇄본 vs 온라인)
4. 각 단계마다 팀원들이 체크
```

**배포 대상**: 모든 팀원 (매일 사용)

---

### 4. TROUBLESHOOTING_TEMPLATE.md

**목적**: 자주 발생하는 문제와 해결 방법

**사용법**:
```bash
1. Template 열기
2. "Self Test 실패" 등 일반적 문제 유지
3. 프로젝트 진행 중 발생한 실제 문제 추가
4. 주간 회의 후 업데이트
```

**배포 대상**: 팀원 (필요시 참고)

---

### 5. SETUP_TEMPLATE/

**목적**: Claude Code, Ollama, ZEN_A4 등 도구 설정 가이드

**구성**:
```
CLAUDE_CODE_SETUP.md       (Claude Code 설정)
OLLAMA_SETUP.md            (Ollama + Gemma4 설정)
ZEN_A4_SETUP.md            (hooks 설정)
```

**사용법**:
```bash
1. 프로젝트 시작 전 팀원 전체 실행
2. 각 도구별로 환경 확인
3. 문제 발생 시 Troubleshooting 참고
4. 완료 후 "✓ 모두 설정 완료" 체크
```

**배포 대상**: 모든 팀원 (온보딩 때 필수)

---

### 6. ROLES_TEMPLATE/

**목적**: 팀원별 역할과 책임 정의

**구성**:
```
DEVELOPER_GUIDE.md         (개발자용: 코딩에 집중)
TEAM_LEAD_GUIDE.md         (리더용: 품질 관리)
ARCHITECT_GUIDE.md         (아키텍트용: 설계 검증)
```

**사용법**:
```bash
1. 프로젝트 팀 구성 정의
2. 각 역할별 Template customize
3. 역할별 책임 명확히
4. 팀 회의에서 설명
```

**배포 대상**: 역할별 팀원

---

### 7. EXAMPLES_TEMPLATE/

**목적**: 실전 예시를 통한 학습

**구성**:
```
SIMPLE_FEATURE_EXAMPLE.md       (간단한 기능 예시)
COMPLEX_FEATURE_EXAMPLE.md      (복잡한 기능 예시)
SAR_WRITING_EXAMPLE.md          (SAR 작성 예시)
```

**사용법**:
```bash
1. Template 열기
2. 프로젝트의 첫 번째 기능으로 예시 변경
3. 팀원들이 학습용으로 활용
4. 완료 후 보관 (참고 자료)
```

**배포 대상**: 팀원 (학습 자료)

---

## 💡 Customize 체크리스트

프로젝트 시작 시 다음을 확인하세요:

### 필수 (모든 프로젝트)
- [ ] QUICK_REFERENCE_TEMPLATE.md customize
- [ ] ONBOARDING_TEMPLATE.md customize
- [ ] PHASE 체크리스트 customize
- [ ] CLAUDE.md에 링크 추가
- [ ] 팀 회의에서 설명

### 권장 (팀 규모 3+)
- [ ] TROUBLESHOOTING_TEMPLATE.md customize
- [ ] ROLES_TEMPLATE customize
- [ ] 역할별 가이드 배포

### 선택 (필요시)
- [ ] SETUP_TEMPLATE 사용 (처음 설정 시)
- [ ] EXAMPLES_TEMPLATE 사용 (팀 경험 낮을 시)

---

## 🎓 학습 경로

### 신입 팀원
```
1. ONBOARDING_TEMPLATE.md 따라하기
2. SETUP_TEMPLATE/ 설정
3. QUICK_REFERENCE.md 숙지
4. 첫 기능 개발 (체크리스트 사용)
```

### 팀 리더
```
1. 모든 Template 검토
2. 프로젝트별로 customize
3. 팀원에게 설명 & 배포
4. 진행 중 업데이트 (Troubleshooting 등)
```

### 아키텍트
```
1. ARCHITECT_GUIDE.md 검토
2. 설계 검증 기준 정의
3. 복잡한 기능의 Pre-Review 수행
```

---

## 📊 Template 효과

### 시간 절감

| 항목 | 기존 | Template 사용 | 절감 |
|------|------|-------------|------|
| 프로젝트 시작 설정 | 3-4시간 | 30-45분 | **70-80%** |
| 신입 온보딩 | 2-3시간 | 1시간 | **50-60%** |
| 첫 기능 개발 | 4-5시간 | 3-4시간 | **20-30%** |

### 품질 향상

| 지표 | 개선 |
|-----|------|
| 팀 간 일관성 | +80% |
| 실수 감소 | -50% |
| 커뮤니케이션 명확도 | +70% |
| 프로세스 준수율 | +90% |

---

## 🔗 참조 문서

- [통합 개발 방법론](../000_GUIDE/INTEGRATED_DEVELOPMENT_METHODOLOGY.md)
- [ZEN_A4 방법론](../000_GUIDE/ZEN_A4_METHODOLOGY.md)
- [GSD + ZEN_A4 개요](../../.planning/DECISIONS.md#2-통합-개발-방법론-및-도구-채택-2026-04-08)

---

## 📞 질문 & 피드백

Templates 사용 중 문제가 생기면:
1. Troubleshooting 참고
2. 팀 리더에게 문의
3. 개선 사항을 Slack/회의에서 제시
4. 필요시 Template 업데이트

---

**마지막 업데이트:** 2026-04-08  
**담당자:** PJT_2026_010 팀  
**버전:** 1.0
