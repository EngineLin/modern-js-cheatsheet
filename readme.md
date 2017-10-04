# 現今版本的 JavaScript 小抄

![現今版本的 JavaScript 小抄](https://i.imgur.com/aexPxMb.png)
<small>圖片來源: [Ahmad Awais ⚡️](https://github.com/ahmadawais)</small>

## 介紹

### 動機

這個文件是 JavaScript 的小抄， 你會經常在現今的專案以及大部分現代簡潔的程式碼中遇到
you will frequently encounter in modern projects and most contemporary 程式碼範例.

這個手冊並不打算從基礎教你 JavaScript，而是藉由協助那些從現代程式庫中因為 JavaScript 的概念，掙扎著學習看起來模糊不清的基礎知識的人(或者說那些痛苦的學習React的人)，能夠更進一步發展。
This guide is not intended to teach you JavaScript from the ground up, but to help developers with basic knowledge who may struggle to get familiar with modern codebases (or let's say to learn React for instance) because of the JavaScript concepts used.

另外，有時候我會提供一些要點，或許是有待商榷的，但我會小心地提供。當我提供時只是個人私下的建議。
Besides, I will sometimes provide personal tips that may be debatable but will take care to mention that it's a personal recommendation when I do so.

多數在這裡的觀念都是來自 JavaScript 更新之後的部分( ES2015，也稱做 ES6 )。你可以找到這一次更新後加入的特色
> **筆記:** Most of the concepts introduced here are coming from a JavaScript language update (ES2015, often called ES6). You can find new features added by this update [這裡](http://es6-features.org); 這個製作的很好。

### 補充資源

當你掙扎於離解一個概念時，我建議你從下列資源找答案:
When you struggle to understand a notion, I suggest you look for answers on the following resources:

- [MDN (Mozilla Developer Network)](https://developer.mozilla.org/en-US/search?q=)
- [You don't know JS (book)](https://github.com/getify/You-Dont-Know-JS)
- [ES6 Features with examples](http://es6-features.org)
- [WesBos blog (ES6)](http://wesbos.com/category/es6/)
- [Reddit (JavaScript)](https://www.reddit.com/r/javascript/)
- [Google](https://www.google.com/) 用以找尋特定 Blog 或者資源 || to find specific blog and resources
- [StackOverflow](https://stackoverflow.com/questions/tagged/javascript)

## 目錄

- [現今版本的 JavaScript 小抄](#modern-javascript-cheatsheet)
  * [介紹](#introduction)
    + [動機](#motivation)
    + [補充資源](#complementary-resources)
  * [目錄](#table-of-contents)
  * [觀念](#notions)
    + [變數宣告子: var, const, let](#variable-declaration-var-const-let)
      - [簡短解釋](#short-explanation)
      - [程式碼範例](#sample-code)
      - [細節解釋](#detailed-explanation)
      - [外部資源](#external-resource)
    + [箭頭函數](#-arrow-function)
      - [程式碼範例](#sample-code-1)
      - [細節解釋](#detailed-explanation-1)
        * [簡潔](#concision)
        * [*this* 的參照](#this-reference)
      - [有用的資源](#useful-resources)
    + [函數的自動生成參數](#function-default-parameter-value)
      - [外部資源](#external-resource-1)
    + [Destructuring 物件跟陣列](#destructuring-objects-and-arrays)
      - [程式碼範例與解釋](#explanation-with-sample-code)
      - [有用的資源](#useful-resources-1)
    + [陣列方法 - map / filter / reduce](#array-methods---map--filter--reduce)
      - [程式碼範例](#sample-code-2)
      - [解釋](#explanation)
        * [Array.prototype.map()](#arrayprototypemap)
        * [Array.prototype.filter()](#arrayprototypefilter)
        * [Array.prototype.reduce()](#arrayprototypereduce)
      - [外部資源](#external-resource)
    + [Spread 操作子 "..."](#spread-operator-)
      - [程式碼範例](#sample-code-3)
      - [解釋](#explanation-1)
        * [可迭代的 (向陣列)](#in-iterables-like-arrays)
        * [函數的 rest 參數](#function-rest-parameter)
        * [物件的屬性的 spreading](#object-properties-spreading)
      - [外部資源](#external-resources)
    + [物件的屬性的速寫法](#object-property-shorthand)
      - [解釋](#explanation-2)
      - [外部資源s](#external-resources-1)
    + [協定](#promises)
      - [程式碼範例](#sample-code-4)
      - [解釋](#explanation-3)
        * [建立協定](#create-the-promise)
        * [協定處理器的用法](#promise-handlers-usage)
      - [外部資源s](#external-resources)
    + [模板文字](#template-literals)
      - [程式碼範例](#sample-code-5)
      - [外部資源](#external-resources-2)
    + [匯入/匯出](#imports--exports)
      - [程式碼範例與解釋](#explanation-with-sample-code-1)
        * [匯出命名](#named-exports)
        * [自動匯入/匯出](#default-import--export)
      - [外部資源](#external-resources-3)
    + [JavaScript 的 *this*](#-javascript-this)
      - [外部資源](#external-resources-4)
    + [類別](#class)
      - [例子](#samples)
      - [外部資源](#external-resources-5)
    + [異步/等待](#async-await)
      - [程式碼範例](#sample-code-6)
      - [程式碼範例與解釋](#explanation-with-sample-code-2)
      - [外部資源](#external-resources-6)
    + [Truthy / Falsy](#truthy--falsy)
      - [外部資源](#external-resources-7)
  * [字彙表](#glossary)
    + [作用域](#-scope)
    + [變數的修改](#-variable-mutation)

## 觀念

### 宣告變數: var, const, let

在 JavaScript 中有三種關鍵字能夠宣告一個新變數，並且每種之間都有差異性。它們分別是 ```var```, ```let``` 跟 ```const```.
In JavaScript, there are three keywords available to declare a variable, and each has its differences. Those are ```var```, ```let``` and ```const```.

#### 簡介

利用 ```const``` 來宣告的變數不能夠重新分配，而 ```let``` 跟 ```var``` 卻可以。
Variables declared with ```const``` keyword can't be reassigned, while ```let``` and ```var``` can.

我建議你總是利用 ```const``` 宣告你的變數，只有當你需要在晚點 *mutate* (專業術語，指宣告後修改)或者重新分配你的變數時使用 ```let``` 來宣告。
I recommend always declaring your variables with ```const``` by default, and with ```let``` if you need to *mutate* it or reassign it later.

<table>
  <tr>
    <th></th>
    <th>Scope</th>
    <th>Reassignable</th>
    <th>Mutable</th>
   <th><a href="#tdz_sample">Temporal Dead Zone</a></th>
  </tr>
  <tr>
    <th>const</th>
    <td>Block</td>
    <td>No</td>
    <td><a href="#const_mutable_sample">Yes</a></td>
    <td>Yes</td>
  </tr>
  <tr>
    <th>let</th>
    <td>Block</td>
    <td>Yes</td>
    <td>Yes</td>
    <td>Yes</td>
  </tr>
   <tr>
    <th>var</th>
    <td>Function</td>
    <td>Yes</td>
    <td>Yes</td>
    <td>No</td>
  </tr>
</table>

#### 簡短程式碼

```javascript
const person = "Nick";
person = "John" // 會出現一個錯誤， person 無法被重新分配 Will raise an error, person can't be reassigned
```

```javascript
let person = "Nick";
person = "John";
console.log(person) // "John" 使用 let 宣告是可以重新分配的 "John", reassignment is allowed with let
```

#### 解釋細節

[*scope*](#scope_def) 之於變數大概是 "這個變數在程式碼中的哪個位置是有效的" 的意思。
The [*scope*](#scope_def) of a variable roughly means "where is this variable available in the code".

##### var

```var``` 宣告的變數是 *function scoped*，代表這個變數在一個涵式( function )裡面被創造出來，任何在涵式裡的事物皆可以存取這個變數。另外，一個在涵式內創造的 *function scoped* 變數無法被外界事物存取。
```var``` declared variables are *function scoped*, meaning that when a variable is created in a function, everything in that function can access that variable. Besides, a *function scoped* variable created in a function can't be accessed outside this function.

我建議你銘記這個 : 一個 *X scoped* 的變數意味著這個變數本身是 X 的屬性。
I recommend you to picture it as if an *X scoped* variable meant that this variable was a property of X.

```javascript
function myFunction() {
  var myVar = "Nick";
  console.log(myVar); // "Nick" - myVar 在涵式內可以被存取 || "Nick" - myVar is accessible inside the function
}
console.log(myVar); // 會出現一個參照錯誤， myVar 無法在涵式外被存取 || Throws a ReferenceError, myVar is not accessible outside the function.
```

繼續專注在變數作用域( variable scope )，還有一個更加微妙的例子:
Still focusing on the variable scope, here is a more subtle example:

```javascript
function myFunction() {
  var myVar = "Nick";
  if (true) {
    var myVar = "John";
    console.log(myVar); // "John"
    //事實上，myVar 處於 涵式作用域( function scoped )，我們只是利用宣告 "John" 來替代 myVar 中的 "Nick"
    // actually, myVar being function scoped, we just erased the previous myVar value "Nick" for "John"
  }
  console.log(myVar); // "John" - 看看 if 模塊如何影響它的內容
                      // "John" - see how the instructions in the if block affected this value
}
console.log(myVar); // 會出現一個參照錯誤， myVar 無法在涵式外被存取 || Throws a ReferenceError, myVar is not accessible outside the function.
```

另外，在執行的時候，利用 *var* 宣告的變數會被移動到作用域的最上方。這就是我們稱呼的 [var hoisting](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var#var_hoisting).
Besides, *var* declared variables are moved to the top of the scope at execution. This is what we call [var hoisting](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/var#var_hoisting).

這是部分程式碼:
This portion of code:

```js
console.log(myVar) // undefined -- 沒有出現錯誤 || undefined -- no error raised
var myVar = 2;
```

在執行時可以理解成:
is understood at execution like:

```js
var myVar;
console.log(myVar) // undefined -- 沒有出現錯誤 || undefined -- no error raised
myVar = 2;
```

##### let

```var``` 跟 ```let ``` 差不多，但是 ```let``` 在宣告變數時
```var``` and ```let ``` are about the same, but ```let``` declared variables

- 是 *block scoped* (模塊作用域)
- are *block scoped*
-在這些變數在被分配之前無法存取
- are **not** accessible before they are assigned
在同一個模塊內無法再次被宣告
- can't be re-declared in the same scope

來利用 模塊作用域( block-scoping ) 的衝突來討論我們提供的例子:
Let's see the impact of block-scoping taking our previous example:

```javascript
function myFunction() {
  let myVar = "Nick";
  if (true) {
    let myVar = "John";
    console.log(myVar); // "John"
    // 事實上， myVar 處於模塊作用域， 我們指是創造一個新的變數 myVar.
    // actually, myVar being block scoped, we just created a new variable myVar.
    // 這個變數無法在這個模塊( {} 內部)之外存取並且完全自第一個 myVar 外獨立被創造
    // this variable is not accessible outside this block and totally independent
    // from the first myVar created !
  }
  console.log(myVar); 
  // "Nick"，看看 if 模塊如何"沒有"影響它的內容
  // "Nick", see how the instructions in the if block DID NOT affect this value
}
console.log(myVar); 
// 出現參照錯誤，myVar 無法於涵式外存取
// Throws a ReferenceError, myVar is not accessible outside the function.
```

<a name="tdz_sample"></a> 現在，*let* (以及 *const*) 宣告的變數在分配之前無法被存取的意思是:
<a name="tdz_sample"></a> Now, what it means for *let* (and *const*) variables for not being accessible before being assigned:

```js
console.log(myVar) // 出現參照錯誤 || raises a ReferenceError !
let myVar = 2;
```
與 *var* 的變數對比，如果妳試著在 *let* 或者 *const* 宣告的變數中讀取或者寫入，將會出現一個錯誤訊息。這現象通常被稱作 [*暫時死區*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#Temporal_Dead_Zone_and_errors_with_let) 或 *TDZ*.
By contrast with *var* variables, if you try to read or write on a *let* or *const* variable before they are assigned an error will be raised. This phenomenon is often called [*Temporal dead zone*](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/let#Temporal_Dead_Zone_and_errors_with_let) or *TDZ*.

> **筆記:** 技術上來說，*let* 跟 *const* 的變數的宣告都會被提升( hoisted )，但不是他們的分配的動作。它們無法在被分配之前被使用，感覺上就好像它們沒有被提升( hoisting )但其實是有的。如果你想了解更多，試著在這裡找到更多資訊 [這有更加詳細的解釋](http://jsrocks.org/2015/01/temporal-dead-zone-tdz-demystified)
> **Note:** Technically, *let* and *const* variables declarations are being hoisted too, but not their assignation. Since they're made so that they can't be used before assignation, it intuitively feels like there is no hoisting, but there is. Find out more on this [very 細節解釋 here](http://jsrocks.org/2015/01/temporal-dead-zone-tdz-demystified) if you want to know more.

此外，你不能二度宣告一個使用 *let* 宣告的變數:
In addition, you can't re-declare a *let* variable:

```js
let myVar = 2;
let myVar = 3; // 出現句型錯誤 || Raises a SyntaxError
```

##### const

```const``` 宣告的變數表現就像 *let* 宣告的變數，但是它無法被重新分配。
```const``` declared variables behave like *let* variables, but also they can't be reassigned.

總結它們，*const* 宣告的變數:
To sum it up, *const* variables:

- 是模塊作用域
- are *block scoped*
- 在分配之前無法存取
- are not accessible before being assigned
- 在同一個作用域無法二度宣告
- can't be re-declared in the same scope
- 無法重新分配
- can't be reassigned

```js
const myVar = "Nick";
myVar = "John" 
// 出現錯誤，無法重新分配
// raises an error, reassignment is not allowed
```

```js
const myVar = "Nick";
const myVar = "John" 
// 出現錯誤，無法二度宣告
// raises an error, re-declaration is not allowed
```

<a name="const_mutable_sample"></a> 不過這有一點細節 : ```const``` 宣告的變數並不是[**不能修改**](#mutation_def) ! 具體來說，這意味著 *物件* 跟 *陣列* 利用 ```const``` 宣告的變數是 **可以** 被修改的。
<a name="const_mutable_sample"></a> But there is a subtlety : ```const``` variables are not [**immutable**](#mutation_def) ! Concretely, it means that *object* and *array* ```const``` declared variables **can** be mutated.

物件來說:
For objects:
```js
const person = {
  name: 'Nick'
};
person.name = 'John' 
// 這是可行的! 變數 person 整體不能重新分配，但可以修改內容。
// this will work ! person variable is not completely reassigned, but mutated
console.log(person.name) // "John"
person = "Sandra" 
// 出現錯誤， 因為 const 宣告的變數是不允許重新分配的
// raises an error, because reassignment is not allowed with const declared variables
```

陣列來說:
For arrays:
```js
const person = [];
person.push('John'); 
// 這是可行的! 變數 person 整體不能重新分配，但可以修改內容。
// this will work ! person variable is not completely reassigned, but mutated
console.log(person[0]) // "John"
person = ["Nick"] 
// 出現錯誤， 因為 const 宣告的變數是不允許重新分配的
// raises an error, because reassignment is not allowed with const declared variables
```

#### 外部資源

- [How let and const are scoped in JavaScript - WesBos](http://wesbos.com/javascript-scoping/)
- [Temporal Dead Zone (TDZ) Demystified](http://jsrocks.org/2015/01/temporal-dead-zone-tdz-demystified)

### <a name="arrow_func_concept"></a> 矢量涵式

在 ES6 JavaScript 更新包括了 *arrow functions*，這是另一個方式宣告與使用涵式。它帶來這些好處:
The ES6 JavaScript update has introduced *arrow functions*, which is another way to declare and use functions. Here are the benefits they bring:

- 更簡潔
- More concise
- *this* 從環境被拿取
- *this* is picked up from surroundings
- 將 return 隱藏起來(不用打但是依舊有功能)
- implicit return

#### 簡單的程式碼

- 簡潔以及隱藏 return
- Concision and implicit return

```js
function double(x) { return x * 2; } 
// 傳統方式
// Traditional way
console.log(double(2)) // 4
```

```js
const double = x => x * 2; 
// 利用矢量涵式來寫相同涵式並且隱藏了 return
// Same function written as an arrow function with implicit return
console.log(double(2)) // 4
```

- *this* 的參照
- *this* reference

在矢量涵式中，*this* 就會等同於該封閉環境下執行的內容的 *this* 的值。至少，使用矢量涵式的情況下，你不需要再使用 "that = this" 的把戲，當你需要呼叫一個包含在涵式中的涵式。
In an arrow function, *this* is equal to the *this* value of the enclosing execution context. Basically, with arrow functions, you don't have to do the "that = this" trick before calling a function inside a function anymore.

```js
function myFunc() {
  this.myVar = 0;
  setTimeout(() => {
    this.myVar++;
    console.log(this.myVar) // 1
  }, 0);
}
```

#### 解釋細節

##### 簡潔

矢量涵式在許多方面都比傳統涵式更加簡潔。讓我們複習所有可能的例子:
Arrow functions are more concise than traditional functions in many ways. Let's review all the possible cases:

- 隱藏 VS 顯露 return
- Implicit VS Explicit return

一個 **explicit return** 代表一個將 *return* 關鍵字使用在它的內容裡的涵式。
An **explicit return** is a function where the *return* keyword is used in its body.

```js
  function double(x) {
    return x * 2; 
    // 這涵式可見地回傳 x * 2， *return* 關鍵字被使用。
    // this function explicitly returns x * 2, *return* keyword is used
  }
```

在傳統寫涵式的方法裡，return 永遠都會被寫出來。但在矢量涵式中，你可以使用 *implicit return* 方法，這代表你可以省略 *return* 卻依舊可以回傳值。
In the traditional way of writing functions, the return was always explicit. But with arrow functions, you can do *implicit return* which means that you don't need to use the keyword *return* to return a value.

來做一個隱藏的 return 涵式，那程式碼必須被寫在同一個句子裡。
To do an implicit return, the code must be written in a one-line sentence.

```js
  const double = (x) => {
    return x * 2; 
    // 這裡就是 Explicit return
    // Explicit return here
  }
```

當這裡只有一個回傳值，我們可以使用 implicit return
Since there only is a return value here, we can do an implicit return.

```js
  const double = (x) => x * 2;
```

這樣一來，我們只需要 **移除中斷路徑符號( brackets 指大括號 {} )** 跟 **return** 關鍵字。這就是為何它被稱做 *implicit* return，因為 *return* 關鍵字並不在那哩，但是涵式依舊會回傳 ```x * 2```。
To do so, we only need to **remove the brackets** and the **return** keyword. That's why it's called an *implicit* return, the *return* keyword is not there, but this function will indeed return ```x * 2```.

> **筆記:** 如果你的涵式並沒有回傳一個值(*副作用*)，它就不會進行回傳，不論是 explicit 或 implicit 的形式。
> **Note:** If your function does not return a value (with *side effects*), it doesn't do an explicit nor an implicit return.

另外， 如果你想要隱藏地還傳一個 *物件*，你 **必須用插入符號( 代表中小括號 () )將它包起來** 不然它會與區壞結構規則產生衝突:
Besides, if you want to implicitly return an *object* you **must have parenthesis around it** since it will conflict with the block braces:

```js
const getPerson = () => ({ name: "Nick", age: 24 })
console.log(getPerson()) 
// { name: "Nick", age: 24 } -- 利用矢量函數隱藏地回傳這個物件
// { name: "Nick", age: 24 } -- object implicitly returned by arrow function
```

只有一個
- Only one argument

如果在涵式中你只參照一個參數，你可以忽綠包覆參數地插入符號。 如果我們利用 *double* 這個程式碼提取數值:
If your function only takes one parameter, you can omit the parenthesis around it. If we take back the above *double* code:

```js
  const double = (x) => x * 2; 
  // 這個矢量函數只參照一個參數
  // this arrow function only takes one parameter
```

可以忽略用來包覆參數的插入符號:
Parenthesis around the parameter can be avoided:

```js
  const double = x => x * 2; 
  // 這個矢量函數只參照一個參數
  // this arrow function only takes one parameter
```

- 無參數
- No arguments

當它們沒有提供參數數值給矢量函數時，你需要使用插入符號不然它的句型就會錯誤。
When there is no argument provided to an arrow function, you need to provide parentheses, or it won't be valid syntax.

```js
  () => { 
    // 有插入符號，所以沒問題。
    // parenthesis are provided, everything is fine
    const x = 2;
    return x;
  }
```

```js
  => { 
    // 沒有插入符號，無法作用。
    // No parenthesis, this won't work!
    const x = 2;
    return x;
  }
```

##### *this* 的參照

為了利用介紹矢量函數來深入瞭解 *this*，你必須知道 [this](#this_def) 的在 JavaScript 的習性。
To understand this subtlety introduced with arrow functions, you must know how [this](#this_def) behaves in JavaScript.

在矢量函式中，*this* 就會等同於該封閉環境下執行的內容的 *this* 的值。那麼，矢量函數不會創造一個新的 *this* 是什麼意思，它從它的環境中拿一個過來取代。
In an arrow function, *this* is equal to the *this* value of the enclosing execution context. What it means is that an arrow function doesn't create a new *this*, it grabs it from its surrounding instead.

若沒有矢量函數，你想要自一個放在函示裡面的 *this* 存取一個變數時，你必須使用 *that = this* 或 *self = this* 的手法。
Without arrow function, if you wanted to access a variable from *this* in a function inside a function, you had to use the *that = this* or *self = this* trick.

例如，在 myFunc 變數中使用 setTimeout function:
For instance, using setTimeout function inside myFunc:

```js
function myFunc() {
  this.myVar = 0;
  var that = this; 
  // that = this 手法
  // that = this trick
  setTimeout(
    function() { 
      // 一個新的 *this* 在這個函示作用域內生成
      // A new *this* is created in this function scope
      that.myVar++;
      console.log(that.myVar) // 1

      console.log(this.myVar) 
      // undefined -- 看上方函式說明
      // undefined -- see function declaration above
    },
    0
  );
}
```

但在矢量函式中，*this* 是從自身的周圍拿取:
But with arrow function, *this* is taken from its surrounding:

```js
function myFunc() {
  this.myVar = 0;
  setTimeout(
    () => { 
      // this 自周圍拿取，也就是自 myFunc 拿取
      // this taken from surrounding, meaning myFunc here
      this.myVar++;
      console.log(this.myVar) // 1
    },
    0
  );
}
```

#### 有用的資源

- [Arrow functions introduction - WesBos](http://wesbos.com/arrow-functions/)
- [JavaScript arrow function - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Arrow_functions)
- [Arrow function and lexical *this*](https://hackernoon.com/javascript-es6-arrow-functions-and-lexical-this-f2a3e2a5e8c4)

### 函式自動生成的參數數值

自 ES2015 版本的 JavaScript 更新後開始，你可以使用下列句型，設定自動生成參數數值在你的函式內的參數:
Starting from ES2015 JavaScript update, you can set default value to your function parameters using the following syntax:

```js
function myFunc(x = 10) {
  return x;
}
console.log(myFunc()) 
// 10 -- 沒有提供 x 的數值所以自動生成數值 10 就被分配給 myFunc 中的 x
// 10 -- no value is provided so x default value 10 is assigned to x in myFunc
console.log(myFunc(5)) 
// 5 -- 當 x 的數值被提供時，在 myFunc 內的 x 自然就等於提供的數值 5
// 5 -- a value is provided so x is equal to 5 in myFunc

console.log(myFunc(undefined)) 
// 10 -- undefined 作為參數數值被提供時自動生成數值會啟用，x 被分配 10
// 10 -- undefined value is provided so default value is assigned to x
console.log(myFunc(null)) 
// null -- null 作為參數提供時視為一個數值 null，更多細節請看下方
// null -- a value (null) is provided, see below for more details
```

自動生成參數只有在兩種請況下起作用:
The default parameter is applied in two and only two situations:

- 當沒有參數數值被提供時
- No parameter provided
- 當 *undefined* 被當作參數數值提供時
- *undefined* parameter provided

換句話說，當你使用 *null* 當作參數數值提供時，自動生成參數並不會起作用
In other words, if you pass in *null* the default parameter **won't be applied**.

> **筆記:**  自動生成數值的分配可以與解構參數結合使用(看下一個標題提供的例子)
> **Note:** Default value assignment can be used with destructured parameters as well (see next notion to see an example)

#### 外部資源

- [Default parameter value - ES6 Features](http://es6-features.org/#DefaultParameterValues)
- [Default parameters - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Functions/Default_parameters)

### 解構物件與陣列

*解構( Destructuring )* 是一個便利的方式，利用提取物件或陣列中的儲存的資料來建立新變數。
*Destructuring* is a convenient way of creating new variables by extracting some values from data stored in objects or arrays.

舉幾個例子，*destructuring* 可以用來解構函式參數或像是在 React 專案中的 *this.props*
To name a few use cases, *destructuring* can be used to destructure function parameters or *this.props* in React projects for instance.

#### 利用簡單程式碼解釋

- 物件
- Object

我們來思考下列的物件例子:
Let's consider the following object for all the samples:

```js
const person = {
  firstName: "Nick",
  lastName: "Anderson",
  age: 35,
  sex: "M"
}
```

沒有使用 destructuring 的情況
Without destructuring

```js
const first = person.firstName;
const age = person.age;
const city = person.city || "Paris";
```

使用 destructuring 時全部都在一行:
With destructuring, all in one line:

```js
const { firstName: first, age, city = "Paris" } = person; //就是這個啦! || That's it !

console.log(age) 
// 35 -- 一個新的變數被建立並且等於 person.age 的數值
// 35 -- A new variable age is created and is equal to person.age
console.log(first) 
// "Nick" -- 一個新變數 first 被建立並且等於 person.firstName 的數值
// "Nick" -- A new variable first is created and is equal to person.firstName
console.log(firstName) 
// Undefined -- person.firstName 是存在的 "但是" 被建立的新變數被宣告為 first
// Undefined -- person.firstName exists BUT the new variable created is named first
console.log(city) 
// "Paris" -- 一個新變數 city 被建立並且等同於 person.city 的數值，但數值是 undefined，所以自動生成參數使 city 等同於自動生成參數的數值 "Paris"
// "Paris" -- A new variable city is created and since person.city is undefined, city is equal to the default value provided "Paris".
```

**Note :** 在 ```const { age } = person;``` 中，於關鍵字 *const* 後方的中斷路徑符號(大括號)不是用來宣告物件或者模塊的，單純是 *destructuring* 的句型用法。
**Note :** In ```const { age } = person;```, the brackets after *const* keyword are not used to declare an object nor a block but is the *destructuring* syntax.

- 函式參數
- Function parameters

*Destructuring* 在函式中經常被使用在解構物件的參數
*Destructuring* is often used to destructure objects parameters in functions.

沒有 destructuring 的情況
Without destructuring

```js
function joinFirstLastName(person) {
  const firstName = person.firstName;
  const lastName = person.lastName;
  return firstName + '-' + lastName;
}

joinFirstLastName(person); // "Nick-Anderson"
```

Destructuring 物件參數 *person* 後我們得到更簡潔的函式:
In destructuring the object parameter *person*, we get a more concise function:

```js
function joinFirstLastName({ firstName, lastName }) { 
  // 利用 destructuring person 這個參數來建立變數 firstName 及 lastName
  // we create firstName and lastName variables by destructuring person parameter
  return firstName + '-' + lastName;
}

joinFirstLastName(person); // "Nick-Anderson"
```
Destructuring 甚至可以更優雅的使用在[陣列函式](#arrow_func_concept):
Destructuring is even more pleasant to use with [arrow functions](#arrow_func_concept):

```js
const joinFirstLastName = ({ firstName, lastName }) => firstName + '-' + lastName;

joinFirstLastName(person); // "Nick-Anderson"
```

- 陣列
- Array

來利用下列陣列思考:
Lets consider the following array:

```js
const myArray = ["a", "b", "c"];
```

沒有 destructuring 的情況
Without destructuring

```js
const x = myArray[0];
const y = myArray[1];
```

使用 destructur 的情況
With destructuring

```js
const [x, y] = myArray; // 就是這樣啦! || That's it !

console.log(x) // "a"
console.log(y) // "b"
```

#### 有用的資源

- [ES6 Features - Destructuring Assignment](http://es6-features.org/#ArrayMatching)
- [Destructuring Objects - WesBos](http://wesbos.com/destructuring-objects/)
- [ExploringJS - Destructuring](http://exploringjs.com/es6/ch_destructuring.html)

### 陣列方法 - map / filter / reduce

*Map*, *filter* 及 *reduce* 它們是來自被稱做[*函式化編程*](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0)的編程範例的陣列方法。
*Map*, *filter* and *reduce* are array methods that are coming from a programming paradigm named [*functional programming*](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-functional-programming-7f218c68b3a0).

總結來說:
To sum it up:

- **Array.prototype.map()** 擷取一個陣列，在每一個元素上做某些事情，接著回傳轉換過的的元素組成的陣列。
- **Array.prototype.map()** takes an array, does something on its elements and returns an array with the transformed elements.
- **Array.prototype.filter()** 擷取一個陣列，決定元素是否留下或不留下，並回傳要留下的元素組成的陣列。
- **Array.prototype.filter()** takes an array, decides element by element if it should keep it or not and returns an array with the kept elements only
- **Array.prototype.reduce()** 擷取一個陣列及參數，元素會被放到同一個值裡(將這個值回傳)
- **Array.prototype.reduce()** takes an array and aggregates the elements into a single value (which is returned)

我推薦你們盡可能使用它們，在遵照函式編程的原則上。因為它們可以組合，並且簡潔又優雅。
I recommend to use them as much as possible in following the principles of functional programming because they are composable, concise and elegant.

關於這三個方法，你可以在很多情況下避免使用 *for* 及 *forEach* 迴圈。當你打算使用 *for* 迴圈時，試著改用 *map*, *filter* 及 *reduce* 的組合。你會在剛開始時很痛苦，因為這逼迫你使用不同方式思考，但是萬事起頭難，一定會越來越順利。
With those three methods, you can avoid the use of *for* and *forEach* loops in most situations. When you are tempted to do a *for* loop, try to do it with *map*, *filter* and *reduce* composed. You might struggle to do it at first because it requires you to learn a new way of thinking, but once you've got it things gets easier.

#### 簡單程式碼

```js
const numbers = [0, 1, 2, 3, 4, 5, 6];
const doubledNumbers = numbers.map(n => n * 2); // [0, 2, 4, 6, 8, 10, 12]
const evenNumbers = numbers.filter(n => n % 2 === 0); // [0, 2, 4, 6]
const sum = numbers.reduce((prev, next) => prev + next, 0); // 21
```

組合 map, filter 及 reduce 來計算所有學生中等級超過 10 的人的分數總和:
Compute total grade sum for students above 10 by composing map, filter and reduce:

```js
const students = [
  { name: "Nick", grade: 10 },
  { name: "John", grade: 15 },
  { name: "Julia", grade: 19 },
  { name: "Nathalie", grade: 9 },
];

const aboveTenSum = students
  .map(student => student.grade) 
  // 我們 map 學生陣列使之成為一個他們等級組成的陣列
  // we map the students array to an array of their grades
  .filter(grade => grade >= 10) 
  // 我們 filter 這個等級陣列使之只保留等級超過 10 的元素
  // we filter the grades array to keep those above 10
  .reduce((prev, next) => prev + next, 0); 
  // 我們將等級超過 10 的等級一個一個調出來相加
  // we sum all the grades above 10 one by one

console.log(aboveTenSum) 
//44 -- 10 (Nick) + 15 (John) + 19 (Julia), Nathalie 低於 10 就被忽略了
// 44 -- 10 (Nick) + 15 (John) + 19 (Julia), Nathalie below 10 is ignored
```

#### 解釋

來利用我們的例子思考下列數字陣列:
Let's consider the following array of numbers for our examples:

```js
const numbers = [0, 1, 2, 3, 4, 5, 6];
```

##### Array.prototype.map()

```js
const doubledNumbers = numbers.map(function(n) {
  return n * 2;
});
console.log(doubledNumbers); // [0, 2, 4, 6, 8, 10, 12]
```

這裡發生什麼事情? 我們在這個 *數字* 陣列中使用 .map，這 map 遍歷這個陣列上所有元素並將它們丟到我們的函式裡面。這個函式的目的是產出並從該陣列及其丟過來的元素回傳一個新的數值，如此一來，map 就可以取代那個元素。
What's happening here? We are using .map on the *numbers* array, the map is iterating on each element of the array and passes it to our function. The goal of the function is to produce and return a new value from the one passed so that map can replace it.

讓我們將這個函式用的更加乾淨，只為了這一次:
Lets extract this function to make it more clear, just for this once:

```js
const doubleN = function(n) { return n * 2; };
const doubledNumbers = numbers.map(doubleN);
console.log(doubledNumbers); // [0, 2, 4, 6, 8, 10, 12]
```

```numbers.map(doubleN)``` 產生 ```[doubleN(0), doubleN(1), doubleN(2), doubleN(3), doubleN(4), doubleN(5), doubleN(6)]``` 等同於 ```[0, 2, 4, 6, 8, 10, 12]```.
```numbers.map(doubleN)``` produces ```[doubleN(0), doubleN(1), doubleN(2), doubleN(3), doubleN(4), doubleN(5), doubleN(6)]``` which is equal to ```[0, 2, 4, 6, 8, 10, 12]```.

> **筆記:** 如果並沒有想要回傳一個新陣列，只是想要建立一個迴圈，這會有副作用。單純的使用 for / forEach 而不是 map
> **Note:** If you do not need to return a new array and just want to do a loop that has side effects, you might just want to use a for / forEach loop instead of a map.

##### Array.prototype.filter()

```js
const evenNumbers = numbers.filter(function(n) {
  return n % 2 === 0; 
  // true 如果 "n" 是 2 的倍數，false 如果 "n" 不是
  // true if "n" is par, false if "n" isn't
});
console.log(evenNumbers); // [0, 2, 4, 6]
```

我們在 *數字* 陣列使用 .filter，filter 會遍歷所有陣列上的元素並逐一丟到我們的函式內。函式的目標就是主宰了那些數值會被保留、哪些則不會，並回傳布靈值。Filter 便會回傳只有被留下來的數值組成的陣列。
We are using .filter on the *numbers* array, filter is iterating on each element of the array and passes it to our function. The goal of the function is to return a boolean that will determine whether the current value will be kept or not. Filter then returns the array with only the kept values.

##### Array.prototype.reduce()

reduce 方法的目標是 *reduce* 所有陣列中的元素。它遍歷所有元素成為一個單一數值。這個參數如何處理這些元素由你來決定
The reduce method goal is to *reduce* all elements of the array it iterates on into a single value. How it aggregates those elements is up to you.

```js
const sum = numbers.reduce(
  function(acc, n) {
    return acc + n;
  },
  0 
  // 在遍歷的第一步時設定累加變數的數值
  // accumulator variable value at first iteration step
);

console.log(sum) //21
```

就像 .map 及 .filter 方法，.reduce 使用在一個陣列與一個帶有初始參數的函式
Just like for .map and .filter methods, .reduce is applied on an array and takes a function as the first parameter.

時光飛逝，這部分改變了:
This time though, there are changes:

- .reduce 要擷取兩個參數
- .reduce takes two parameters

第一個參數是一個函式，會在每一次遍歷時被執行
The first parameter is a function that will be called at each iteration step.

第二個參數是設定累計參數的初始值(看下一個重點整理)
The second parameter is the value of the accumulator variable (*acc* here) at the first iteration step (read next point to understand).

- 函式參數
- Function parameters

你打算遍歷的函式就是 .reduce 擷取的兩個參數中的第一個。第一個( *acc* here )是累計變數，而第二個參數( *n* )是當前元素。
The function you pass as the first parameter of .reduce takes two parameters. The first one (*acc* here) is the accumulator variable, whereas the second parameter (*n*) is the current element.

累計變數會等於你的函式於遍歷步驟所 **提供** 的回傳的數值。在遍歷的第一步時，*acc* 等於你傳入的數值也就是 .reduce 的第二個參數。
The accumulator variable is equal to the return value of your function at the **previous** iteration step. At the first step of the iteration, *acc* is equal to the value you passed as .reduce second parameter.

###### 第一步迭代

```acc = 0``` 因為 reduce 的第二個參數傳入 0
```acc = 0``` because we passed in 0 as the second parameter for reduce

```n = 0``` *數字* 陣列的第一個元素
```n = 0``` first element of the *number* array

函式回傳 *acc* + *n* --> 0 + 0 --> 0
Function returns *acc* + *n* --> 0 + 0 --> 0

###### 第二步迭代

```acc = 0``` 這個會等於迭代步驟時回傳的數值
```acc = 0``` because its the value the function returned at the previous iteration step

```n = 1``` *數字*陣列的第二個元素
```n = 1``` second element of the *number* array

函式回傳 *acc* + *n* --> 0 + 1 --> 1
Function returns *acc* + *n* --> 0 + 1 --> 1

###### 第三步迭代

```acc = 1``` 這個會等於迭代步驟時回傳的數值
```acc = 1``` because its the value the function returned at the previous iteration step

```n = 2``` *數字*陣列的第三個元素
```n = 2``` third element of the *number* array

函式回傳 *acc* + *n* --> 1 + 2 --> 3
Function returns *acc* + *n* --> 1 + 2 --> 3

###### 第四步迭代

```acc = 3``` 這個會等於迭代步驟時回傳的數值
```acc = 3``` because it's the value the function returned at the previous iteration step

```n = 3``` *數字*陣列的第四個元素
```n = 3``` fourth element of the *number* array

函式回傳 *acc* + *n* --> 3 + 3 --> 6
Function returns *acc* + *n* --> 3 + 3 --> 6

###### [...] 最後一步迭代

```acc = 15``` 這個會等於迭代步驟時回傳的數值
```acc = 15``` because it's the value the function returned at the previous iteration step

```n = 6``` *數字*陣列的最後一個元素
```n = 6``` last element of the *number* array

函式回傳 *acc* + *n* --> 15 + 6 --> 21
Function returns *acc* + *n* --> 15 + 6 --> 21

這就是最後一步的迭代，**.reduce** 回傳 21
As it is the last iteration step, **.reduce** returns 21.

#### 外部資源

- [Understanding map / filter / reduce in JS](https://hackernoon.com/understanding-map-filter-and-reduce-in-javascript-5df1c7eee464)

### 擴展操作子 "..."

擴展操作子 ```...``` 在 ES2015 被介紹，並用於將可迭代元素（如數組）擴展到眾多元素可以合適放置的位置
The spread operator ```...``` has been introduced with ES2015 and is used to expand elements of an iterable (like an array) into places where multiple elements can fit.

#### 簡單程式碼

```js
const arr1 = ["a", "b", "c"];
const arr2 = [...arr1, "d", "e", "f"]; // ["a", "b", "c", "d", "e", "f"]
```

```js
function myFunc(x, y, ...params) {
  console.log(x);
  console.log(y);
  console.log(params)
}

myFunc("a", "b", "c", "d", "e", "f")
// "a"
// "b"
// ["c", "d", "e", "f"]
```

```js
const { x, y, ...z } = { x: 1, y: 2, a: 3, b: 4 };
console.log(x); // 1
console.log(y); // 2
console.log(z); // { a: 3, b: 4 }

const n = { x, y, ...z };
console.log(n); // { x: 1, y: 2, a: 3, b: 4 }
```

#### 解釋

##### 在迭代元素中(例如陣列)

如果我們有兩個下列的字串:
If we have the two following arrays:

```js
const arr1 = ["a", "b", "c"];
const arr2 = [arr1, "d", "e", "f"]; // [["a", "b", "c"], "d", "e", "f"]
```

*arr2* 的第一個元素是個陣列，因為 *arr1* 是被插入 *arr2* 中的。但當我們希望 *arr2* 是一個純字母的陣列。這樣做，我們可以將 *arr1* 內的元素 *spread* 到 *arr2* 中。
*arr2* the first element is an array because *arr1* is injected as is into *arr2*. But what we want is *arr2* to be an array of letters. To do so, we can *spread* the elements of *arr1* into *arr2*.

使用擴展操作子的情況
With spread operator

```js
const arr1 = ["a", "b", "c"];
const arr2 = [...arr1, "d", "e", "f"]; // ["a", "b", "c", "d", "e", "f"]
```

##### 函式 rest operator

在函式參數中，我們可以使用 rest operator 來插入參數數值到一個我們可以將之迴圈的陣列中。這已經有一個 **argument** 物件綁定到每一個函式中，其內容等於全部傳入到函式中的參數組成的陣列
In function parameters, we can use the rest operator to inject parameters into an array we can loop in. There is already an **argument** object bound to every function that is equal to an array of all the parameters passed into the function.

```js
function myFunc() {
  for (var i = 0; i < arguments.length; i++) {
    console.log(arguments[i]);
  }
}

myFunc("Nick", "Anderson", 10, 12, 6);
// "Nick"
// "Anderson"
// 10
// 12
// 6
```

但，我們想要這個函式可以建立新的學生連同他的等級與他的平均等級。是否可以更加便利的截取前兩個參數並放入兩個不同的變數，然後有擁有所有等級放在一個我們可以迭代的陣列中?
But let's say that we want this function to create a new student with its grades and with its average grade. Wouldn't it be more convenient to extract the first two parameters into two separate variables, and then have all the grades in an array we can iterate over?

這正是 rest operator 允許我們做的。
That's exactly what the rest operator allows us to do!

```js
function createStudent(firstName, lastName, ...grades) {
  // firstName = "Nick"
  // lastName = "Anderson"
  // [10, 12, 6] -- "..." 拿取所有多出來的參數並建立一個 "grades" 陣列來包含它們
  // [10, 12, 6] -- "..." takes all other parameters passed and creates a "grades" array variable that contains them

  const avgGrade = grades.reduce((acc, curr) => acc + curr, 0) / grades.length; 
  // 自 grades 陣列中計算出 grade 的平均值
  // computes average grade from grades

  return {
    firstName: firstName,
    lastName: lastName,
    grades: grades,
    avgGrade: avgGrade
  }
}

const student = createStudent("Nick", "Anderson", 10, 12, 6);
console.log(student);
// {
//   firstName: "Nick",
//   lastName: "Anderson",
//   grades: [10, 12, 6],
//   avgGrade: 9,33
// }
```

> **筆記:** createStudent 函式並不好，因為我們沒有確認 grades.length 是否純在或者不等於 0。但他很容易讀所以我沒有加以處理。
> **Note:** createStudent function is bad because we don't check if grades.length exists or is different from 0. But it's easier to read this way, so I didn't handle this case.

##### 物件屬性的擴張

這一點，我建議你讀一讀之前關於迭代與函式參數的 rest operator 的解釋
For this one, I recommend you read previous explanations about the rest operator on iterables and function parameters.

```js
const myObj = { x: 1, y: 2, a: 3, b: 4 };
const { x, y, ...z } = myObj; //在這進行物件 destructuring || object destructuring here
console.log(x); // 1
console.log(y); // 2
console.log(z); // { a: 3, b: 4 }

// z 是 物件解構的 rest : myObj 物件減去 x 及 y 屬性解構
// z is the rest of the object destructured: myObj object minus x and y properties destructured

const n = { x, y, ...z };
console.log(n); // { x: 1, y: 2, a: 3, b: 4 }

// 這裡 z 物件的屬性擃展到 n 裡
// Here z object properties are spread into n
```

#### 外部資源

- [TC39 - Object rest/spread](https://github.com/tc39/proposal-object-rest-spread)
- [Spread operator introduction - WesBos](https://github.com/wesbos/es6-articles/blob/master/28%20-%20Spread%20Operator%20Introduction.md)
- [JavaScript & the spread operator](https://codeburst.io/javascript-the-spread-operator-a867a71668ca)
- [6 Great uses of the spread operator](https://davidwalsh.name/spread-operator)

### 速記物件屬性

當分配一個變數給一個物件的屬性，如果變數的名稱跟物件屬性名稱相同，你可以這樣做:
When assigning a variable to an object property, if the variable name is equal to the property name, you can do the following:

```js
const x = 10;
const myObj = { x };
console.log(myObj.x) // 10
```

#### 解釋

通常(在 ES2015 之前)當你宣告一個新的 *字面物件* 且想要使用變數當作物件內屬性的值，你會寫這樣子的程式碼:
Usually (pre-ES2015) when you declare a new *object literal* and want to use variables as object properties values, you would write this kind of code:

```js
const x = 10;
const y = 20;

const myObj = {
  x: x, // 分配 x 變數的值給 myObj 物件中的屬性 x || assigning x variable value to myObj.x
  y: y // 分配 y 變數的值給 myObj 物件中的屬性 y || assigning y variable value to myObj.y
};

console.log(myObj.x) // 10
console.log(myObj.y) // 20
```

如你所見，這有點重複了，因為 myObj 內的屬性名稱跟你相要分配給物件內屬性的變數名稱是一樣的。
As you can see, this is quite repetitive because the properties name of myObj are the same as the variable names you want to assign to those properties.

使用 ES2015，當變數名稱與屬性名稱相同時，你可以這樣簡寫:
With ES2015, when the variable name is the same as the property name, you can do this shorthand:

```js
const x = 10;
const y = 20;

const myObj = {
  x,
  y
};

console.log(myObj.x) // 10
console.log(myObj.y) // 20
```

#### 外部資源

- [Property shorthand - ES6 Features](http://es6-features.org/#PropertyShorthand)

### 協定

協定是一個可以自不同步函式同步回傳值的物件 ([ref](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261#3cd0)).
A promise is an object which can be returned synchronously from an asynchronous function ([ref](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261#3cd0)).

協定可以用來避免 [回扣地獄](http://callbackhell.com/), 且它越來越頻繁在現代的 JavaScript 專案中遇到
Promises can be used to avoid [callback hell](http://callbackhell.com/), and they are more and more frequently encountered in modern JavaScript projects.

#### 簡單程式碼

```js
const fetchingPosts = new Promise((res, rej) => {
  $.get("/posts")
    .done(posts => res(posts))
    .fail(err => rej(err));
});

fetchingPosts
  .then(posts => console.log(posts))
  .catch(err => console.log(err));
```

#### 解釋

當你做一個 *Ajax request* 時回應並不是同步的，因為你想要的資料需要一點時間才能拿到。有時甚至永遠不會拿到，如果你丟出請求的資源因為一些原因(例如 404 )無法使用。
When you do an *Ajax request* the response is not synchronous because you want a resource that takes some time to come. It even may never come if the resource you have requested is unavailable for some reason (404).

用來控制這樣的情況，ES2015 給了我們 *協定*。協定有三個不同部分:
To handle that kind of situations, ES2015 has given us *promises*. Promises can have three different states:

- 聽候
- Pending
- 兌現
- Fulfilled
- 拒絕
- Rejected

試著討論看看，我們想使用協定來控制一個 Ajax 請求，拿取資源 X
Let's say we want to use promises to handle an Ajax request to fetch the resource X.

##### 創建協定

我們首先要創建一個協定。我們打算使用 jQuery 的方法來做 Ajax 請求給 X
We firstly are going to create a promise. We will use the jQuery get method to do our Ajax request to X.

```js
const xFetcherPromise = new Promise( 
  // 使用 "new" 關鍵字來建立協定並儲存在一個變數中
  // Create promise using "new" keyword and store it into a variable
  function(resolve, reject) { 
    // 協定建構子提取擁有resolve 及 reject 參數自身的函式參數 
    // Promise constructor takes a function parameter which has resolve and reject parameters itself
    $.get("X") 
    // 發送 Ajax 的請求
    // Launch the Ajax request
      .done(function(X) { 
        // 一旦請求完成
        // Once the request is done...
        resolve(X); 
        // ... 解決，X 的值於協定內的屬性上
        // ... resolve the promise with the X value as parameter
      })
      .fail(function(error) { 
        // 如果請求失敗
        // If the request has failed...
        reject(error); 
        // ... 拒絕，協定內的屬性上代入error
        // ... reject the promise with the error as parameter
      });
  }
)
```

見上方例子，協定物件擷取一個擁有 **resolve** 及 **reject** 參數的 *執行* 函式。他的參數就是被呼叫時會將協定的 *pending* 部分移到個別的 *fulfilled* 及 *rejected* 部分
As seen in the above sample, the Promise object takes an *executor* function which takes two parameters **resolve** and **reject**. Those parameters are functions which when called are going to move the promise *pending* state to respectively a *fulfilled* and *rejected* state.

協定在例子創立後是在聽候部分，且它的 *執行* 函式是立即執行的。每一次 *resolve* 或 *reject* 函式在 *執行* 函式時被呼叫，協定就會呼叫本身相關的處理器
The promise is in pending state after instance creation and it's *executor* function is executed immediately. Once one of the function *resolve* or *reject* is called in the *executor* function, the promise will call its associated handlers.

##### 協定的處理器運用

為了拿到協定的資源(或者錯誤)，我們必定要連接他的處理器，利用下列方式:
To get the promise result (or error), we must attach to it handlers by doing the following:

```js
xFetcherPromise
  .then(function(X) {
    console.log(X);
  })
  .catch(function(err) {
    console.log(err)
  })
```

如果協定成功，*resolve* 被執行且函式會走 ```.then``` 且本身的參數執行
If the promise succeeds, *resolve* is executed and the function passed as ```.then``` parameter is executed.

如果失敗，*reject* 會被執行且函式會走到 ```.catch``` 且本身的參數被執行
If it fails, *reject* is executed and the function passed as ```.catch``` parameter is executed.

> **筆記 :** 如果當一個相應的處理器被連接時，協定已經是兌現或拒絕狀態，那個處理器會被呼叫，所以這不會讓異步操作子的完成進度與本身的處理器正在連接之間，產生競賽的情況。[(Ref: MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#Description)
> **Note :** If the promise has already been fulfilled or rejected when a corresponding handler is attached, the handler will be called, so there is no race condition between an asynchronous operation completing and its handlers being attached. [(Ref: MDN)](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise#Description)

#### 外部資源

- [JavaScript Promises for dummies - Jecelyn Yeen](https://scotch.io/tutorials/javascript-promises-for-dummies)
- [JavaScript Promise API - David Walsh](https://davidwalsh.name/promises)
- [Using promises - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Guide/Using_promises)
- [What is a promise - Eric Elliott](https://medium.com/javascript-scene/master-the-javascript-interview-what-is-a-promise-27fc71e77261)
- [JavaScript Promises: an Introduction - Jake Archibald](https://developers.google.com/web/fundamentals/getting-started/primers/promises)
- [Promise documentation - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Global_Objects/Promise)

### 模板文字

模板文字是個單獨及多行的文字的 [*內插值表示式*](https://en.wikipedia.org/wiki/String_interpolation) 
Template literals is an [*expression interpolation*](https://en.wikipedia.org/wiki/String_interpolation) for single and multiple-line strings.

換個說法，它是新的字串句型，當你可以便利的使用任何 JavaScript 表達式(例如變數)
In other words, it is a new string syntax in which you can conveniently use any JavaScript expressions (variables for instance).

#### 程式碼範例

```js
const name = "Nick";
`Hello ${name}, the following expression is equal to four : ${2+2}`;

// Hello Nick, 接下來的表示式會等於 4
// Hello Nick, the following expression is equal to four: 4
```

#### 外部資源

- [String interpolation - ES6 Features](http://es6-features.org/#StringInterpolation)
- [ES6 Template Strings - Addy Osmani](https://developers.google.com/web/updates/2015/01/ES6-Template-Strings)

### 匯入 / 匯出

ES6 模塊被用以從一個明確的模塊讀取變數與函數，利用他自身導入的模塊。
ES6 modules are used to access variables or functions in a module explicitly exported by the modules it imports.

我強烈推薦閱讀 MDN 資源的 匯入 / 匯出部分(見下方外部資源)，它寫的直觀又完整。
I highly recommend to take a look at MDN resources on import/export (see 外部資源s below), it is both straightforward and complete.

#### 程式碼範例與解釋

##### 匯出命名

匯出命名被用以從模塊中會出數個數值
Named exports are used to export several values from a module.

> **筆記 :** 你可以只做匯出命名 [first-class citizens] (https://en.wikipedia.org/wiki/First-class_citizen) 他有一個名子
> **Note :** You can only name-export [first-class citizens](https://en.wikipedia.org/wiki/First-class_citizen) that have a name.

```js
// mathConstants.js
export const pi = 3.14;
export const exp = 2.7;
export const alpha = 0.35;

// -------------

// myFile.js
import { pi, exp } from './mathConstants.js'; 
// 匯入命名 -- 類似解構句型
// Named import -- destructuring-like syntax
console.log(pi) // 3.14
console.log(exp) // 2.7

// -------------

// mySecondFile.js
import * as constants from './mathConstants.js'; 
// 將所有匯出的數值插入到 constants 變數中
// Inject all exported values into constants variable
console.log(constants.pi) // 3.14
console.log(constants.exp) // 2.7
```

縱使匯入命名看起來像 *destructuring*，他們有不同句型，且根本不是一樣的東西。他不支援自動生成數值或者*深入的*解構
While named imports looks like *destructuring*, they have a different syntax and are not the same. They don't support default values nor *deep* destructuring.

另外，你可以使用化名但在這個解構中的句型卻是不同的:
Besides, you can do aliases but the syntax is different from the one used in destructuring:

```js
import { foo as bar } from 'myFile.js'; 
// foo 被匯入並且插入一個新建立的 bar 變數中
// foo is imported and injected into a new bar variable
```

##### 自動匯出 / 匯入

關於自動匯出，在每個模塊中只有單一個自動生成。自動生成可以是一個函數、一個類別、一個物件或人任何其它東西。這數值會觀察主要的匯入，使它能以最簡單的方式匯入。[Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export#Description)
Concerning the default export, there is only a single default export per module. A default export can be a function, a class, an object or anything else. This value is considered the "main" exported value since it will be the simplest to import. [Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export#Description)

```js
// coolNumber.js
const ultimateNumber = 42;
export default ultimateNumber;

// ------------

// myFile.js
import number from './coolNumber.js';
// 自動匯出，會從他自己的名子獨立出來，自動的加入倒 number 這個新建立的變數中
// Default export, independently from its name, is automatically injected into number variable;
console.log(number) // 42
```

函數匯出:
Function exporting:

```js
// sum.js
export default function sum(x, y) {
  return x + y;
}
// -------------

// myFile.js
import sum from './sum.js';
const result = sum(1, 2);
console.log(result) // 3
```

#### 外部資源

- [ES6 Modules in bulletpoints](https://ponyfoo.com/articles/es6#modules)
- [Export - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/export)
- [Import - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/import)
- [Understanding ES6 Modules](https://www.sitepoint.com/understanding-es6-modules/)
- [Destructuring special case - import statements](https://ponyfoo.com/articles/es6-destructuring-in-depth#special-case-import-statements)
- [Misunderstanding ES6 Modules - Kent C. Dodds](https://medium.com/@kentcdodds/misunderstanding-es6-modules-upgrading-babel-tears-and-a-solution-ad2d5ab93ce0)
- [Modules in JavaScript](http://exploringjs.com/es6/ch_modules.html#sec_modules-in-javascript)

### <a name="this_def"></a> JavaScript *this*

*this* 操作子比起其他語言來說有相當不同的行為模式，且在多數情況下會因為函數被呼叫的方式所決定([Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)).
*this* operator behaves differently than in other languages and is in most cases determined by how a function is called. ([Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)).

這個部分有很多細節而且有點困難，我高度建議你深入研究下方的外部資源。然後，我會提供個人再決定 *this* 會等於什麼的想法。我學習這些要點從 [Yehuda Katz 寫的文章](http://yehudakatz.com/2011/08/11/understanding-javascript-function-invocation-and-this/).
This notion is having many subtleties and being quite hard, I highly suggest you to deep dive in the 外部資源s below. Thus, I will provide what I personally have in mind to determine what *this* is equal to. I have learned this tip from [this article written by Yehuda Katz](http://yehudakatz.com/2011/08/11/understanding-javascript-function-invocation-and-this/).

```js
function myFunc() {
  ...
}

// 每一個部分後面，你會發現在 myFunc 裡的 *this* 的值
// After each statement, you find the value of *this* in myFunc

myFunc.call("myString", "hello") 
// "myString" -- 首先 .call 的參數會插入到 *this*
// "myString" -- first .call parameter value is injected into *this*

// 在 non-strict-mode
// In non-strict-mode
myFunc("hello") 
// window -- myFunc() 只是 myFunc.call(window, "hello") 的語法糖
// window -- myFunc() is syntax sugar for myFunc.call(window, "hello")

// 在 strict-mode
// In strict-mode
myFunc("hello") 
// undefined -- myFunc() 是 myFunc.call(undefined, "hello") 的語法糖
// undefined -- myFunc() is syntax sugar for myFunc.call(undefined, "hello")
```

```js
var person = {
  myFunc: function() { ... }
}

person.myFunc.call(person, "test") 
// person Object -- 第一個被呼叫的參數會被插到 *this* 裡面
// person Object -- first call parameter is injected into *this*
person.myFunc("test")
// person Object -- person.myFunc() 是 person.myFunc.call(person, "test") 的語法糖
// person Object -- person.myFunc() is syntax sugar for person.myFunc.call(person, "test")

var myBoundFunc = person.myFunc.bind("hello") 
// 建立一個新函數，此函數中 "hello" 被插入到 *this* 的數值裡面
// Creates a new function in which we inject "hello" in *this* value
person.myFunc("test") 
// person Object -- bind 方法並不會影響到原本的方法
// person Object -- The bind method has no effect on the original method
myBoundFunc("test") 
// "hello" -- myBoundFunc 是 "hello" 連結到 *this* 情況下的 person.myFunc
// "hello" -- myBoundFunc is person.myFunc with "hello" bound to *this*
```

#### 外部資源

- [Understanding JavaScript Function Invocation and "this" - Yehuda Katz](http://yehudakatz.com/2011/08/11/understanding-javascript-function-invocation-and-this/)
- [JavaScript this - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/this)

### 類別

JavaScript 是個 [原形基礎](https://en.wikipedia.org/wiki/Prototype-based_programming) 的語言( 而 Java 則是 [類別基礎](https://en.wikipedia.org/wiki/Class-based_programming)的語言). ES6 版本中的 JavaScript 介紹了類別功能，這是一種用來處理原形基礎繼承的語法糖，而不是在 JavaScript 中真的導入類別基礎既成的模型。([ref](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)).
JavaScript is a [prototype-based](https://en.wikipedia.org/wiki/Prototype-based_programming) language (whereas Java is [class-based](https://en.wikipedia.org/wiki/Class-based_programming) language, for instance). ES6 has introduced JavaScript classes which are meant to be a syntactic sugar for prototype-based inheritance and **not** a new class-based inheritance model ([ref](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)).

如果你在其他語言很熟悉 classes 的用法，就很容易在這被這個 *class* 誤導。如果你有這種傾向，避免假設 JavaScript 中的類別運作方式跟其他語言一樣。將它當作全新的觀念來理解。
The word *class* is indeed error prone if you are familiar with classes in other languages. If you do, avoid assuming how JavaScript classes work on this basis and consider it an entirely different notion.

雖然這份文件避免從語言底層部分教導你，我相信你已經知道繼承的概念與運作模式。這邊依舊提供很適合理解這些概念的連結:
Since this document is not an attempt to teach you the language from the ground up, I will believe you know what prototypes are and how they behave. But here are some links I found great to understand this notion:

- [Understanding Prototypes in JS - Yehuda Katz](http://yehudakatz.com/2011/08/12/understanding-prototypes-in-javascript/)
- [A plain English guide to JS prototypes - Sebastian Porto](http://sporto.github.io/blog/2013/02/22/a-plain-english-guide-to-javascript-prototypes/)
- [Inheritance and the prototype chain - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

#### 範例

ES6 之前的繼承語法:
Before ES6, prototype syntax:

```js
var Person = function(name, age) {
  this.name = name;
  this.age = age;
}
Person.prototype.stringSentence = function() {
  return "Hello, my name is " + this.name + " and I'm " + this.age;
}
```

利用 ES6 的類別的語法:
With ES6 class syntax:

```js
class Person {
  constructor(name, age) {
    this.name = name;
    this.age = age;
  }

  stringSentence() {
    return "Hello, my name is " + this.name + " and I'm " + this.age;
  }
}

const myPerson = new Person("Manu", 23);
console.log(myPerson.age) // 23
console.log(myPerson.stringSentence()) // "Hello, my name is Manu and I'm 23
```

#### 外部資源

用來了解原型概念:
For prototype understanding:

- [Understanding Prototypes in JS - Yehuda Katz](http://yehudakatz.com/2011/08/12/understanding-prototypes-in-javascript/)
- [A plain English guide to JS prototypes - Sebastian Porto](http://sporto.github.io/blog/2013/02/22/a-plain-english-guide-to-javascript-prototypes/)
- [Inheritance and the prototype chain - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Inheritance_and_the_prototype_chain)

用來了解類別的概念:
For classes understanding:

- [ES6 Classes in Depth - Nicolas Bevacqua](https://ponyfoo.com/articles/es6-classes-in-depth)
- [ES6 Features - Classes](http://es6-features.org/#ClassDefinition)
- [JavaScript Classes - MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Classes)

### 異步等待

為了執行[協定](#promises)，這有個稱作 *async / await* 的新語法，你應該常常會在處理異步的程式碼時遇到。
In addition to [Promises](#promises), there is a new syntax you might encounter to handle asynchronous code named *async / await*.

async / await 函數的目的是簡化同步協定的模式與某些協定群的表現。就像協定是將回呼結構化，async / await 是結合協定與發動機 ([Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function))
The purpose of async/await functions is to simplify the behavior of using promises synchronously and to perform some behavior on a group of Promises. Just as Promises are similar to structured callbacks, async/await is similar to combining generators and promises. ([Ref: MDN](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function))

> **筆記 :** 你必須了解協定與協定的運作方式，再來嘗試理解 async / await，因為我們需要倚賴那些知識。
> **Note :** You must understand what are promises and how they work before trying to understand async / await since they rely on it.

> **筆記 2:** [*await* 必須被使用在 *async* 函數裡面](https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial-c7ec10518dd9#f3f0)，這代表你不能使用 await 在程式碼的高層，因為它不在異步函數裡
> **Note 2:** [*await* must be used in an *async* function](https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial-c7ec10518dd9#f3f0), which means that you can't use await in the top level of our code since that is not inside an async function.

#### 程式碼範例

```js
async function getGithubUser(username) { 
  // 異步的關鍵字允許 await 在函數裡的用法，代表函數會回傳一個協定
  // async keyword allows usage of await in the function and means function returns a promise
  try { 
    // 這代表錯誤會被 async 或 await 處理
    // this is how errors are handled with async / await
    const response = await fetch(`https://api.github.com/users/${username}`); 
    // "異步的"等待擷取協定成功兌現，接著才進入下一行
    // "synchronously" waiting fetch promise to resolve before going to next line
    return response.json();
  } catch (err) {
    alert(err);
  }
}

getGithubUser('mbeaudru').then(user => console.log(user)); 
// logging user response - 因為這個函數不在異步函數中，所以不能使用 await 語法。
// logging user response - cannot use await syntax since this code isn't in async function
```

#### 範例程式碼與解釋

*Async / Await* 在協定中建立但可以使用在更加急迫的類型的程式碼中。
*Async / Await* is built on promises but they allow a more imperative style of code.

*異步* 操作子將函數變成一個你可以使用 *await* 操作子的協定中。
*async* operator turns a function into a *promise* in which you can use the *await* operator.

```js
async function myFunc() {
  // 因為這是異步函數，所以可以使用 await 操作子
  // we can use await operator because this function is async
  try {
    return "hello world";
  } catch(e) {
    throw new Error();
  }
}

myFunc().then(msg => console.log(msg)) 
// "hello world" -- myFunc 因為異步操作子的緣故，變成一個協定
// "hello world" -- myFunc is turned into a promise because of async operator
```

當 *return* 的部分在異步函數中被達成，協定就會被兌現，數值會回傳。如果是錯誤在異步函數中被丟出，協定部分就變成 *rejected*.
When the *return* statement of an async function is reached, the promise is fulfilled with the value returned. If an error is thrown inside an async function, the promise state will turn to *rejected*.

*await* 操作子被用在等待 *協定*成功兌現，且只能夠只用在 *異步* 函數裡面。當它被遇到時，程式碼會立刻被暫停，直到協定成功兌現。
*await* operator is used to wait for a *Promise* to be fulfilled and only can be used inside an *async* function body. When encountered, the code execution is paused until the promise is fulfilled.

> **筆記 :** *fetch* 是一種可以使用 AJAX 請求的協定
> **Note :** *fetch* is a Promise that allows to do an AJAX request

先讓我們看看如何使用協定取得 GitHub 使用者:
Let's see how we could fetch a github user with promises first:

```js
function getGithubUser(username) {
  return new Promise((resolve, reject) => {
    fetch(`https://api.github.com/users/${username}`)
      .then(response => {
        const user = response.json();
        resolve(user);
      })
      .catch(err => reject(err));
  })
}

getGithubUser('mbeaudru')
  .then(user => console.log(user))
  .catch(err => console.log(err));
```

這就等同於 *async / await* 寫法下的:
Here's the *async / await* equivalent:

```js
async function getGithubUser(username) { 
  // 成為協定，且 await 關鍵字允許使用
  // promise + await keyword usage allowed
  try { 
    // 我們利用 try / catch 處理異步函數下的錯誤
    // We handle async function errors with try / catch
    const response = await fetch(`https://api.github.com/users/${username}`); 
    // 在擷取的協定兌現前，城市的執行會在這裡被停止。
    // Execution stops here until fetch promise is fulfilled.
    const user = response.json();
    return user; 
    // 等同於 getGithubUser 協定的結果，放 user 數值。
    // equivalent of resolving the getGithubUser promise with user value.
  } catch (err) {
    throw new Error(err); 
    // 等同於 getGithubUser 協定的結果，放 err 數值。
    // equivalent of rejecting getGithubUser promise with err value.
  }
}

getGithubUser('mbeaudru')
  .then(user => console.log(user))
  .catch(err => console.log(err));
```

*async / await* 的語法在串聯獨立的協定時相當的方便
*async / await* syntax is particularly convenient when you need to chain promises that are interdependent.

例如，如果你想要有一個標記可以從資料庫擷取部落格文章接著作者資料時:
For instance, if you need to get a token in order to be able to fetch a blog post on a database and then the author informations:

```js
async function fetchPostById(postId) {
  try {
    const token = await fetch('token_url');
    const post = await fetch(`/posts/${postId}?token=${token}`);
    const author = await fetch(`/users/${post.authorId}`);

    post.author = author;
    return post;
  } catch(e) {
    throw new Error(e);
  }
}

fetchPostById('gzIrzeo64')
  .then(post => console.log(post))
  .catch(err => console.log(err));
```

> **筆記 :** 如你所建，*try / catch* 一定要處理錯誤訊息。但如果你使用 *express routes*，可以在中間放入其他東西，進而避免處理錯誤訊息，就能夠擁有優雅又好讀的程式碼，學習更多從 [Alex Bazhenov 的這些文章](https://medium.com/@Abazhenov/using-async-await-in-express-with-node-8-b8af872c0016)
> **Note :** As you can see, *try / catch* are necessary to handle errors. But if you are making *express routes*, you can use a middleware to avoid error handling and have a very pleasant code to read. See [this article from Alex Bazhenov](https://medium.com/@Abazhenov/using-async-await-in-express-with-node-8-b8af872c0016) to learn more.

#### 外部資源

- [Async/Await - JavaScript.Info](https://javascript.info/async-await)
- [ES7 Async/Await](http://rossboucher.com/await/#/)
- [6 Reasons Why JavaScript’s Async/Await Blows Promises Away](https://hackernoon.com/6-reasons-why-javascripts-async-await-blows-promises-away-tutorial-c7ec10518dd9)
- [JavaScript awaits](https://dev.to/kayis/javascript-awaits)
- [Using Async Await in Express with Node 8](https://medium.com/@Abazhenov/using-async-await-in-express-with-node-8-b8af872c0016)
- [Async Function](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Statements/async_function)
- [Await](https://developer.mozilla.org/en-US/docs/Web/JavaScript/Reference/Operators/await)
- [Using async / await in express with node 8](https://medium.com/@Abazhenov/using-async-await-in-express-with-node-8-b8af872c0016)

### Truthy / Falsy

在 JavaSctipt 中 truthy 或 falsy 值被製成布靈值，當他們被使用在布靈值內容的判斷上時。舉個例子當你使用 ```if``` 來進行判斷的時候:
In JavaScript, a truthy or falsy value is a value that is being casted into a boolean when evaluated in a boolean context. An example of boolean context would be the evaluation of an ```if``` condition:

每個值都會被改成 ```true``` 除非它們等於:
Every value will be casted to ```true``` unless they are equal to:

- false
- 0
- "" (empty string)
- null
- undefined
- NaN

這是 *boolean context* 的例子:
Here are examples of *boolean context*:

- ```if``` 條件評估
- ```if``` condition evaluation

```js
if (myVar) {}
```

```myVar``` 可以是任一個 [first-class citizen](https://en.wikipedia.org/wiki/First-class_citizen) (變數, 函數, 布靈值) 但因為它在一個 boolean context 環境中所以會被轉成布靈值。
```myVar``` can be any [first-class citizen](https://en.wikipedia.org/wiki/First-class_citizen) (variable, function, boolean) but it will be casted into a boolean because it's evaluated in a boolean context.

- ```!``` 操作子是後運算子代表 **NOT**
- After logical **NOT** ```!``` operator

當結果是 true 的時候，這個運算子若單獨使用，會將它轉換並回傳 false，反之，就會回傳 true。
This operator returns false if its single operand can be converted to true; otherwise, returns true.

```js
!0
// true -- 0 是 falsy 的所以會回傳 true 
// true -- 0 is falsy so it returns true
!!0 
// false -- 0 是 falsy 的所以 !0 會回傳 true 接著 !(!0) 就會再次轉換並回傳 false
// false -- 0 is falsy so !0 returns true so !(!0) returns false
!!"" 
// false -- 空字串是 falsy 的所以不是不是 false ( NOT (NOT false) )就會等於 false
// false -- empty string is falsy so NOT (NOT false) equals false
```

- 使用 *布靈* 物件建構子
- With the *Boolean* object constructor

```js
new Boolean(0) // false
new Boolean(1) // true
```

- 三元判斷
- In a ternary evaluation

```js
myVar ? "truthy" : "falsy"
```

myVar 在布靈文中判斷.
myVar is evaluated in a boolean context.


## 詞彙表

### <a name="scope_def"></a> 作用域

數值或表示式的內文是 "可讀取" 或可以參照的。如果一個變數或其他表示是不在正確的作用域內，它們就沒有辦法使用。
The context in which values and expressions are "visible," or can be referenced. If a variable or other expression is not "in the current scope," then it is unavailable for use.

資源: [MDN](https://developer.mozilla.org/en-US/docs/Glossary/Scope)

### <a name="mutation_def"></a> 變數的修改

當一個變數建立(初始化)後再去改變它的值，就稱作 mutate
A variable is said to have been mutated when its initial value has changed afterward.

```js
var myArray = [];
myArray.push("firstEl") 
// myArray 被修改
// myArray is being mutated
```

如果一個變數不能夠進行 mutate，我們就說它 *immutable*
A variable is said to be *immutable* if it can't be mutated.

[Check MDN Mutable article](https://developer.mozilla.org/en-US/docs/Glossary/Mutable) for more details.
