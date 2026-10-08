# index — 스테이징 영역

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
