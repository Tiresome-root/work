# bisect — 문제 커밋 찾기

[전체 목차](README.md)

> 공식 레벨 소스를 기준으로 작성한 풀이입니다. 명령어는 각 레벨의 초기 상태에서 게임 안의 터미널에 순서대로 입력합니다. 아래의 확인 결과는 기대하는 상태이며, 게임 화면에서의 완료 여부와 캡처는 직접 확인해야 합니다.

## 1. Yellow brick road

**문제 목표:** 열쇠를 처음 잃은 커밋을 찾고 main을 마지막 정상 커밋으로 되돌린다.

**풀이**

```bash
git bisect start
git bisect bad main
git bisect good main~29
```

```bash
git bisect run grep -q 'You still have your key.' you
```

```bash
first_bad=$(git rev-parse refs/bisect/bad)
last_good=$(git rev-parse "$first_bad^")
git bisect reset
git checkout main
git reset --hard "$last_good"
```

**확인할 결과:** 최초 불량 커밋은 12, 마지막 정상 커밋은 11이다. 12에서 열쇠를 떨어뜨리고 13에서 새가 가져간 뒤 14에서 새도 사라진다.

**배운 개념:** bisect는 정상/불량 구간을 절반씩 좁힌다. bisect run은 검사 명령의 종료 코드 0을 정상, 1을 불량으로 판단한다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/bisect/bisect)
