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
کدهای جاوااسکریپت در محیطی به نام execution context اجرا می شوند. این محیط از دو بخش تشکیل شده است:
</div>

<h3 dir="rtl">
	Memory (Variable Environment)
	</h3>
<div dir="rtl">
جایی است که متغیرها و توابع به صورت key/value در آن ذخیره می شوند.
</div>

<h3 dir="rtl">
	Code (Thread of Execution)
	</h3>
<div dir="rtl">
جایی است که کدها در آن خط به خط اجرا می شوند.
</div>

<h4 dir="rtl">
	جاوااسکریپت یک زبان synchronous signle-threaded است.
	</h4>
	
<div dir="rtl">
منظور از single-threaded آن است که جاوااسکریپت هر بار تنها می تواند یک خط دستور را اجرا کند.
</div>
<div dir="rtl">
منظور از synchronous single-threaded آن است که جاوااسکریپت خطوط دستور را یک به یک و به صورت متوالی و پشت سر هم اجرا کند.
</div>
