<h1 dir="rtl">
Execution Context
</h1>

<div align="center">
  
![Execution Context](https://raw.githubusercontent.com/hosseinimh/javascript-tutorial/main/assets/execution_context.png)
</div>

<h2 dir="rtl">
Execution Context چیست؟
</h2>

<div dir="rtl">
کدهای جاوااسکریپت برای اجرا نیاز دارند که به کد ماشین تبدیل شوند. این کار با ایجاد محیطی ویژه به نام execution context توسط موتور جاوااسکریپت مرورگر یا در سطح شل توسط Node انجام می‌شود که وظیفه‌اش تبدیل و اجرای کد جاوااسکریپت است. این محیط از دو بخش تشکیل شده است:
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
<br/>
<div dir="rtl">
در function execution context؛ global object نداریم بلکه متغیری به نام arguments ایجاد و مقداردهی می‌شود که شامل آرایه‌ای از 
ورودی‌های تابع است.
</div>

```js
function func1(a, b, c) {
  console.log(arguments[0]); // 1

  console.log(arguments[1]); // 2

  console.log(arguments[2]); // 3
}

func1(1, 2, 3);
```

<h3 dir="rtl">
 Execution Phase
</h3>
	
1. 	اجرای خط به خط کد
2. ایجاد execution context جدید برای هر فراخوانی تابع

<br />

<h2 dir="rtl">
 Global Execution Context
</h2>
<div align="center">
  
![Global Execution Context](https://raw.githubusercontent.com/hosseinimh/javascript-tutorial/main/assets/global_execution_context.gif)
</div>

<h2 dir="rtl">
 Function Execution Context
</h2>
<div align="center">
  
![Function Execution Context](https://raw.githubusercontent.com/hosseinimh/javascript-tutorial/main/assets/function_execution_context.gif)
</div>

<h2 dir="rtl">
Call Stack
	</h2>

<div align="center">
  
![The Call Stack](https://raw.githubusercontent.com/hosseinimh/javascript-tutorial/main/assets/call_stack.jpg)
</div>

<div dir="rtl">
Call Stack ترتیب اجرای execution context ها را مدیریت می‌کند. فرآیند ذخیره‌سازی داده‌ها در استک، LIFO است یعنی آخرین ورودی اولین خروجی. با اجرای کد جاوااسکریپت، ابتدا global execution context در Call Stack؛ push می‌شود. هر بار که تابعی فراخوانی می‌شود exection context آن در استک push شده و بعد از برگشت از تابع pop می‌شود. به این ترتیب جاوااسکریپت دقیقا می‌داند که چه Scope و متغیرهایی هم‌اکنون در حال استفاده است. فرآیند push و pop با اجرای خط به خط کد ادامه پیدا می‌کند تا در انتها با رسیدن به آخرین خط کد، global execution context نیز از Call Stack خارج شده و استک خالی می‌شود.
</div>

<div align="center">
  
![Call Stack](https://raw.githubusercontent.com/hosseinimh/javascript-tutorial/main/assets/call_stack.png)
</div>
