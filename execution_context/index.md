<h1 dir="rtl">
Execution Context
</h1>

<div align="center">
  
![Execution Context](https://raw.githubusercontent.com/hosseinimh/javascript-tutorial/main/images/execution_context.png)
</div>

<h2 dir="rtl">
Execution Context چیست؟
</h2>

<div dir="rtl">
کدهای جاوااسکریپت در محیطی به نام execution context اجرا می‌شوند. این محیط از دو بخش تشکیل شده است:
</div>

<h3 dir="rtl">
	Memory (Variable Environment)
	</h3>
<div dir="rtl">
جایی است که متغیرها و توابع به صورت key/value در آن ذخیره می‌شوند.
</div>

<h3 dir="rtl">
	Code (Thread of Execution)
	</h3>
<div dir="rtl">
جایی است که کدها در آن خط به خط اجرا می‌شوند.
</div>

<h2 dir="rtl">
	جاوااسکریپت یک زبان synchronous signle-threaded است.
	</h2>
	
<div dir="rtl">
منظور از single-threaded آن است که جاوااسکریپت هر بار تنها می‌تواند یک خط دستور را اجرا کند.
</div>
<div dir="rtl">
منظور از synchronous آن است که جاوااسکریپت خطوط دستور را یک به یک و به صورت <b>متوالی و پشت سر هم</b> اجرا می‌کند.
</div>

<h2 dir="rtl">
انواع execution context
	</h2>
	<ul dir="rtl">
	<li>Global execution context: با اولین اجرای برنامه ایجاد می‌شود.</li>
		<li>Function execution context: با هر بار فراخوانی تابع ایجاد می‌شود.</li>
</ul>

<h2 dir="rtl">
ایجاد exeution context دو فاز دارد:
	</h2>
	<ul dir="rtl">
	<li>Memory Creation Phase (Creation Phase)</li>
		<li>Execution Phase</li>
</ul>

<h3 dir="rtl">
 Memory Creation Phase
</h3>
	
1. 	ایجاد global object ؛ (browser: window, Node.js: global)
2. ایجاد `this` object و bind آن به global object
3. راه‌اندازی memory heap برای ذخیره متغیرها و رفرنس‌های توابع
4. ذخیره توابع و متغیرها در execution context و مقداردهی اولیه 'undefined' در متغیرها

<h3 dir="rtl">
 Execution Phase
</h3>
	
1. 	اجرای خط به خط کد
2. ایجاد execution context جدید برای هر فراخوانی تابع
