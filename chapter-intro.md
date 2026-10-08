**문제 목표:** form.txt에 Git을 배우고 싶은 이유를 한 줄 추가한다.

강의 슬라이드처럼 form.txt 아이콘을 클릭하고 마지막에 이유를 한 줄 적은 뒤 Save를 눌러도 된다.

**풀이**

```bash
printf '%s\n' '- To collaborate with my teammates' >> form.txt
```

**확인할 결과:** form.txt의 줄 수가 5줄 이상이 된다. 게임에서는 곧 고양이가 내용을 바꾸는 연출이 나온다.

## 2. Making backups

**문제 목표:** 최종 백업 파일에 새로운 이유를 추가한다.

**풀이**

```bash
printf '%s\n' '- To collaborate with my teammates' >> form2_really_final.txt
```

**확인할 결과:** form2_really_final.txt가 5줄 이상이다.

## 3. Enter the time machine

**문제 목표:** 현재 연습 폴더를 Git 저장소로 초기화한다.

init 문제는 파란 init 카드를 끌어 놓아도 된다. cli 문제는 게임 하단 터미널에 명령어를 직접 입력한다.

**풀이**

```bash
git init
```

**확인할 결과:** .git 디렉터리가 생기고 초기화 목표가 초록색으로 바뀐다.

## 4. The command line

**문제 목표:** 현재 연습 폴더를 Git 저장소로 초기화한다.

init 문제는 파란 init 카드를 끌어 놓아도 된다. cli 문제는 게임 하단 터미널에 명령어를 직접 입력한다.

**풀이**

```bash
git init
```

**확인할 결과:** .git 디렉터리가 생기고 초기화 목표가 초록색으로 바뀐다.

## 5. Your first commit

**문제 목표:** glass의 최초 상태와 바뀐 상태를 각각 커밋한다.

**풀이**

```bash
git add glass
git commit -m "Record full glass"
```

```bash
printf '%s\n' 'The glass is empty.' > glass
```

```bash
git add glass
git commit -m "Drink the water"
```

**확인할 결과:** 커밋이 2개 이상이고 최신 glass 내용이 최초 상태와 다르다.

## 6. Working together

**문제 목표:** 선생님의 최신 명단을 받고 이름을 추가해 다시 보낸다.

**풀이**

```bash
git pull --no-rebase teacher main
```

```bash
printf '%s\n' '- dohyeungkim' >> students
```

```bash
git add students
git commit -m "Add dohyeungkim to students"
git push teacher main
```

**확인할 결과:** 자신과 teacher 양쪽 main의 students에 기존 학생들과 추가한 이름이 남아 있다.
