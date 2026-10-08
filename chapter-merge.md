# merge — 이력 병합

[전체 목차](README.md)

> 공식 레벨 소스를 기준으로 작성한 풀이입니다. 명령어는 각 레벨의 초기 상태에서 게임 안의 터미널에 순서대로 입력합니다. 아래의 확인 결과는 기대하는 상태이며, 게임 화면에서의 완료 여부와 캡처는 직접 확인해야 합니다.

## 1. Merging timelines

**문제 목표:** 바게트, 커피, 도넛을 소비한 세 이력을 병합한다.

**풀이**

```bash
baguette_tip=$(git log --all --reflog --format=%H --grep="^You eat the baguette$" -1)
coffee_tip=$(git log --all --reflog --format=%H --grep="^You drink the coffee$" -1)
git merge --no-edit "$baguette_tip"
git merge --no-edit "$coffee_tip"
```

**확인할 결과:** HEAD의 you에 세 가지 소비 결과가 있고 HEAD가 병합 커밋이다.

**배운 개념:** 서로 다른 부분의 변경은 자동으로 병합할 수 있다. 병합 커밋에는 부모 커밋이 둘 이상 있다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/merge/merge)

## 2. Contradictions

**문제 목표:** pancakes와 muesli를 main에 합치면서 아침 식사 내용을 조정한다.

git merge muesli에서 CONFLICT가 나오는 것이 정상이다. 파일을 열어 내용을 조정해도 되고 아래 명령어로 최종 내용을 저장해도 된다.

**풀이**

```bash
git checkout main
git merge --ff-only pancakes
```

```bash
git merge muesli
```

```bash
printf '%s\n' 'Had blueberry pancakes and muesli for breakfast.' '' 'Is at work.' > sam
git add sam
git commit -m "Merge breakfast choices"
```

**확인할 결과:** main에 두 이력을 부모로 가진 병합 커밋이 생기고 sam에 충돌 표시가 없다.

**배운 개념:** 같은 줄을 다르게 수정하면 충돌한다. 최종 내용을 직접 정하고 add와 commit으로 병합을 마친다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/merge/conflict)
