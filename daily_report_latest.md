# 알파랩 일간 리포트 — 2026-09-17
*생성: 2026-09-17 08:50 KST*

## 📌 헤드라인
🔴 인프라 경고 발생중 (zec_infra_alert.md 확인 필요)

## 📋 레지스트리 현황
| 상태 | 오늘 | 전날대비 |
|---|---|---|
| confirmed | 3 | (변화없음)
| consolidated | 3 | (변화없음)
| forward_testing | 4 | (변화없음)
| inconclusive | 107 | (변화없음)
| info_only | 1 | (변화없음)
| near_miss | 105 | (변화없음)
| paper_running | 8 | (변화없음)
| paper_running_correlated | 5 | (변화없음)
| rejected | 250 | (변화없음)
| retracted | 5 | (변화없음)

최신 discovery_log: **D639** (전날 D639, +0건)

## 🆕 신규확정/강등
없음

## 📍 페이퍼트레이딩
- 완료거래: 77건 (+1)
- 오픈포지션: 72건 (변화없음)
- 승격기준 근접 알파 없음

## 🚦 파이프라인
- explore: 3 (변화없음)
- ci: 3 (변화없음)
- paper_new: 15 (변화없음) 🔴병목
- paper_watch: 2 (변화없음)
- paper_healthy: 0 (변화없음)
- promote: 0 (변화없음)
- live: 0 (변화없음)
- exit: 467 (변화없음)

## 🌳 컴포넌트 조합 (테크트리 관점)
*discovery건수/confirmed개수 자체가 아니라, 검증된 컴포넌트를 몇 개 조합했는지 · 조합이 실제로 부모(단일요소)보다 강한지가 진짜 진척 - 사용자 직접지시 반영.*
- 트레잇매핑된 살아있는 알파: 20건, 평균 조합다양성 2.4종(서로 다른 카테고리 기준)
- 단순자산확장(breadth-only, 조합력 증가 없음): 4건
- 부모보다 강한 조합: MULTICHANNEL_4CH_3OF4_V1
- ⚠️ 부모보다 약한 조합(결합이 오히려 희석됨): MULTICHANNEL_BREAKOUT_AGREEMENT_V1, WIDE_TRAIL_OPTIONALITY_V1, MULTITIMEFRAME_BREAKOUT_AGREEMENT_V1, DONCHIAN_TAKER_CONFLUENCE_V1, ATR_TAKER_CONFLUENCE_V1 외 7건
- 미조합 유망 트레잇쌍 후보(메타엔진 큐에 반영됨):
  - ATR비율 확장+모멘텀부호 순응 + 펀딩비율 단기/장기평균차 방향일치
  - ATR비율 확장+모멘텀부호 순응 + 1H+4H 동일지표 동시확인
  - 켈트너채널(EMA±ATR) 상/하단 돌파 + 펀딩비율 단기/장기평균차 방향일치

## 🐛 버그/인프라
**인프라 경고 있음**:
# ⚠️ 인프라 자체점검 - 이상 19건 발견

마지막 점검: 2026-09-16 23:44:34 UTC

## 🔴 심각 (6건)
- **[alive_alpha_terrible_performance]** TAKER_RATIO_TRAILING_V1(status=paper_running) 완료거래 3건, 승률0%, 평균-13.01% - status는 alive지만 실적이 명백히 나쁨. 자동정지는 안 함(status 재분류는 검토 몫), 강력경고만.
- **[alive_alpha_terrible_performance]** BREAKOUT_RETEST_CONFIRMATION_V1(status=paper_running) 완료거래 5건, 승률20%, 평균-8.04% - status는 alive지만 실적이 명백히 나쁨. 자동정지는 안 함(status 재분류는 검토 몫), 강력경고만.
- **[alive_alpha_terrible_performance]** FUNDING_MOMENTUM_CONFIRMATION_V1(status=paper_running_correlated) 완료거래 4건, 승률0%, 평균-10.76% - status는 alive지만 실적이 명백히 나쁨. 자동정지는 안 함(status 재분류는 검토 몫), 강력경고만.

*(전문은 zec_infra_alert.md 참조)*

## 💰 노출액
- 노출액 비율: 109.3% 🧊(동결상태)

## 🎯 다음 우선순위 제안
- 파이프라인 병목(paper_new)이 여전 - 승격/라이브전환 경로 점검 필요
- 인프라 경고 원인 확인/해소 필요
