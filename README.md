# Specialized Logger

Encrypted logging made great again.

Specialized Logger is an Android library that provides you flexibility and reliability when logging. It comes with a simple to use logger as well as an encrypted logger for commercial products.

---

## How to Use 

The library is intended for logging purposes. 

### Step 1

Include the below dependencies in your `build.gradle` project.

```gradle
buildscript {
    repositories {
        google()
        jcenter()
        maven { url "https://newtronlabs.jfrog.io/artifactory/libs-release-local" }
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.5.2'
        classpath 'com.newtronlabs.android:plugin:4.0.3'
    }
}

allprojects {
    repositories {
        google()
        jcenter()
        maven { url "https://newtronlabs.jfrog.io/artifactory/libs-release-local" }
    }
}

subprojects {
    apply plugin: 'com.newtronlabs.android'
}
```

In the `build.gradle` for your app.

```gradle
dependencies {
    compileOnly 'com.newtronlabs.specializedlogger:specializedlogger:4.0.0'
}
```

### Step 2

**Simple Logging**

```java
SLog.d("Test", logMsg);

Throwable tr = new NullPointerException("Testing a null pointer exception!");
SLog.v("Test", logMsg, tr);
```

**Encrpted Logging**

```java
// Example Cipher and Key.
DESKeySpec keySpec = new DESKeySpec("Your secret Key phrase".getBytes("UTF8"));
SecretKeyFactory keyFactory = SecretKeyFactory.getInstance("DES");
SecretKey key = keyFactory.generateSecret(keySpec);\
Cipher cipher;
cipher = Cipher.getInstance("DES");

// Switch To Secure Logger
SLog.setLogger(new SecureLogger(cipher, key));
SLog.v("Test", "This is now encrypted!");
```

---

## License

https://gist.github.com/NewtronLabs/216f45db2339e0bc638e7c14a6af9cc8

## Contact

solutions@newtronlabs.com
