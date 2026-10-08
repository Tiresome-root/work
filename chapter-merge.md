# merge — 이력 병합

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
