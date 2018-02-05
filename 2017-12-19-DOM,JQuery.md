## DOM & CSS

### css는 id, tag, class에 3가지 식별자를 기준으로 css를 적용할 수 있다.

- id : 고유한값이다.
- class, tag : 여러개가 될 수 있다.
- 디자인을 겹치고 싶을때 class를 주로 많이 쓰고 한가지만 적용할때 id를 주로 쓴다.

```
body {
	background-color : lightblue;

}
h1 {
	color : white;
  	text-align: center;
}

p {
  	font-family : verdana;
  	font-size : 20px;
}

```

#### DOM : Document Object Model
- html태그를 계층 구조로 변환을 시켜준다.
- 모든 HTML엘리먼트는 객체이므로 JS로 조작이 가능하다.

```
document.createElement('ul');
<ul></ul>
var item1 = document.createElement('li');
undefined
var menu = document.createElement('ul');
undefined
var item2 = document.createElement('li');
undefined
item1.innerHTML = '설렁탕';
"설렁탕"
item2.innerHTML = '순대국';
"순대국"
menu.appendChild(item1);
<li>설렁탕</li>
menu.appendChild(item2);
```