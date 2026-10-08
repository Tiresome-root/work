# shit-happens — 실수 복구

[전체 목차](README.md)

> 공식 레벨 소스를 기준으로 작성한 풀이입니다. 명령어는 각 레벨의 초기 상태에서 게임 안의 터미널에 순서대로 입력합니다. 아래의 확인 결과는 기대하는 상태이며, 게임 화면에서의 완료 여부와 캡처는 직접 확인해야 합니다.

## 1. Restore a deleted file

**문제 목표:** 작업 폴더에서 삭제한 essay를 복구한다.

**풀이**

```bash
git checkout -- essay
```

**확인할 결과:** essay 내용이 important content다.

**배운 개념:** 이 문제는 스테이징하지 않은 삭제이므로 인덱스의 파일을 작업 폴더로 복구하면 된다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/shit-happens/restore-a-file)

## 2. Restore a file from the past

**문제 목표:** 첫 커밋의 좋은 essay를 가져와 새로운 커밋으로 기록한다.

**풀이**

```bash
git checkout HEAD~1 -- essay
git commit -m "Restore the good essay"
```

**확인할 결과:** 새 main 커밋의 essay가 good version이다.

**배운 개념:** 과거 커밋에서 파일만 가져오면 현재 브랜치의 이력을 지우지 않고 복구할 수 있다. 이 checkout은 인덱스도 갱신한다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/shit-happens/restore-a-file-from-the-past)

## 3. Undo a bad commit

**문제 목표:** 잘못된 마지막 커밋을 취소하고 숫자와 메시지를 수정해 다시 커밋한다.

**풀이**

```bash
git reset HEAD~1
```

```bash
printf '%s\n' '1 2 3 4 5 6 7 8 9 10' > numbers
git add numbers
git commit -m "More numbers"
```

**확인할 결과:** 마지막 메시지가 More numbers이고 숫자가 1부터 10까지다. 잘못된 커밋은 main 이력에서 제외된다.

**배운 개념:** 기본 mixed reset은 브랜치와 인덱스를 되돌리지만 작업 폴더는 유지한다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/shit-happens/bad-commit)

## 4. I pushed something broken

**문제 목표:** 이미 팀에 보낸 문제 커밋의 효과만 취소해서 다시 보낸다.

**풀이**

```bash
git revert --no-edit HEAD~1
git push team main
```

**확인할 결과:** team/main의 text에서 very bad가 사라지고 바로 이전 커밋에는 해당 내용이 남아 있다.

**배운 개념:** revert는 기존 이력을 유지하면서 변경을 반대로 적용한 새 커밋을 만든다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/shit-happens/pushed-something-broken)

## 5. Go back to where you were before

**문제 목표:** 직전에 방문했던 커밋을 reflog로 찾아 돌아간다.

레벨을 막 시작한 상태 기준이다. 중간에 다른 checkout을 했다면 reflog에서 checkout: moving from 3 to main 기록 이전의 해당 해시를 선택한다.

**풀이**

```bash
git reflog
```

```bash
git checkout 'HEAD@{1}'
```

**확인할 결과:** HEAD가 3 브랜치의 커밋과 같다.

**배운 개념:** reflog는 로컬 HEAD와 참조가 이동한 기록이다. HEAD@{1}은 직전 HEAD 기록을 뜻한다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/shit-happens/reflog)
