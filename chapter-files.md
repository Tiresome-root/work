# files — 파일 다루기

## 1. Unexpected Roommates

**문제 목표:** 거미줄 파일 3개를 지우고 침대는 남긴다.

**풀이**

```bash
rm tiny_web big_web thick_web
```

**확인할 결과:** bed는 존재하고 tiny_web, big_web, thick_web는 없다.

## 2. Interior design

**문제 목표:** 노란 침대와 어울리는 가구 파일 2개를 만든다.

**풀이**

```bash
printf '%s\n' 'A yellow wooden desk.' > desk
printf '%s\n' 'A yellow comfortable chair.' > chair
```

**확인할 결과:** bed, desk, chair가 있고 모든 파일 내용에 yellow가 들어 있다.
