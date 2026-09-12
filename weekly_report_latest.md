# 알파랩 주간 리포트 — 2026-09-12
*생성: 2026-09-12 16:33 KST (최근 7일 집계, 일간리포트 4건 확인됨)*

## 📌 주간 헤드라인
이번주 신규시도 25건 중 확정 2건(수율 8.0%)

## 📊 주간누적
- 신규시도: 25건
- 확정: 2건 / 근접미확정: 9건 / 기각: 6건 / 판정불가: 0건
- 수율(확정/전체시도): 8.0%

## ⭐ 이번주 하이라이트
- [20260911] **신규확정/승격**:
- TRAITCOMBO_D158_D203_V1: (신규) → **confirmed**
**강등**:
- DONCHIAN_TRAILING_V1: paper_running → **consolidated**
- ATR_EXPANSION_TRAILING_V1: paper_running → **consolidated**
- KELTNER_TRAILING_V1: paper_running → **consolidated**
- DONCHIAN_TRAILING_HIGHVOL_V1: paper_running → **near_miss**
- ATR_EXPANSION_TRAILING_HIGHVOL_V1: paper_running → **near_miss**
- KELTNER_TRAILING_HIGHVOL_V1: paper_running → **near_miss**
- [20260912] **신규확정/승격**:
- PUMP_EXHAUSTION_SHORT_V1: near_miss → **confirmed**

## 🔧 이번주 추가된 시스템/인프라
- D186: 자체감사(2026-09-05) 5개 지적사항 후속조치 완료 — 인프라수정/포트폴리오킬스위치/노출액문서화/상관위험태깅/다중비교보정
- D196: 포트폴리오 노출액 상한 룰(신규배포/사이징증대 자동보류) 신설
- D310: DASH_MACD_DEEP_OPT / ZEN_MACD_DEEP_OPT 페이퍼배포 누락 발견 + 즉시배포
- D539: 초고변동성 서브시스템 - 진행상태 정리 + BL-1/BL-2/BL-3 착수 (2026-09-10)

## 🌳 컴포넌트 조합 (테크트리 관점)
*"discovery 몇건, confirmed 몇건"보다 "뭐랑 뭐가 합쳐져서 뭐가 나왔고, 이게 이전 세대보다 강한지"가 사용자가 지정한 진짜 목표 - 이 관점으로 이번주 정리.*
- 현재 트레잇매핑된 살아있는 알파: 22건, 평균 조합다양성 2.5종
- 단순자산확장(breadth-only): 5건 - 조합력 증가 없이 자산만 늘린 것
- 부모(단일요소)보다 강한 조합: 1건 / 약한 조합: **12건**
  - 약한 조합 목록: MULTICHANNEL_BREAKOUT_AGREEMENT_V1, WIDE_TRAIL_OPTIONALITY_V1, MULTITIMEFRAME_BREAKOUT_AGREEMENT_V1, DONCHIAN_TAKER_CONFLUENCE_V1, ATR_TAKER_CONFLUENCE_V1, KELTNER_TAKER_CONFLUENCE_V1, DAILY_MACD_TAKER_CONFLUENCE_V1, DAILY_MACD_TAKER_CONFLUENCE_HIGHVOL_V1, FUNDING_MOMENTUM_CONFIRMATION_V1, DONCHIAN_MOMENTUM_RANK_FILTER_V1, WHALE_DONCHIAN_CONFLUENCE_V1, DONCHIAN_EXIT_SWING_RR_V1
  - **솔직한 평가**: 지금까지 시도된 조합 대부분이 부모 단일요소보다 통계적으로 약함(k-of-n 합의류가 신호빈도를 줄여 표본이 희석되는 패턴 반복) - "조합하면 강해진다"는 가설이 아직 실증적으로 확인되지 않음, 다음주 다른 조합방식(예: 신호레벨 AND가 아니라 포트폴리오레벨 분산) 검토 필요.
- 다음주 시도해볼 미조합 트레잇쌍:
  - ATR비율 확장+모멘텀부호 순응 + 펀딩비율 단기/장기평균차 방향일치
  - ATR비율 확장+모멘텀부호 순응 + 1H+4H 동일지표 동시확인
  - 켈트너채널(EMA±ATR) 상/하단 돌파 + 펀딩비율 단기/장기평균차 방향일치

## 📈 검증 엄밀도
## 2026-09-08 (1차, 세션 진행 중 작성) — 살아있는 알파 29건 시점

