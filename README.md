# github_maven_androidDemo
> Welcome to github-maven_androidDemo. github+maven android TEST Demo. 以main分支作为maven仓库，master分支为test demo(Take main branch as Maven repository, and master branch as test  demo)


**<h2>github+maven对接步骤</h2>**
 
> **<h3> 1. 项目build.gradle里面添加配置<h3>**
 
 repositories {
    jcenter()
     maven{
            url "https://raw.githubusercontent.com/devgogogo/github_maven_androidDemo/main"
        }
  }

> **<h3>2. app模块build.gradle里面添加asiabill sdk库<h3>**
 
 dependencies {
     implementation "com.test:github_maven_androidDemo:1.0.0"//具体版本号根据你的需求来确定
 }
