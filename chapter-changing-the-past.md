# changing-the-past — 이력 재구성

[전체 목차](README.md)

> 공식 레벨 소스를 기준으로 작성한 풀이입니다. 명령어는 각 레벨의 초기 상태에서 게임 안의 터미널에 순서대로 입력합니다. 아래의 확인 결과는 기대하는 상태이며, 게임 화면에서의 완료 여부와 캡처는 직접 확인해야 합니다.

## 1. Rebasing

**문제 목표:** 세 갈래의 아침 활동을 7개 커밋으로 된 선형 main 이력으로 만든다.

**풀이**

```bash
git checkout coffee
git rebase baguette
```

```bash
git checkout donut
git rebase coffee
```

```bash
git checkout main
git merge --ff-only donut
```

**확인할 결과:** main의 커밋 수가 7이고 병합 커밋 없이 세 소비 결과가 모두 남는다.

**배운 개념:** rebase는 변경을 다른 기반 위에 다시 적용하므로 커밋 해시가 바뀐다. 여기서는 main을 최종 이력까지 fast-forward한다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/changing-the-past/rebase)

## 2. Reordering events

**문제 목표:** 속옷 → 바지 → 셔츠 → 신발 순서로 사건을 다시 배열한다.

대안은 git rebase -i HEAD~4로 편집기를 열어 pick 줄의 순서를 바꾸는 것이다.

**풀이**

```bash
shoes_commit=$(git rev-parse main~3)
pants_commit=$(git rev-parse main~2)
underwear_commit=$(git rev-parse main~1)
shirt_commit=$(git rev-parse main)
git reset --hard main~4
git cherry-pick "$underwear_commit" "$pants_commit" "$shirt_commit" "$shoes_commit"
```

**확인할 결과:** git log --reverse --oneline에서 초기 상태, 속옷, 바지, 셔츠, 신발 순서의 5개 커밋을 확인한다.

**배운 개념:** cherry-pick은 지정한 커밋의 변경을 현재 이력에 적용한다. 재배열 전에 해시를 저장하면 reset 후에도 찾을 수 있다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/changing-the-past/reorder)
