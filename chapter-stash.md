# stash — 변경 임시 보관

[전체 목차](README.md)

> 공식 레벨 소스를 기준으로 작성한 풀이입니다. 명령어는 각 레벨의 초기 상태에서 게임 안의 터미널에 순서대로 입력합니다. 아래의 확인 결과는 기대하는 상태이며, 게임 화면에서의 완료 여부와 캡처는 직접 확인해야 합니다.

## 1. Stashing

**문제 목표:** 작성 중인 밀가루 재료 변경을 임시 보관한다.

**풀이**

```bash
git stash push -m "Flour ingredient"
```

**확인할 결과:** git stash list에 항목이 생기고 recipe에서 미커밋 밀가루 줄이 사라진다.

**배운 개념:** stash는 아직 커밋하지 않은 변경을 임시 보관하고 작업 폴더를 정리한다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/stash/stash)

## 2. Pop from Stash

**문제 목표:** 보관한 변경을 작업 폴더로 다시 꺼낸다.

**풀이**

```bash
git stash pop
```

**확인할 결과:** recipe에 500g Flour가 돌아오고 stash 목록이 비어 있다.

**배운 개념:** pop은 성공적으로 적용되면 해당 stash를 제거한다. apply는 적용 후에도 항목을 남긴다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/stash/stash-pop)

## 3. Clear the Stash

**문제 목표:** 연습용으로 쌓인 stash 항목을 모두 지운다.

**풀이**

```bash
git stash list
git stash clear
```

**확인할 결과:** git stash list가 비어 있다.

**배운 개념:** clear는 모든 stash를 지운다. 특정 항목만 지울 때는 stash drop을 사용한다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/stash/stash-clear)

## 4. Branch from stash

**문제 목표:** 보관된 변경을 새 recipe-work 브랜치에서 이어서 작업한다.

**풀이**

```bash
git stash branch recipe-work
```

**확인할 결과:** main과 recipe-work가 있고 recipe-work 작업 폴더에 밀가루 줄이 복구된다.

**배운 개념:** stash branch는 보관 당시 기반에서 새 브랜치를 만들고 변경을 적용한다. 자동 커밋은 하지 않는다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/stash/stash-branch)

## 5. Merging popped stash

**문제 목표:** 소금 변경과 stash의 밀가루 변경 사이 충돌을 해결하고 커밋한다.

첫 pop에서 충돌이 발생한다. 이 레벨에서 clear는 해결한 연습용 stash를 정리하기 위해 사용한다.

**풀이**

```bash
git stash pop
```

```bash
printf '%s\n' 'Apple Pie:' '- 4 Apples' '- 500g Flour' '- Pinch of Salt' > recipe
git add recipe
git commit -m "Combine flour and salt"
```

```bash
git stash clear
```

**확인할 결과:** 커밋된 recipe에 Flour와 Salt가 모두 있고 stash 목록은 비어 있다.

**배운 개념:** stash를 꺼낼 때도 같은 위치의 수정이 충돌할 수 있다. 충돌한 pop은 항목을 남기므로 해결 후 정리한다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/stash/stash-merge)
