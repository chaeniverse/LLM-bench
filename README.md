# LLM-bench

K-Pop 가상 아이돌 챗봇용 LLM 벤치마크 노트북 모음. 동일 모델의 행동 분석 (edge case · first chat) 과 모델 간 비교 (lightweight model selection) 두 갈래로 구성됩니다.

## Notebooks

| 축 | `notebooks/edge_case_test.ipynb` | `notebooks/first_chat_test.ipynb` | `notebooks/llm-bench.ipynb` |
|---|---|---|---|
| **변주 대상** | 시나리오 (16 edge case) | 캐릭터 (10인 × MBTI) | **모델 (4종)** |
| **테스트 모델** | Gemini-3-pro-preview 단일 | Gemini-3-pro-preview 단일 | Gemini-3-flash / Gemini-2.5-flash / Claude-Sonnet-4.5 / GPT-4o-latest |
| **시나리오** | 부정 위주 — 회사 기밀 요청 / 부적절 요청 / prompt injection / 반복 질문 / 일상 스트레스 / 심각 고민 | 긍정 위주 — 첫 인사 (greeting) | 혼합 — 인사 + 6 edge case |
| **평가 목적** | 단일 모델의 **안전성·robustness** 진단 | 단일 모델의 **캐릭터 일관성·인사 품질** | **모델 간 비교 / 경량 모델 선정** |
| **Judge** | LLM-as-Judge (5축 rubric) | LLM-as-Judge (자연스러움 / 캐릭터 일관성 / 감정 톤) | Claude-Sonnet-4-6 judge (5축 + 가중 종합 점수) |
| **결정 로직** | (없음 — 정성 검수) | (없음 — 정성 검수) | 응답시간 < 3s && 가중 종합 ≥ 4.0 → Top 모델 선정 |
| **출력** | 엣지 케이스별 HTML 카드 | 캐릭터 카드 HTML | dark HTML + 모델 비교 테이블 |

**한 줄 요약**

- `edge_case_test` 와 `first_chat_test` 는 **동일 모델 안에서 시나리오/캐릭터를 변주** 하는 정성 검증 (한 모델이 얼마나 잘 버티나·잘 표현하나).
- `llm-bench` 는 **모델 자체를 변주** 해서 비교·선정하는 정량 벤치마크 (어떤 모델을 쓸 것인가).

## 관련 포트폴리오 포스트

- [LLM Model Benchmark](https://chaeniverse.github.io/projects/kpop-virtual-idol-llm-benchmark/) — `edge_case_test`, `llm-bench`
- [MBTI Persona Priming](https://chaeniverse.github.io/projects/kpop-virtual-idol-mbti/) — `first_chat_test`

## 보안

K-Pop 가상 아이돌 앱 내부 정보는 prompt / 캐릭터 ID / config 파일 등에 포함되어, 본 repo에는 **3개 notebook 만** 공개합니다. 그 외 prompt config·결과 산출물·내부 도식은 별도 비공개 저장소에 보관합니다.
