<h1 dir="rtl">
Currying
</h1>

<div align="center">
  
![Currying](https://raw.githubusercontent.com/hosseinimh/javascript-tutorial/main/currying/images/currying.png)
</div>

<h2 dir="rtl">
Currying چیست؟
</h2>
<div dir="rtl">
فرآیندی در برنامه‌نویسی فانکشنال است که در آن یک تابع با چندین آرگومان مثل f(a,b,c) به دنباله‌ای از توابع تو در تو، f(a)(b)(c)، تبدیل می‌شود.
</div>
<div dir="rtl">
Currying تابع را فراخوانی نمی‌کند بلکه آن را تبدیل به زنجیره‌ای از closure ها می‌کند که یکی پس از دیگری فراخوانی می‌شوند. هر closure تنها یک آرگومان از آرگومان‌های ورودی را می‌پذیرد.
</div>
<h2 dir="rtl">
Currying در عمل
</h2>
<div dir="rtl">
دو راه برای curry کردن یک تابع وجود دارد:

- استفاده از تابع bind
- استفاده از closure
</div>
<h3 dir="rtl">
استفاده از تابع bind
</h3>

```js
const sum = function (a, b) {
  console.log(a + b);
};

// تابع bind یک کپی از تابع sum می‌سازد.
const sumOfTwo = sum.bind(null, 2);
sumOfTwo(6); // 8

const sumOfFive = sum.bind(null, 4);
sumOfFive(8); // 12
```

<h3 dir="rtl">
استفاده از closure
</h3>

```js
const sum = function (a) {
  return function (b) {
    console.log(a + b);
  };
};

sum(2)(6); // 8

const sumOfFive = sum(5);
sumOfFive(7); // 12
```

<h2 dir="rtl">
مزایای استفاده از currying
</h2>

<h3 dir="rtl">
1- code reusability
</h3>

توابع curried را می‌توان در قسمت‌های مختلف برنامه به عنوان reusable code استفاده کرد. تابع زیر را در نظر بگیرید:

```js
function add(x, y) {
  return x + y;
}
```

با کمک curry می‌توان تابعی ایجاد کرد که همواره ورودی را با عدد 5 جمع کند و به عنوان خروجی برگرداند:

```js
const add5 = add.bind(null, 5);

add5(10); // 15
add5(20); // 25
```

<h3 dir="rtl">
2- code readability
</h3>

شکستن منطق برنامه به تکه‌های کوچک‌تر باعث خوانایی بیشتر کد می‌شود.

به عنوان مثال، تابع زیر میزان بنزین مورد نیاز برای رسیدن به مقصدی با فاصله معین را محاسبه می‌کند:

```js
function neededGas(gasPerHundred, distance) {
  return gasPerHundred * (distance % 100);
}
```

فرض کنید میزان بنزین مصرفی خودروی پژو در هر 100 کیلومتر 8 لیتر و پراید 6 لیتر باشد:

```js
const peugeotNeededGas = neededGas.bind(null, 8);
const prideNeededGas = neededGas.bind(null, 6);
```

حالا می‌توان برای هر خودرو تابعی نوشت که **صرفا** میزان بنزین مورد نیاز آن **خودرو** را از مشهد به تهران محاسبه کند:

```js
const peugeotMashTehNeededGas = peugeotNeededGas(800); // 64
const prideMashTehNeededGas = prideNeededGas(800); //  48
```

پیاده‌سازی کد بالا با closure به این شکل است:

```js
function neededGas(gasPerHundred) {
  return function (distance) {
    return gasPerHundred * (distance % 100);
  };
}

const peugeotNeededGas = neededGas(8);
const prideNeededGas = neededGas(6);

const peugeotMashTehNeededGas = peugeotNeededGas(800); // 64
// یا
// const peugeotMashTehNeededGas = neededGas(8)(800); // 64

const prideMashTehNeededGas = prideNeededGas(800); // 48
// یا
// const prideMashTehNeededGas = neededGas(6)(800); // 48
```

<h3 dir="rtl">
3- تفکیک تسک‌ها و خطایابی بهتر
</h3>

با تبدیل کد به قسمت‌های کوچک‌تر، امکان تست هر بخش به صورت مجزا وجود دارد. همچنین از آن جا که هر تکه کد کار به خصوصی را انجام می‌دهد، single responsibility در کد، بهتر رعایت خواهد شد.

<h2 dir="rtl">
Partial Application
</h2>

<div dir="rtl">
Partial Application تکنیکی است که تابعی با چندین آرگومان را به تابعی با آرگومان‌های کمتر تبدیل می‌کند.
</div>

```js
const getApiURL = (apiHostname, resourceName, resourceId) => {
  return `https://${apiHostname}/api/${resourceName}/${resourceId}`;
};

const getUserURL = (userId) => {
  return getApiURL("localhost:3000", "users", userId);
};

const getOrderURL = (orderId) => {
  return getApiURL("localhost:3000", "orders", orderId);
};

const getProductURL = (productId) => {
  return getApiURL("localhost:3000", "products", productId);
};
```

<h3 dir="rtl">
	Partial Application vs Currying
</h3>

<div dir="rtl">
هدف از Partial Application، تبدیل تابعی با پیچیدگی و آرگومان‌های زیاد به تابعی با پیچیدگی، آرگومان‌ها و عملیات داخلی کمتر است. اما در Currying تابع اولیه تبدیل به زنجیره‌ای از closure ها می‌شود که هر کدام تنها یک آرگومان دارند.
</div>

<h2 dir="rtl">
تمرین
</h2>

<h3 dir="rtl">
1. پیاده سازی sum(2)(6)(1)
</h3>

```js
// function sum(a, b, c) {
//   return a + b + c;
// }
// console.log(sum(2,6,1));

function sum(a) {
  return function (b) {
    return function (c) {
      return a + b + c;
    };
  };
}
cosole.log(sum(2)(6)(1));
```

<h3 dir="rtl">
2. پیاده سازی evaluate('sum')(5)(2)
</h3>

```js
function evaluate(operation) {
  return (a) => {
    return (b) => {
      if (operation === "sum") return a + b;
      else if (operation === "multiply") return a * b;
      else if (operation === "divide") return a / b;
      else if (operation === "subtract") return a - b;
      else return "No / Invalid Operation Selected";
    };
  };
}

const mul = evaluate("multiply");
console.log(mul(5, 2)); // 10
console.log(evaluate("sum")(5)(2)); // 7
```

<h3 dir="rtl">
3. Infinite currying
</h3>

```js
function sum(a) {
  return function (b) {
    if (b) {
      return sum(a + b);
    }
    return a;
  };
}
// یا
// const sum = a => b => b ? sum(a + b) : a;

console.log(sum(7)(4)(8)(2)()); // 21
```

<h3 dir="rtl">
4. DOM Manipulation
</h3>

```js
function updateElementText(id) {
  return function (content) {
    document.getElementById(id).textContent = content;
  };
}

const updateHeader = updateElementText("heading");
updateHeader("Hello");
```

<div dir="rtl">
با این روش، تابعی ساختیم که تنها وظیفه‌اش بروزرسانی متن عنصر heading است و می‌توان آن را بارها و بارها فراخوانی کرد بدون آن که نیازی باشد که هر بار تابع getElementById فراخوانی شود.
</div>
