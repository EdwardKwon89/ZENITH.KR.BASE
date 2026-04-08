# 🏗️ PJT_2026_010 - ZENITH Base Template v0.5

> **완전히 자동화된 개발 환경과 문서 체계를 갖춘 프로젝트 기본 템플릿**

이 프로젝트는 모든 신규 프로젝트의 기반이 되는 **안정적인 기본 템플릿(v0.5)**입니다.  
GSD + ZEN_A4 방법론, SAR 시스템, Phase별 체크리스트가 통합되어 있습니다.

---

## 📋 개요

| 항목 | 설명 |
| --- | --- |
| **용도** | 신규 프로젝트의 기본 템플릿 |
| **버전** | v0.5 (Stable) |
| **상태** | 🔒 Frozen (실 프로젝트 적용 후 개선) |
| **기술** | Claude Code + Ollama (로컬 LLM) |
| **방법론** | GSD + ZEN_A4 (하이브리드) |
| **저장소** | https://github.com/EdwardKwon89/ZENITH.KR.BASE |

---

## 🚀 빠른 시작 (5분)

### 1단계: 템플릿 복제

```bash
# v0.5 태그 기반으로 복제
git clone -b v0.5 https://github.com/EdwardKwon89/ZENITH.KR.BASE.git [새프로젝트명]
cd [새프로젝트명]
```

### 2단계: 템플릿 커스터마이징

다음 파일들에서 placeholder를 실제 값으로 변경:

| 변경 항목 | 변경 위치 |
| --- | --- |
| **[PROJECT_NAME]** | `CLAUDE.md`, `docs/09_TEMPLATES/020_ONBOARDING_TEMPLATE.md` |
| **[TEAM_SIZE]** | `docs/09_TEMPLATES/020_ONBOARDING_TEMPLATE.md` |
| **[TECH_STACK]** | `CLAUDE.md`, 프로젝트 루트의 `package.json` 등 |

### 3단계: 팀에 배포

수정된 템플릿을 팀원에게 공유하고 온보딩 시작

```bash
# 온보딩 가이드 위치
docs/09_TEMPLATES/020_ONBOARDING_TEMPLATE.md
```

---

## 📁 프로젝트 구조

```
PJT_2026_010/
├── README.md                          # 이 파일 (템플릿 사용 가이드)
├── CLAUDE.md                          # 프로젝트 전체 설정 및 협업 방식
├── .planning/
│   ├── DECISIONS.md                   # 기술 의사결정 기록
│   └── CONTEXT.md                     # 프로젝트 컨텍스트 & 아키텍처
│
└── docs/
    ├── 00_GUIDE/                      # 핵심 개발 가이드
    │   ├── 000_GUIDE_README.md        # 가이드 인덱스
    │   ├── 001_Document_Writing_Guide.md
    │   ├── 101_ZEN_A4_METHODOLOGY.md
    │   ├── 102_INTEGRATED_DEVELOPMENT_METHODOLOGY.md
    │   ├── 201_SAR_RULE.md
    │   ├── 202_CHECK_LIST_PROCEDURE.md
    │   └── 203_PROJECT_APPLICATION_CHECKLIST.md
    │
    ├── 08_Self_Audit/                 # 오류 관리 & 자체 감시 (SAR 시스템)
    │   ├── 000_Self_Audit_README.md   # SAR 시스템 개요
    │   ├── 001_Self_Audit_Overview.md
    │   └── SAR_reports/               # 실제 SAR 파일들 저장
    │       └── (SAR_YYYY-MM-DD_NNN_Category_설명.md)
    │
    ├── 09_TEMPLATES/                  # 신규 프로젝트 템플릿 & 가이드
    │   ├── 000_TEMPLATES_README.md    # 템플릿 인덱스
    │   ├── 010_QUICK_REFERENCE_TEMPLATE.md
    │   ├── 020_ONBOARDING_TEMPLATE.md
    │   ├── 030_TROUBLESHOOTING_TEMPLATE.md
    │   ├── 040_SETUP_TEMPLATE/
    │   │   ├── OLLAMA_DIRECT_INSTALL_TEMPLATE.md
    │   │   ├── DOCKER_COMPOSE_OLLAMA_TEMPLATE.md
    │   │   └── README.md
    │   └── 050_CHECKLISTS_TEMPLATE/
    │       ├── PHASE_1_DESIGN_CHECKLIST.md
    │       ├── PHASE_2_EXECUTE_CHECKLIST.md
    │       ├── PHASE_3_VERIFY_CHECKLIST.md
    │       └── COMMIT_CHECKLIST.md
    │
    └── 10_Reference/                  # 완전한 참조 & 정책 문서
        ├── 000_Reference_README.md    # 참조 인덱스
        ├── 001_Complete_Document_Writing_Guide.md
        └── 002_Audit_Management_Policy.md
```

