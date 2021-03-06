Bandwidth와 Latency 

- 성능에 관한 이슈는 Bandwidth와 Latency가 있는데, Latency에 관한 이슈가 많다.


### 성능개선전략 (1) - CDN
CDN(content delivery network) : 지역마다 컨텐츠를 제공을 하는 서버를 둔다. Latency를 낮추기 위한 수단중에 하나이다.

Q. Latency를 떨어뜨리는 이유? 
A. 네트워크는 Latency는 너무 빠르다.  근대 응답이 안온다. 왜?. 내가 개발을 잘 못해서...

Q. 웹서비스에서 성능상 가장 이슈가 되는것?
A. 동적HTML, JS, CSS, Image등. HTML은 금방 다운로드가 되지만, 나머지는 JS,CSS,Image가 많이 차지한다. 주로 이미지. 한번다운로드 받으면 다시 받지 않는것이 좋은거다. 변하지 않는 자원들을 캐싱을 해서, 서버에 재요청을 안하는거다. 메모리캐시와 디스크캐시가 있다. 

HTTP Response에 Cache-Control: max-age로 얼마나 캐시를 유지할 수 있는지를 설정할 수 있다.


![](/Users/jaeyeonkim/Desktop/httpCaching.png)

- 브라우저는 캐싱을 URL path경로로 한다. 경로를 바꾸면 캐싱하고 있던 자원을 버리고, 다시 다운로드를 받는다.

![](/Users/jaeyeonkim/Desktop/httpRequest.png)

- 백엔드개발을 할때, 경로를 설정을 할때 동적으로 하지 않으면 업데이트를 할때 굉장히 어려워진다. 추가적인 작업을 해야된다.
- 캐시를 잘 쓰면 서버성능향상이 엄청되고, BandWidth를 적게 사용을 한다.

### 성능개선전략 (2) - 압축

- 모든 컨텐츠에 대해서 압축을 하는게 다 좋은게 아니다. 압축을 하면 비용이 든다.
- 압축은 서버가 하고, 압축해지는 클라이언트가 든다. 압축을 하고 해제하는 과정에서 CPU의 자원 메모리자원이 소모가 된다. 압축률도 고려가 된다. 텍스트파일이 압출률이 높다. 70-80%가 나온다. 반면 이미지나 동영상은 이미 압축된 데이터를 쓰기때문에, 압축을 해도 비율이 낮다.

![](/Users/jaeyeonkim/Desktop/httpCompressor.png)

- 압축을 하는 타입(방법)도 고려가 되어야된다. 위에서는 gzip이다.

### 성능개선전략 (3) - 요청횟수를 줄이자

- css sprite를 이용을 해서, 서비스에서 사용을 하는 작은이미지들을 다 모아서 하나의 이미지파일로 만들어서 css를 이용을 해서 이미지의 포지션만을 보여준다.


#### 소켓을 식별하는 4가지 구성요소
- 클라이언트 IP, PORT // 서버 IP, PORT 총4개를 가지고 식별한다.
- 클라이언트포트는 랜덤으로 지정이 된다. 쓰레드가 설정이 될때마다 랜덤으로 클라이언트특정포트가 할당이된다.

