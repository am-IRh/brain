# Rendering Logic
The goal of CSS is to allow you to control the appearance and layout of your app's content.

## Inheritance
- CSS inheritance simplifies the process of styling by allowing parent elements to pass on certain properties to child element, reducing the need for repetitive coding
- Not all CSS pro
- perties are inherited by default. For instance, border and background-image properties are not inherited to avoid messy and unwanted results. However, inheritance can be forced on non-inheritable properties using the ‘inherit’ keyword.
- Only Certain Properties are Inherited
	- As an example, if the `border` property was inheritable, setting a border on a single element would cause the same border to appear on all its child elements. Similarly, if children inherited the `background-image` property from their parents, the result would be messy.
## Logical properties
یک مجموعه از پراپرتی ها هستند که به جای وابسته بودن به جهت فیزیکی (بالا، پایین، ..) به جهت نوشتار Writing Mode وابسته هستند
اگه زبان سایت از انگلیسی به RTL تغییر کنه خودش تشخیص میده که inline start سمت چپ هست یا راست
یعنی به جای 

```css
margin-left: 16px;
```
میگیم: 
```css
margin-inline-start: 16px;
```

[[JOSH COURSE]]
[MDN REF](https://developer.mozilla.org/en-US/docs/Web/CSS/Guides/Logical_properties_and_values)

## Box Model
در CSS هر المنت به شکل یک جعبه (BOX) در نظر گرفته می‌شود

وقتی بنویسی

```css
width: 200px;
height: 100px;
```

در حالت پیش‌فرض (`content-box`) این اندازه فقط برای Content هست
### Box Sizing 
دو مقدار اصلی داره
- Content-box (default)
- border-box
	- این حالت راحت تر هست CSS محاسبه میکنه 
```css
.box {  
	width:300px;  
	padding:20px;  
	border:5px solid;  
	box-sizing:border-box;  
}
```
کل عرض 300 با padding و border 
300 - pl20 - pr-20 - bl5 - br5 = content: 250px  

**درصدها (`%`) از Content Box والد محاسبه می‌شوند، نه از کل Border Box.**
**همیشه Content Box والد مبنای محاسبه درصد است.**

در padding های درصدی نسبت به (width) محاسبه می شوند
## outline
کمی مشابه به border هست با این تفاوت که جزو box model نیست و تفاوت اندازش روی box تاثیر نمیزاره مانند border

بیشتر استفاده ان برای focus است.
`outline-offset:10px;` 
میتونی outline رو از عنصر دور کنی.

## Flow layout
وقتی صحبت از **layout** در CSS می‌شود، CSS بیشتر شبیه مجموعه‌ای از **زبان‌های کوچک** است تا یک زبان یکپارچه و یک‌دست.

هر عنصر HTML، چیدمانش توسط یک **الگوریتم layout** محاسبه می‌شود. به این‌ها **layout mode** می‌گویند، و در کل **7 حالت متفاوت** وجود دارد.

در این دوره چندتا از این حالت‌ها را بررسی می‌کنیم، از جمله:

- [[Positioned layout]]
- **Flexible Box layout** یا همان [[Flexbox]]
- **Grid layout** یا همان **CSS [[Grid Layout]]**

فعلاً اما تمرکز ما روی **Flow layout** است
حالت پیش‌فرض در CSS است.
در Flow layout هر عنصر یکی از این مقادیر DISPLAY را دارد
- inline
- block
- inline block
### Inline elements don't want to make a fuss
عناصر inline دوست ندارند دردسر درست کنند.
میتونی آن ها رو در جهت inline با margin-left و margin-right جا‌به‌جا کنی اما نمیتونی width یا height آن ها رو تغییر بدی. و درجهت block عنصر inline همون‌جایی که هست باقی می‌مونه. 



- عناصر inline معمولاً `width` و `height` نمی‌گیرند.
- `margin-top` و `margin-bottom` هم مثل block عمل نمی‌کنند.
- `padding-top` و `padding-bottom` می‌گیرند، ولی ممکن است رفتار عجیب داشته باشند.
- بعضی عناصر inline مثل `img` ممکن است پایین خودشان یک **فضای اضافه‌ی کوچک** نشان بدهند.
- این فضا از `padding` یا `margin` نیست؛ به خاطر `line-height` و رفتار typography در inline layout است.
- برای حذف این فاصله:
    - `display: block;` برای `img`
    - یا `line-height: 0;` برای parent
#### inline block
اگر بخواهی یک inline element مثل block قابل‌کنترل شود،
می‌توانی از `display: inline-block` یا `display: block` استفاده کنی.
- `inline-block` این مزیت را دارد که:
    - مثل inline داخل خط می‌نشیند
    - ولی `width`، `height`، padding و margin عمودی را بهتر و کامل‌تر می‌پذیرد
### width Algorithms
در CSS درصد و keyword: auto تفاوت های با هم دارند
وقتی عرض المنت پدر 400px باشه و ما المنت فرزند رو `width: 100%` قرار میدیم المنت کامل عرض رو پوشش میده ولی اگه `margin` داشته باشیم المنت از فریم صفحه خارج میشه

ولی با auto این مشکل رو نداریم چون به اندازه که میتونه عرض رو قرار میده اگه المنت والد رو 400px در نظر بگیرم و `margin: 10 * 2` از هر طرف `400 - 20` میشه و عرض ما میشه 380
#### width keyword value
- min-content
	- وقتی این مقدار رو ست می‌کنیم میخوایم بر اساس محتوای فرزند تا جایی که میتونه کوچیک بشه
- max-content
	- مثل ٪ هست با این تفاوت که `line break` نداره و محتوا توی یه row قرار میگیره

### height Algorithms
در بعضی شرایط مانند width عمل می‌کنه ولی در بعضی کیس ها متفاوت هست. 
رفتار پیش‌فرض width برای block-level-element که تمام عرض صفحه رو پر کنند. درحالی که رفتار `height` تا جایی که ممکنه و جا برای تمام element content ها موجود هست کوچیک شود رفتارش نزدیک به `min-content` هست تا `width: auto`

ما اغلب برای height انتظار داریم بیشتر داینامیک باشه ممکنه دوست داشته باشیم مقدار height رو `750px` ست کنیم. ولی معمولا این کار رو انجام نمی‌دیم
میخواهیم طراحی ما با ۲۰۰ کلمه یا ۲۰هزار کلمه هم کار کنه و حتی برای پیچ های با محتوای ثابت انتظار داریم که کانتینر ما برای موبایل اسکرین ها بزرگتر بشه و برای دسکتاپ کوچکتر
معمولا از مقدار ثابت دوری می‌کنیم

## Margin Collapse
وقتی دو تا **margin عمودی (vertical)** به هم می‌رسند، مرورگر به جای اینکه مقدارشان را با هم جمع کند، آن‌ها را در هم ادغام (collapse) می‌کند و فقط یکی از آن‌ها را اعمال می‌کند. فقط برای عمودی اتفاق می‌افتد. و در افقی margin ها جمع می‌شوند

- Margins only collapse in Flow layout
- Nesting doesn't prevent collapsing

```css

<style>

	  p {
	
	    margin-top: 48px;
	
	    margin-bottom: 48px;
	
	  }

</style>

<div>

  <p>Paragraph One</p>

</div>

<p>Paragraph Two</p>
```
the margins will still collapse!
چطور ممکنه؟ ما تصور اشتباهی در مورد نحوه عملکرد margin داریم
هدف از `margin` افزایش فاصله بین siblings هست برای `gap` بین فرزند و والدش نیست این چیزی هست که `padding` برای آن است

همیشه تلاش می‌کند فاصله‌ی بین عناصر هم‌سطح را افزایش دهد، حتی اگر مجبور شود مقدار margin را به عنصر والد منتقل کند!
در این مثال، نتیجه دقیقاً طوری است که انگار `margin` را روی `<div>` گذاشته‌ایم، نه روی `<p>`.
اگر دیواره‌ای (مثل `padding` یا `border`) بین وجود داشته باشد، `margin` نمیتواند از جعبه عبور کند و به بیرون برود. و دیگه collapse نمیشه جون مانعی سر راه وجود داره

با height هم میتونیم جلوی collapse رو بگیریم اگه ارتفا div بیشتر از `margin` باشه یک gap به وجود میاد و جلوی collapse رو می‌گیره

توی همون direction ممکنه collapse به وجود بیاد وقتی ارتفا به پایین داده میشه collapse المنت پایین ازبین میره ولی وقتی هیچ gap برای المنت بالا نیست برای المنت بالا collapse به وجود میاد

‍
### Negative Margin & Margin Collapse

## دو Margin منفی

اگر هر دو Margin منفی باشند، **جمع نمی‌شوند**.

CSS فقط **منفی‌ترین مقدار (بیشترین قدر مطلق)** را انتخاب می‌کند.

```css
margin-bottom: -25px;
margin-top: -75px;
```

نتیجه:

```text
-75px
```

---

## یک Margin مثبت و یک Margin منفی

اگر یکی مثبت و یکی منفی باشد، **با هم جمع می‌شوند**.

```css
margin-bottom: 40px;
margin-top: -15px;
```

نتیجه:

```text
40 + (-15) = 25px
```

یا:

```css
margin-bottom: 20px;
margin-top: -50px;
```

نتیجه:

```text
20 + (-50) = -30px
```

یعنی عنصر دوم ۳۰ پیکسل روی عنصر اول قرار می‌گیرد (Overlap).

---

## قانون طلایی

- ✅ هر دو مثبت → بزرگ‌ترین مقدار اعمال می‌شود.
- ✅ هر دو منفی → منفی‌ترین مقدار (بیشترین قدر مطلق) اعمال می‌شود.
- ✅ یکی مثبت، یکی منفی → مقدارها با هم جمع می‌شوند.