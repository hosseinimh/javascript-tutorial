<h1 dir="rtl">
Scope
</h1>

<div align="center">
  
![Scope](https://raw.githubusercontent.com/hosseinimh/javascript-tutorial/main/assets/scope.jpg)
</div>

<h2 dir="rtl">
Scope چیست؟
</h2>

<div dir="rtl">
سطح در دسترس متغیرها را تعیین می‌کند. در واقع scope؛ execution context فعلی است که نشان می‌دهد در حال حاضر کدام متغیرها، توابع و اشیا قابل دسترسند.
</div>

<h2 dir="rtl">
انواع Scope
	</h2>

<ul dir="rtl">
	<li>Global Scope</li>
		<li>Module/Local Scope</li>
		<li>Function Scope</li>
		<li>Block Scope</li>
</ul>

<div align="center">
  
![Scope](https://raw.githubusercontent.com/hosseinimh/javascript-tutorial/main/assets/scope.png)
</div>

<h3 dir="rtl">
Global Scope
	</h3>
<div dir="rtl">
اگر متغیری داخل یک تابع، ماژول یا بلاک تعریف نشده باشد، global است.
	</br>
	اگر برنامه ماژولار باشد، تعریف متغیر global کمی فرق می‌کند. در این حالت می‌توان با قرار دادن کد زیر در فایل HTML متغیر global تعریف کرد:
</div>

```
<script>
  var GLOBAL_DATA = {value: 1};
</script>
```

<div dir="rtl">
	و یا مستقیما متغیری را به <i>window</i> global object اضافه کرد:
	</div>

```js
window.GLOBAL_DATA = { value: 1 };
```

<h3 dir="rtl">
Module Scope
	</h3>
	
<div dir="rtl">
در برنامه‌های ماژولار، هر متغیری خارج از تابع یا بلاک کد، module scope است و خارج از آن ماژول قابل دسترس نیست.
<br/>
اگر بخواهیم در ماژول دیگری از متغیر، تابع یا شی ماژول فعلی استفاده کنیم باید در ماژول فعلی آن را export کرده و در ماژول دیگر آن را import کنیم:
</div>

```js
// module1.js  در
export { var1, toDo };

// module2.js  در
import { var1, toDo };
```

<div dir="rtl">
به عبارت دیگر، ماژول را می‌توان تابعی تصور کرد که خودکار اجرا شده، داده‌های import را به عنوان ورودی می‌گیرد و خروجی را به شکل داده‌های export برمی‌گرداند.
</div>

<h3 dir="rtl">
Function Scope
	</h3>
<div dir="rtl">
متغیرهایی که داخل تابع تعریف می‌شوند در کل تابع در دسترس‌اند اما در خارج آن نه.
</div>

```js
function sum() {
  var result = 10;
}
console.log(result);
// Uncaught ReferenceError: result is not defined
```

<h3 dir="rtl">
Block Scope
	</h3>
<div dir="rtl">
به یک مجموعه خطوط کد داخل آکولادهای باز و بسته نوشته می‌شود block گفته می‌شود. تنها متغیرهایی که توسط let و const تعریف می‌شوند دارای block scope هستند. متغیرهای تعریف شده توسط var؛ function scope هستند.
</div>

```js
{
  let x = 5;
}
console.log(x);
// Uncaught ReferenceError: x is not defined

{
  var y = 5;
}
console.log(y); // 5
```

<h2 dir="rtl">
Scope chain
	</h2>

<div align="center">

![Scope chain](https://raw.githubusercontent.com/hosseinimh/javascript-tutorial/main/assets/scope_chain.jpg)

</div>

<div dir="rtl">
Scope ها سلسله‌مراتبی‌اند به طوری که scope فرزند به scope همه پدران خود دسترسی دارد اما عکس آن صادق نیست.
	<br/>
	Scope chain زنجیره‌ای از scope های والد فرزندی هستند که برای پیدا کردن یک متغیر یا تابع در آن جستجو می‌شوند.
	<br />
</div>

<div align="center">

![Scope chain](https://raw.githubusercontent.com/hosseinimh/javascript-tutorial/main/assets/scope_chain.png)

</div>

<div dir="rtl">
وقتی متغیری در کد استفاده می‌شود، موتور جاوااسکریپت سعی می‌کند مقدار آن را در scope فعلی پیدا کند. اگر نتوانست در scope بالاتر جستجو می‌کند و این کار را تا زمانی که به global scope برسد ادامه می‌دهد.
</div>

<h2 dir="rtl">
Lexical Environment
	</h2>
	
<div dir="rtl">
هنگامی که موتور جاوااسکریپت execution context جدیدی می‌سازد، در فاز execution آن، Lexical Environment را برای نگهداری متغیرهای درون آن Scope ایجاد می‌کند.
	<br />
	Lexical environment ساختار داده‌ای حاوی نگاشتی از شناسه / مقدار است که در آن شناسه نام متغیر یا تابع و مقدار برابر مقدار متغیر و یا ارجاعی به تابع است.
</div>

<h4 dir="rtl">
Lexical Environment شامل دو قسمت است:	</h4>

<ul dir="rtl">
	<li>Environment record: محلی برای نگهداری متغیرها و توابع به همراه مقادیر و ارجاعاتشان</li>
		<li>ارجاع به outer environment: ارجاع به Lexical Environment والد</li>
</ul>

```js
let language = "JavaScript";
function a() {
  const b = "Dart";
  console.log("Inside function a");
}
a();
console.log("Global execution context");
```

```js
globalLexicalEnvironment = {
  environmentRecord: {
      language    : 'JavaScript',
      a : < reference to function object >
  }
  outer: null
}
```

```js
functionLexicalEnvironment = {
  environmentRecord: {
      b    : 'Dart',
  }
  outer: <globalLexicalEnvironment>
}
```

<h2 dir="rtl">
Lexical Scope
	</h2>
	
<div dir="rtl">
محلی که متغیر یا تابع تعریف شده را Lexical scope می‌گویند. Lexical scope توانایی یک function scope به دسترسی به متغیرهای scope والد است.
</div>

```js
var a = 10;
var func = function () {
  var b = 20;
  console.log("a and b is accessible (outer):", a, b);
  var innerFunc = function () {
    var c = 30;
    console.log("a and b and c is accessible (inner):", a, b, c);
  };
  innerFunc();
  return;
};
func();
console.log("only a is accessible (global):", a);
```