---

## 📚 문서 안내

### 🟢 처음 시작하는 팀원 (1-2시간)

```
1. docs/00_GUIDE/000_GUIDE_README.md        (15분)
   └─ 전체 가이드 인덱스 & 추천 경로

2. docs/09_TEMPLATES/010_QUICK_REFERENCE_TEMPLATE.md  (5분)
   └─ 개발 흐름 한눈에 보기

3. docs/09_TEMPLATES/020_ONBOARDING_TEMPLATE.md      (1-2시간)
   └─ Phase 1~4 따라하며 첫 기능 완성
   └─ Self Check & Self Test 포함
```

### 🔵 새 기능 개발 시작 (매번)

```
1. docs/09_TEMPLATES/010_QUICK_REFERENCE_TEMPLATE.md    (참고)
2. docs/09_TEMPLATES/050_CHECKLISTS_TEMPLATE/           (체크)
   ├─ PHASE_1_DESIGN_CHECKLIST.md
   ├─ PHASE_2_EXECUTE_CHECKLIST.md
   └─ PHASE_3_VERIFY_CHECKLIST.md
3. docs/00_GUIDE/201_SAR_RULE.md                        (오류 발생시)
4. docs/00_GUIDE/202_CHECK_LIST_PROCEDURE.md            (오류 후)
```

### 🟡 심화 학습 (PM/아키텍트, 3-4시간)

```
1. docs/00_GUIDE/101_ZEN_A4_METHODOLOGY.md
   └─ 하이브리드 개발 방법론 상세 설명

2. docs/00_GUIDE/102_INTEGRATED_DEVELOPMENT_METHODOLOGY.md
   └─ 통합 개발 절차 & 도구 역할 분담

3. docs/10_Reference/001_Complete_Document_Writing_Guide.md
   └─ 완전한 문서 작성 규칙 (심화)

4. docs/10_Reference/002_Audit_Management_Policy.md
   └─ SAR & Check List 조직 차원 정책
```

---

## 🎯 사용 시나리오

### 시나리오 1: 새 프로젝트 시작

```
Step 1: 이 템플릿 복제 (5분)
        ↓
Step 2: docs/09_TEMPLATES/020_ONBOARDING_TEMPLATE.md 실행 (4-5시간)
        ├─ Phase 1: 설계 + Self Check
        ├─ Phase 2: 구현 + Self Test
        ├─ Phase 3: Claude 검증
        └─ Phase 4: 커밋
        ↓
Result: 첫 기능 완성! ✅
```

### 시나리오 2: 오류 발생 후 재발 방지

```
오류 발생
  ↓
docs/00_GUIDE/201_SAR_RULE.md 참고
  ↓
SAR 파일 작성 (docs/08_Self_Audit/SAR_reports/)
  ↓
docs/00_GUIDE/202_CHECK_LIST_PROCEDURE.md 참고
  ↓
Check List 업데이트 (Phase 체크리스트에 항목 추가)
  ↓
다음 기능에서 같은 오류 자동 방지! ✅
```

### 시나리오 3: 문제 해결

```
문제 발생
  ↓
docs/09_TEMPLATES/030_TROUBLESHOOTING_TEMPLATE.md 검색
  ├─ 찾음 → 해결 방법 실행
  └─ 못 찾음 → 팀 리더 상담
```

---

## 🔑 핵심 특징

### 1️⃣ **자동화된 개발 프로세스**
- **Ollama (Gemma4-9B)**: 함수 자동완성 → 개발 시간 70%
- **Claude Code**: 설계/검증/상담 → 개발 시간 30%
- **ZEN_A4 훅**: 자동 리뷰 (PreToolUse/PostToolUse/Stop)

