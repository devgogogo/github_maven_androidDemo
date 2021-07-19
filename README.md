# github_maven_androidDemo
> Welcome to github-maven_androidDemo. github+maven android TEST Demo. 以main分支作为maven仓库，master分支为test demo(Take main branch as Maven repository, and master branch as test  demo)



**<h2>github+maven sdk生产步骤</h2>**
> **<h3> 1. 在library module下面build.gradle末尾添加配置<h3>**

``` 
apply plugin: 'maven'
uploadArchives {
    repositories.mavenDeployer {
        def mavenDirPath = file('D:\\testsdk') // 本地存放目录(自行选择)，可放在gradle.properties文件中引用
        repository(url:"file://${mavenDirPath.absolutePath}") // 必须双引号，单引号不会转义$
        pom.project {
            groupId "com.test" // 可以随意取，一般取包名
            artifactId "github_maven_androidDemo" // 可以随意取，一般取库的名字
            version "1.0.0" // 版本号
        }
    }
}
 
//以下代码会生成jar包源文件，如果是不开源码，请不要输入这段
//aar包内包含注释
task androidSourcesJar(type: Jar) {
    classifier = 'sources'
    from android.sourceSets.main.java.sourceFiles
}

artifacts {
    archives androidSourcesJar
}
```

**<h2>github+maven对接步骤</h2>**
 
> **<h3> 1. 项目build.gradle里面添加配置<h3>**
 
 ```
 repositories {
    jcenter()
     maven{
            url "https://raw.githubusercontent.com/devgogogo/github_maven_androidDemo/main"
        }
  }
```
 
> **<h3>2. app模块build.gradle里面添加asiabill sdk库<h3>**
 
 ```
 dependencies {
     implementation "com.test:github_maven_androidDemo:1.0.0"//具体版本号根据你的需求来确定
 }
 ```
