# index — 스테이징 영역

[전체 목차](README.md)

> 공식 레벨 소스를 기준으로 작성한 풀이입니다. 명령어는 각 레벨의 초기 상태에서 게임 안의 터미널에 순서대로 입력합니다. 아래의 확인 결과는 기대하는 상태이며, 게임 화면에서의 완료 여부와 캡처는 직접 확인해야 합니다.

## 1. Step by step

**문제 목표:** step-by-step 브랜치를 선택하고 경보가 울리는 상태를 커밋한다.

**풀이**

```bash
git checkout step-by-step
```

```bash
printf '%s\n' 'The smoke detector is sounding an alarm.' > smoke_detector
git add smoke_detector
git commit -m "Sound the alarm"
```

**확인할 결과:** 현재 브랜치가 step-by-step이고 그 브랜치에 경보 상태가 기록된다.

**배운 개념:** 한 커밋에 한 가지 의미 있는 변경을 담으면 사건의 순서와 원인을 이해하기 쉽다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/index/compare)

## 2. Add new files to the index

**문제 목표:** 새 candle 파일을 스테이징한 뒤 커밋한다.

**풀이**

```bash
git add candle
```

```bash
git commit -m "Record the candle"
```

**확인할 결과:** 최초 커밋에 candle이 있다.

**배운 개념:** 새 파일은 git add로 인덱스에 넣어야 커밋에 포함된다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/index/new)

## 3. Update files in the index

**문제 목표:** candle을 수정하고 인덱스를 갱신한 뒤 커밋한다.

**풀이**

```bash
printf '%s\n' 'The candle has been blown out.' > candle
```

```bash
git add candle
```

```bash
git commit -m "Blow out the candle"
```

**확인할 결과:** 작업 폴더 수정 → 스테이징 → 커밋 순서를 거쳐 candle의 새 상태가 기록된다.

**배운 개념:** 인덱스는 자동 갱신되지 않는다. 파일을 수정한 다음 git add를 다시 해야 수정본을 커밋한다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/index/change)

## 4. Resetting files in the index

**문제 목표:** 이미 스테이징된 세 변경 중 빨간 촛불만 커밋한다.

**풀이**

```bash
git reset HEAD -- green_candle blue_candle
```

```bash
git commit -m "Blow out only the red candle"
```

**확인할 결과:** 커밋 속 green_candle과 blue_candle은 burning이고 red_candle만 꺼져 있다.

**배운 개념:** 경로를 지정한 git reset은 해당 파일의 스테이징을 취소한다. 작업 폴더의 수정은 남는다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/index/reset)

## 5. Adding changes step by step

**문제 목표:** 세 물건을 모두 수정하되 한 파일씩 세 번 나누어 커밋한다.

**풀이**

```bash
printf '%s\n' 'The hammer falls onto the bottle.' > hammer
printf '%s\n' 'The bottle breaks and spills its liquid.' > bottle
printf '%s\n' 'The sugar cube dissolves in the spilled liquid.' > sugar_cube
```

```bash
git add hammer
```

```bash
git commit -m "The hammer falls"
```

```bash
git add bottle
```

```bash
git commit -m "The bottle breaks"
```

```bash
git add sugar_cube
```

```bash
git commit -m "The sugar dissolves"
```

**확인할 결과:** 초기 커밋 뒤에 각각 한 파일만 바꾼 커밋이 3개 생긴다.

**배운 개념:** 여러 파일을 동시에 수정해도 인덱스로 다음 커밋에 포함할 변경을 선택할 수 있다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/index/steps)
