### 문제 1

양수를 입력받아 이 수를 반지름으로 하는 원의 넓이를 반환하는 함수를 작성하세요.

```js
function circleArea(num) {
  return num ** 2 * 3.14
}

circleArea(5) // 78.5 반환
```

### 문제 2

두 정수 `min`, `max` 를 입력받아, `min` 이상 `max` 미만인 임의의 정수를 반환하는 함수를 작성하세요.

```js
function randomInteger(min, max) {
  let numArr = []

  for (let i = min; i < max; i++) {
    numArr.push(i)
  }
  return numArr[Math.floor(Math.random() * numArr.length)]
} 

randomInteger(-2, 5) // -2와 4사이의 아무 정수나 반환
```

### 문제 3

정수를 입력받아, 5 단위로 올림한 수를 반환하는 함수를 작성하세요.

예:
```
ceilBy5(32); -> 35
ceilBy5(37); -> 40
```

풀이(1):
```js
function ceilBy5(integer) {
  return Math.ceil(integer / 5) * 5;
}

ceilBy5(32); // 35 반환
ceilBy5(37); // 40 반환
```

풀이(2: 화살표 함수):
```js
const ceilBy5 = (integer) => {return Math.ceil(integer / 5) * 5;}

ceilBy5(32); // 35 반환
ceilBy5(37); // 40 반환
```

### 문제 4

배열을 입력받아, 요소들의 순서를 뒤섞은 새 배열을 반환하는 함수를 작성하세요.

```js
function shuffle(arr) {
  let arr2 = arr.slice()
  arr2.sort((x, y) => Math.floor(Math.random() * arr2.length))
  return arr2
}

shuffle([1, 2, 3, 4, 5]) // [3, 1, 4, 5, 2] 와 같이 순서가 뒤섞인 새 배열 반환
```

### 문제 5

임의의 HTML 색상 코드를 반환하는 함수를 작성하세요.

```js
function colorGenerator() {
  let letters = '0123456789ABCDEF';
  let color = '#';
  for (var i = 0; i < 6; i++) {
    color += letters[Math.floor(Math.random() * 16)];
  }
  return color;
}

colorGenerator() // '#EAB164'와 같은 임의의 HTML 색상 코드를 반환 
```

### 문제 6

양수를 입력받아, 그 수만큼의 길이를 갖는 임의의 문자열을 반환하는 함수를 작성하세요.

```js
function randomString(num) {
  let numLength = (num).toString().length
  let charSet = 'abcdefghijklmnopqrstuvwxyzABCDEFGHIJKLMNOPQRSTUVWXYZ'
  let result = ''
  for (let i = 0; i < numLength; i++) {
    result += charSet[Math.floor(Math.random() * charSet.length)]
  }
  return result
}

randomString(12345) // 'SpgHS'와 같은 임의의 문자열을 반환
```

### 문제 7

수 타입의 값으로만 이루어진 배열을 입력받아, 그 값들의 표준편차를 구하는 함수를 작성하세요.

강사님 풀이:
```js
function stdDev(arr) {
  // arr의 평균 구하기
  const sum = arr.reduce((acc, item) => acc + item, 0)
  const mean = sum / arr.length
  // 각 요소에 대한 편차 구하기 (평균 = 값 - 평균)
  const ps = arr.map(item => item - mean) // (map 메소드는 배열의 각 요소에 함수를 적용해서, 그 반환값을 요소로 갖는 새로운 배열을 만듦
  // 각 요소에 대해 제곱하기)
  const powers = ps.map(item => item ** 2) // item ** 2 =item * item
  // 위 제곱한 배열의 평균 구하기
  const vv = powers.reduce((acc, item) => acc + item, 0) / powers.length
  // 루트 씌우기
  return Math.sqrt(vv)
}

stdDev([1, 2, 3, 4, 5]) // 1.4142135623730951 반환  
```
