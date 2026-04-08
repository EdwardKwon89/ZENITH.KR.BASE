# 📊 08_Self_Audit 문서 인덱스

> **폴더명**: 08_Self_Audit (오류 관리 & 자체 감시)  
> **목적**: 프로젝트 개발 중 발견된 모든 오류를 기록하고 재발을 방지  
> **관리자**: Team Lead  
> **최종 업데이트**: 2026-04-08  

---

## 📌 폴더 개요

이 폴더는 **SAR (Self_Audit_Report)** 시스템으로 운영됩니다.

### 목적
- ✅ 모든 오류를 기록 (Self Check/Test에서 발견)
- ✅ 오류의 근본 원인 분석
- ✅ 재발 방지 (Check List로 예방)
- ✅ 팀 학습 (집단 지식 축적)

---

## 📄 문서 목록

| # | 문서명 | Link | 개요 |
| --- | --- | --- | --- |
| **000** | **Self_Audit 인덱스** | [000_Self_Audit_README.md](./000_Self_Audit_README.md) | SAR 시스템 개요 |
| **001** | **Self_Audit 개요** | [001_Self_Audit_Overview.md](./001_Self_Audit_Overview.md) | SAR의 역할과 운영 방식 |

---

## 📁 SAR 저장소 구조

```
08_Self_Audit/
├── 000_Self_Audit_README.md (이 파일)
├── 001_Self_Audit_Overview.md
└── SAR_reports/ (실제 SAR 파일들)
    ├── SAR_2026-04-10_001_Implementation_NullCheck누락.md
    ├── SAR_2026-04-10_002_Security_환경변수검증누락.md
    └── ... (월별/번호별)
```

---

## 🔄 SAR 시스템 작동

```
1. 오류 발견 (Phase 1/2/3)
   ↓
2. SAR 작성 (10-20분)
   ├─ 파일명: SAR_YYYY-MM-DD_NNN_Category_설명.md
   └─ 필수: 현상/원인/조치/검증/예방
   ↓
3. Check List 추가 (5-10분)
   ├─ SAR의 "Prevention" 섹션 추출
   └─ Phase 체크리스트에 항목 추가
   ↓
4. 재발 방지 (다음 기능)
   ├─ Check List 확인
   └─ 같은 오류 이미 방지! ✅
```

---

## 📊 SAR 분류

### 8가지 분류
- **Design**: 아키텍처/설계 미흡
- **Implementation**: 구현 오류
- **Testing**: 테스트 부족
- **Security**: 보안 취약점
- **Performance**: 성능 문제
- **Integration**: 통합 오류
- **Documentation**: 문서 부족
- **Other**: 기타

### 4가지 심각도
- **CRITICAL**: 보안/데이터 손실 위험
- **HIGH**: 기능 장애
- **MEDIUM**: 코드 품질 문제
- **LOW**: 스타일/미흡함

---

## 📈 월간 통계 추적

매월 마지막 주 금요일 분석:
- 총 SAR 수
- 분류별 분포
- 심각도별 분포
- 오류율 감소 추이

---

## 🚀 빠른 시작

### SAR 작성하는 법

```
1. 오류 발견
   ↓
2. SAR 파일 생성
   파일명: SAR_YYYY-MM-DD_NNN_Category_설명.md
   예: SAR_2026-04-10_001_Implementation_NullCheck누락.md
   ↓
3. 필수 섹션 작성
   - 현상 (What): 무엇이 일어났나?
   - 원인 (Why): 왜 발생했나?
   - 조치 (How): 어떻게 수정했나?
   - 검증 (Verification): 제대로 수정됐나?
   - 예방 (Prevention): 앞으로 어떻게 방지?
   ↓
4. Check List 항목 추가
   Phase 1/2/3 체크리스트에
   예: □ Null Check: 모든 외부 응답 검증 (SAR-001)
```

---

## 📚 참고 문서

- [001_Document_Writing_Rule.md](../00_GUIDE/001_Document_Writing_Guide.md) - SAR 작성 규칙
- [201_SAR_RULE.md](../00_GUIDE/201_SAR_RULE.md) - SAR 작성 상세 규칙
- [202_CHECK_LIST_PROCEDURE.md](../00_GUIDE/202_CHECK_LIST_PROCEDURE.md) - Check List 관리

---

**버전**: v1.0 | **최종 업데이트**: 2026-04-08
