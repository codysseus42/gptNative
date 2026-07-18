# gptNative
Beginner-made, hand-crafted prompts for LLM workflow automation.
gpt에게 일 제대로 시키기 abc

# 고객 클레임 대응 자동화 — 클레임처리GPT 프롬프트 엔지니어링

## 프로젝트 개요

고객 클레임 접수 → 담당자 상담 → **클레임 처리 제안서** 생성까지를 자동화하는
업무 특화 봇(클레임처리GPT)을 설계하고, 이 과업에 가장 적합한 LLM을 근거 기반으로 선정하는 프로젝트입니다.

### 업무 과업

담당자가 클레임 정보를 입력하면, 봇이 확인 질문을 거쳐 아래 6개 섹션의 제안서를 생성합니다.

1. 고객 답변 초안 (검토용)
2. 사실 정리 (확인된 사실 / 미검증 주장 분리)
3. 담당자 판단과 근거
4. 사측 권고 조치
5. 우려 내용 (자기검토)
6. 발송 전 담당자 확인사항

핵심 설계 목표는 **환각 방지**입니다. 근거를 유저 제출 자료로 한정하고,
미확인 정보는 `[확인필요]` `[추측]` `[내용모순]` 마커와 경고 블록으로 가시화합니다.

### 타겟 사용자

- CS/고객관계 담당자 (클레임 1차 대응)

### 입력 / 출력

| 구분 | 내용 |
| --- | --- |
| 입력 | 고객클레임 원문(필수) · 경위와 사실관계(필수) · 유저의견(필수) · 회사규정(조건부 필수) · 고객관계/참고자료/호칭/말투/확인질문규칙(선택) |
| 출력 | 상담 답변(평문) 또는 6섹션 제안서(+필요 시 경고·마커) |

---

## 제출 문서

| 문서 | 내용 | 바로가기 |
| --- | --- | --- |
| `01_model_comparison.md` | 후보 모델 4종 비교(동일 대본 10턴 실측) · 환각 검증 5문항 · 비용 산출 · 최종 선정 근거  | [01_model_comparison.md](./01_model_comparison.md) |
| `02_system_design.md` | 시스템 프롬프트 설계 의도 · 입력 템플릿 · Few-shot 예시 3종 · 되묻기(확인질문) 설계 · v1→v2 개선 | [02_system_design.md](./02_system_design.md) |
| `03_conversation_log.md` | 선정 모델 실행 로그(10턴+) · 조건 변경 2회(내용/어조) 반영 검증 | [03_conversation_log.md](./03_conversation_log.md) |

시스템 프롬프트 전문: [systemprompt_v1.md](./systemprompt_v1.md) · [systemprompt_v2.md](./systemprompt.md)

---

## 평가 기준 대응

| 평가 항목 | 대응 문서 | 해당 절 |
| --- | --- | --- |
| 업무 과업 정의 | [README.md](./README.md) | 프로젝트 개요 |
| 모델 비교 (3종 이상) | [01_model_comparison.md](./01_model_comparison.md) | 비교목적 |
| 비교 대상 모델명 | [01_model_comparison.md](./01_model_comparison.md) |비교목적 |
| 모델 비교 (3종 이상) | [01_model_comparison.md](./01_model_comparison.md) |비교에 사용한 동일 입력 |
| 비교 평가축(4개이상) | [01_model_comparison.md](./01_model_comparison.md) |평가축(점수표) |
| 비교 모델별 점수(1~5) | [01_model_comparison.md](./01_model_comparison.md) | 평가축(점수표)|
| 비교 근거 | [01_model_comparison.md](./01_model_comparison.md) | 평가축(점수표)|
| 최종 선정 결론(3줄이상) | [01_model_comparison.md](./01_model_comparison.md) | 최종 선정 근거|
| 과업 선택 문제정의 | [02_system_design.md](./02_system_design.md) | 문제정의 |
|타겟사용자| [02_system_design.md](./02_system_design.md) | 타겟사용자 |
| 유저프롬프트 포함 여부| [02_system_design.md](./02_system_design.md) | 업무 과업 입력 템플릿 |
| 입력 데이터 형태 | [02_system_design.md](./02_system_design.md) | 업무 과업 입력 템플릿 |
| 입력 템플릿 | [02_system_design.md](./02_system_design.md) | 업무 과업 입력 템플릿 |
| 페르소나를 구체적으로 정의(이름/역활(직무)/전문분야/말투/금지사항/우선순위| [02_system_design.md](./02_system_design.md) | 페르소나 |
| 시스템프롬프트 포함 여부 | [02_system_design.md](./02_system_design.md) | 시스템 프롬프트 |
| 출력 규격 | [02_system_design.md](./02_system_design.md) | 시스템 프롬프트 |
|역활(페르소나) | [02_system_design.md](./02_system_design.md) | 시스템 프롬프트 |
|목표(업무과업)| [02_system_design.md](./02_system_design.md) | 시스템 프롬프트 |
|출력 형식 규칙| [02_system_design.md](./02_system_design.md) | 시스템 프롬프트 |
|안전장치| [02_system_design.md](./02_system_design.md) | 시스템 프롬프트 |
|사실/정책/수치가 포함될 때의 처리 규칙| [02_system_design.md](./02_system_design.md) | 시스템 프롬프트 |
| Few-shot 예시(3개) | [02_system_design.md](./02_system_design.md) | Few-shot 설계 |
| 모호한 입력 되묻기 | [02_system_design.md](./02_system_design.md) | 환각 검증 설계 |
| 환각 검증 설계(사실 기반 검증 질문 5개) | [02_system_design.md](./02_system_design.md) | 환각 검증 설계 |
|합격기준 기대정답/허용오차/참고 근거 | [02_system_design.md](./02_system_design.md) | 환각 검증 설계 |
| 단계적 추론 유도 적용 | [02_system_design.md](./02_system_design.md) | 개선이력 (v1→v2 개선) |
| 시나리오 설명 | [03_conversation_log.md](./03_conversation_log.md) | 시나리오 설명 |
| 안전/윤리 개인정보,폭력/선정적 콘텐츠,사실/정책/수치 포함된 답변 근거/확인 필요 | [02_system_design.md](./02_system_design.md) | 시스템 프롬프트  |
| 10턴 이상 대화 전문 | [03_conversation_log.md](./03_conversation_log.md) | 10턴 이상 대화 전문 |
|조건변경/추가정보제공 | [03_conversation_log.md](./03_conversation_log.md) | 10턴 이상 대화 전문 |
|문맥유지 | [03_conversation_log.md](./03_conversation_log.md) | 10턴 이상 대화 전문 |
| 문제 지점과 개선 요약 | [03_conversation_log.md](./03_conversation_log.md) | 문제 지점과 개선 요약 (v1→v1.5->v2 개선)  |
|모델/환경 기록, 무료 버전 제한점|[01_model_comparison.md](./01_model_comparison.md),[03_conversation_log.md](./03_conversation_log.md)| 비교에 사용한 동일 입력,시나리오 설명|
| 제출문 편집 섹션/번호/요약,원본첨부 | [03_conversation_log.md](./03_conversation_log.md) | 10턴 이상 대화 전문,추가(로그)  |
| 보너스2-멀티모달 확장 결과의 시각화| [bonusImage](./bonus2) |이미지들 |
---

모든 실험은 동일 시스템 프롬프트·동일 대본·동일 설정(Together AI Playground)으로 수행하여
모델 간 비교의 공정성을 확보했습니다. 상세 설정은 각 문서의 실험 환경 절 참조.