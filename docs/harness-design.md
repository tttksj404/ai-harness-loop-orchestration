# Harness design checklist

하네스는 모델에게 일을 시키는 프롬프트 모음이 아니라, 업무 경계를 실행 가능한 계약으로 만드는 장치다.

## 입력 계약

| 항목 | 질문 | 실패 시 동작 |
|---|---|---|
| 목적 | 이 요청은 어떤 업무 결정을 돕는가? | 목적이 불명확하면 사람에게 되돌림 |
| 데이터 등급 | 공개·내부·제한·개인정보 중 어디인가? | 등급 확인 전 외부 모델 호출 금지 |
| 출처 | 문서 버전·작성일·소유자가 확인되는가? | 출처 없는 답변 보류 |
| 범위 | 이번 실행이 읽고 쓸 수 있는 범위는 어디까지인가? | 범위를 벗어난 도구 호출 차단 |

## 실행 계약

- 도구는 allowlist로 관리하고, 읽기와 쓰기 권한을 구분한다.
- 외부 전송·파일 변경·업무 시스템 반영은 기본적으로 승인 대기한다.
- 출력은 자유 문장만 받지 않고 `answer`, `evidence`, `confidence`, `status`, `next_action` 같은 필드를 갖게 한다.
- 검증되지 않은 결과는 `draft` 또는 `review` 상태로 닫는다.
- 모델이 실패하면 기준선·규칙·수동 처리로 돌아갈 수 있어야 한다.

## 출력 계약 예시

```json
{
  "status": "draft",
  "answer": "승인된 문서에서 확인한 초안",
  "evidence": [
    {"source": "approved-document-id", "version": "v1.2", "section": "3.1"}
  ],
  "uncertainties": ["최종 품질 판정은 담당자 확인 필요"],
  "next_action": "quality-review"
}
```

## 최소 게이트

1. 입력 자료와 권한이 계약에 맞는가?
2. 결과에 출처와 상태가 있는가?
3. 기준선과 비교했는가?
4. 예외·금지 조건을 검출했는가?
5. 담당자가 승인할 수 있는 형태인가?
6. 실행 기록에서 다음 개선점을 찾을 수 있는가?

## 그래프와의 경계

하네스가 허용하는 권한과 도구가 그래프의 노드 계약보다 우선한다. 그래프에 `write` 노드가 있어도 하네스가 승인 전 쓰기를 금지하면 `waiting_human_approval` 또는 `blocked`로 종료해야 한다.

- 노드는 입력·출력 schema, side effect, 허용 도구, evidence, retry budget을 가진다.
- 엣지는 성공·실패·route·parallel·join·interrupt·compensation 조건을 가진다.
- 실행 상태에는 `run_id`, `checkpoint`, node run, evidence, decision, idempotency key가 남는다.

실행 그래프의 전체 설계와 예시는 [Graph Engineering 가이드](graph-engineering.md)와 [`examples/graph-run-contract.yaml`](../examples/graph-run-contract.yaml)에 있다.
