# Node.JS

자바스크립트 런타임(실행환경)  
이벤트기반, 논블로킹 I/O모델(비동기 I/O)을 사용해 가볍고 효율적  

> **tip**
> * vs에서 ctrl+` 하면 terminal창 열리고, node test1.js 하면 실행 됨  
> * 코드 실행과정을 보여주는 곳 [http://latentflip.com/loupe/](http://latentflip.com/loupe/)


## 객체 리터럴 
```javascript

const sayNode = function () {
    console.log('Node');
};
const es = 'ES';
const newObj={  //객체 리터럴
    sayJS() { //객체 메서드에 함수 연결할 때 sayJS라는 함수가 할당되어 있구나
        console.log('JS');
    },
    sayNode, //sayNode라는 변수 혹은 함수가 할당되어 있구나 ----- 1
    [es+6]: 'Fantastic', //변수가 됨 ES6이라는 이름의 값의 동적naming
};

newObj.sayNode(); //newObj의 sayNode() 호출 ----- 2 이때는 변수인지 함수인지 명확히 알아야함
newObj.sayJS();
console.log(newObj.ES6);
console.log(newObj.es6);

```

![JS vs Node](./img/js&node.png)


## 화살표 함수

```javascript

console.log(this);

function add(x,y){ //독립적 함수
    console.log(this===global);
    return console.log(x+y);
}

var add2 = function(x,y){  // add2변수에 할당된 함수
    console.log(this===global);
    return console.log(x+y);
}

const add3 = (x,y) => { // 화살표함수
    console.log(this===global);
    console.log(this); //자기문서객체
    return console.log(x+y);
}

const add4 = (x,y) => (console.log(x+y)); //화살표함수의 축약 한줄짜리 함수일 경우
const add5 = x => console.log(++x); //하나의 파라미터 받을때 소괄호 생략가능

add(10,20);
add2(10,20);
add3(10,20);
add4(10,20);
add5(10);

```
