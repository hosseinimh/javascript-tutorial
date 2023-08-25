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
سطح در دسترس متغیرها را تعیین می‌کند. در واقع scope؛ execution context فعلی است که نشان می‌دهد در حال حاضر کدام متغیرها، توابع و اشیا قابل دسترسند. Scope ها سلسله‌مراتبی‌اند به طوری که scope فرزند به scope همه پدران خود دسترسی دارد اما عکس آن نه.
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
به یک مجموعه خطوط کد داخل آکولادهای باز و بسته نوشته می‌شود block گفته می‌شود. تنها متغیرهایی که توسط let و const تعریف می‌شوند دارای block scope هستند.
</div>

```js
{
  let x = 5;
}
console.log(x);
// Uncaught ReferenceError: x is not defined
```
