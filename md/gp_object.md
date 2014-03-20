# Object?

- 배열
- 함수
- 정규 표현식
- 오브젝트

#### 프로퍼티들의 저장소

---

# Property?

##### 이름과 값을 갖는다.

---

# Property Name?

##### 이름으로 어떤 문자열도 사용될 수 있다.
##### 심지어 빈문자열도 가능하다.

---

# 프로퍼티의 값?

##### `undefined`를 제외한 어떤 값이든 사용할수 있다.

---

# Object?

##### 프로퍼티의 이름과 값에 어떠한 제약사항도 없다.

##### 데이타를 모으고 관리하는 데 유용하게 쓰인다.

##### 다른 오브젝트를 포함할 수도 있다.

##### 다른 오브젝트로부터 프로퍼티들을 상속받을 수 있다.

---

# 오브젝트 표현

##### `{` 과 `}`사이에 아무것도 없거나 하나 이상의 이름과 값의 쌍으로 표현한다.

---

# Example


```js
var empty_object = {};

var stooge = {
	"first-name": "Jerome",
	"last-name": "Howard"
};
```


---

# Property Name

##### 이름이 예약어가 아니거나 유효하다면,
##### 홑따옴표나 쌍따옴표로 이름을 둘러싸지 않아도 된다.

---

# Example

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

##### 유효한 자바스크립트 이름이거나 예약어가 아니면 . 표기법을 사용할 수 있다.

## Example

```js
stooge["first-name"] // "Joe"
flight.departure.IATA // "SYD"
```

---

# 값 가져오기

##### 존재하지 않는 이름에 접근하면 undefined 값을 가져온다.

## Example

```js
stooge["middle-name"] // undefined
flight.status // undefined
stooge["FIRST-NAME"] // undefined
```

---

# 값 할당

##### `||` 연산자를 사용하여 기본값을 채워줄수 있다.

## Example

```js
var middle = stooge["middle-name"] || "(none)";
var status = flight.status || "unknown";
```

---
# 값 가져오기

##### `undefined` 로부터 값을 얻는다면 `TypeError` exception이 생긴다.

## Example

```js
flight.equipment // undefined
flight.equipment.model // throw "TypeError"
flight.equipment && flight.equipment.model // undefined
```

---

# Update

##### 오브젝트에 있는 값은 할당해서 변경할 수 있다.

---

# Update

##### 변경하려는 프로퍼티에 이름이 이미 있다면, 프로퍼티 값은 변경된다.

## Example

```js
stooge['first-name'] = 'Jerome';
```

---

# Update

##### 프로퍼티의 이름을 갖고 있지 않다면, 오브젝트에 추가된다.

## Example

```js
stooge['middle-name'] = 'Lester';
stooge.nickname = 'Curly';
flight.equipment = {
	model: 'Boeing 777'
};
flight.status = 'overdue';
```

---

# Reference

##### 오브젝트들은 참조에 의해 전달된다.

##### 절대 복사되지 않는다.

## Example

```js
var x = stooge;
x.nickname = 'Curly';
var nick = stooge.nickname;
	// nick is 'Curly' because x and stooge
	// are references to the same object
var a = {}, b = {}, c = {};
	// a, b, and c each refer to a
	// different empty object
a = b = c = {};
	// a, b, and c all refer to
	// the same empty object
```

---

# Prototype

##### 모든 오브젝트들은
##### 프로퍼티들을 상속 받을수 있는 프로토타입 오브젝트에 연결되어있다.

##### 오브젝트를 만들때 프로토타입으로 오브젝트를 선택할수 있다.

---

# `create` Method

##### `Object` 함수에 `create` 메소드를 추가하자

##### `create` 메소드는 프로토타입으로서 이전의 오브젝트를 이용하여
##### 새로운 오브젝트를 만든다.

## Example

```js
if (typeof Object.create !== 'function') {
	Object.create = function (o) {
		var F = function () {};
		F.prototype = o;
		return new F();
	};
}

var another_stooge = Object.create(stooge);
```

---

# Prototype

##### 프로토타입 링크는 변경할때 아무런 효과가 없다.
##### 오브젝트를 변경할때 오브젝트의 포로토타입은 변경되지 않는다.

## Example

```js
another_stooge['first-name'] = 'Harry';
another_stooge['middle-name'] = 'Moses';
another_stooge.nickname = 'Moe';
```

---

# Prototype

##### 프로토타입 링크는 오직 참조할때만 쓰인다.


##### 오브젝트에 없는 프로퍼티의 이름에 접근하려고 하면 프로토타입에 참조하여 가져오려고 합니다.

##### 찾으려는 프로퍼티의 이름을 찾거나 `Object.prototype`에 도달할때까지 계속 찾습니다.
##### 찾으려는 프로퍼티의 이름을 못찾으면 `undefiend`를 반환합니다.


---






