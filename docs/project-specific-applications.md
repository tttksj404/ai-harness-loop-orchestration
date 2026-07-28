# 프로젝트별 적용 사례

이 저장소는 하나의 `AI Harness` 프로젝트를 대표하는 저장소가 아니라, 여러 프로젝트에서 오케스트레이션·하네스·루프 엔지니어링을 어떻게 적용했는지 보여주는 색인이다.

## 프로젝트 정체: 무엇을 만든 프로젝트인가

| 프로젝트 | 정체 |
|---|---|
| first_repo (공개 링크 보류) | 개인 AI 개발환경과 에이전트 운영 규칙을 관리하는 Agent Workspace다. |
| [ssafy-race](https://github.com/tttksj404/ssafy-race) | 주행 전략을 단일 변경 실험으로 검증하는 레이스 최적화 프로젝트다. |
| [uncensored-AI](https://github.com/tttksj404/uncensored-AI) | 작업 강도별 Ollama·GGUF 로컬 모델을 선택·호출하는 모델 라우터·에이전트 도구다. |
| [quiz-validator](https://github.com/tttksj404/quiz-validator) | 생성형 AI가 만든 객관식 연습문제를 점검하는 휴리스틱 품질 게이트다. |
| [AI- / Sentinel-30](https://github.com/tttksj404/AI-) | 보이스피싱 대응을 증거 구조화·위험 라우팅·운영자 검토로 설계한 AI 보안 개념·발표 프로젝트다. |
| [strategy-arena](https://github.com/tttksj404/strategy-arena) | Binance 공개 데이터로 암호자산 전략을 만들고 백테스트하는 연구용 웹앱이다. |
| [realestate-economy](https://github.com/tttksj404/realestate-economy) | 부동산 매물·거래·경매 데이터를 지역경제 신호로 분석하는 데이터 서비스 프로토타입이다. |
| StockPulse AI / AntHill | 뉴스·가격·규칙 기반 신호로 사용자의 매매 판단을 돕는 개인용 웹 서비스 프로토타입이다. |
| 현재 Jupyter AI 모델 프로젝트 | CCTV 사람 식별·추적 품질을 비교하는 진행 중인 GPU 모델 실험이다. |
| Document Forge / adsense | PDF·HWP/HWPX 문서 처리와 선택적 AI 글쓰기 신호를 제공하는 브라우저 우선 유틸리티다. |
| company-news-analyzer | 기업·ETF를 뉴스·가격·밸류에이션 자료로 분석하는 로컬 데이터 파이프라인이다. |
| KRA·keirin EV | 공식 경주 데이터로 기대값과 리스크를 검토하는 연구 프로젝트다. |
| codex-global-skills | 여러 환경에 Codex skill·prompt·loop 자산을 배포·검증하는 운영 자산이다. |
| we-meet | Unity·C#·Firebase로 로그인·서버 저장·일기 기능을 만든 팀 앱 프로젝트다. |
| SSAFY 2인 프로젝트 | 요구사항·ERD·API·일정·사용자 여정을 연결한 2인 팀 프로젝트다. |


| 프로젝트 | Orchestration | Harness | Loop engineering |
|---|---|---|---|
| first_repo (공개 링크 보류) | 역할·에이전트·도구·스킬로 작업을 분해하고 위임·검증·handoff 순서를 고정 | `_ai_context`, 규칙, 권한, 검증 경계 | 실패·미완료 상태를 readback과 continuation 조건에 반영 |
| [ssafy-race](https://github.com/tttksj404/ssafy-race) | spec → baseline → single change → measure → gate 순서 | 완주율·충돌·패널티·p95 loop time 게이트 | 개선이면 keep, 안정성 저하면 revert하고 다음 가설 생성 |
| [uncensored-AI](https://github.com/tttksj404/uncensored-AI) | 작업 강도별 로컬 모델 라우팅과 `ask`·`agent` 실행 모드 | read-only·write·shell·automatic 권한 모드 | session·regression·watchdog 테스트로 경계 재검증 |
| [quiz-validator](https://github.com/tttksj404/quiz-validator) | 생성 문항 → 규칙 → 공식 샘플 calibration → HARD/SOFT 판정 | 11개 규칙과 불확실 문항 보류 | 실패 유형을 다음 테스트 케이스로 환류 |
| [AI- / Sentinel-30](https://github.com/tttksj404/AI-) | 발화 → 구조화 증거 → 위험 유형 → 대응 시나리오 | 출처·개인정보·사람 검토 지점 | 누락·오탐 시나리오를 다음 분류 기준에 반영 |
| [strategy-arena](https://github.com/tttksj404/strategy-arena) | 수집 → 후보 → walk-forward/holdout → 리스크 검증 | 기간·OOS·리스크 한도 경계 | 실패 원인과 재현성을 다음 실험에 반영 |
| [realestate-economy](https://github.com/tttksj404/realestate-economy) | 수집 → 지역 계산 → 규칙 신호 → RAG → 로컬 모델 → API | 최신성·출처·key·health check | 수집·API 실패를 다음 실행 조건과 테스트로 환류 |

## 보조 색인과 비공개 사례

`ai-harness-loop-orchestration`은 위 프로젝트들을 연결하는 공개 색인이다. `first_repo`, StockPulse AI, 현재 Jupyter 기반 AI 모델 프로젝트, Document Forge, company-news-analyzer, KRA·keirin EV, codex-global-skills, we-meet, SSAFY 프로젝트는 실제 경험 근거를 보유하지만 공개 링크를 쓰지 않거나 공개 범위를 제한한다. 따라서 이 저장소에는 개인 데이터·비공개 코드·실험 산출물을 복사하지 않고 적용 방식만 기록한다.

### StockPulse AI / AntHill
- 무엇: 뉴스·가격·규칙 기반 신호로 사용자의 매매 판단을 돕는 개인용 웹 서비스 프로토타입이다.
- Orchestration: 규칙 기준선 → 필요 시 LLM 설명 → `evidence_trace` 확인 → 사용자 판단.
- Harness: 규칙 결과·LLM 설명·근거 계산을 분리하고 모델 실패 시 결정론적 fallback으로 돌아간다.
- Loop engineering: Playwright·trace 오류를 다음 규칙 테스트와 fallback 표시 조건에 반영한다.

### 현재 Jupyter 기반 AI 모델 프로젝트
- 무엇: CCTV 사람 식별·추적 품질을 비교하는 진행 중인 GPU 모델 실험이다.
- Orchestration: manifest·적격성 → baseline → 후보 역할 비교 → held-out·identity·track → 사람 검토.
- Harness: 결과 JSON·provenance·데이터 분할을 고정하고 response-level label과 logit·feature KD를 구분한다.
- Loop engineering: validator 결과를 `review`·`blocked`·`NOT_APPROVED`로 판정해 다음 notebook 조건에 반영한다.

### Document Forge / adsense
- 무엇: PDF·HWP/HWPX 문서 처리와 선택적 AI 글쓰기 신호를 제공하는 브라우저 우선 유틸리티다.
- Orchestration: 동의·파일 검사 → 파싱 → 정제·미리보기 → 선택적 AI proxy → 다운로드.
- Harness: ZIP 제한·sanitization·`shell=False`·timeout·임시 폴더 격리로 입력과 실행 범위를 제한한다.
- Loop engineering: 파싱·위험 파일 오류를 재현 가능한 안전 테스트와 blocker 조건으로 되돌린다.

### company-news-analyzer
- 무엇: 기업·ETF를 뉴스·가격·밸류에이션 자료로 분석하는 로컬 데이터 파이프라인이다.
- Orchestration: 입력 → 데이터 수집 → freshness·노출 한도 → 로컬 분석 → `pass/warn/block`.
- Harness: kill switch와 live-readiness gate로 오래된 자료를 확정 분석으로 내보내지 않는다.
- Loop engineering: stale 데이터와 준비 실패를 다음 수집·검증 조건으로 환류한다.

### KRA·keirin EV
- 무엇: 공식 경주 데이터로 기대값과 리스크를 검토하는 연구 프로젝트다.
- Orchestration: 공식 데이터 → 모델 → OOS·연도 분할 → 리스크 시뮬레이션 → 승격 여부.
- Harness: 음수·불확실한 결과는 +EV로 포장하지 않는 fail-closed 기준을 적용한다.
- Loop engineering: 검증 실패를 다음 모델·데이터 가설로 되돌리고 기준 미달 결과는 보류한다.

### codex-global-skills
- 무엇: 여러 환경에 Codex skill·prompt·loop 자산을 배포·검증하는 운영 자산이다.
- Orchestration: 설치 → 업데이트 → 호환성 확인 → verify → 동기화.
- Harness: `auth.json`·API key·브라우저 세션·MCP 로그인을 배포 대상에서 제외한다.
- Loop engineering: 환경별 실패를 호환성 체크리스트와 다음 배포 검증에 반영한다.

### we-meet
- 무엇: Unity·C#·Firebase로 로그인·서버 저장·일기 기능을 만든 팀 앱 프로젝트다.
- Orchestration: AI 제안 → 직접 실행 → 예외 확인 → 사용자 흐름 점검 → 기능 반영.
- Harness: AI 코드를 그대로 병합하지 않고 실제 실행과 예외 확인을 통과한 것만 반영한다.
- Loop engineering: 실행 오류를 다음 질문·수정·재실행으로 되돌린다.

### SSAFY 2인 프로젝트
- 무엇: 요구사항·ERD·API·일정·사용자 여정을 연결한 2인 팀 프로젝트다.
- Orchestration: 요구사항 → ERD/API → Must/Should → 마일스톤 → 사용자 여정.
- Harness: acceptance criteria·담당자·범위·일정을 고정해 합의되지 않은 확장을 통제한다.
- Loop engineering: 피드백과 구현 제약을 다음 backlog와 일정에 환류한다.

비공개·로컬 항목은 실제 코드·데이터·실험 결과를 이 저장소에 복사하지 않았으며, 위 목적과 적용 방식만 공개한다.

이력서에는 공개 프로젝트를 각각 별도 항목으로 적고, 이 저장소는 개별 항목을 대신하지 않는 보조 링크로 사용한다.
