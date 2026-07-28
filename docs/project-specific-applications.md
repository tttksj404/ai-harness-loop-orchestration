# 프로젝트별 적용 사례

이 저장소는 하나의 `AI Harness` 프로젝트를 대표하는 저장소가 아니라, 여러 프로젝트에서 오케스트레이션·하네스·루프 엔지니어링을 어떻게 적용했는지 보여주는 색인이다.

| 프로젝트 | Orchestration | Harness | Loop engineering |
|---|---|---|---|
| [first_repo](https://github.com/tttksj404/first_repo) | 역할·에이전트·도구·스킬로 작업을 분해하고 위임·검증·handoff 순서를 고정 | `_ai_context`, 규칙, 권한, 검증 경계 | 실패·미완료 상태를 readback과 continuation 조건에 반영 |
| [ssafy-race](https://github.com/tttksj404/ssafy-race) | spec → baseline → single change → measure → gate 순서 | 완주율·충돌·패널티·p95 loop time 게이트 | 개선이면 keep, 안정성 저하면 revert하고 다음 가설 생성 |
| [uncensored-AI](https://github.com/tttksj404/uncensored-AI) | 작업 강도별 로컬 모델 라우팅과 `ask`·`agent` 실행 모드 | read-only·write·shell·automatic 권한 모드 | session·regression·watchdog 테스트로 경계 재검증 |
| [quiz-validator](https://github.com/tttksj404/quiz-validator) | 생성 문항 → 규칙 → 공식 샘플 calibration → HARD/SOFT 판정 | 11개 규칙과 불확실 문항 보류 | 실패 유형을 다음 테스트 케이스로 환류 |
| [AI- / Sentinel-30](https://github.com/tttksj404/AI-) | 발화 → 구조화 증거 → 위험 유형 → 대응 시나리오 | 출처·개인정보·사람 검토 지점 | 누락·오탐 시나리오를 다음 분류 기준에 반영 |
| [strategy-arena](https://github.com/tttksj404/strategy-arena) | 수집 → 후보 → walk-forward/holdout → 리스크 검증 | 기간·OOS·리스크 한도 경계 | 실패 원인과 재현성을 다음 실험에 반영 |
| [realestate-economy](https://github.com/tttksj404/realestate-economy) | 수집 → 지역 계산 → 규칙 신호 → RAG → 로컬 모델 → API | 최신성·출처·key·health check | 수집·API 실패를 다음 실행 조건과 테스트로 환류 |

## 프로젝트가 무엇이었는가

- **first_repo**: 개인 AI 개발환경을 위한 Agent Workspace다. `_ai_context`와 `AGENTS.md`로 작업 규칙, 에이전트 역할, 도구, 검증, handoff를 운영한다.
- **ssafy-race**: 주행 전략을 한 번에 바꾸지 않고 baseline과 단일 변경 실험으로 비교하는 레이스 최적화 프로젝트다. 생성형 AI 제품이 아니라 실험 설계와 loop engineering 사례다.
- **uncensored-AI**: Ollama·GGUF 로컬 모델을 작업 강도에 따라 선택하고, `list`·`route`·`ask`·`agent`로 호출하는 로컬 모델 라우터다.
- **quiz-validator**: 생성형 AI가 만든 객관식 연습문제를 11개 규칙과 공식 AWS SAA 샘플 calibration으로 점검하는 품질 게이트다.
- **AI- / Sentinel-30**: 보이스피싱 대응을 증거 구조화·위험 라우팅·운영자 검토로 설계한 AI 보안 개념·발표 프로젝트다. production 안티프로드 서비스로 주장하지 않는다.
- **strategy-arena**: Binance 공개 데이터를 이용해 암호자산 전략을 만들고 백테스트하는 연구용 웹앱이다. 실거래 봇이 아니라 OOS·리스크 검증을 위한 분석 도구다.
- **realestate-economy**: 부동산 매물·거래·경매 데이터를 지역경제 신호로 분석하는 데이터 서비스 프로토타입이다. 수집·지표·RAG·로컬 모델·API를 연결한다.

## 보조 색인과 비공개 사례

`ai-harness-loop-orchestration`은 위 프로젝트들을 연결하는 공개 색인이다. StockPulse AI, 현재 Jupyter 기반 AI 모델 프로젝트, Document Forge, company-news-analyzer, KRA·keirin EV, codex-global-skills, we-meet, SSAFY 프로젝트는 실제 경험 근거를 보유하지만 공개 링크가 없거나 공개 범위를 제한한다. 따라서 이 저장소에는 개인 데이터·비공개 코드·실험 산출물을 복사하지 않고 적용 방식만 기록한다.

이력서에는 공개 프로젝트를 각각 별도 항목으로 적고, 이 저장소는 개별 항목을 대신하지 않는 보조 링크로 사용한다.
