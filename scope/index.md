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
سطح دسترسپذیری متغیرها را تعیین می  کند. در واقع scope؛ execution context فعلی است که نشان می دهد کدام متغیر ها، توابع و اشیا در حال حاضر قابل دسترسند. Scope ها سلسله مراتبی اند به طوری که scope فرزند به scope والد دسترسی دارند اما عکس آن نه.
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
	اگر برنامه ماژولار باشد، تعریف متغیر global کمی فرق می کند. در این حالت می توان با قرار دادن کد زیر در فایل HTML متغیر global تعریف کرد:
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
