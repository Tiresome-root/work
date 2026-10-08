# branches — 브랜치와 시간 이동

[전체 목차](README.md)

> 공식 레벨 소스를 기준으로 작성한 풀이입니다. 명령어는 각 레벨의 초기 상태에서 게임 안의 터미널에 순서대로 입력합니다. 아래의 확인 결과는 기대하는 상태이며, 게임 화면에서의 완료 여부와 캡처는 직접 확인해야 합니다.

## 1. Moving through time

**문제 목표:** 사건의 마지막 커밋에서 동생의 동전을 저금통에 돌려놓고 새 커밋을 만든다.

이 레벨에는 main 브랜치가 없다. reflog로 이력을 확인하고 메시지로 마지막 사건의 해시를 찾는다. 게임에서는 노란 커밋을 선택해도 된다.

**풀이**

```bash
git reflog --all
```

```bash
last_event=$(git log --all --reflog --format=%H --grep="^Little sister does something$" -1)
git checkout "$last_event"
```

```bash
printf '%s\n' 'This piggy bank belongs to the big sister.' 'It contains 10 coins.' > piggy_bank
printf '%s\n' 'A young girl with brown, curly hair.' > little_sister
git add piggy_bank little_sister
git commit -m "Return the coins"
```

**확인할 결과:** 최신 커밋의 piggy_bank에 10 coins가 있고 little_sister에는 없으며 이력이 4개 커밋으로 이어진다.

**배운 개념:** checkout으로 과거 상태를 볼 수 있다. 문제는 마지막 사건에서 이어지는 수정 커밋을 요구한다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/branches/checkout-commit)

## 2. Make parallel commits

**문제 목표:** 아이가 우리에 들어가기 전으로 돌아가 아이와 사자가 모두 안전한 새 이력을 만든다.

**풀이**

```bash
git checkout HEAD~3
```

```bash
printf '%s\n' 'The lion has eaten its food and is happy.' > cage/lion
git add cage/lion
git commit -m "Feed the lion safely"
```

**확인할 결과:** child가 우리 밖에 존재하고 사자가 더 이상 very hungry 상태가 아니다.

**배운 개념:** 과거 커밋에서 새 커밋을 만들면 기존 미래와 갈라지는 이력이 생긴다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/branches/fork)

## 3. Creating branches

**문제 목표:** 생일과 공연 커밋에 birthday, concert 브랜치를 각각 붙인다.

**풀이**

```bash
birthday_commit=$(git log --all --reflog --format=%H --grep="^Go to the birthday$" -1)
concert_commit=$(git log --all --reflog --format=%H --grep="^Go to the concert$" -1)
git branch birthday "$birthday_commit"
git branch concert "$concert_commit"
```

**확인할 결과:** git show birthday와 git show concert가 각각 알맞은 사건을 보여 준다.

**배운 개념:** 브랜치는 커밋을 가리키는 이름이다. git branch로 생성만 하면 현재 위치는 바뀌지 않는다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/branches/branch-create)

## 4. Branches grow with you!

**문제 목표:** 생일 커밋에 직접 이동해 커밋하고, 공연 브랜치에 이동해서도 커밋한다.

**풀이**

```bash
git checkout --detach birthday
```

```bash
printf '%s\n' 'You give your friend a present.' >> you
git add you
git commit -m "Give a birthday present"
```

```bash
git checkout concert
```

```bash
printf '%s\n' 'You get your ticket signed.' >> you
git add you
git commit -m "Get the ticket signed"
```

**확인할 결과:** birthday는 원래 위치에 남고 concert는 추가한 커밋을 가리킨다.

**배운 개념:** 커밋에 직접 이동한 detached HEAD에서는 기존 브랜치가 움직이지 않는다. 브랜치를 checkout하면 새 커밋과 함께 브랜치도 앞으로 이동한다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/branches/grow)

## 5. Deleting branches

**문제 목표:** 안전하게 학교에 도착하는 leap 브랜치만 남긴다.

**풀이**

```bash
git checkout leap
git branch -D friend music ice-cream
```

**확인할 결과:** git branch 결과에 leap만 남는다.

**배운 개념:** 브랜치 삭제는 이름을 지우는 작업이다. -D는 병합하지 않은 브랜치도 삭제한다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/branches/branch-remove)

## 6. Moving branches around

**문제 목표:** 서로 바뀐 baguette와 coffee의 위치를 바로잡고 donut에서 도넛을 먹는다.

**풀이**

```bash
baguette_tip=$(git rev-parse coffee)
coffee_tip=$(git rev-parse baguette)
git checkout baguette
git reset --hard "$baguette_tip"
git checkout coffee
git reset --hard "$coffee_tip"
```

```bash
git checkout donut
```

```bash
printf '%s\n' 'You do not have a baguette.' '' 'You do not have coffee.' '' 'You ate a donut.' > you
git add you
git commit -m "Eat the donut"
```

**확인할 결과:** 각 브랜치의 you에 각각 ate a baguette, drank coffee, ate a donut이 들어 있다.

**배운 개념:** 브랜치를 checkout한 뒤 reset하면 해당 브랜치가 가리키는 커밋을 바꾼다. 이동 전 두 해시를 저장해야 원래 위치를 잃지 않는다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/branches/reorder)
