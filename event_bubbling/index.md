<h1 dir="rtl">
Event bubbling
</h1>

<div align="center">
  
![Event bubbling](https://raw.githubusercontent.com/hosseinimh/javascript-tutorial/main/assets/event_bubbling.jpg)
</div>

<h2 dir="rtl">
Event Deligation چیست؟
</h2>

<div dir="rtl">
الگویی برای بهینه هندل کردن event هاست. در این الگو، به‌جای افزودن event listener برای هر عنصر HTML، یک event listener به عنصر والد اضافه کرده و از پارامتر event در تابع callback برای شناسایی عنصر target و نحوه هندل کردن آن استفاده می‌کنیم.
	<br/>
		<br/>
	فرض کنید لیستی داینامیک داریم که میخواهیم با کلیک بر روی هر آیتم یک event فراخوانی شود.
	<br/>
	یکی از راه ها اختصاص event listener به هر کدام از آیتم هاست.
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
راه حل دیگر تعیین نماینده یا deligate برای فراخوانی event است.
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