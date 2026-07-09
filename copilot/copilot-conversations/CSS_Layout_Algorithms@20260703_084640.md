---
epoch: 1783055800154
modelKey: "gpt-5.4-mini|openai"
topic: "CSS Layout Algorithms"



tags:
  - copilot-conversation
---

**user**: When it comes to layout, CSS is more like a collection of mini-languages than a single cohesive language.

Every HTML element will have its layout calculated by a layout algorithm. These are known as “layout modes”, and there are 7 distinct ones.

We'll cover several layout modes in this course, including Positioned layout, “Flexible Box” layout (AKA Flexbox), and Grid layout (AKA CSS Grid). For now, though, let's focus on Flow layout.

Flow layout is the default layout mode. All the examples we've seen so far are rendered in Flow layout. A plain HTML document, with no CSS applied, uses Flow layout exclusively.

In Flow layout, every element will use a display value of either inline, block, or inline-block. This value governs how the Flow layout algorithm will place the element. The default value depends on the tag; div elements are block by default, while spans are inline.

Inline elements are generally meant to highlight a selection of text. You might use a <strong> tag to add weight to a specific word in a sentence, or use an <a> tag to add a link.

Most elements, however, are block elements. They can be used to create a block of text, or to arrange boxes into a layout. The <div> element, along with its semantic HTML5 alternatives (eg. section, nav, header, footer, article, etc), are block elements. So are paragraphs, headings, form tags, blockquotes, and so on.

It's no coincidence that block and inline align with the directions we were speaking about earlier. In flow layout, block elements stack in the block direction, and inline elements stack in the inline direction.

It's more than just direction, though. There are a set of rules that these display types follow. Let's look at them in turn:
اینو برام فارسی ترجمه میکنی راجع به لیوت ها توی css هست میخوام توی داک خودم بنویسم
[Context: Notes: 01 - Programming/Front-end/CSS/CSS Fundamental.md]
[Timestamp: 2026/07/03 08:46:40]

**ai**: حتماً — این هم ترجمه‌ی فارسیِ روان و مناسب برای نوشتن داخل داک/نوت خودت:

---

# Flow Layout

وقتی صحبت از **layout** در CSS می‌شود، CSS بیشتر شبیه مجموعه‌ای از **زبان‌های کوچک** است تا یک زبان یکپارچه و یک‌دست.

هر عنصر HTML، چیدمانش توسط یک **الگوریتم layout** محاسبه می‌شود. به این‌ها **layout mode** می‌گویند، و در کل **7 حالت متفاوت** وجود دارد.

در این دوره چندتا از این حالت‌ها را بررسی می‌کنیم، از جمله:
- **Positioned layout**
- **Flexible Box layout** یا همان **Flexbox**
- **Grid layout** یا همان **CSS Grid**

فعلاً اما تمرکز ما روی **Flow layout** است.

---

## Flow layout چیست؟

**Flow layout** حالت پیش‌فرض layout در CSS است. تمام مثال‌هایی که تا الان دیده‌ایم در همین حالت رندر می‌شوند. اگر یک سند HTML ساده بدون هیچ CSS داشته باشیم، فقط از **Flow layout** استفاده می‌کند.

در Flow layout، هر عنصر یکی از این مقادیر `display` را دارد:
- `inline`
- `block`
- `inline-block`

این مقدار مشخص می‌کند که الگوریتم Flow layout چطور آن عنصر را در صفحه قرار دهد. مقدار پیش‌فرض به تگ HTML بستگی دارد؛ مثلاً:
- `div` به طور پیش‌فرض `block` است
- `span` به طور پیش‌فرض `inline` است

---

## inline elements

عناصر **inline** معمولاً برای برجسته کردن بخشی از متن استفاده می‌شوند. مثلاً:
- از تگ `<strong>` برای پررنگ کردن یک کلمه در جمله استفاده می‌کنیم
- از تگ `<a>` برای ساختن لینک استفاده می‌کنیم

---

## block elements

بیشتر عناصر، **block** هستند. این عناصر می‌توانند برای ساختن یک بخش از متن یا برای چیدن باکس‌ها در یک layout استفاده شوند.

تگ `<div>` و همچنین جایگزین‌های معنایی HTML5 آن مثل:
- `section`
- `nav`
- `header`
- `footer`
- `article`

همگی **block element** هستند.

همین‌طور:
- `p`
- heading ها مثل `h1` تا `h6`
- تگ‌های فرم
- `blockquote`
- و موارد مشابه

هم block هستند.

---

## ارتباط block و inline با جهت‌ها

اتفاقی نیست که **block** و **inline** با جهت‌هایی که قبلاً درباره‌شان صحبت کردیم هماهنگ هستند.

در **flow layout**:
- عناصر **block** در جهت block روی هم قرار می‌گیرند
- عناصر **inline** در جهت inline کنار هم قرار می‌گیرند

اما موضوع فقط جهت نیست؛ بلکه این display type ها یک سری قوانین مشخص هم دارند که باید به‌ترتیب بررسی شوند.

