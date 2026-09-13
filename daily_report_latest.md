# 알파랩 일간 리포트 — 2026-09-14
*생성: 2026-09-14 08:50 KST*

## 📌 헤드라인
⚠️ 알파 5건 재등급 하향 발생 - DAILY_MACD_TAKER_CONFLUENCE_HIGHVOL_V1, DONCHIAN_MOMENTUM_RANK_FILTER_V1, DOGE_DONCHIAN_REAPPLY_V1

## 📋 레지스트리 현황
| 상태 | 오늘 | 전날대비 |
|---|---|---|
| confirmed | 3 | (-4)
| consolidated | 3 | (변화없음)
| forward_testing | 2 | (변화없음)
| inconclusive | 107 | (변화없음)
| info_only | 1 | (변화없음)
| near_miss | 104 | (+11)
| paper_running | 8 | (-1)
| paper_running_correlated | 5 | (변화없음)
| rejected | 247 | (+5)
| retracted | 5 | (변화없음)

최신 discovery_log: **D613** (전날 D562, +51건)

## 🆕 신규확정/강등
**강등**:
- DAILY_MACD_TAKER_CONFLUENCE_HIGHVOL_V1: paper_running → **near_miss**
- DONCHIAN_MOMENTUM_RANK_FILTER_V1: confirmed → **near_miss**
- DOGE_DONCHIAN_REAPPLY_V1: confirmed → **near_miss**
- ADA_DONCHIAN_REAPPLY_V1: confirmed → **near_miss**
- TRAITCOMBO_ZEC_COMPANION_V1_D175183185191_V1: confirmed → **near_miss**

## 📍 페이퍼트레이딩
- 완료거래: 48건 (+3)
- 오픈포지션: 64건 (+3)
- 승격기준 근접 알파 없음

## 🚦 파이프라인
- explore: 3 (변화없음)
- ci: 3 (-4)
- paper_new: 15 (-1) 🔴병목
- paper_watch: 0 (변화없음)
- paper_healthy: 0 (변화없음)
- promote: 0 (변화없음)
- live: 0 (변화없음)
- exit: 463 (+16)

## 🌳 컴포넌트 조합 (테크트리 관점)
*discovery건수/confirmed개수 자체가 아니라, 검증된 컴포넌트를 몇 개 조합했는지 · 조합이 실제로 부모(단일요소)보다 강한지가 진짜 진척 - 사용자 직접지시 반영.*
- 트레잇매핑된 살아있는 알파: 20건, 평균 조합다양성 2.4종(서로 다른 카테고리 기준)
- 단순자산확장(breadth-only, 조합력 증가 없음): 2건
- 부모보다 강한 조합: MULTICHANNEL_4CH_3OF4_V1
- ⚠️ 부모보다 약한 조합(결합이 오히려 희석됨): MULTICHANNEL_BREAKOUT_AGREEMENT_V1, WIDE_TRAIL_OPTIONALITY_V1, MULTITIMEFRAME_BREAKOUT_AGREEMENT_V1, DONCHIAN_TAKER_CONFLUENCE_V1, ATR_TAKER_CONFLUENCE_V1 외 7건
- 미조합 유망 트레잇쌍 후보(메타엔진 큐에 반영됨):
  - ATR비율 확장+모멘텀부호 순응 + 펀딩비율 단기/장기평균차 방향일치
  - ATR비율 확장+모멘텀부호 순응 + 1H+4H 동일지표 동시확인
  - 켈트너채널(EMA±ATR) 상/하단 돌파 + 펀딩비율 단기/장기평균차 방향일치

## 🐛 버그/인프라
**인프라 경고 있음**:
# ⚠️ 인프라 자체점검 - 이상 20건 발견

마지막 점검: 2026-09-13 23:44:35 UTC

## 🔴 심각 (7건)
- **[scheduled_task]** ZEC_DonchianTakerConfluence_Paper_Poll: 마지막 실행결과 오류(LastTaskResult=2147946720)
- **[scheduled_task]** ZEC_FundingMomentumConfirmation_Paper_Poll: 마지막 실행결과 오류(LastTaskResult=2147946720)
- **[scheduled_task]** ZEC_Multichannel4ch_Paper_Poll: 마지막 실행결과 오류(LastTaskResult=2147946720)
- **[scheduled_task]** ZEC_MultichannelAgreement_Paper_Poll: 마지막 실행결과 오류(LastTaskResult=2147946720)
- **[scheduled_task]** ZEC_MultitimeframeAgreement_Paper_Poll: 마지막 실행결과 오류(LastTaskResult=2147946720)
- **[scheduled_task]** ZEC_TakerRatio_Trailing_Paper_Poll: 마지막 실행결과 오류(LastTaskResult=2147946720)
- **[scheduled_task]** ZEC_WideTrailOptionality_Paper_Poll: 마지막 실행결과 오류(LastTaskResult=2147946720)

## 🟡 경고 (11건)

*(전문은 zec_infra_alert.md 참조)*

## 💰 노출액
- 노출액 비율: 109.3% 🧊(동결상태)

## 🎯 다음 우선순위 제안
- 파이프라인 병목(paper_new)이 여전 - 승격/라이브전환 경로 점검 필요
- 인프라 경고 원인 확인/해소 필요
