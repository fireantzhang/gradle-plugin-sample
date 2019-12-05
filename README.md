# Gradle-plugin-sample

这个 Demo 主要两个目的：

1. 简单展示 Gradle 自定义插件开发，并支持在 `build.gradle` 中配置自定义信息；
2. 为 [了解如何从源码层寻找消除 Android Build Gradle 过期 API 的方案](https://mp.weixin.qq.com/s/G2T9iORgyOIczzLBgWPlvg) 提供说明便利，介绍 Android 项目中的自定义配置项是从哪里产生的；

### 文件夹结构说明

- `plugin` 文件夹是自定开发插件的项目，运行 `./gradlew clean uploadArchives` 命令即可在该目录下的 `repo` 文件夹生成一个对应的插件版本，如下：

  ```
  ./repo
  └── com
      └── fireantzhang
          └── plugin
              └── fireantPlugin
                  ├── 1.0.0
                  │   ├── fireantPlugin-1.0.0.jar
                  │   ├── fireantPlugin-1.0.0.jar.md5
                  │   ├── fireantPlugin-1.0.0.jar.sha1
                  │   ├── fireantPlugin-1.0.0.pom
                  │   ├── fireantPlugin-1.0.0.pom.md5
                  │   └── fireantPlugin-1.0.0.pom.sha1
                  ├── maven-metadata.xml
                  ├── maven-metadata.xml.md5
                  └── maven-metadata.xml.sha1
  ```

- `sample` 文件夹是一个示例 Android 工程项目，引入 `plugin` 中开发的 `fireantPlugin` 插件，并且配置相关的信息，执行 `./gradlew myAndroidTask` 即可运行插件中的自定义任务，得到如下内容：

  ```
  » ./gradlew myAndroidTask
  
  > Task :app:myAndroidTask
  自定义插件中执行任务：myAndroidTask，获取到的参数为：MyAndroidInfo{devName='fireantzhang', devAge=18} 
  ```