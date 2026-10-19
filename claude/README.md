# Claude용 프롬프트 사전 검토

## Claude Code에 설치

이 저장소를 내려받고 저장소 폴더에서 아래 둘 중 하나를 실행하세요. 같은 이름의 스킬이 이미 있다면 먼저 내용을 비교하고 병합하세요. 아래 명령은 기존 파일이 있으면 중단합니다.

### 개인용 설치 · Windows PowerShell

```powershell
$reviewSkillPath = Join-Path $HOME '.claude/skills/prompt-review'
if (Test-Path -LiteralPath $reviewSkillPath) { throw '기존 prompt-review 스킬을 먼저 확인하세요.' }
New-Item -ItemType Directory -Path $reviewSkillPath -Force | Out-Null
Copy-Item -LiteralPath './claude/prompt-review/SKILL.md' -Destination $reviewSkillPath
```

### 개인용 설치 · macOS / Linux

```sh
if [ -e "$HOME/.claude/skills/prompt-review" ]; then
  printf '%s\n' '기존 prompt-review 스킬을 먼저 확인하세요.'
else
  mkdir -p "$HOME/.claude/skills/prompt-review" &&
    cp claude/prompt-review/SKILL.md "$HOME/.claude/skills/prompt-review/SKILL.md"
fi
```

프로젝트에만 적용하려면 해당 프로젝트의 `.claude/skills/prompt-review/SKILL.md`에 같은 파일을 넣으세요. 저장소의 `claude/` 폴더 자체는 Claude Code 자동 검색 경로가 아니므로 복사 설치가 필요합니다.

Claude Code에서 `/prompt-review`를 입력하고 검토할 원문을 전달하세요. 목록에 보이지 않으면 파일명·경로를 확인하고 새 세션에서 다시 확인하세요. 자연어 호출도 지원하도록 description에 조건을 넣었습니다.

```text
/prompt-review 팀 회의록을 정리해서 보내줘.
```

명령 뒤의 문장 또는 다음 메시지의 문안을 검토 대상으로 사용합니다. 여러 문안이 있으면 어느 문안을 검토할지 확인합니다.

## Claude 일반 대화·프로젝트

[SKILL.md](prompt-review/SKILL.md)의 YAML 앞부분(`---` 사이)을 제외한 본문을 대화 첫 메시지 또는 프로젝트 지침에 붙여 넣고, `프롬프트 검토해줘`와 원문을 보내세요. 이는 문안 적용 방식이며 Claude Code의 명령 설치와는 다릅니다.

사용자 정의 스킬을 지원하는 환경에서는 `prompt-review/` 폴더를 해당 환경의 공식 등록 방식으로 추가할 수 있습니다. 지원 여부와 메뉴는 계정·환경에 따라 확인하세요.

설치 구조와 호출 방식의 근거: [Claude Code 공식 Skills 문서](https://code.claude.com/docs/en/skills).
