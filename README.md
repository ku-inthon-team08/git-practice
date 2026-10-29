# git-practice

해커톤 전까지 자유롭게 연습하셔도 됩니다!

---

## ⚡ 한눈에 보기

> **내 브랜치를 만들고 → 수정하고 → 커밋해서 → 푸시한 뒤 → PR(Pull Request)을 올린다.**
> 이 5단계만 기억하면 협업은 끝!

```text
 ① 브랜치 만들기  →  ② 코드 수정  →  ③ 커밋  →  ④ 푸시  →  ⑤ PR 올리기  →  팀원 확인 후 병합(Merge)
```

### 🧾 복사해서 쓰는 최소 명령어

```bash
git pull origin main                  # 0. 최신 코드 받기
git switch -c feature/내작업          # 1. 내 브랜치 만들고 이동
# ... 파일 수정 ...
git add .                             # 2. 변경 파일 담기
git commit -m "feat: 로그인 버튼 추가"  # 3. 기록 남기기
git push -u origin feature/내작업     # 4. GitHub에 올리기
# 5. GitHub 웹에서 Pull Request 생성
```

---

## 📑 목차

1. [처음 한 번만 하는 준비](#1-처음-한-번만-하는-준비)
2. [기본 개념 3분 정리](#2-기본-개념-3분-정리)
3. [협업 작업 순서 (단계별)](#3-협업-작업-순서-단계별)
4. [커밋 메시지 규칙](#4-커밋-메시지-규칙)
5. [충돌(Conflict) 해결하기](#5-충돌conflict-해결하기)
6. [자주 하는 실수와 해결법](#6-자주-하는-실수와-해결법)
7. [명령어 치트시트](#7-명령어-치트시트)
8. [꼭 지켜요! 협업 약속](#8-꼭-지켜요-협업-약속)

---

## 1. 처음 한 번만 하는 준비

### ① Git 설치 확인

```bash
git --version
```

버전이 나오면 설치 완료! 안 나온다면 [git-scm.com](https://git-scm.com)에서 설치해요.

### ② 내 정보 등록

커밋에 **누가 작업했는지** 이름이 남아요. GitHub 가입 이메일을 쓰는 걸 추천해요.

```bash
git config --global user.name "내 이름"
git config --global user.email "내 이메일@example.com"
```

### ③ 저장소 내려받기 (clone)

```bash
git clone https://github.com/ku-inthon-team08/git-practice.git
cd git-practice
```

> 💡 `clone`은 **딱 한 번만** 하면 돼요. 이후엔 `pull`로 최신 상태를 받아요.

---

## 2. 기본 개념 3분 정리

| 용어 | 쉬운 설명 |
|------|-----------|
| **Repository (저장소)** | 프로젝트 파일과 변경 기록을 모아둔 폴더 |
| **Remote (원격)** | GitHub에 있는 저장소 (`origin`이라고 불러요) |
| **Local (로컬)** | 내 컴퓨터에 있는 저장소 |
| **Branch (브랜치)** | 원본을 건드리지 않고 작업하는 **나만의 작업 공간** |
| **Commit (커밋)** | 변경 내용을 저장하는 **스냅샷** (게임의 세이브 포인트) |
| **Push (푸시)** | 내 컴퓨터의 커밋을 GitHub로 **올리기** |
| **Pull (풀)** | GitHub의 최신 내용을 내 컴퓨터로 **받아오기** |
| **Pull Request (PR)** | "내 작업을 합쳐주세요!" 하는 **요청서** |
| **Merge (병합)** | 브랜치의 작업을 메인에 **합치기** |

### 🗺️ 파일이 이동하는 길

```text
 작업 폴더 ──add──▶ 스테이징 ──commit──▶ 내 컴퓨터 저장소 ──push──▶ GitHub
 (수정 중)         (담아둠)            (기록 완료)             (공유 완료)
                                                      ◀──pull── 
```

---

## 3. 협업 작업 순서 (단계별)

### Step 0. 최신 상태로 맞추기 (작업 시작 전 필수!)

```bash
git switch main
git pull origin main
```

> ✅ 작업 전에 항상 최신 코드를 받아요. 안 그러면 나중에 충돌이 많이 생겨요.

### Step 1. 내 브랜치 만들기

```bash
git switch -c feature/로그인
```

- `-c` = 새로 만들면서 이동
- 브랜치 이름 예시: `feature/로그인`, `fix/오타수정`, `docs/readme`
- **`main`에서 직접 작업하지 않아요!**

### Step 2. 코드 수정하기

평소처럼 파일을 편집해요. 중간중간 상태를 확인하면 좋아요.

```bash
git status      # 어떤 파일이 바뀌었는지 보기
git diff        # 정확히 뭐가 바뀌었는지 보기
```

### Step 3. 커밋하기 (저장 + 기록)

```bash
git add .
git commit -m "feat: 로그인 버튼 추가"
```

- `git add .` : 바뀐 파일을 전부 담기
- 특정 파일만 담고 싶다면 `git add index.html`
- 작은 단위로 **자주** 커밋하는 게 좋아요.

### Step 4. GitHub에 푸시하기

```bash
git push -u origin feature/로그인
```

> 💡 처음 푸시할 때만 `-u`를 붙여요. 이후엔 `git push`만 써도 돼요.

### Step 5. Pull Request 만들기

1. GitHub 저장소 페이지로 이동
2. 노란색 **`Compare & pull request`** 버튼 클릭
3. **제목**과 **설명**을 작성 (무엇을, 왜 바꿨는지)
4. 오른쪽 **Reviewers**에 팀원 지정
5. **`Create pull request`** 클릭

### Step 6. 리뷰 받고 병합하기

- 팀원이 코드를 보고 코멘트를 남겨요.
- 수정 요청이 있으면 **같은 브랜치에서** 수정 → 커밋 → 푸시하면 PR에 자동 반영돼요.
- 승인(Approve)을 받으면 **`Merge pull request`** 버튼으로 병합해요.
- 병합 후 브랜치는 `Delete branch`로 정리해요.

### Step 7. 병합 후 내 컴퓨터 정리

```bash
git switch main
git pull origin main
git branch -d feature/로그인
```

그리고 다음 작업은 다시 **Step 0**부터! 🔁

---

## 4. 커밋 메시지 규칙

**"무엇을 했는지"가 한눈에 보이게** 써요.

```text
타입: 한 줄 요약
```

| 타입 | 언제 쓰나요? | 예시 |
|------|--------------|------|
| `feat` | 새 기능 추가 | `feat: 회원가입 폼 추가` |
| `fix` | 버그 수정 | `fix: 버튼 클릭 안 되는 문제 해결` |
| `docs` | 문서 수정 | `docs: README 사용법 추가` |
| `style` | 디자인/포맷 수정 (기능 변화 없음) | `style: 메인 색상 변경` |
| `refactor` | 코드 정리 (기능 변화 없음) | `refactor: 중복 함수 분리` |
| `chore` | 기타 설정 | `chore: .gitignore 추가` |

**✅ 좋은 예 / ❌ 나쁜 예**

```text
✅ feat: 로그인 버튼 추가
✅ fix: 모바일에서 메뉴가 안 보이는 문제 수정

❌ 수정
❌ ㅇㅇ
❌ 이것저것 고침
```

---

## 5. 충돌(Conflict) 해결하기

**충돌이란?** 같은 파일의 같은 부분을 두 사람이 동시에 고쳤을 때 Git이 "어느 쪽이 맞아요?" 하고 물어보는 상황이에요. **오류가 아니라 자연스러운 일**이니 당황하지 않아도 돼요!

### 해결 순서

**① 최신 main을 내 브랜치로 가져오기**

```bash
git switch feature/로그인
git pull origin main
```

**② 충돌 표시 찾기** — 파일을 열면 이런 표시가 보여요.

```text
<<<<<<< HEAD
내가 작성한 내용
=======
팀원이 작성한 내용
>>>>>>> main
```

**③ 원하는 내용만 남기고 표시(`<<<<<<<`, `=======`, `>>>>>>>`)는 모두 지우기**

> 어떤 걸 남길지 헷갈리면 **작성한 팀원과 함께** 정해요. 🙌

**④ 저장 후 다시 커밋 & 푸시**

```bash
git add .
git commit -m "fix: 충돌 해결"
git push
```

---

## 6. 자주 하는 실수와 해결법

| 상황 | 해결 방법 |
|------|-----------|
| 커밋 메시지를 잘못 썼어요 (아직 푸시 전) | `git commit --amend -m "새 메시지"` |
| `add`를 잘못한 파일이 있어요 | `git restore --staged 파일명` |
| 수정한 내용을 되돌리고 싶어요 | `git restore 파일명` ⚠️ 저장 안 한 변경은 사라져요 |
| 엉뚱한 브랜치에서 작업했어요 | 새 브랜치를 만들어 이동: `git switch -c 새브랜치` (변경사항이 함께 따라와요) |
| 지금 어느 브랜치인지 모르겠어요 | `git branch` (`*` 표시가 현재 위치) |
| `push`가 거절(rejected)됐어요 | 먼저 `git pull origin 브랜치명` 후 다시 `git push` |
| 작업하다 급하게 브랜치를 옮겨야 해요 | `git stash`로 임시 보관 → 이동 후 `git stash pop`으로 복구 |
| 지난 기록을 보고 싶어요 | `git log --oneline` |

> 🚫 **`git push --force`는 팀원의 작업을 지울 수 있어요.** 팀원과 상의 없이 쓰지 않아요!

---

## 7. 명령어 치트시트

### 📥 시작 · 받아오기

```bash
git clone <주소>              # 저장소 내려받기 (처음 1회)
git pull origin main          # 최신 내용 받기
git fetch                     # 변경 여부만 확인 (내용은 반영 안 함)
```

### 🌿 브랜치

```bash
git branch                    # 브랜치 목록 보기
git switch 브랜치명           # 브랜치 이동
git switch -c 브랜치명        # 새 브랜치 만들고 이동
git branch -d 브랜치명        # 브랜치 삭제
```

### 💾 저장 · 올리기

```bash
git status                    # 현재 상태 확인
git add .                     # 전체 변경사항 담기
git commit -m "메시지"        # 커밋
git push -u origin 브랜치명   # 푸시 (처음)
git push                      # 푸시 (이후)
```

### 🔍 확인

```bash
git diff                      # 변경 내용 비교
git log --oneline             # 커밋 기록 간단히 보기
```

---

## 8. 꼭 지켜요! 협업 약속

- ✅ **작업 시작 전** `git pull`로 최신 코드 받기
- ✅ **`main`에서 직접 작업하지 않기** — 항상 브랜치를 만들어서!
- ✅ **작은 단위로 자주 커밋**하기
- ✅ 커밋 메시지는 **무슨 일을 했는지** 알 수 있게 쓰기
- ✅ **PR로 리뷰**를 받은 뒤 병합하기
- ✅ 모르겠으면 **혼자 고민하지 말고 팀원에게 질문**하기 🙋
- ❌ `git push --force` 함부로 쓰지 않기
- ❌ 비밀번호, API 키 같은 **민감한 정보는 절대 커밋하지 않기**

---

> 🎯 **막히면 이것부터!** `git status` → 지금 상태를 알려주고, 다음에 뭘 하면 되는지 힌트도 줘요.
