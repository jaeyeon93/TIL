Recursion 적용 미로찾기
----

#### 현재 위치에서 출구까지 가는 경로가 있으려면

1. 현재 위치가 출구이거나 혹은..
2. 이웃한 셀들 중 하나에서 현재 위치를 지나지 않고 출구까지 가는 경로가 있거나..


- 미로찾기의 경우 Decision Problem이라고 한다. 답이 yes or no인 경우로 떨어지기 때문

![](/Users/jaeyeonkim/Desktop/recursion_findpathway.png)

- 최대 4개의 인접한 셀이 존재를 한다.
- 무한루프에 빠지지 않도록 주의를 해야한다.
- 이미 가본위치와 가보지 않은 위치를 구분을 해야한다.
- mark로 표시를 해야한다.

![](/Users/jaeyeonkim/Desktop/recursion_findpathway.png)


![](/Users/jaeyeonkim/Desktop/findpathway_code.png)

- 사람이 지나다니는 통로는 0으로 표시
- 벽은 1로 표시
- 이미 방문해본 길이지만 꽝인길은 2로 표시
- 이미 방문해본 길이지만 가볼 수 있는길은 3으로 표시

![](/Users/jaeyeonkim/Desktop/findpathway_code2.png)

![](/Users/jaeyeonkim/Desktop/findpathway_code3.png)

- x== n-1 && y == n-1
- 북 동 남 서 순으로 실행이 된다.