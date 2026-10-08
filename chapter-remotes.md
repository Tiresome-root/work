# remotes — 원격 협업

[전체 목차](README.md)

> 공식 레벨 소스를 기준으로 작성한 풀이입니다. 명령어는 각 레벨의 초기 상태에서 게임 안의 터미널에 순서대로 입력합니다. 아래의 확인 결과는 기대하는 상태이며, 게임 화면에서의 완료 여부와 캡처는 직접 확인해야 합니다.

## 1. Friend

**문제 목표:** 친구와 번갈아 essay에 다섯 번째 줄까지 작성한다.

첫 push 뒤에는 게임이 친구의 네 번째 줄을 자동으로 만든다. 화면 갱신을 기다린 다음 두 번째 pull을 실행한다.

**풀이**

```bash
git pull --no-rebase friend main
```

```bash
printf '%s\n' 'Line 3, written by dohyeungkim' >> essay
git add essay
git commit -m "Write line 3"
git push friend main
```

```bash
git pull --no-rebase friend main
```

```bash
printf '%s\n' 'Line 5, written by dohyeungkim' >> essay
git add essay
git commit -m "Write line 5"
git push friend main
```

**확인할 결과:** 양쪽 essay에 5줄이 있고 친구가 작성한 gnihihi, blurbblubb 줄도 보존된다.

**배운 개념:** 상대 변경을 받은 후 작업하고 커밋을 보내는 과정을 반복해 공동 작업한다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/remotes/friend)

## 2. Problems

**문제 목표:** 로컬 초록색 제안과 친구의 파란색 제안을 병합해 보낸다.

pull 단계에서 충돌이 발생하는 것이 정상이다. 해결 후 push한다.

**풀이**

```bash
git add file
git commit -m "Suggest green"
```

```bash
git pull --no-rebase friend main
```

```bash
printf '%s\n' 'The bike shed should be green and blue' > file
git add file
git commit -m "Agree on both colors"
git push friend main
```

**확인할 결과:** 작업 폴더가 깨끗하고 friend의 main이 두 제안을 합친 병합 커밋을 가리킨다.

**배운 개념:** 분기된 이력을 먼저 병합하고 충돌을 해결해야 상대 변경을 보존하며 push할 수 있다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/remotes/problems)
