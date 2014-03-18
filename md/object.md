# Object?

- 배열
- 함수
- 정규 표현식
- 오브젝트

---

# Object?

#### 프로퍼티들의 저장소

---

# Property?

##### 이름과 값을 갖는다.

---

# 프로퍼티의 이름?

##### 이름으로 어떤 문자열도 사용될 수 있다.
##### 심지어 빈문자열도 가능하다.

---

# 프로퍼티의 값?

##### `undefined`를 제외한
##### 어떤 값이든 사용할수 있다.

---

# Object?

##### 프로퍼티의 이름과 값에
##### 어떠한 제약사항도 없다.

---

# Object?

##### 데이타를 모으고 관리하는 데
##### 유용하게 쓰인다.

---

# Object?

##### 다른 오브젝트를
##### 포함할 수도 있다.

---

# Object?

##### 다른 오브젝트로부터
##### 프로퍼티들을 상속받을 수 있다.

---

# 오브젝트 표현

##### `{` 과 `}`사이에 아무것도 없거나
##### 하나 이상의 이름과 값의 쌍으로 표현한다.

---

# 예제

``` js
var empty_object = {};

var stooge = {
	"first-name": "Jerome",
	"last-name": "Howard"
};
```

---

# 프로퍼티 이름

##### 이름이 예약어가 아니거나 유효하다면,
##### 홑따옴표나 쌍따옴표로 이름을 둘러싸지 않아도 된다.

---

# 예제

```js
var flight = {
	airline: "Oceanic",
	number: 815,
	departure: {
		IATA: "SYD",
		time: "2004-09-22 14:55",
		city: "Sydney"
	},
	arrival: {
		IATA: "LAX",
		time: "2004-09-23 10:42",
		city: "Los Angeles"
	}
};
```

---

# 값 가져오기

##### `[`와 `]`사이에 문자열 표현식을 사용한다.

---

# 값 가져오기

##### 유효한 자바스크립트 이름이거나
##### 예약어가 아니면
##### . 표기법을 사용할 수 있다.

---

# 예제

```js
stooge["first-name"] // "Joe"
flight.departure.IATA // "SYD"
```

---

##### 존재하지 않는 이름에 접근하면
##### undefined 값을 가져온다.

---

# 예제

```js
stooge["middle-name"] // undefined
flight.status // undefined
stooge["FIRST-NAME"] // undefined
```

---

##### `||` 연산자를 사용하여
##### 기본값을 채워줄수 있다.

---

# 예제

```js
var middle = stooge["middle-name"] || "(none)";
var status = flight.status || "unknown";
```

---

##### `undefined` 로부터 값을 얻는다면
##### `TypeError` exception이 생긴다.

---

# 예제

```js
flight.equipment // undefined
flight.equipment.model // throw "TypeError"
flight.equipment && flight.equipment.model // undefined
```

---