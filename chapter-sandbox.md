# sandbox — 자유 실습

[전체 목차](README.md)

> 공식 레벨 소스를 기준으로 작성한 풀이입니다. 명령어는 각 레벨의 초기 상태에서 게임 안의 터미널에 순서대로 입력합니다. 아래의 확인 결과는 기대하는 상태이며, 게임 화면에서의 완료 여부와 캡처는 직접 확인해야 합니다.

## 1. Empty sandbox

**문제 목표:** 자유 실습: 새 파일을 만들고 최초 커밋과 브랜치를 만든다.

**풀이**

```bash
printf '%s\n' 'My Git practice' > practice.txt
git add practice.txt
git commit -m "Start practice"
git checkout -b experiment
```

**확인할 결과:** 공식 성공 조건은 없다. experiment 브랜치와 practice.txt 커밋 생성 여부를 확인한다.

**배운 개념:** 빈 저장소에서 add → commit → branch 흐름을 다시 연습한다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/sandbox/empty)

## 2. Sandbox with a remote

**문제 목표:** 자유 실습: 원격 변경을 받고 연습용 브랜치와 태그를 보낸 뒤 삭제한다.

**풀이**

```bash
git pull --no-rebase friend main
git checkout -b practice-remote
```

```bash
printf '%s\n' 'Line 3, remote practice' >> essay
git add essay
git commit -m "Practice remote work"
git push -u friend practice-remote
git tag practice-v1
git push friend refs/tags/practice-v1
```

```bash
git push friend --delete practice-remote
git push friend --delete refs/tags/practice-v1
git checkout main
git branch -D practice-remote
git tag -d practice-v1
```

**확인할 결과:** 공식 성공 조건은 없다. main에 친구의 두 번째 줄이 있고 연습용 브랜치와 태그가 양쪽에서 제거되었는지 확인한다.

**배운 개념:** 브랜치와 태그는 로컬 생성·삭제와 원격 생성·삭제가 별개다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/sandbox/remote)

## 3. Sandbox with three commits

**문제 목표:** 자유 실습: 세 커밋을 살펴보고 과거에서 별도 브랜치를 만든다.

**풀이**

```bash
git log --oneline --graph --all
git checkout -b alternate HEAD~1
```

```bash
printf '%s\n' 'You decide to read a book.' >> you
git add you
git commit -m "Read a book instead"
git tag practice-ending
git log --oneline --graph --all
```

**확인할 결과:** 공식 성공 조건은 없다. 기존 두 브랜치와 alternate의 다른 결말을 그래프에서 확인한다.

**배운 개념:** 과거에서 분기해도 main과 not_main의 기존 이력은 남는다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/sandbox/three-commits)
