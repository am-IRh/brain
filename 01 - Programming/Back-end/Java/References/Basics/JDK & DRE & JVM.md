## JDK (Java Development Kit):
ابزارها و کتابخانه های را برای توسعه برنامه های جاوا فراهم می‌کند. عموما توسط برنامه نویس ها استفاده می‌شود و که شامل JRE و JVM می‌شود. JDK وابسته به پلتفرم هست پس برای هر OS ورژن های متفاوتی وجود دارد

**نحوه کار JDK**
- **Source Code (.java):** Developer writes a Java program.
- **Compilation:** The JDK’s compiler (javac) converts the code into bytecode stored in .class files.
- **Execution:** The JVM executes the bytecode, translating it into native instructions.
## JRE (Java Runtime Environment): 
یک میحطی برای اجرای برنامه های جاوا فراهم می‌کند اما شامل ابزار های توسعه نیست. برای end-user در نظر گرفته شده کسی که فقط نیاز داره برنامه رو اجرا کنه.
- Contains the JVM and standard class libraries.
- Provides all runtime requirements for Java applications.
- Does not support compilation or debugging.
**Note:**
- JRE is only for running applications, not for developing them.
- It is platform-dependent (different builds for different OS).
**نحوه کار:**
1. ****Class Loading:**** Loads compiled .class files into memory.
2. ****Bytecode Verification:**** Ensures security and validity of bytecode.
3. ****Execution:**** Uses the JVM (interpreter + JIT compiler) to execute instructions and make system calls.
## JVM (Java Virtual Machine):
موتور اصلی اجرای جاوا است مسئول تبدیل Bytecode به دستورالعمل های مخصوص ماشین هست
- Part of both JDK and JRE.
- Performs memory management and garbage collection.
- Provides portability by executing the same bytecode on different platforms.
**Note:**

- JVM implementations are platform-dependent.
- Bytecode is platform-independent and can run on any JVM.
- Modern JVMs rely heavily on Just-In-Time (JIT) compilation for performance.
**نحوه کار:**

![class_loader](https://media.geeksforgeeks.org/wp-content/uploads/20251003170021775913/class_loader.webp "Click to enlarge")

1. ****Loading:**** Class loader loads bytecode into memory.
2. ****Linking:**** Performs verification, preparation, and resolution.
3. ****Initialization:**** Executes class constructors and static initializers.
4. ****Execution:**** Interprets or compiles bytecode into native code.

## JDK vs JRE vs JVM

| Aspect              | JDK                                             | JRE                                    | JVM                                                      |
| ------------------- | ----------------------------------------------- | -------------------------------------- | -------------------------------------------------------- |
| Purpose             | Used to develop Java applications               | Used to run Java applications          | Executes Java bytecode                                   |
| Platform Dependency | Platform-dependent (OS specific)                | Platform-dependent (OS specific)       | JVM is OS-specific, but bytecode is platform-independent |
| Includes            | JRE + Development tools (javac, debugger, etc.) | JVM + Libraries (e.g., rt.jar)         | ClassLoader, JIT Compiler, Garbage Collector             |
| Use Case            | Writing and compiling Java code                 | Running a Java application on a system | Convert bytecode into native machine code                |



