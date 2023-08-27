<h1 dir="rtl">
Event bubbling
</h1>

<div align="center">
  
![Event bubbling](https://raw.githubusercontent.com/hosseinimh/javascript-tutorial/main/assets/event_bubbling.jpg)
</div>

<div dir="rtl">
هرگاه یک عنصر HTML داخل عنصر دیگری باشد و هر دوی این عناصر event مشترکی را هندل کنند، آن گاه ترتیب انتشار (اجرا) event handler در بین این عناصر به یکی از دو روش زیر صورت می گیرد:

<br />	
<br />	
<ul dir="rtl">
<li>
Event bubbling: در این حالت event ابتدا توسط داخلی ترین عنصر هندل می شود و سپس به عناصر بیرونی انتشار می یابد.
		</li>
<br />	
<div align="center">

![Event bubbling](https://raw.githubusercontent.com/hosseinimh/javascript-tutorial/main/assets/event_bubbling.png)

</div>
	
<li>
Event capturing: در این حالت event ابتدا توسط بیرونی ترین عنصر هندل می شود و سپس به عناصر داخلی انتشار می یابد.
		</li>
	</ul>
</div>

<h2 dir="rtl">
ترتیب انتشار Event؛ (Event Propagation) شامل سه فاز است:
	</h2>
	
<div dir="rtl">
1- <b>Capturing Phase</b>: در طول این فاز، event از بالاترین عنصر صفحه یعنی شی window، سپس document، سپس html و در نهایت event.target (عنصری که event را تریگر کرده) انتشار می یابد.
	<br/>
	2- <b>Target Phase</b>: دومین فاز وقتی است که به event.target می رسد.
		<br/>
	3- <b>Bubbling Phase</b>: این فاز از event.target شروع شده و به عناصر والد انتشار می یابد.
</div>

<div align="center">
  
![Event Propagation](https://raw.githubusercontent.com/hosseinimh/javascript-tutorial/main/assets/event_propagation.png)
</div>

<h2 dir="rtl">
Event Deligation چیست؟
</h2>

<div dir="rtl">
الگویی برای بهینه هندل کردن event هاست. در این الگو، به‌جای افزودن event listener برای هر عنصر HTML، یک event listener به عنصر والد اضافه کرده و از پارامتر event در تابع callback برای شناسایی عنصر target و نحوه هندل کردن آن استفاده می‌کنیم.
	<br/>
		<br/>
	فرض کنید لیستی داینامیک داریم که می‌خواهیم با کلیک بر روی هر آیتم یک event فراخوانی شود.
	<br/>
	یکی از راه‌ها اختصاص event listener به هر کدام از آیتم‌هاست.
</div>

<div align="center">
  
![Without event deligation](https://raw.githubusercontent.com/hosseinimh/javascript-tutorial/main/assets/without_event_deligation.png)
</div>

```js
const customUI = document.createElement("ul");

for (var i = 1; i <= 10; i++) {
  const newElement = document.createElement("li");
  newElement.textContent = "This is line " + i;
  newElement.addEventListener("click", () => {
    console.log("Responding");
  });
  customUI.appendChild(newElement);
}
```

<div dir="rtl">
راه‌حل دیگر تعیین نماینده یا deligate برای فراخوانی event است.
</div>

<div align="center">
  
![With event deligation](https://raw.githubusercontent.com/hosseinimh/javascript-tutorial/main/assets/with_event_deligation.png)
</div>

```js
const customUI = document.createElement("ul");

function responding(evt) {
  if (evt.target.nodeName === "li") console.log("Responding");
}

for (var i = 1; i <= 10; i++) {
  const newElement = document.createElement("li");
  newElement.textContent = "This is line " + i;
  customUI.appendChild(newElement);
}

customUI.addEventListener("click", responding);
```

<h3 dir="rtl">
مزایا
</h3>

<ul dir="rtl">
	<li>تعداد کمتری event handler ایجاد و در حافظه نگهداری می‌شود.</li>
		<li>باعث تمیزتر شدن کد و کاهش کدهای تکراری می‌شود.</li>
</ul>

<h3 dir="rtl">
معایب
</h3>

<ul dir="rtl">
	<li>برخی از event ها مثل focus یا blur؛ bubble نمی‌شوند.</li>
</ul>

<h2 dir="rtl">
تفاوت stopPropagation و preventDefault
</h2>

<div dir="rtl">
stopPropagation از انتشار بیشتر event فعلی در فازهای capturing و bubbling جلوگیری می کند.
	<br/>
	preventDefault از عمل پیش فرض مرورگر در زمان وقوع event جلوگیری می کند. 
</div>
