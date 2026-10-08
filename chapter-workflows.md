# workflows — 협업 작업 흐름

[전체 목차](README.md)

> 공식 레벨 소스를 기준으로 작성한 풀이입니다. 명령어는 각 레벨의 초기 상태에서 게임 안의 터미널에 순서대로 입력합니다. 아래의 확인 결과는 기대하는 상태이며, 게임 화면에서의 완료 여부와 캡처는 직접 확인해야 합니다.

## 1. Cloning a repo

**문제 목표:** 친구 저장소를 복제하고 solution 브랜치에서 2 + 3을 고친 뒤 게임의 PR 신호를 만든다.

git tag pr은 이 게임만의 PR 모의 동작이다. 실제 GitHub에서는 브랜치를 push한 뒤 Pull Request를 생성해야 한다.

**풀이**

```bash
git clone ../friend .
git checkout -b solution
```

```bash
printf '%s\n' '2 + 3 = 5' > file
git add file
git commit -m "Solve the addition"
git tag pr
```

**확인할 결과:** 게임의 친구 자동 동작이 solution을 가져와 main에 합치고 file에 5가 나타난다.

**배운 개념:** clone은 저장소와 이력을 복제한다. 별도 브랜치에서 변경을 만들면 검토와 통합 단위를 분리할 수 있다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/workflows/pr)
