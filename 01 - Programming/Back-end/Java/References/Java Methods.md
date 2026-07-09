**متدها** در جاوا بلاک(block)های کد هستند که وظیفه خاصی را انجام می‌دهند. متد به ما اجازه می‌دهد که از کدها استفاده مجدد کنیم. همه متدها متعلق به یک کلاس هستند. متدها شبیه به توابع هستند و رفتار آبجکت را آشکار(expose) می‌کنند.

- متد اجازه می‌دهد یک قطعه کد یکبار بنویسیم‌و‌هرجا در برنامه نیاز بود استفاده مجددکنیم.
- این باعث میشه کد تمیز و organizeشده و درک و مدیریت راحت‌تر باشه
## Why Use Method
شکستن کد به methodهای جداگانه به بهبود خوانایی قابلیت استفاده مجدد و قابلیت نگهداری‌ کمک می‌کند
- **Code Re-usability:** Write once, use multiple times without repeating code so that code re-usability increase.
- **Modularity:** Dividing a program into separate methods allows each method to handle a specific task, making the code more organized and easier to manage.
- **Readability:** Smaller, named methods make the code easier to read and understand.
- **Maintainability:** It’s easier to fix bugs or update code when it's organized into methods.
## Method Call Stack in Java

جاوا یک زبان OOP است که زبان مبتنی بر Stack (Stack based) که در آن `method` نقش مهمی و کلیدی در کنترل جریان و اجرای برنامه دارند 

(a key role in controlling the program's execution flow)
وقتی یک متد call میشه جاوا از یک ساختار داخلی به نام call stack استفاده می‌کند که اجرا شدن متغییرها و return address را مدیریت کنه

یک ساختار داده است که براساس قانون LIFO کار می‌کنه
> **Last In, First Out**
> 
> آخرین چیزی که وارد شده، اولین چیزی است که خارج می‌شود.

### Method Execution
when a method is called
- A new stack frame is added to the call stack to store method details
- The method runs its code
- After execution, the stack frame is removed, and control, goes back to the calling method
- Java automatically manages the call stack using the Java Virtual Machine (JVM).

More in [[Java's Call Stack]]

## Predefined Method
متد های هستند که از قبل توسط کلاس لایبرری های جاوا تعریف شدن. و همچین با اسم standard library method - built-in method شناخته می‌شوند