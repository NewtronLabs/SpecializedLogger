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
        jcenter()
        maven { url "http://code.newtronlabs.com:8081/artifactory/libs-release-local" }
    }
    dependencies {
        classpath 'com.android.tools.build:gradle:3.1.3'
        classpath 'com.newtronlabs.android:plugin:2.0.1'
    }
}

allprojects {
    repositories {
        jcenter()
        maven { url "http://code.newtronlabs.com:8081/artifactory/libs-release-local" }
    }
}

subprojects {
    apply plugin: 'com.newtronlabs.android'
}
```

In the `build.gradle` for your app.

```gradle
dependencies {
    compileOnly 'com.newtronlabs.specializedlogger:specializedlogger:2.0.0'
}
```

### Step 2

**Simple Logging**

```java
Slog.d("Test", logMsg);

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

Specialized Logger binaries and source code can only be used in accordance with Freeware license. That is, freeware may be used without payment, but may not be modified. The developer of Specialized Logger retains all rights to change, alter, adapt, and/or distribute the software. Specialized Logger is not liable for any damages and/or losses incurred during the use of Specialized Logger.

You may not decompile, reverse engineer, pull apart, or otherwise attempt to dissect the source code, algorithm, technique or other information from the binary code of Specialized Logger unless it is authorized by existing applicable law and only to the extent authorized by such law. In the event that such a law applies, user may only attempt the foregoing if: (1) user has contacted Newtron Labs to request such information and Newtron Labs has failed to respond in a reasonable time, or (2) reverse engineering is strictly necessary to obtain such information and Newtron Labs has failed to reply. Any information obtained by user from Newtron Labs may be used only in accordance to the terms agreed upon by Newtron Labs and in adherence to Newtron Labs confidentiality policy. Such information supplied by Newtron Labs and received by user shall not be disclosed to a third party or used to create a software substantially similar to the technique or expression of the Newtron Labs Specialized Logger software.

You are solely responsible for determining the appropriateness of using Specialized Logger and assume any risks associated with Your use of Specialized Logger. In no event and under no legal theory, whether in tort (including negligence), contract, or otherwise, unless required by applicable law (such as deliberate and grossly negligent acts) or agreed to in writing, shall Newtron Labs be liable to You for damages, including any direct, indirect, special, incidental, or consequential damages of any character arising as a result of this License or out of the use or inability to use the Specialized Logger (including but not limited to damages for loss of goodwill, work stoppage, computer failure or malfunction, or any and all other commercial damages or losses), even if Newtron Labs has been advised of the possibility of such damages. 

## Contact

solutions@newtronlabs.com
