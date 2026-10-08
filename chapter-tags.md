# tags — 태그

[전체 목차](README.md)

> 공식 레벨 소스를 기준으로 작성한 풀이입니다. 명령어는 각 레벨의 초기 상태에서 게임 안의 터미널에 순서대로 입력합니다. 아래의 확인 결과는 기대하는 상태이며, 게임 화면에서의 완료 여부와 캡처는 직접 확인해야 합니다.

## 1. Creating tags

**문제 목표:** 현재 커밋에 버전 이름을 붙인다.

**풀이**

```bash
git tag v1
```

**확인할 결과:** v1 태그가 현재 커밋을 가리킨다.

**배운 개념:** 태그는 특정 커밋을 표시하는 이름이며 브랜치처럼 새 커밋을 따라 이동하지 않는다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/tags/add-tag)

## 2. Removing tags

**문제 목표:** 기존 태그 3개를 삭제한다.

**풀이**

```bash
git tag -d v1 v2 v3
```

**확인할 결과:** git tag 결과가 비어 있다.

**배운 개념:** 태그를 지워도 커밋 자체가 삭제되는 것은 아니다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/tags/remove-tag)

## 3. Tagging later

**문제 목표:** 두 번째 기능 커밋에 v1을 붙인다.

**풀이**

```bash
git tag v1 HEAD~1
```

**확인할 결과:** v1이 Adding feature 2 커밋을 가리킨다.

**배운 개념:** 태그 생성 시 커밋을 지정하면 과거 커밋에도 이름을 붙일 수 있다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/tags/add-tag-later)

## 4. Remote Tags

**문제 목표:** 친구의 v1을 가져오고 최신 커밋의 v2를 친구에게 보낸다.

친구의 v1은 게임 자동 동작으로 생성된다. 레벨을 연 직후 잠깐 기다리고 실행한다.

**풀이**

```bash
git fetch friend --tags
git tag v2
git push friend refs/tags/v2
```

**확인할 결과:** 로컬 v1은 이전 커밋, 로컬과 friend의 v2는 최신 커밋을 가리킨다.

**배운 개념:** 일반 브랜치 push가 모든 태그를 보내지는 않는다. fetch는 가져오는 이력의 태그를 자동으로 받기도 하며 --tags는 모든 원격 태그를 명시적으로 가져온다.

[공식 문제 및 성공 조건](https://github.com/git-learning-game/oh-my-git/blob/cfa2625dbd09b50e3108bb9119f2d3b3043fb1b3/levels/tags/remote-tag)
