# PackageTest

#### 概述
  在项目提测后，测试或者验收者总是希望在同一部手机上安装不同环境的apk安装包，方便对比一些UI的显示。那么问题来了，一个项目怎么在一部手机上安装不同环境的apk呢？那就是给项目根据不同环境设置不同的包名，就可以实现现在的功能。

#### 步骤一、app module中的 build.gradle 中配置 productFlavors
~~~
        dev {
            applicationId "com.example.dev"
            manifestPlaceholders = [app_name: "app_dev"]
        }
        uat {
            applicationId "com.example.uat"
            manifestPlaceholders = [app_name: "app_uat"]
        }
        develop {
            applicationId "com.example.develop"
            manifestPlaceholders = [app_name: "app_develop"]
        }
        online {
            applicationId "com.example.online"
            manifestPlaceholders = [app_name: "app_online"]
        }
~~~
#### 步骤二、build --> build .. APKs
可以选中我们需要打的包（或者签名包）

#### 步骤三、应用名称设置，用于区分不同包名的apk：需要在menifest中设置 android:label 即可
~~~
    <application
        android:allowBackup="true"
        android:icon="@mipmap/ic_launcher"
        android:label="${app_name}"
        android:roundIcon="@mipmap/ic_launcher_round"
        android:supportsRtl="true"
        android:theme="@style/AppTheme">
~~~



