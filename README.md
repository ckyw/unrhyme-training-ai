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
| [`docs/trial-demo/index.html`](./docs/trial-demo/index.html) | 2시간 트라이얼 HTML 발표 덱: 32장, 강사 메모, 실습 프롬프트, 타이머와 샘플 |
| [`examples/job-matcher/SKILL.md`](./examples/job-matcher/SKILL.md) | JD 적합성 평가 스킬 (`jd-fit-evaluator`) |

`docs/trial-demo/`에는 첫 트라이얼 덱이 구현되어 있습니다. `PROJECT.md`에 제안된 다른 교육 자료와 `datasets/`, `templates/` 등의 나머지 구조는 아직 확정·구현되지 않았습니다.

## 2시간 트라이얼 발표 덱

[**HTML 발표 덱 보기 및 다운로드**](./docs/trial-demo/index.html)

`PROJECT.md`의 Discovery Session을 구체화한 **32장·120분 첫 운영안**입니다. 사회초년생이 자신의 경험을 정리하고 관심 직무와 비교한 뒤, AI와 함께 작은 웹페이지를 수정하는 흐름으로 진행합니다. 패션·리테일 경력자의 전직을 예시로 사용하며, 공고와 경력 사례는 모두 수업용 가상 자료입니다.

### 실행 방법

1. 위 링크에서 GitHub 파일 화면을 엽니다.
2. **Download raw file**로 `index.html`을 내려받습니다.
3. 저장한 HTML 파일을 Chrome·Edge 등 브라우저에서 엽니다.

발표 화면은 CSS와 JavaScript를 포함한 단일 HTML 파일로, 별도 설치나 인터넷 연결 없이 실행할 수 있습니다. AI 실습은 참가자가 사용하는 AI 대화창과 인터넷 연결이 필요합니다. API 키나 유료 계정은 필수 조건이 아닙니다. 덱은 AI 분석 API를 실행하거나 개인 정보를 수집하지 않습니다.

### 120분 진행 구성

| 시간 | 활동 | 주요 결과 |
|---|---|---|
| 0~10분 | 오리엔테이션과 목표 공유 | 현재 경험과 관심 직무 |
| 10~25분 | AI와 일하는 방법 | 맥락 있는 요청, 사실·해석·가정 구분 |
| 25~45분 | 경력 프로필 작성 | 경험 3개와 자기소개 초안 |
| 45~65분 | 관심 JD 분석 | 업무·필수 조건·우대 조건과 근거 |
| 65~75분 | 휴식 | 작성한 자료 저장 |
| 75~95분 | 경험과 직무의 갭 분석 | 근거 상태와 보완 과제 1개 |
| 95~115분 | HTML 데모 수정과 검증 | 바뀐 화면과 직접 확인한 항목 |
| 115~120분 | 회고와 다음 행동 | 다음 7일 실행 계획 |

### 포함된 발표·실습 도구

- **강사 메모:** 슬라이드별 권장 시간, 진행 가이드, 다음 슬라이드 안내
- **프롬프트 4종:** 경력 정리, JD 분석, 갭 분석, HTML 수정 요청과 복사 버튼
- **실습 타이머:** 시작·일시정지·초기화, 슬라이드 이동 중에도 진행
- **실습용 HTML:** 26·27번 슬라이드에서 `career-demo.html` 다운로드. 26번에서는 샘플 화면도 열어볼 수 있습니다.
- **발표 조작:** 목차, 전체화면, 작은 화면 대응, 인쇄용 레이아웃

| 키 | 기능 |
|---|---|
| `←` `→` 또는 `Space` | 슬라이드 이동 |
| `Home` / `End` | 처음 / 마지막 슬라이드 |
| `O` / `N` | 목차 / 강사 메모 |
| `T` / `F` | 타이머 / 전체화면 |
| `H` / `Esc` | 도움말 / 열린 창 닫기 |
| `P` | 브라우저 인쇄 및 PDF 저장 |

강사 메모는 화면 공유에 보일 수 있으므로 참가자에게 화면을 공유하기 전에 닫아주세요. PDF 저장 시 배경 그래픽을 켜면 슬라이드 색상을 유지할 수 있습니다. 실습 결과에는 실제로 확인한 경험과 근거만 사용하고, 회사 기밀과 개인 정보는 입력하지 않습니다.

마지막에 소개하는 4주 Core 파일럿은 후속 프로그램의 기획안입니다. 운영 일정·모집·가격은 아직 확정하지 않았습니다.

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

## 저장소 작업 방식

GitHub 수정·커밋·푸시는 **Git과 인증된 GitHub CLI(`gh`)를 우선 사용**합니다. 컴퓨터 유즈는 사용자가 명시적으로 요청한 경우에만 사용합니다. 작업 전 기존 내용과 원격 변경을 비교하고, 테스트 후 변경 파일만 커밋하며, 푸시 후 원격 SHA를 확인합니다.

- [에이전트 작업 규칙](./AGENTS.md)
- [인증 준비와 GitHub 작업 절차](./directives/github-workflow.md)

## 운영 원칙

- **사실 구분:** `운영 확정 / 검증 중인 가설 / 예시`를 명확히 표기합니다.
- **난이도 분리:** `Demo / Core / Extension` 라벨을 붙입니다.
- **보안·윤리:** 개인정보, API 키, 실제 지원자의 이력서, 기업 내부 데이터는 저장소에 올리지 않습니다.
- **도구 독립성:** ChatGPT·Claude·Gemini·Codex는 대체 가능한 수단으로 취급합니다.

자세한 내용과 아직 결정되지 않은 질문은 [`PROJECT.md`](./PROJECT.md)를 참고하세요.
