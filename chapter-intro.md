# intro — Git 시작하기

[전체 목차](README.md)

> 공식 레벨 소스를 기준으로 작성한 풀이입니다. 명령어는 각 레벨의 초기 상태에서 게임 안의 터미널에 순서대로 입력합니다. 아래의 확인 결과는 기대하는 상태이며, 게임 화면에서의 완료 여부와 캡처는 직접 확인해야 합니다.

## 1. Living dangerously

**문제 목표:** form.txt에 Git을 배우고 싶은 이유를 한 줄 추가한다.

강의 슬라이드처럼 form.txt 아이콘을 클릭하고 마지막에 이유를 한 줄 적은 뒤 Save를 눌러도 된다.

**풀이**

```bash
printf '%s\n' '- To collaborate with my teammates' >> form.txt
```

**확인할 결과:** form.txt의 줄 수가 5줄 이상이 된다. 게임에서는 곧 고양이가 내용을 바꾸는 연출이 나온다.

**배운 개념:** 파일을 수정하는 것만으로는 이전 내용을 복구할 수 없다. 변경 이력이 필요하다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/intro/risky)

## 2. Making backups

**문제 목표:** 최종 백업 파일에 새로운 이유를 추가한다.

**풀이**

```bash
printf '%s\n' '- To collaborate with my teammates' >> form2_really_final.txt
```

**확인할 결과:** form2_really_final.txt가 5줄 이상이다.

**배운 개념:** 파일을 계속 복사해 백업하면 최신 버전을 찾거나 여러 사람의 수정을 합치기 어렵다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/intro/copies)

## 3. Enter the time machine

**문제 목표:** 현재 연습 폴더를 Git 저장소로 초기화한다.

init 문제는 파란 init 카드를 끌어 놓아도 된다. cli 문제는 게임 하단 터미널에 명령어를 직접 입력한다.

**풀이**

```bash
git init
```

**확인할 결과:** .git 디렉터리가 생기고 초기화 목표가 초록색으로 바뀐다.

**배운 개념:** git init은 현재 폴더에 변경 이력을 관리할 .git 디렉터리를 만든다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/intro/init)

## 4. The command line

**문제 목표:** 현재 연습 폴더를 Git 저장소로 초기화한다.

init 문제는 파란 init 카드를 끌어 놓아도 된다. cli 문제는 게임 하단 터미널에 명령어를 직접 입력한다.

**풀이**

```bash
git init
```

**확인할 결과:** .git 디렉터리가 생기고 초기화 목표가 초록색으로 바뀐다.

**배운 개념:** git init은 현재 폴더에 변경 이력을 관리할 .git 디렉터리를 만든다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/intro/cli)

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

**배운 개념:** 커밋은 특정 시점의 파일 상태를 기록한다. 수정 후 다시 add와 commit을 해야 새 상태가 기록된다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/intro/commit)

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

**배운 개념:** pull은 원격 변경을 가져와 통합하고 push는 로컬 커밋을 원격에 보낸다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/intro/remote)