### 2️⃣ **완전한 문서 체계**
- 폴더별 README 및 인덱싱
- 문서 명명 규칙 (prefix 번호)
- 심화도별 가이드 (입문/심화/전문)

### 3️⃣ **오류 관리 & 재발 방지**
- **SAR (Self-Audit Report)**: 모든 오류 추적
- **Check List**: 오류 재발 방지
- **월간 분석**: 통계 기반 개선

### 4️⃣ **Phase별 체크리스트**
- Phase 1 (Design): 아키텍처/요구사항 검증
- Phase 2 (Execute): 구현/테스트 검증
- Phase 3 (Verify): Claude 검증
- Phase 4 (Commit): 최종 확인

---

## 📊 개발 방법론

### ZEN_A4 (가벼운 GSD 하이브리드)

```
Phase 1: Design (설계)
├─ Self Check 필수 ✓
└─ Gate: 아키텍처/요구사항 검증

Phase 2: Execute (구현)
├─ Self Test 필수 ✓
│  └─ 단위테스트, 커버리지 80%+, 수동테스트, 보안 검증
└─ Gate: 기능 동작 확인

Phase 3: Verify (검증)
├─ Claude 검증
└─ Gate: 코드 품질/보안 확인

Phase 4: Commit (커밋)
└─ 깃 커밋 & 푸시
```

**기대 효과:**
- 개발 속도: +50%
- 버그 감소: -30~40%
- 코드 리뷰 반려율: -50%
- 테스트 커버리지: 80%+ 필수

---

## 🛠️ 개발 도구 & 자동화

### 📋 기본 필수 도구

