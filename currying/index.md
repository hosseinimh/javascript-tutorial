# Currying

## Currying چیست؟

فرآیندی در برنامه نویسی فانکشنال است که در آن یک تابع با چندین آرگومان، f(a,b,c)، به دنباله ای از توابع تودر تو، f(a)(b)(c)، تبدیل می شود.

<p style="dir:rtl;">
Currying تابع را فراخوانی نمی کند بلکه آن را تبدیل به زنجیره ای از Closure ها می کند که یکی پس از دیگری فراخوانی می شوند. هر Closure تنها یک آرگومان از آرگومان های ورودی می پذیرد.
</p>

## Currying در عمل

دو راه برای curry کردن یک تابع وجود دارد:

- استفاده از تابع bind
- استفاده از Closure

### استفاده از تابع bind

```js
const sum = function (a, b) {
  console.log(a + b);
};

// تابع bind یک کپی از تابع sum می سازد.
const sumOfTwo = sum.bind(this, 2);
sumOfTwo(6); // 8

const sumOfFive = sum.bind(this, 4);
sumOfFive(8); // 12
```

### استفاده از closure

```js
let sum = function (a) {
  return function (b) {
    console.log(a + b);
  };
};

sum(2)(6); // 8

const sumOfFive = sum(5);
sumOfFive(7); // 12
```

### مزایای استفاده از currying

#### 1- code reusability

توابع `curried` را می توان در بخش های مختلف برنامه به عنوان `reusable code` استفاده کرد.
به عنوان مثال، تابع مجموع زیر را در نظر بگیرید:

```js
function add(x, y) {
  return x + y;
}
```

با کمک `curry` می توان تابعی ایجاد کرد که همواره ورودی با عدد 5 جمع کرده و به عنوان خروجی برگرداند:

```js
const add5 = add.bind(null, 5);

add5(10); // 15
add5(20); // 25
```

#### 2- code readability

شکستن منطق برنامه به تکه های کوچک تر باعث خوانایی بیشتر کد می شود.
فرض کنید تابعی دارید که میزان بنزین مصرفی را برای رسیدن به مقصدی با فاصله معین محاسبه کند:

```js
function neededGas(gasPerHundred, distance) {
  return (distance % 100) * gasPerHundred;
}
```

فرض کنیم میزان بنزین مصرفی خودروی پژو در هر 100 کیلومتر 8 لیتر و پراید 6 لیتر باشد:

```js
const peugeotNeededGas = neededGas.bind(null, 8);
const prideNeededGas = neededGas.bind(null, 6);
```

حالا می توان میزان بنزین مورد نیاز از مشهد تا تهران را به ازای هر خودرو محاسبه کرد:

```js
const peugeotMashTehNeededGas = peugeotNeededGas(800); // 64
const prideMashTehNeededGas = prideNeededGas(800); //  48
```

#### 3- تفکیک تسک ها و خطایابی بهتر

با تبدیل کد به بخش های کوچک تر، امکان تست هر بخش به صورت مجزا وجود دارد. همچنین از آن جا که هر تکه کد کار خاصی را انجام می دهد، single responsibility در کد بهتر رعایت خواهد شد.
