# 컴퓨터 유즈 없이 GitHub 작업하기

## 목표와 범위

`ckyw/unrhyme-training-ai`의 파일을 기존 내용과 비교해 수정하고, 테스트 후 Git CLI로 커밋·푸시한다. GitHub CLI는 계정 확인과 API 조회에 사용한다. 브라우저 조작은 사용자가 명시적으로 요청한 경우에만 사용한다.

## 입력과 출력

- 입력: 사용자의 변경 요청, 현재 저장소, 인증된 `gh` 계정
- 출력: 검증한 원격 커밋 SHA, 변경 파일 URL, 테스트 결과

## 인증 준비

Git과 GitHub CLI가 설치되어 있고 `gh api user --jq .login`이 의도한 계정을 반환하는지 확인한다. 토큰 자체를 출력하지 않는다.

이 저장소의 최초 설정에서는 기존 `ckyw` 인증을 사용했고, 저장소 로컬 Git 설정에만 GitHub CLI 인증 도우미를 연결했다. 이 설정은 `.git/config`에 있으므로 복제·다른 컴퓨터로 자동 전달되지 않는다. 전역 Git 설정과 `.env`는 변경하지 않았다.

새 복제본에서도 기존 `gh` 인증을 사용하려면 해당 저장소 폴더에서 다음을 실행한다. `gh`가 실행 경로에 있어야 한다.

```sh
git config --local --replace-all credential.https://github.com.helper ''
git config --local --add credential.https://github.com.helper '!gh auth git-credential'
```

기존 인증이 없다면 사용자에게 `gh auth login --hostname github.com --git-protocol https`로 로그인하도록 안내한다. 인증정보를 채팅으로 요청하거나 저장소에 저장하지 않는다.

## 실행 절차

1. `git remote get-url origin`, `git status --short --branch`로 대상과 로컬 변경을 확인한다.
2. `gh api repos/ckyw/unrhyme-training-ai --jq '{default_branch, permissions}'`로 기본 브랜치와 계정 권한을 확인한다.
3. `git fetch origin` 후 원격 변경을 확인한다. 로컬 작업이 깨끗하고 현재 브랜치가 원격보다 뒤에만 있으면 `git pull --ff-only`로 갱신한다. 분기되었거나 미커밋 변경이 있으면 덮어쓰지 않고 차이를 확인해 보존한다.
4. 기존 파일과 비교해 요청한 변경만 적용한다. 반복 작업은 `execution/`의 기존 도구를 먼저 확인한다.
5. 관련 테스트와 `git diff --check`를 실행한다. 문서만 바꾼 경우에도 링크·경로와 실제 절차를 확인한다.
6. `git diff`를 검토하고 수정한 파일만 경로를 지정해 스테이징한다. `git diff --cached`로 최종 범위를 확인한 후 커밋한다.
7. 현재 작업 브랜치와 사용자가 요청한 반영 대상을 확인한 뒤 일반 푸시한다. 강제 푸시는 하지 않는다. PR이 필요한 브랜치 규칙이 있으면 그 규칙을 따른다.
8. `git rev-parse HEAD`와 원격 브랜치 SHA를 비교하고, GitHub API로 해당 커밋의 변경 파일을 확인한다. 커밋 URL과 변경 파일 URL을 보고한다.

## 오류와 예외

- **연동 API 403:** `Resource not accessible by integration`은 연동 자체의 권한 제한일 수 있다. 2026-10-21 확인 당시 연결 도구의 blob 쓰기는 403이었지만 기존 `gh` 인증과 Git 푸시는 사용할 수 있었다. 기존 CLI 경로를 사용하고, 광범위한 플러그인 권한 변경이나 브라우저 전환을 자동 수행하지 않는다.
- **샌드박스 네트워크 제한:** 네트워크 요청 실패만으로 인증 만료라고 판단하지 않는다. 허용된 네트워크 실행 경로에서 다시 확인한다. 자동 승인 검토가 거부한 작업은 우회하지 않는다.
- **인증 실패:** 계정과 인증 상태를 확인한다. 필요한 경우 사용자 로그인 단계만 요청한다.
- **동시 원격 변경:** 푸시가 거절되면 다시 fetch하고 차이를 검토한다. 다른 변경을 보존한 채 조정하고 테스트 후 푸시한다.
- **브랜치 보호:** 보호 규칙을 변경하지 않고 별도 브랜치와 PR을 사용한다.