---

اگر بخوای، من می‌تونم همین متن رو هم:
- **کوتاه‌تر و خلاصه‌تر** برای داکت بنویسم
- یا **به صورت یادداشت‌وار و مرتب‌تر** برای [[CSS Fundamental]] برات بازنویسی کنم.
[Timestamp: 2026/07/03 08:46:47]

**user**: Inline elements don't want to make a fuss

If you've ever tried to adjust the positioning or size of an inline element, you've likely been confounded by the fact that a bunch of CSS properties just don't work.

For example, this snippet will have no effect:

strong {
  height: 2em;
}

You can picture inline elements as go-with-the-flow-type folks. They don't want to inconvenience anyone by pushing any boundaries. They're like polite dinner-party guests who sit exactly where they're assigned.

You can shift things in the inline direction with margin-left and margin-right, but you can't change its width or height. And in terms of the block direction, an inline element is where it is, and that's the end of the story.

Inline elements can be given vertical padding, but the results can be surprising, and we need to exercise caution. We'll explore this more in the Typography module.
Exceptions

There are two exceptions to this rule. The first is replaced elements.

A replaced element is one that embeds a "foreign" object. This includes:

    <img />
    <video />
    <canvas />

These elements are all technically inline, but they're special: they can affect block layout. You can give them explicit dimensions, or add some margin-top.

How do we reconcile this? I have a trick. I like to pretend that it's a foreign object within an inline wrapper. When you pass it a width or height, you're applying those properties to the foreign object. The inline wrapper still goes with the flow.

The second exception is the <button> tag. They aren't quite replaced elements, but they function the same way. They can be given a width/height.
[Context: Notes: 01 - Programming/Front-end/CSS/CSS Fundamental.md]
[Timestamp: 2026/07/03 09:07:23]

**ai**: حتماً — این هم ترجمه‌ی فارسیِ روان و مناسب برای داک:

---

# Inline elements don't want to make a fuss

اگر تا حالا تلاش کرده باشی موقعیت یا اندازه‌ی یک **inline element** را تغییر بدهی، احتمالاً با این موضوع روبه‌رو شده‌ای که خیلی از propertyهای CSS روی آن‌ها کار نمی‌کنند.

مثلاً این کد هیچ اثری نخواهد داشت:

```css
strong {
  height: 2em;
}
```

می‌توانی inline elements را مثل آدم‌های خیلی آرام و بی‌دردسر تصور کنی؛ کسانی که نمی‌خواهند با رد کردن مرزها، مزاحم جریان طبیعی صفحه شوند. آن‌ها شبیه مهمان‌های مودب یک مهمانی شام هستند که دقیقاً همان‌جایی می‌نشینند که برایشان تعیین شده است.

---

## رفتار inline elements

- می‌توانی آن‌ها را در **جهت inline** با `margin-left` و `margin-right` جابه‌جا کنی
- اما نمی‌توانی `width` یا `height` آن‌ها را تغییر بدهی
- در **جهت block** هم عنصر inline همان‌جایی است که هست، و تمام

---

## padding عمودی در inline elements

می‌توان به عناصر inline `padding` عمودی داد، اما نتیجه ممکن است غیرمنتظره باشد، پس باید با احتیاط از آن استفاده کرد. این موضوع را در ماژول Typography بیشتر بررسی می‌کنیم.

---

## Exceptionها

دو استثنا برای این قاعده وجود دارد:

### 1. Replaced elements

**Replaced element** به عنصری گفته می‌شود که یک شیء "خارجی" را درون خودش embed می‌کند. این شامل موارد زیر است:

- `<img />`
- `<video />`
- `<canvas />`

این عناصر از نظر فنی **inline** هستند، اما خاص‌اند: آن‌ها می‌توانند روی **block layout** تأثیر بگذارند. می‌توانی برایشان اندازه‌ی مشخص (`width` و `height`) تعیین کنی، یا مثلاً `margin-top` بدهی.

### چطور این را درک کنیم؟

یک ترفند خوب این است که آن‌ها را مثل یک **شیء خارجی داخل یک wrapper inline** تصور کنیم. وقتی `width` یا `height` می‌دهی، در واقع داری این ویژگی‌ها را به همان شیء خارجی اعمال می‌کنی، در حالی که wrapper inline همچنان با flow طبیعی صفحه جلو می‌رود.

---

### 2. تگ `<button>`

استثنای دوم، تگ `<button>` است. این تگ دقیقاً replaced element نیست، اما تقریباً مثل آن عمل می‌کند. یعنی می‌توان برای آن `width` و `height` تعیین کرد.

---

اگر بخواهی، می‌توانم همین بخش را هم برایت:
- **کوتاه‌تر و تمیزتر برای نوت**
- یا **به سبک آموزشی‌تر و مرتب‌تر برای Obsidian**
بازنویسی کنم.
[Timestamp: 2026/07/03 09:07:31]