| 도구 | 용도 | 설치 |
| --- | --- | --- |
| **Claude Code** | 설계/검증/상담 | [claude.com/code](https://claude.com/code) (Subscription) |
| **Ollama** | 로컬 LLM (함수 자동완성) | [ollama.ai](https://ollama.ai) (무료) |
| **Gemma4-9B** | LLM 모델 | `ollama run gemma4:9b` |
| **Git** | 버전 관리 | 설치 필요 |

### 🤖 ZEN_A4 자동화 Agents

ZEN_A4 방법론에서 3가지 훅(Hooks)으로 자동 실행되는 에이전트들:

#### **PreToolUse Hook** (코드 작성 전)

복잡도가 높은 기능 감지 시 자동 실행:

| Agent | 역할 | 자동 실행 조건 |
| --- | --- | --- |
| **planner** | 구현 계획 수립 | 복잡한 기능 감지 |
| **architect** | 아키텍처 검증 | 아키텍처 변경 감지 |
| **security-reviewer** | 보안 검증 | 보안 관련 코드 감지 |

#### **PostToolUse Hook** (코드 작성 후)

모든 코드 자동 품질 검증:

| Agent | 검증 항목 |
| --- | --- |
| **code-reviewer** | 가독성, 패턴, 최적화 |
| **security-reviewer** | 보안 취약점, 인젝션, 암호화 |
| **tdd-guide** | 테스트 커버리지, 격리, 모킹 |
| **language-specific reviewers** | 언어별 관례, 성능, 안티패턴 |
| **doc-updater** | 문서 완성도, 가독성 |

#### **Stop Hook** (커밋 전)

최종 품질 게이트 (80% 커버리지, Self Check/Test 통과, 보안 스캔 등):

```
커밋 차단 조건:
❌ 테스트 커버리지 < 80%
❌ Self Check 미통과 (Phase 1)
❌ Self Test 미통과 (Phase 2)
❌ 보안 스캔 실패
❌ SAR 미작성 (오류 발견 시)

✅ 모두 통과 → 커밋 가능
```

**자세히:** [101_ZEN_A4_METHODOLOGY.md](docs/00_GUIDE/101_ZEN_A4_METHODOLOGY.md)

### 🔌 MCP Servers (선택 통합)

| MCP | 용도 | 상태 |
| --- | --- | --- |
| **context7** | 라이브러리 문서 검색 | 옵션 |
| **pencil** | 디자인 파일 편집 | 옵션 |

**설정:** CLAUDE.md에서 mcp.allowedServers 구성

### 📝 선택 도구

| 도구 | 용도 | 설치 |
| --- | --- | --- |
| **TypeScript/JavaScript** | Node.js 프로젝트 | 필요시 |
| **Python** | Python 프로젝트 | 필요시 |
| **Docker** | 컨테이너화 | docs/09_TEMPLATES/040_SETUP_TEMPLATE/ |

### 🔧 설정 가이드

#### 기본 설정

```
1. Claude Code 설치 & Subscription 활성화
2. Ollama 설정
   docs/09_TEMPLATES/040_SETUP_TEMPLATE/OLLAMA_DIRECT_INSTALL_TEMPLATE.md

3. ZEN_A4 Hooks 활성화
   .claude/settings.json에서 hooks 구성
```

#### 팀 협업 설정

```
1. Docker Compose로 Ollama 표준화
   docs/09_TEMPLATES/040_SETUP_TEMPLATE/DOCKER_COMPOSE_OLLAMA_TEMPLATE.md

2. MCP Servers 활성화
   CLAUDE.md의 mcp 섹션 참고
```

---

## 📦 버전 정보

| 버전 | 상태 | 내용 |
| --- | --- | --- |
| **v0.5** | 🔒 Frozen | 완전한 기본 템플릿 (현재) |
| v0.6+ | 🚀 계획 | 실 프로젝트 적용 후 개선사항 반영 |

**v0.5 특징:**
- 표준화된 폴더 구조 (00_, 08_, 09_, 10_)
- 포괄적인 README 파일들
- 완전한 SAR 시스템
- Phase별 체크리스트
- 팀 개발 방법론 (ZEN_A4)

---

## 🔗 주요 문서

| 문서 | 대상 | 소요시간 |
| --- | --- | --- |
| [CLAUDE.md](CLAUDE.md) | 모든 팀원 | 필독 |
| [00_GUIDE_README.md](docs/00_GUIDE/000_GUIDE_README.md) | 전체 | 15분 |
| [101_ZEN_A4_METHODOLOGY.md](docs/00_GUIDE/101_ZEN_A4_METHODOLOGY.md) | PM/개발자 | 1시간 |
| [020_ONBOARDING_TEMPLATE.md](docs/09_TEMPLATES/020_ONBOARDING_TEMPLATE.md) | 신규 팀원 | 4-5시간 |
| [201_SAR_RULE.md](docs/00_GUIDE/201_SAR_RULE.md) | 개발자 (필요시) | 20분 |

---

## ✅ 체크리스트: 새 프로젝트 준비

```bash
□ Step 1: 템플릿 복제
  git clone -b v0.5 https://github.com/EdwardKwon89/ZENITH.KR.BASE.git [새프로젝트명]

□ Step 2: 기본 정보 변경
  □ [PROJECT_NAME] → 실제 프로젝트명
  □ [TEAM_SIZE] → 팀 규모
  □ [TECH_STACK] → 기술스택

□ Step 3: 팀 구성원에게 공유
  □ CLAUDE.md 읽기
  □ docs/09_TEMPLATES/020_ONBOARDING_TEMPLATE.md 시작

□ Step 4: 첫 기능 개발 시작
  □ Phase 1: 설계 + Self Check
  □ Phase 2: 구현 + Self Test
  □ Phase 3: Claude 검증
  □ Phase 4: 커밋
```

---

## 🤝 기여 & 개선

이 v0.5는 안정화 단계입니다.

**실 프로젝트 적용 후 발견된 개선사항:**
1. 이슈 보고: [GitHub Issues](https://github.com/EdwardKwon89/ZENITH.KR.BASE/issues)
2. 개선사항: `release/v0.5` 브랜치에서 패치 작업
3. 새 버전: v0.6, v0.7 등으로 태그 생성

---

## 📞 문의 & 지원

| 항목 | 연락처 |
| --- | --- |
| 기술 문제 | `docs/09_TEMPLATES/030_TROUBLESHOOTING_TEMPLATE.md` |
| 프로젝트 설정 | `CLAUDE.md` & `docs/00_GUIDE/` |
| 개발 방법론 | `docs/00_GUIDE/101_ZEN_A4_METHODOLOGY.md` |

---

## 📄 라이선스

이 프로젝트는 기본 템플릿입니다. 자유롭게 fork하고 커스터마이징하세요.

---

**마지막 업데이트**: 2026-04-08 | **버전**: v0.5 (Stable)  
**저장소**: https://github.com/EdwardKwon89/ZENITH.KR.BASE
