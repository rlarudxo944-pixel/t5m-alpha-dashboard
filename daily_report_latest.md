# 알파랩 일간 리포트 — 2026-09-13
*생성: 2026-09-13 08:50 KST*

## 📌 헤드라인
⚠️ 알파 1건 재등급 하향 발생 - PUMP_EXHAUSTION_SHORT_V1

## 📋 레지스트리 현황
| 상태 | 오늘 | 전날대비 |
|---|---|---|
| confirmed | 7 | (변화없음)
| consolidated | 3 | (변화없음)
| forward_testing | 2 | (변화없음)
| inconclusive | 107 | (변화없음)
| info_only | 1 | (변화없음)
| near_miss | 93 | (+2)
| paper_running | 9 | (변화없음)
| paper_running_correlated | 5 | (변화없음)
| rejected | 242 | (+3)
| retracted | 5 | (변화없음)

최신 discovery_log: **D562** (전날 D551, +11건)

## 🆕 신규확정/강등
**신규확정/승격**:
- TRAITCOMBO_ZEC_COMPANION_V1_D175183185191_V1: (신규) → **confirmed**
**강등**:
- PUMP_EXHAUSTION_SHORT_V1: confirmed → **rejected**

## 📍 페이퍼트레이딩
- 완료거래: 45건 (변화없음)
- 오픈포지션: 61건 (변화없음)
- 승격기준 근접 알파 없음

## 🚦 파이프라인
- explore: 3 (변화없음)
- ci: 7 (변화없음)
- paper_new: 16 (변화없음) 🔴병목
- paper_watch: 0 (변화없음)
- paper_healthy: 0 (변화없음)
- promote: 0 (변화없음)
- live: 0 (변화없음)
- exit: 447 (+5)

## 🌳 컴포넌트 조합 (테크트리 관점)
*discovery건수/confirmed개수 자체가 아니라, 검증된 컴포넌트를 몇 개 조합했는지 · 조합이 실제로 부모(단일요소)보다 강한지가 진짜 진척 - 사용자 직접지시 반영.*
- 트레잇매핑된 살아있는 알파: 22건, 평균 조합다양성 2.5종(서로 다른 카테고리 기준)
- 단순자산확장(breadth-only, 조합력 증가 없음): 5건
- 부모보다 강한 조합: MULTICHANNEL_4CH_3OF4_V1
- ⚠️ 부모보다 약한 조합(결합이 오히려 희석됨): MULTICHANNEL_BREAKOUT_AGREEMENT_V1, WIDE_TRAIL_OPTIONALITY_V1, MULTITIMEFRAME_BREAKOUT_AGREEMENT_V1, DONCHIAN_TAKER_CONFLUENCE_V1, ATR_TAKER_CONFLUENCE_V1 외 7건
- 미조합 유망 트레잇쌍 후보(메타엔진 큐에 반영됨):
  - ATR비율 확장+모멘텀부호 순응 + 펀딩비율 단기/장기평균차 방향일치
  - ATR비율 확장+모멘텀부호 순응 + 1H+4H 동일지표 동시확인
  - 켈트너채널(EMA±ATR) 상/하단 돌파 + 펀딩비율 단기/장기평균차 방향일치

## 🐛 버그/인프라
**인프라 경고 있음**:
# ⚠️ 인프라 자체점검 - 이상 10건 발견

마지막 점검: 2026-09-12 23:44:34 UTC

## 🟡 경고 (9건)
- **[backtest_outlier]** CAKE_MACD_DEEP_OPT: TRAIN PF=16.34(이상치 수준, >10.0) + CI하한=0.000(0근접) - DASHUSDT 이상틱과 동일 시그니처(대개 자산 자체가 극단적 신규상장/저유동성일 때 발생, 단일봉 데이터오류 가능성도 배제말고 kline_cache 스팟체크 권장)
- **[backtest_outlier]** WIF_MACD_DEEP_OPT: TRAIN PF=12.04(이상치 수준, >10.0) + CI하한=0.000(0근접) - DASHUSDT 이상틱과 동일 시그니처(대개 자산 자체가 극단적 신규상장/저유동성일 때 발생, 단일봉 데이터오류 가능성도 배제말고 kline_cache 스팟체크 권장)
- **[backtest_outlier]** SEI_MACD_DEEP_OPT: TRAIN PF=12.20(이상치 수준, >10.0) + CI하한=0.000(0근접) - DASHUSDT 이상틱과 동일 시그니처(대개 자산 자체가 극단적 신규상장/저유동성일 때 발생, 단일봉 데이터오류 가능성도 배제말고 kline_cache 스팟체크 권장)

*(전문은 zec_infra_alert.md 참조)*

## 💰 노출액
- 노출액 비율: 109.3% 🧊(동결상태)

## 🎯 다음 우선순위 제안
- 파이프라인 병목(paper_new)이 여전 - 승격/라이브전환 경로 점검 필요
- 인프라 경고 원인 확인/해소 필요