### 세션 초반 대비 지금, 검증 엄밀도가 어디까지 올라왔나

**세션 초반(대략 D1~D140대)**: 가설 하나당 검증단계는 사실상 "TRAIN 그리드서치 → TEST 1회
→ 부트스트랩 CI가 1을 배제하는지"가 전부였음. 이건 나쁜 출발은 아니었음(rule5의 TRAIN/TEST
분리 자체는 처음부터 지켰음) - 하지만 딱 거기까지였고, 그 이상의 검증축은 없었음.

**지금 갖춰진 것**(오늘까지 실제로 코드로 존재하고 최소 1회 이상 실행된 것만 나열, 계획중인
것 제외):
1. **look-ahead perturbation 게이트**(`zec_new_indicator_gate.py`, D142 전후 도입) - 다만
   오늘(D255/D257) 이 게이트 자체에 구조적 결함(NaN-vacuity, 일봉MACD 3종 완전미검증)이
   있었다는 걸 발견하고 실측으로 메꿈. 게이트가 "있다"와 "제대로 작동한다"는 다르다는 걸
   이 세션 스스로 증명한 셈.
2. **다중비교보정**(Bonferroni + BH-FDR, `zec_multiple_comparison_correction.py`) - 그러나
   이건 "특정 시점의 스냅샷"일 뿐, 세션이 계속 진행되며 새 시도가 추가될 때마다 m(전체시도수)이
   바뀌므로 수동 재실행이 필요(자동 아님) - 이 한계는 아직 안 고쳐짐.
3. **DSR(Deflated Sharpe Ratio, Bailey&López de Prado)** - BH-FDR/Bonferroni와 다른 가정으로
   병기, 오늘 처음 실측한 4건 전부 DSR>0.95 미달(BH-FDR은 통과) - 두 방법이 갈릴 수 있다는 걸
   확인했지만, "그럼 어느 쪽을 최종기준으로 삼을지"는 아직 정책 결정이 안 됨(이것도 숙제).
4. **롤링 워크포워드 재검증** - 고변동성풀 트레일링 3종에서 "가장 최근 구간(2025-10~)만
   CI가 1을 포함"하는 패턴을 잡아냄(D252) - 단발성 TEST로는 절대 못 잡는 종류의 신호.
5. **적대적 재검토 게이트**(별도 컨텍스트 서브에이전트) - 첫 실행에서 바로 잘못된 confirmed
   1건(D248)을 잡아냄. **이게 이 세션에서 가장 확실하게 가치를 증명한 장치**.
6. **알파디케이 모니터링** - 다만 대부분 알파가 아직 표본부족(n<15)이라 실질적으로는 거의
   작동을 못 하고 있음(정상이지만, "갖췄다"와 "작동중이다"를 구분해야 함).
7. **메타엔진 피드백루프** - discovery_log/registry/사후분석을 스스로 읽고 다음 가설을 우선
   순위화 - 다만 오늘까지 이 엔진이 만든 가설 중 confirmed까지 간 게 아직 없음(가동 초기).

**정직한 평가**: 검증 "축"의 개수는 확실히 늘었음(1개→7개). 그런데 그 축들 중 몇 개
(다중비교보정의 수동재실행, 알파디케이의 표본부족, 메타엔진의 아직-확정없음)는 "설치는
됐지만 아직 실질적으로 자주 작동하지는 않는" 상태임. 오늘 게이트감사(D255/D257)에서 드러난
것처럼, "장치가 있다"는 착각을 실제로 깨는 데 진짜 시간을 씀 - 이게 엄밀도를 올리는 가장
현실적인 방법이었음(추상적으로 "더 엄격해지자"가 아니라, 구체적으로 하나씩 검사해서 구멍을
찾는 것).

### 다음에 더 올릴 수 있는 것 (사용자가 언급한 것 + 스스로 추가)

- **용량(capacity) 분석 — 미착수**: 지금 전부 페이퍼($1~60/자산 소액)라 슬리피지/시장충격을

*(전문은 zec_rigor_retrospective.md 참조)*

