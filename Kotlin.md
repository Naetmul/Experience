# Kotlin

### Error while compiling Kotlin/Native in Windows

- `java.lang.ClassNotFoundException: com.sun.tools.javac.util.Context` during `gradlew dependencies:update`
  - Solution: Add the JDK directory path to Windows environemnt `PATH`. The JDK directory should be in front of `C:\ProgramData\Oracle\Java\javapath`.
