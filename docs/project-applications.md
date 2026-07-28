# 프로젝트별 적용 사례

> 공개 포트폴리오의 최신 프로젝트 목적·O/H/L 기준 문서는 [project-specific-applications.md](project-specific-applications.md)다. 이 문서는 보조적인 적용 매트릭스이며, 이력서에서 대표 기준으로 링크하지 않는다.

모든 프로젝트에 같은 에이전트 구조를 억지로 붙이지 않았다. 반복적이고 예측 가능한 일은 규칙 기반 workflow로 두고, 모델·도구·사람의 역할이 갈리는 곳에만 오케스트레이션을 넣었다. 아래에서 **O**는 오케스트레이션, **H**는 하네스, **L**은 루프 엔지니어링을 뜻한다.

| 프로젝트 | O: 역할과 순서 | H: 경계와 중단 | L: 실패의 환류 |
|---|---|---|---|
| StockPulse AI | 규칙 기준선 → 선택적 LLM 코치 → 근거 확인 → 사용자 반영 | `evidence_trace`, 키·모델 오류 fallback, 추천 표현 제한 | trace·Playwright 실패를 표시 규칙과 fallback에 반영 |
| quiz-validator | 생성 문항 → 11개 규칙 → 공식 샘플 calibration → HARD/SOFT 판정 | 규칙·샘플·임계값 고정, 미통과 문항 보류 | 놓친 유형을 규칙·테스트·점수 보고에 추가 |
| Strategy Arena | 데이터 수집 → 구간 분리 → walk-forward·holdout → 리스크 점검 | OOS·시간 경계·리스크 한도, 미검증 후보 미승격 | search-loop 실패를 다음 실험 가드레일로 반영 |
| realestate-economy | 정시 수집 → 지표·규칙 → RAG → 로컬 모델 → API·화면 | 최신성·출처·key·healthcheck 확인 | 수집·API 오류를 상태 점검과 테스트로 환류 |
| 현재 Jupyter 모델 | 적격성 → 기준선 → 모델 역할 비교 → held-out·identity·track → 사람 검토 | notebook·JSON·manifest, proxy/실제 지표 분리 | gate 실패를 validator와 다음 조건에 반영하고 `NOT_APPROVED` 유지 |
| Document Forge | 동의·파일 확인 → 파싱 → AI proxy → 미리보기 | 파일·ZIP·HTML·shell·timeout·임시공간 제한 | 파싱·보안 실패를 다음 차단 조건으로 전환 |
| company-news-analyzer | 입력 → 뉴스·가격·가치평가 → freshness·exposure → 상태 표시 | kill switch, readiness, `pass/warn/block` | 오래된 자료와 준비 실패를 게이트에 반영 |
| KRA/keirin EV | 공식 수집 → 모델 → OOS·연도 분할 → 리스크 → fail-closed | 불확실·음수 결과 미승격, 시간 분할 | 실패 결과를 리스크 조건과 다음 검증으로 환류 |
| codex-global-skills | 설치 → 업데이트 → verify → 여러 환경 동기화 | 인증정보·세션 제외, `install.sh`·`verify.sh` | 환경별 실패를 호환성 검사로 되돌림 |
| Sentinel-30 | 구조화 추출 → RAG 근거 → 위험 라우팅 → 운영자 검토 | 개인정보·출처·사람 승인, 기획 범위 고정 | 애매한 사례를 분류 기준과 다음 시나리오로 환류 |
| we-meet | AI 제안 → 직접 실행 → 예외 확인 → 사용자 흐름 → 반영 | 제안 코드를 그대로 병합하지 않음 | 오류와 시연 피드백을 다음 질문·수정에 반영 |
| SSAFY 프로젝트 | 요구사항 → ERD·API → Must/Should → 마일스톤 → 여정 점검 | 범위·수용 기준·담당·일정 고정 | 주간 피드백을 backlog와 다음 마일스톤에 반영 |

## 공통으로 반복한 판단

1. 모델이 답을 만들었는지보다 기준선보다 나아졌는지 확인했다.
2. 출력에 출처·상태·불확실성을 붙이고, 확인되지 않은 결과는 `draft`, `review`, `blocked` 중 하나로 닫았다.
3. 모델·도구 실패를 숨기지 않고 규칙 결과, 수동 처리, fallback으로 되돌렸다.
4. 실패 원인을 입력 누락, 출처 충돌, 권한 문제, 도구 오류, 출력 형식 오류, 데이터 부적격 등으로 나눠 다음 테스트·프롬프트·규칙·SOP에 반영했다.

## 범위와 표현

이 문서는 개인 개발환경과 프로젝트에서 구성·시험한 방식을 설명한다. 비공개 프로젝트의 코드나 로컬 Jupyter 데이터는 공개하지 않으며, 이 저장소가 특정 기업에 적용된 성과나 production 정확도를 의미하지 않는다.
