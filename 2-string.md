### 문제 1

두 문자열을 입력받아, 대소문자를 구분하지 않고(case insensitive) 두 문자열이 동일한지를 반환하는 함수를 작성하세요.

예:
```
insensitiveEqual('hello', 'hello'); -> true
insensitiveEqual('hello', 'Hello'); -> true
insensitiveEqual('hello', 'world'); -> false
```

풀이:
```js
function insensitiveEqual(x, y) {
  return x.toLowerCase() === y.toLowerCase ()
  
  // 위의 코드로 단순화 됨
  // if (x.toLowerCase() === y.toLowerCase()) {
  //   return true
  // } else {
  //   return false
  // }
}
```

### 문제 2

문자열 `s`와 자연수 `n`을 입력받아, 만약 `s`의 길이가 `n`보다 작으면 `s`의 왼쪽에 공백으로 추가해서 길이가 `n`이 되게 만든 후 반환하고, 아니면 `s`를 그대로 반환하는 함수를 작성해보세요.

예:
```
leftPad('hello', 8); -> '   hello'
leftPad('hello', 3); -> 'hello'
```

풀이:
```js
function leftPad(s, n) {
  if (s.length < n) {
    const spaceNum = n - s.length
    return ' '.repeat(spaceNum) + s
  } else {
    return s
  }
}
```

### 문제 3

문자열을 입력받아, 문자열 안에 들어있는 모든 모음(a, e, i, o, u)의 갯수를 반환하는 함수를 작성하세요.

풀이:
```js
function count(str) {
  let num = 0
  for (let i = 0; i < str.length; i++) {
    if (str[i] === 'a' || str[i] === 'e' || str[i] === 'i' || str[i] === 'o' || str[i] === 'u') {
      num += 1
    } 
  }
  return num
}

count('hello')
```

### 문제 4

문자열을 입력받아, 해당 문자열에 포함된 문자의 종류와 갯수를 나타내는 객체를 반환하는 함수를 작성하세요.

예:
```
countChar('tomato'); -> {t: 2, o: 2, m: 1, a: 1}
```

강사님 풀이:
```js
function countChar(input) {
  const obj = {}
  for (let i = 0; i < input.length; i++) {
    const char = input[i]
    // 글자를 본적이 없다면 "글자": 1 을 적어준다.
    if ( !(char in obj) ) {
      obj[char] = 1
    } else {
    // 글자를 본적이 있다면 횟수를 1 증가 시켜준다.
      obj[char]++
    }
  }
  return obj
}

countChar('tomato')
```

### 문제 5

문자열을 입력받아 그 문자열이 회문(palindrome)인지 판별하는 함수를 작성하세요. (회문이란, '토마토', 'never odd or even'과 같이 뒤에서부터 읽어도 똑같이 읽히는 문자열을 말합니다.)

강사님 풀이(1):
```js
const isPalindrome = (input) => {
  for (let i = 0; i < input.length; i++) {
    const left = i;
    const right = input.length - i - 1;
    if (input[left] !== input[right]) {
      return false
    }
  }
  return true
}

isPalindrome ('토마토')
```
강사님 풀이(2):
```js
const isPalindrome = (input) => {
  for (let i = 0; i <= input.length / 2 -1; i++) {
    const left = i;
    const right = input.length - i - 1;
    if (input[left] !== input[right]) {
      return false
    }
  }
  return true
}

isPalindrome ('토마토')
```

### 문제 6

문자열을 입력받아, 그 문자열의 모든 '부분 문자열'로 이루어진 배열을 반환하는 함수를 작성하세요.

예:
```
subString('햄버거');
// 결과: ['햄', '햄버', '햄버거', '버', '버거', '거']
```

### 문제 7

문자열을 입력받아, 해당 문자열에서 중복된 문자가 제거된 새로운 문자열을 반환하는 함수를 작성하세요.

예:
```
removeDuplicates('tomato'); -> 'toma'
removeDuplicates('bartender'); -> 'bartend'
```

```js
const removeDuplicates = (input) => {
  let memory = ''
  for (let i = 0; i < input.length; i++) {
    if (memory.includes(input[i]) !== true) {
      memory += input[i]
    } 
  }
  return memory
}

removeDuplicates('tomato')
```

### 문제 8

이메일 주소를 입력받아, 아이디 부분을 별표(`*`)로 가린 새 문자열을 반환하는 함수를 작성하세요.

- 루프로 먼저 풀어보세요.
- `split` 메소드를 이용해서 풀어보세요.

```js
const email = (input) => {
  let seen = false
  let memory = ''
  for (let i = 0; i < input.length; i++) {
    if (input[i] === '@') {
      seen = true;
    } 

    if (seen === true) {
      memory += input[i]
    } else if (seen !== true){
      memory += '*'
    }
  }
  return memory
}

email('pyoonj0953@gmail.com')
```

풀이 (2):
```js
const removeId2 = (input) => {
  // '@'을 기준으로 쪼갠 후
  const splitted = input.split('@')
  // id 부분과 같은 길이를 갖는 별표 문자열을 만든다.
  const stars = '*'.repeat(splitted[0].length)
  // 별표를 @, 도메인 부분과 이어붙인 후 반환한다.
  return stars + '@' + splitted[1]
}
```

### 문제 9

문자열을 입력받아, 대문자는 소문자로, 소문자는 대문자로 바꾼 결과를 반환하는 함수를 작성하세요.

