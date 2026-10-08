# files — 파일 다루기

[전체 목차](README.md)

> 공식 레벨 소스를 기준으로 작성한 풀이입니다. 명령어는 각 레벨의 초기 상태에서 게임 안의 터미널에 순서대로 입력합니다. 아래의 확인 결과는 기대하는 상태이며, 게임 화면에서의 완료 여부와 캡처는 직접 확인해야 합니다.

## 1. Unexpected Roommates

**문제 목표:** 거미줄 파일 3개를 지우고 침대는 남긴다.

**풀이**

```bash
rm tiny_web big_web thick_web
```

**확인할 결과:** bed는 존재하고 tiny_web, big_web, thick_web는 없다.

**배운 개념:** 파일 삭제와 Git 커밋은 별개다. 이 문제는 작업 폴더의 파일 삭제를 연습한다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/files/files-delete)

## 2. Interior design

**문제 목표:** 노란 침대와 어울리는 가구 파일 2개를 만든다.

**풀이**

```bash
printf '%s\n' 'A yellow wooden desk.' > desk
printf '%s\n' 'A yellow comfortable chair.' > chair
```

**확인할 결과:** bed, desk, chair가 있고 모든 파일 내용에 yellow가 들어 있다.

**배운 개념:** 파일 이름은 물건의 이름, 파일 내용은 물건의 상태를 나타낸다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/files/files-add)
