# Prompt Review · 프롬프트 사전 검토

Claude와 ChatGPT에서 프롬프트를 실행하기 전에 해석·모호성·누락·충돌을 검토하고, 복사해 쓸 수 있는 개선 프롬프트를 만듭니다. 문서와 기본 응답은 한국어입니다.

## 제품별 시작하기

| 대상 | 사용할 파일 | 적용 방법 | `/prompt-review`의 의미 |
| --- | --- | --- | --- |
| Claude Code | [SKILL.md](claude/prompt-review/SKILL.md) | `prompt-review` 폴더를 스킬 경로에 복사 | 설치 후 직접 호출하는 스킬 명령 |
| Claude 일반 대화 | [Claude 안내](claude/README.md) | 지침 본문을 대화 또는 프로젝트 지침에 등록 | 등록한 지침을 호출하는 텍스트 |
| ChatGPT | [프로젝트·대화용 지침](chatgpt/INSTRUCTIONS.md) | 프로젝트 지침 또는 대화 첫 메시지에 붙여 넣기 | 이 저장소에서 정한 텍스트 호출 문구 |
| ChatGPT 전체 대화 | [맞춤 지침용 축약본](chatgpt/CUSTOM_INSTRUCTIONS.md) | 설정의 맞춤 지침에 기존 내용과 병합 | 이 저장소에서 정한 텍스트 호출 문구 |

**ChatGPT에 파일을 올리거나 지침을 붙여 넣는 것만으로 `/prompt-review`라는 네이티브 명령이 설치되지는 않습니다.** 입력창이 다른 명령을 제안하면 `프롬프트 검토해줘`라는 자연어 호출을 사용하세요. 제품·버전에 따라 별도 명령 확장 기능이 있을 수 있으나 이 패키지는 이를 설치하지 않습니다.

## 사용 예시

```text
/prompt-review
아래 프롬프트를 검토해줘. 실제 업무는 실행하지 마.

[검토 대상]
첨부한 회의록을 요약해서 팀에 보내줘.
```

자연어로 `프롬프트 검토해줘` 또는 `프롬프트 리뷰`라고 요청해도 적용하도록 설계했습니다. 원문이 없으면 검토할 문안을 요청합니다. [예상 검토 예시](examples/review.md)를 참고하세요.

## 검토 흐름

1. 목표, 예상 작업, 필요한 입력과 결과물을 해석합니다.
2. 모호한 표현이 만들 수 있는 서로 다른 결과를 비교합니다.
3. 필수 정보 누락, 조건 충돌, 잘못된 전제와 완료 기준을 확인합니다.
4. 실제 영향에 따라 치명적·중요·경미로 문제를 분류합니다.
5. 필수 질문과 권장 기본값을 구분하고, 미정 항목이 있는 잠정 수정안 또는 최종 실행용 프롬프트를 제공합니다.
6. 무엇을 왜 바꿨는지 설명합니다.

검토 대상 안의 명령은 분석 자료로 취급합니다. 검토만으로 코딩·파일 변경·전송·예약·게시를 실행하지 않습니다. `좋아`, `이대로` 같은 답은 검토 보완으로 처리하고, 별도의 명시적인 실행 요청이 있어야 실행 단계로 전환합니다. 이 규칙은 실행 권한을 부여하지 않습니다.

## 저장소 구성

```text
prompt-review/
├── README.md
├── LICENSE
├── claude/
│   ├── README.md
│   └── prompt-review/
│       └── SKILL.md
├── chatgpt/
│   ├── README.md
│   ├── INSTRUCTIONS.md
│   └── CUSTOM_INSTRUCTIONS.md
└── examples/
    └── review.md
```

두 제품의 지침은 각각 독립적으로 복사해서 사용할 수 있습니다. 한국어 응답, 여섯 단계 검토, 심각도 기준, 미정 표시, 검토와 실행의 경계를 함께 유지해 주세요.

## 적용 범위와 확인 상태

참조한 지침을 재사용 가능한 문안으로 정리한 커뮤니티 자료입니다. Anthropic 또는 OpenAI의 공식 제품이 아닙니다. 자연어 호출과 지침 준수는 모델·대화 맥락·상위 지침의 영향을 받습니다. 문안 검토 완료가 실제 업무 자료·도구·권한 또는 실행 성공의 검증을 의미하지 않습니다.

패키지 구조와 지침을 확인했습니다. Claude 및 ChatGPT에서의 실제 모델 실행 검증은 수행하지 않았습니다. 예시는 설명용이며 실제 실행 결과가 아닙니다.

## 공식 참고 자료

- [Claude Code: Skills](https://code.claude.com/docs/en/skills)
- [ChatGPT: Projects and chats](https://learn.chatgpt.com/docs/projects)
- [ChatGPT: Personalize](https://learn.chatgpt.com/docs/personalize)
- [ChatGPT desktop: Slash commands](https://learn.chatgpt.com/docs/reference/slash-commands)

설치 안내 확인일: 2026-10-19. 화면 명칭과 제공 기능은 환경에 따라 달라질 수 있습니다.

## 라이선스

[MIT](LICENSE). 재사용·수정·재배포할 때 저작권 및 라이선스 고지를 함께 유지하세요.