```js
function swapCase(input) {
  let memory = ''
  let capital = false
  for (let i = 0; i < input.length; i++) {
    if (input[i].toUpperCase() === input[i]) {
      capital = true;
    } else {
      capital = false;
    }
    
    if (capital === true) {
      memory += input[i].toLowerCase()
    } else if (capital !== true) {
      memory += input[i].toUpperCase()
    }
  }
  return memory
}

swapCase('JavaScript')
```


### 문제 10

문자열을 입력받아, 각 단어의 첫 글자를 대문자로 바꾼 결과를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)

풀이 (1):
```js
const firstLetterCapital = (input) => {
  let seenFirst = false
  let seenBlank = false
  let memory = ''
  for (let i = 0; i < input.length; i++) {
    if (i === 0) {
      seenFirst = true;
    } else {
      seenFirst = false;
    }
    
    if (input[i] === ' ') {
      seenBlank = true;
    } else {
      seenBlank = false;
    }

    if (seenFirst === true) {
      memory += input[i].toUpperCase()
    } else if (seenBlank == true){
      memory += ' ' + input[i + 1].toUpperCase()
      i++;
    } else {
      memory += input[i] 
    } 
  }
  return memory
}

firstLetterCapital('i am hungry')
```

강사님 풀이 (1):
```js
// 배열을 사용하지 않고, 루프를 사용해서 풀기
function capitalize(input) {
  let seenBlank = true
  let memory = ''

  for (let i = 0; i < input.length; i++) {
    if (seenBlank) {
      memory += input[i].toUpperCase()
    } else {
      memory += input[i]
    }

    if (input[i] === ' ') {
      seenBlank = true
    } else {
      seenBlank = false
    }
  }

  return memory
}

capitalize('i am hungry')

```

강사님 풀이 (2):
```js
// 배열 메소드를 사용해서 풀기
const capitalize = input => input.split(' ')
  .map(word => word.slice(0, 1).toUpperCase() + word.slice(1))
  .join(' ')

capitalize('i am hungry')
```


### 문제 11

문자열을 입력받아, 문자열 안에 들어있는 단어 중 가장 긴 단어를 반환하는 함수를 작성하세요. (문자열에 개행이 없다고 가정합니다.)

풀이 1(가장 긴 단어가 하나인 경우):
```js
const longestWord = (input) => {
  const arrWord = input.split(' ')
  arrWord.sort((x, y) => y.length - x.length);
  return arrWord[0]
}

longestWord('a bbb ccc dddd') // 'dddd' 반환
```

풀이 2(가장 긴 단어가 복수일 경우):
```js
const longestWord = (input) => {
  const arrWord = input.split(' ')
  arrWord.sort((x, y) => y.length - x.length);
  const arrLongestWords = []

  for (let item of arrWord) {
    if (arrWord[0].length === item.length) {
      arrLongestWords.push(item)
    }
  }
  return arrLongestWords
}

longestWord('ccc A bb CCC BB') // [ 'ccc', 'CCC' ] 반환
```


### 문제 12

문자열 `s`과 자연수 `n`을 입력받아, `s`의 첫 `n`개의 문자만으로 이루어진 새 문자열을 반환하는 함수를 작성하세요.

풀이 (1: slice) :
```js
function firstLetters(s, n) {
  return s.slice(0, n)
}

firstLetters('Hello World JavaScript', 5) // 'Hello' 반환
firstLetters('Hello World JavaScript', 11) // 'Hello World' 반환
```

풀이 (2: splice):
```js
function firstLetters(s, n) {
  let arrS = [...s]
  arrS.splice(n, arrS.length - n)
  return arrS.join('')
}

firstLetters('Hello World JavaScript', 5) // 'Hello' 반환
firstLetters('Hello World JavaScript', 11) // 'Hello World' 반환
```

### 문제 13

Camel case의 문자열을 입력받아, snake case로 바꾼 새 문자열을 반환하는 함수를 작성하세요.

풀이:
```js
const camelCaseToSnakeCase = (input) => {
  let arrSnake = ''
  for (let i = 0; i < input.length; i++) {
    if (input[i] === input[i].toLowerCase()) {
      arrSnake += input[i]
    } else {
      arrSnake += '_' + input[i].toLowerCase()
    }
  }
  return arrSnake
}

camelCaseToSnakeCase ('helloWorldJavaScript') // 'hello_world_java_script' 반환
```

### 문제 14

Snake case의 문자열을 입력받아, camel case로 바꾼 새 문자열을 반환하는 함수를 작성하세요.

### 문제 15

`String.prototype.split`과 똑같이 동작하는 함수를 작성하세요.

예:
```
split('Hello World'); -> ['Hello World']
split('Hello World', ' '); -> ['Hello', 'World']
split('let,const,var', ',') -> ['let', 'const', 'var']
```

풀이:
```js
function split(str, x) {
  if (x == null) {
    return [str]
  } else {
    let arrStrSplit = str.split(x)
    return arrStrSplit
  }
}

split('Hello World') // ['Hello World'] 반환
split('Hello World', ' ') // ['Hello', 'World'] 반환
split('let,const,var', ',') // ['let', 'const', 'var'] 반환
```


### 문제 16

2진수를 표현하는 문자열을 입력받아, 그 문자열이 나타내는 수 타입의 값을 반환하는 함수를 작성하세요. (`parseInt`를 사용하지 말고 작성해보세요.)

예:
```
convertBinary('1101'); -> 13
```

### 문제 17

숫자로만 이루어진 문자열을 입력받아, 연속된 두 짝수 사이에 하이픈(-)을 끼워넣은 문자열을 반환하는 함수를 작성하세요.

예:
```
insertHyphen('437027423'); -> '4370-274-23'
```