## 🧹 시스템 최적화/클린업 점검
*읽기전용 점검 - 아무것도 자동삭제하지 않음. 정리대상 후보는 사용자 확인 후 별도 조치.*
**[2026-09-09 안전원칙 확정] 삭제 대신 아카이브 - 클린업 실행시 항상 이 규칙**:
1. 파일: 삭제(rm) 대신 `_cleanup_archive/YYYYMMDD/`로 이동
2. 레지스트리행: 행삭제 대신 status만 `archived`로 변경(행 자체는 영구보존)
3. 예약작업: 즉시등록해제 대신 우선 비활성화 요청만 등록, 14일 유예 후 완전삭제 재검토
4. 아카이브 폴더 자체도 30일+ 지난 것은 검토대상으로만 나열(자동삭제 없음)

**1) 고아 스크립트 후보** (전체 .py 203개 중 run_*.bat(34개)/다른스크립트import 어디서도 미참조)
- 133개 발견(일부는 의도적 수동실행/1회성 분석스크립트일 수 있음 - 검토 필요, 자동삭제 안 함):
  - `bb_supertrend_reversal.py`
  - `cross_asset_param_lab.py`
  - `leverage_ev_search.py`
  - `leverage_scale_extended_grid.py`
  - `mtf_macd_hardlocked_backtest.py`
  - `symbol_full_discovery.py`
  - `symbol_full_discovery_v3.py`
  - `t5m_native_off_engine.py`
  - `t5m_orchestrator.py`
  - `withdrawal_simulation.py`
  - `zec_adaptive_trail_optionality_strategy.py`
  - `zec_asset_specific_optimizer.py`
  - `zec_atr_expansion_trailing_robustness_lf.py`
  - `zec_atr_expansion_trailing_strategy.py`
  - `zec_autocorr_regime_strategy.py`
  - `zec_autocorr_robustness.py`
  - `zec_avg_trade_size_strategy.py`
  - `zec_breakout_retest_confirmation_strategy.py`
  - `zec_btc_taker_spillover_strategy.py`
  - `zec_cointegration_spread_strategy.py`
  - `zec_confirmed_recipe_crossasset.py`
  - `zec_confluence_generalization_strategy.py`
  - `zec_conviction_candle_bigpool_strategy.py`
  - `zec_conviction_candle_strategy.py`
  - `zec_correlation_regime_strategy.py`
  - `zec_cross_exchange_basis_confirmation_strategy.py`
  - `zec_cross_sectional_momentum_rotation_strategy.py`
  - `zec_cross_sectional_momentum_strategy.py`
  - `zec_crossasset_paradigm_driver.py`
  - `zec_crosssectional_pool_split_strategy.py`
  - ...외 103개

**2) 예약작업(run_*.bat) 이슈** *(파일시스템 기반 근사 - 실제 Task Scheduler 등록/활성상태(Ready/Disabled)는 이 자동점검이 확인 못 함, PowerShell을 이 스크립트 내부에서 호출하면 이 환경에서 행(hang)이 걸리는 제약 있음 - 등록상태 확인은 Claude가 별도로 주기적 수동점검 권장)*
- ⚠️ run_interactive_backtest_app.bat: 대상 스크립트 없음: zec_interactive_backtest_app.py

**3) 오래된 캐시파일**(30일+ 미수정)
- kline_cache: 전체 1141개/388.4MB, 오래된것 0개/0.0MB
- kline_cache_takerbuy: 전체 1개/2.2MB, 오래된것 0개/0.0MB
- bybit_kline_cache: 전체 18개/13.9MB, 오래된것 0개/0.0MB
- leadtrader_cache: 전체 44개/1.9MB, 오래된것 0개/0.0MB
- whale_hourly_cache: 전체 11개/3.1MB, 오래된것 0개/0.0MB
- zec_test_trades_cache: 전체 4개/0.1MB, 오래된것 0개/0.0MB

**4) retracted 상태 레지스트리 행**
- retracted 행: 5건
- ALIVE_STATUSES에 누수됨: 아니오(정상 - 대시보드/리포트 집계에서 정상적으로 제외됨)
- 대상: VOLSKEW_CROSSASSET, FTM_MACD_DEEP_OPT, SKEWNESS_ASYMMETRY_V1, KURTOSIS_MOMENTUM_V1, AUTOCORR_REGIME_V1

**5) 아카이브 폴더 내 30일+ 경과 항목**(정리검토대상, 자동삭제 안 함)
- 없음(아카이브 폴더가 비어있거나 전부 최근것)

**6) 비활성화 요청 대기중인 예약작업**
- 없음

## 🎯 다음주 제안
- 특별한 방향전환 필요 없음 - 기존 진행중 트랙 계속
