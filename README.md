# unrhyme Training

> **Status:** Draft v0.1 — 방향성·제품 정의 단계입니다. 확정된 커리큘럼이 아닙니다.
> **Working title:** CareerForge by unrhyme (프로그램명은 가칭이며 추후 확정)

**unrhyme Training은 사회초년생이 AI를 활용해 자신의 경험을 재해석하고, 필요한 역량을 직접 만들고 증명하면서, 다음 커리어 선택지를 넓혀가는 개인 주도형 커리어 빌딩 프로그램입니다.**

회사에 필요한 AX 인재를 양성하는 기업교육이 아니라, 개인이 자신의 커리어에 투자하는 학습 환경을 만드는 것을 목표로 합니다.

- **대상:** 입사 1~3년 차, 현 직무의 확장·전환을 고민하지만 무엇을 증명해야 할지 막막한 사람
- **방법:** AI 리터러시 → 경력 구조화 → 시장/JD 해석 → 작은 프로젝트 제작 → 공개 포트폴리오 → 피드백·개선
- **성과:** 도구 수강 이력이 아니라, 본인이 설명할 수 있는 공개 결과물과 다음 커리어 행동

> 수료를 취업·이직 성공이나 특정 직무 역량의 공인 인증으로 표현하지 않습니다. 이 프로그램의 효과는 검증해야 할 가설입니다.

## 이 저장소는

unrhyme Training의 교육 철학, 프로그램 정의, 교육 자료, 데모, 템플릿, 검증 기록을 관리하는 단일 출처입니다. 기업 내부 AX 제품 저장소가 아닙니다.

## 현재 포함된 내용

| 경로 | 설명 |
|---|---|
| [`PROJECT.md`](./PROJECT.md) | 프로젝트 정의: 포지셔닝, 페르소나, 학습 철학, 프로그램 구조(초안), 로드맵, 미결정 질문 |
| [`examples/job-matcher/SKILL.md`](./examples/job-matcher/SKILL.md) | JD 적합성 평가 스킬 (`jd-fit-evaluator`) |

`PROJECT.md`에 제안된 나머지 폴더 구조(`docs/`, `datasets/`, `templates/` 등)는 아직 확정·구현되지 않았습니다.

## JD 적합성 평가 스킬 (`jd-fit-evaluator`)

Job Matching POC를 위한 스킬입니다. 학습자가 가진 경력 자료를 채용공고(JD)와 대조해, **어떤 요구사항에 어떤 근거가 있고 어디에 갭이 있는지**를 설명 가능한 형태로 정리합니다.

- **입력:** JD 텍스트(사용자가 직접 붙여넣기) + 경력 자료(PDF·docx 파일, 공개 포트폴리오 URL) 1개 이상
- **출력:** Markdown 리포트 (저장 위치·파일명은 사용자가 지정)
- **평가 방식:** 점수·퍼센트·합격 확률 없이 근거 중심의 정성 평가
  - 요구사항별 판정: `근거 확인` / `부분 근거` / `근거 없음(갭)`
  - 서술을 Fact / Interpretation / Assumption으로 구분
  - 평가 차원: 직무 일치, 필수 역량, 프로젝트 근거, 우대 역량, 도메인
  - 갭마다 입증을 위해 만들 수 있는 작은 결과물을 함께 제안

**가드레일**

- 채용공고를 크롤링하지 않고, 사용자가 제공한 JD 텍스트만 사용합니다.
- 근거 없는 경험·성과·수치를 만들어 넣거나 경력을 과장하지 않습니다.
- 자료에 없는 스킬은 맞는 것으로 판정하지 않습니다.
- 개인정보·회사 기밀·API 키는 리포트에 옮기지 않습니다.

> 현재 스킬 상태: 초안이며 실제 이력서·JD로 시범 실행한 검증은 아직 하지 않았습니다.

### 설치 (Claude Code 마켓플레이스)

이 저장소는 `unrhyme-jd-fit`이라는 Claude Code 플러그인 마켓플레이스입니다. 아래 두 방법 중 하나로 `jd-fit-evaluator` 플러그인을 설치할 수 있습니다.

**방법 1. 일반 터미널에서 실행** (macOS 터미널, Windows PowerShell 등. Claude Code 세션 밖)

```bash
claude plugin marketplace add ckyw/unrhyme-training-ai
claude plugin install jd-fit-evaluator@unrhyme-jd-fit
```

설치 확인: `claude plugin list`

**방법 2. Claude Code 세션 안에서 입력** (`claude`로 세션을 연 뒤 슬래시 명령으로 입력)

```text
/plugin marketplace add ckyw/unrhyme-training-ai
/plugin install jd-fit-evaluator@unrhyme-jd-fit
```

Claude Code 2.1.275 이상에서는 마켓플레이스 등록과 설치를 한 줄로도 할 수 있습니다.

```text
/plugin install jd-fit-evaluator --marketplace ckyw/unrhyme-training-ai
```

> `claude plugin ...`은 터미널 명령이고, `/plugin ...`은 Claude Code 세션 안의 슬래시 명령입니다. 두 형태를 섞어 쓰지 않도록 주의하세요.

| 파일 | 역할 |
|---|---|
| [`.claude-plugin/marketplace.json`](./.claude-plugin/marketplace.json) | 마켓플레이스 정의 (`name`: `unrhyme-jd-fit`, `owner`: `unrhyme`) |
| [`examples/job-matcher/.claude-plugin/plugin.json`](./examples/job-matcher/.claude-plugin/plugin.json) | 플러그인 정보 |
| [`examples/job-matcher/SKILL.md`](./examples/job-matcher/SKILL.md) | 스킬 본문 |

플러그인 버전은 `1.0`이며, `claude plugin validate`로 마켓플레이스와 플러그인 검증을 통과했습니다. Claude.ai에서 쓰려면 별도로 ZIP 업로드가 필요합니다.

## 운영 원칙

- **사실 구분:** `운영 확정 / 검증 중인 가설 / 예시`를 명확히 표기합니다.
- **난이도 분리:** `Demo / Core / Extension` 라벨을 붙입니다.
- **보안·윤리:** 개인정보, API 키, 실제 지원자의 이력서, 기업 내부 데이터는 저장소에 올리지 않습니다.
- **도구 독립성:** ChatGPT·Claude·Gemini·Codex는 대체 가능한 수단으로 취급합니다.

자세한 내용과 아직 결정되지 않은 질문은 [`PROJECT.md`](./PROJECT.md)를 참고하세요.
