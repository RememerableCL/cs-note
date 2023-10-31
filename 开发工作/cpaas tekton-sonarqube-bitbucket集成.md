#待处理  


# reference

repository mirrors
[Mirrors | Bitbucket Data Center and Server 8.14 | Atlassian Documentation](https://confluence.atlassian.com/bitbucketserver/mirrors-776640046.html)

# pr 
## bitbucket webhook
### webhook 新增
[Manage webhooks | Bitbucket Data Center and Server 7.12 | Atlassian Documentation](https://confluence.atlassian.com/bitbucketserver0712/manage-webhooks-1063557703.html?utm_campaign=in-app-help&utm_medium=in-app-help&locale=zh_CN%2Czh&utm_source=stash)
[Create and trigger a webhook tutorial | Bitbucket Cloud | Atlassian Support](https://support.atlassian.com/bitbucket-cloud/docs/create-and-trigger-a-webhook-tutorial/)

![image.png](https://cdn.nlark.com/yuque/0/2023/png/23176849/1695267858675-cd709913-a622-4af4-b751-4c6cc65fdd20.png#averageHue=%23fefdfd&clientId=uf60d235e-8df1-4&from=paste&height=448&id=uc7628bbc&originHeight=448&originWidth=647&originalType=binary&ratio=1&rotation=0&showTitle=false&size=32762&status=done&style=none&taskId=u0eb4de46-3e76-4892-ad35-5c76023e7ac&title=&width=647)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/23176849/1695266386881-c040d1c3-3db8-4ff2-a4a4-f7179865669a.png#averageHue=%23fefefd&clientId=uf60d235e-8df1-4&from=paste&height=71&id=lv6s5&originHeight=71&originWidth=237&originalType=binary&ratio=1&rotation=0&showTitle=false&size=2440&status=done&style=none&taskId=ufdeb2612-8c25-4e97-90ed-f68bcbe184c&title=&width=237)
### webhook http body
[Event payloads | Bitbucket Cloud | Atlassian Support](https://support.atlassian.com/bitbucket-cloud/docs/event-payloads/)
[Event payload | Bitbucket Data Center and Server 7.12 | Atlassian Documentation](https://confluence.atlassian.com/bitbucketserver0712/event-payload-1063557708.html?utm_campaign=in-app-help&utm_medium=in-app-help&locale=zh_CN%2Czh&utm_source=stash#Eventpayload-pullrequest)
[Event payload | Bitbucket Data Center and Server 7.12 | Atlassian Documentation](https://confluence.atlassian.com/bitbucketserver0712/event-payload-1063557708.html?utm_campaign=in-app-help&utm_medium=in-app-help&locale=zh_CN%2Czh&utm_source=stash#Eventpayload-pullrequest)

## build upgrate
[https://developer.atlassian.com/server/bitbucket/how-tos/updating-build-status-for-commits/](https://developer.atlassian.com/server/bitbucket/how-tos/updating-build-status-for-commits/)
## request limits
[https://support.atlassian.com/bitbucket-cloud/docs/api-request-limits/](https://support.atlassian.com/bitbucket-cloud/docs/api-request-limits/)

## rest api
```shell
 curl -u auto_cpaas:MzEzMTk5OTM0MTE3OoBrVupQCl91S/Tk2B0VPPIIivMV --request GET  --url https://code.xwwxkj.com/rest/api/latest/projects/cpaas   --header 'Accept: application/json'

 curl -u auto_cpaas:MzEzMTk5OTM0MTE3OoBrVupQCl91S/Tk2B0VPPIIivMV   https://code.xwwxkj.com/rest/api/latest/projects/cpaas/repos/cpaas/commits/2122a5142d2c0d312fcc1973673a8492e246dc46/builds  -X POST -d '{
"state": "INPROGRESS",
"key": "$(params.latestCommit)",
"name": "$(params.latestCommit)",
"url": "http://172.16.1.10:32004",
"description": "fg"
 }'  -H "Content-Type: application/json"# 是头的原因 

  curl -u auto_cpaas:MzEzMTk5OTM0MTE3OoBrVupQCl91S/Tk2B0VPPIIivMV https://code.xwwxkj.com/rest/build-status/1.0/commits/2122a5142d2c0d312fcc1973673a8492e246dc46 -X POST -d '{
"state": "INPROGRESS",
"key": "$(params.latestCommit)",
"name": "$(params.latestCommit)",
"url": "http://172.16.1.10:32004",
"description": "fg"
 }'  -H "Content-Type: application/json" -i
         


curl -u auto_cpaas:MzEzMTk5OTM0MTE3OoBrVupQCl91S/Tk2B0VPPIIivMV --request GET \
  --url 'http://code.xwwxkj.com/rest/insights/1.0/projects/cpaas/repos/cpaas/commits/2122a5142d2c0d312fcc1973673a8492e246dc46/annotations' --header 'Accept: application/json'
# 没有report，用不了这个

 curl -u auto_cpaas:MzEzMTk5OTM0MTE3OoBrVupQCl91S/Tk2B0VPPIIivMV --request PUT https://code.xwwxkj.com/rest/insights/latest/projects/cpaas/repos/cpaas/commits/cae6e9393495c3a131d3d2eef229ea075f14c4af/reports/com.cpaas  --header 'Accept: application/json' --header 'Content-Type: application/json' --data '{
  "coverageProviderKey": "<string>",
  "createdDate": 1630041546433,
  "data": [
    {
      "value": 1,
      "type": "NUMBER",
      "title": "data.title"
    }
  ],
  "details": "This is the details of the report, it can be a longer string describing the report.",
  "link": "http://insight.example.com",
  "logoUrl": "http://insight.example.com/logo",
  "reporter": "Reporter/tool that produced this report",
  "result": "PASS",
  "title": "report.title"
}'

  curl -u auto_cpaas:MzEzMTk5OTM0MTE3OoBrVupQCl91S/Tk2B0VPPIIivMV https://code.xwwxkj.com/rest/insights/latest/projects/cpaas/repos/cpaas/commits/cae6e9393495c3a131d3d2eef229ea075f14c4af/reports/com.cpaas/annotations -X POST -d'{"annotations": [
    {
      "externalId": "message-2",
      "line": 127,
      "link": "https://www.baidu.com/",
      "message": "tedstgdgdgdg",
      "path": "cpaas-match-report/src/main/java/com/xuanwu/cpaas/matchreport/strategy/impl/DefaultLongReplyMessageMergeImpl.java",
      "severity": "MEDIUM",
      "type": "CODE_SMELL"
    }
  ]
}' -H "Content-Type: application/json" -i

curl --request PUT --url 'https://code.xwwxkj.com/rest/insights/latest/projects/{projectKey}/repos/{repositorySlug}/commits/{commitId}/reports/{key}/annotations/{externalId}' \
  --header 'Content-Type: application/json' \
  --data '{
  "externalId": "message-1",
  "line": 4,
  "link": "https://link.to.tool/that/produced/annotation/message-1",
  "message": "This is a bug here because reasons",
  "path": "path/to/file/in/repo",
  "severity": "MEDIUM",
  "type": "CODE_SMELL"
}'

curl  -u auto_cpaas:MzEzMTk5OTM0MTE3OoBrVupQCl91S/Tk2B0VPPIIivMV --request POST --url 'https://code.xwwxkj.com/rest/api/latest/projects/cpaas/repos/cpaas/pull-requests/1406/blocker-comments' --header 'Accept: application/json' --header 'Content-Type: application/json'  --data '{
  "version": 1,
  "id": 1,
  "state": "OPEN",
  "text": "PANXIANHAO",
  "severity": "NORMAL",
  "threadResolved": true,
  "properties": {}
}'

curl  -u auto_cpaas:MzEzMTk5OTM0MTE3OoBrVupQCl91S/Tk2B0VPPIIivMV --request POST --url 'https://code.xwwxkj.com/rest/api/latest/projects/cpaas/repos/cpaas/pull-requests/1406/blocker-comments' --header 'Accept: application/json' --header 'Content-Type: application/json'  --data '{
  "version": 1,
  "id": 1,
  "state": "OPEN",
  "text": "PANXIANHAO",
  "severity": "NORMAL",
  "threadResolved": true,
  "anchor": { 
         "diffType": "COMMIT",  
         "path": "cpaas-match-report/src/main/java/com/xuanwu/cpaas/matchreport/strategy/impl/DefaultLongReplyMessageMergeImpl.java", 
         "srcPath": "cpaas-match-report/src/main/java/com/xuanwu/cpaas/matchreport/strategy/impl/DefaultLongReplyMessageMergeImpl.java", 
          "line": 127,
          "fileType": "FROM",
          "fromHash": "cae6e9393495c3a131d3d2eef229ea075f14c4af",
          "toHash": "f65a8313726a45e974fa8892ec53208eb8ada3a3"
     },
  "properties": {}
}'


curl  -u auto_cpaas:MzEzMTk5OTM0MTE3OoBrVupQCl91S/Tk2B0VPPIIivMV --request POST --url 'https://code.xwwxkj.com/rest/api/latest/projects/cpaas/repos/cpaas/pull-requests/1406/comments' --header 'Accept: application/json' --header 'Content-Type: application/json'  --data '{
  "version": 1,
  "id": 1,
  "state": "OPEN",
  "text": "An insightful comment.",
  "severity": "NORMAL",
  "threadResolved": true,
  "properties": {
    "anchor": {
"diffType": "COMMIT",
  "lineType": "CONTEXT",
  "fileType": "FROM",
  "line": 71,
"fromHash": "6df3858eeb9a53a911cd17e66a9174d44ffb02cd",
"path": "cpaas-match-report/src/main/java/com/xuanwu/cpaas/matchreport/strategy/impl/DefaultLongReplyMessageMergeImpl.java",
"srcPath": "cpaas-match-report/src/main/java/com/xuanwu/cpaas/matchreport/strategy/impl/DefaultLongReplyMessageMergeImpl.java",
"toHash": "04c7c5c931b9418ca7b66f51fe934d0bd9b2ba4b"
}
  }
}'

 
```

## 请求认证
[Personal access tokens | Bitbucket Data Center and Server 7.12 | Atlassian Documentation](https://confluence.atlassian.com/bitbucketserver0712/personal-access-tokens-1063557386.html?utm_campaign=in-app-help&utm_medium=in-app-help&locale=zh_CN%2Czh&utm_source=stash#Personalaccesstokens-usingpersonalaccesstokens)
[Use OAuth on Bitbucket Cloud | Bitbucket Cloud | Atlassian Support](https://support.atlassian.com/bitbucket-cloud/docs/use-oauth-on-bitbucket-cloud/)
也可以使用账号：密码的方式
### personal token
auto_cpaas:MzEzMTk5OTM0MTE3OoBrVupQCl91S/Tk2B0VPPIIivMV
## code insight
[Code Insights | Bitbucket Data Center and Server 7.12 | Atlassian Documentation](https://confluence.atlassian.com/bitbucketserver0712/code-insights-1063557675.html)
[https://developer.atlassian.com/server/bitbucket/how-tos/code-insights/](https://developer.atlassian.com/server/bitbucket/how-tos/code-insights/)
# checkstyle
[GitHub - checkstyle/checkstyle: Checkstyle is a development tool to help programmers write Java code that adheres to a coding standard. By default it supports the Google Java Style Guide and Sun Code Conventions, but is highly configurable. It can be invoked with an ANT task and a command line program.](https://github.com/checkstyle/checkstyle)
## checkstyle jar commad
[https://checkstyle.sourceforge.io/cmdline.html](https://checkstyle.sourceforge.io/cmdline.html)
[使用Checkstyle工具检查java代码风格-腾讯云开发者社区-腾讯云](https://cloud.tencent.com/developer/article/1599030)
注意要在整个项目的root目录执行jar作为进程工作目录
[https://github.com/vir56k/demo/tree/master/checkstyle](https://github.com/vir56k/demo/tree/master/checkstyle)

## integrate checkstyle with maven
[https://maven.apache.org/plugins/maven-checkstyle-plugin/usage.html](https://maven.apache.org/plugins/maven-checkstyle-plugin/usage.html)

[Jenkins部署及代码静态检查工具Checkstyle集成](https://zhuanlan.zhihu.com/p/69632001)
[jenkins 集成 checkstyle_checkstyle jar下载_globalcoding的博客-CSDN博客](https://blog.csdn.net/u011149152/article/details/123491656)



# tekton
##  pipeline finally
[https://tekton.dev/docs/pipelines/pipelines/#consuming-task-execution-results-in-finally](https://tekton.dev/docs/pipelines/pipelines/#consuming-task-execution-results-in-finally)

1. 接受task的状态、输出result进一步处理
2. 加了finally的pipelineRunResult的status结果
## 发送http给消息推送组件
[curl 模拟 GET\POST 请求，以及 curl post 上传文件_curl post请求_FungLeo的博客-CSDN博客](https://blog.csdn.net/FungLeo/article/details/80703365)
## tekton context 变量
[https://stackoverflow.com/questions/72831206/tekton-get-pipeline-name-inside-task](https://stackoverflow.com/questions/72831206/tekton-get-pipeline-name-inside-task)
[https://tekton.dev/docs/pipelines/variables/](https://tekton.dev/docs/pipelines/variables/)
## tekton pipeline state
[https://tekton.dev/docs/pipelines/pipelines/#pipelinerun-status-with-finally](https://tekton.dev/docs/pipelines/pipelines/#pipelinerun-status-with-finally)
finally接受pipelineRun结果

## task results
[https://github.com/tektoncd/pipeline/blob/main/examples/v1/taskruns/alpha/step-stream-results.yaml](https://github.com/tektoncd/pipeline/blob/main/examples/v1/taskruns/alpha/step-stream-results.yaml)
在task中的step传递result，是作为一个文件，使用cat等读取文件方式读取，而不是直接取值
# 覆盖率
[https://en.wikipedia.org/wiki/Java_code_coverage_tools](https://en.wikipedia.org/wiki/Java_code_coverage_tools)
[https://www.jacoco.org/jacoco/](https://www.jacoco.org/jacoco/)

## jacoco
在工程根目录添加**lombok.confg**文件，其中加入lombok.addLombokGeneratedAnnotation = true的配置，jacoco即可忽略所有lombok自动生成的方法([https://projectlombok.org/features/configuration](https://projectlombok.org/features/configuration))
合并单元、功能、集成
[https://juejin.cn/post/7107150214100123678](https://juejin.cn/post/7107150214100123678)
合并不同版本代码覆盖率
[https://zhuanlan.zhihu.com/p/459188446](https://zhuanlan.zhihu.com/p/459188446)
[https://juejin.cn/post/6844903999473188877](https://juejin.cn/post/6844903999473188877)
# sonarque
[SonarQube scanning](https://codefresh.io/docs/docs/testing/sonarqube-integration/)
[https://github.com/SonarSource/sonar-scanning-examples](https://github.com/SonarSource/sonar-scanning-examples)

1. create from bitbucket

其中，bitbucket账号管理，创建personal token
![image.png](https://cdn.nlark.com/yuque/0/2023/png/23176849/1695363063516-5969336e-c5fd-44ad-ad70-dd1987e86b57.png#averageHue=%23fefefd&clientId=u2c8fd0d9-4837-4&from=paste&height=347&id=u69a0ccf6&originHeight=347&originWidth=1801&originalType=binary&ratio=1&rotation=0&showTitle=false&size=36216&status=done&style=none&taskId=u5b88e230-f47b-4a1e-8f34-f22e8c1aaf0&title=&width=1801)

[Bitbucket Server integration](https://docs.sonarsource.com/sonarqube/9.9/devops-platform-integration/bitbucket-integration/bitbucket-server-integration/)

2. 选中项目

![image.png](https://cdn.nlark.com/yuque/0/2023/png/23176849/1695363045494-b9d5f20c-48a1-48ab-83cb-ff7e57aba964.png#averageHue=%23f6f6f5&clientId=u2c8fd0d9-4837-4&from=paste&height=352&id=uf710e553&originHeight=352&originWidth=740&originalType=binary&ratio=1&rotation=0&showTitle=false&size=24603&status=done&style=none&taskId=u3439af13-d519-42e9-a49b-6d96e58ddc1&title=&width=740)

3. 选择集成的ci组件

创建token，选择不过期的
![image.png](https://cdn.nlark.com/yuque/0/2023/png/23176849/1695363156671-04edafbe-5f94-47ba-b501-c96192451fab.png#averageHue=%23f8f7f7&clientId=u2c8fd0d9-4837-4&from=paste&height=362&id=udf32e981&originHeight=362&originWidth=835&originalType=binary&ratio=1&rotation=0&showTitle=false&size=26089&status=done&style=none&taskId=uf3aee918-e048-4def-a597-5f0cd611e18&title=&width=835)
cpaas: **sqp_302aba4b26fa3d6a3d1832c1140bbb67b423fda7**
**mvn clean verify sonar:sonar \**
**  -Dsonar.projectKey=CPAAS_cpaas_AYq7gWkdcNdOUVRcFiVe \**
**  -Dsonar.host.url=**[**http://sonarqube.traefik.devcilium.wxchina.com:30669**](http://sonarqube.traefik.devcilium.wxchina.com:30669)** \**
**  -Dsonar.login=sqp_302aba4b26fa3d6a3d1832c1140bbb67b423fda7**

mvn clean package -Dmaven.test.skip=true \
sonar:sonar \
-Dsonar.projectKey=CPAAS_cpaas_AYq7gWkdcNdOUVRcFiVe\
-Dsonar.host.url=[http://10.20.121.41:30205\](http://10.20.121.41:30205\)
-Dsonar.login=sqp_302aba4b26fa3d6a3d1832c1140bbb67b423fda7\
[How to set Java source code version](https://community.sonarsource.com/t/how-to-set-java-source-code-version/22137/3)

```shell
mvn clean package -Dmaven.test.skip=true  sonar:sonar  -Dsonar.projectKey=CPAAS_cpaas_AYq7gWkdcNdOUVRcFiVe -Dsonar.host.url=http://10.20.121.41:30205 -Dsonar.login=sqp_302aba4b26fa3d6a3d1832c1140bbb67b423fda7 -Dsonar.inclusions=cpaas-simulate-http/src/main/java/com/xuanwu/cpaas/simulate/http/controller/DingYuController.java,cpaas-msg-hub/src/main/java/com/xuanwu/cpaas/msghub/constant/MessageTaskType.java  

mvn clean package -Dmaven.test.skip=true  sonar:sonar  -Dsonar.projectKey=1234564dgd -Dsonar.host.url=http://10.20.121.41:30205 -Dsonar.login=sqa_4bfba2fef6441ce7316bd11d66bb52ac855e1e1d -Dsonar.inclusions=cpaas-channel-hub/src/main/java/com/xuanwu/cpaas/channelhub/service/SubChannelService.java,cpaas-channel-hub/src/main/java/com/xuanwu/cpaas/channelhub/service/impl/ChannelServiceImpl.java,cpaas-channel-hub/src/main/java/com/xuanwu/cpaas/channelhub/service/impl/SubChannelServiceImpl.java,cpaas-channel-hub/src/main/java/com/xuanwu/cpaas/channelhub/service/thirdparty/config/ChannelConfigAggregationService.java,cpaas-channel-hub/src/main/java/com/xuanwu/cpaas/channelhub/service/thirdparty/config/impl/ChannelConfigAggregationServiceImpl.java,


mvn clean install -Dmaven.test.failure.ignore=true  sonar:sonar -Pcoverage -Dsonar.projectKey==CPAAS_cpaas_AYq7gWkdcNdOUVRcFiVe -Dsonar.host.url=http://10.20.121.41:30205 -Dsonar.login=sqa_4bfba2fef6441ce7316bd11d66bb52ac855e1e1d 
```

```shell
echo ------------------- 开始代码检查 $WORKSPACE -------------------
 
# 环境参数初始化
export PATH=$PATH
export BUILD_ID=dontKillMe
source /etc/profile
 
# 删除删一次扫描的报告
rm -rf $WORKSPACE/sonar-report.json
 
# 定位到要扫描的工作目录
cd $PARENT_WORKSPACE
 
# 只获取本地 PR 提交和目标合并分支之间的差异文件，目的是要做增量扫描
waitCheckFiles=`git diff --name-only $PULL_REQUEST_TO_HASH $PULL_REQUEST_FROM_HASH | grep '\.java' | xargs printf '%s,'`
 
# 开始执行 sonar-scanner 扫描
SONAR_SCAN_RESULT=`sonar-scanner -Dsonar.inclusions=$waitCheckFiles`
 
# 因为 sonar-scanner 上传报告后，sonarQube 需要点时间处理报告，所以这里获取报告延后一点
sleep 15s
 
# 通过项目跟目录获取到 sonar-scanner 配置 projectKey
SONAR_PROJECT_KEY="$(grep sonar.projectKey= sonar-project.properties | awk -F '=' '{print $2}' | tr -d '\r')"
 
# 从 sonarQube 上拉取分析报告，并通过 jq 命令 + jq 模板把分析报告转换成 bitbucket 需要的格式
curl --silent -u admin:cpaas@WX123 "http://172.16.1.10:30010/api/issues/search?componentKeys=$SONAR_PROJECT_KEY&resolved=false" | jq -f $SONAR_SCANNER_HOME/conf/sonar-report-builder.jq > $WORKSPACE/sonar-report.json

```
```shell
sonar-scanner -Dsonar.projectKey=CPAAS_cpaas_AYq7gWkdcNdOUVRcFiVe -Dsonar.host.url=http://10.20.121.41:30205 -Dsonar.login=sqp_302aba4b26fa3d6a3d1832c1140bbb67b423fda7 -Dsonar.language=java -Dsonar.exclusions=cpaas-simulate-gate/src/**/*,cpaas-protocol/src/**/* -Dsonar.test.exclusions=src/test/**/* -Dsonar.sourceEncoding=utf-8 -Dsonar.sources=src/main -Dsonar.java.binaries=target/classes -Dsonar.inclusions=com/xuanwu/cpaas/msghub/constant/MessageTaskType.java


sonar-scanner -Dsonar.projectKey=CPAAS_cpaas_AYq7gWkdcNdOUVRcFiVe -Dsonar.host.url=http://10.20.121.41:30205 -Dsonar.login=sqp_302aba4b26fa3d6a3d1832c1140bbb67b423fda7 -Dsonar.java.source=1.8 -Dsonar.sourceEncoding=UTF-8 -Dsonar.exclusions=**/protobuf/** -Dsonar.caching.enabled -Dsonar.java.binaries=cpaas-msg-hub/target/classes,cpaas-simulate-http/target/classes -Dsonar.java.libraries=./**/*.jar -Dsonar.inclusions=cpaas-simulate-http/src/main/java/com/xuanwu/cpaas/simulate/http/controller/DingYuController.java,cpaas-msg-hub/src/main/java/com/xuanwu/cpaas/msghub/constant/MessageTaskType.java

sonar-scanner -Dsonar.projectKey=CPAAS_cpaas_AYq7gWkdcNdOUVRcFiVe -Dsonar.host.url=http://10.20.121.41:30205 -Dsonar.login=sqp_302aba4b26fa3d6a3d1832c1140bbb67b423fda7 -Dsonar.java.source=1.8 -Dsonar.sourceEncoding=UTF-8 -Dsonar.exclusions=**/protobuf/** -Dsonar.caching.enabled -Dsonar.java.binaries=./target/classes -Dsonar.java.libraries=./**/*.jar -Dsonar.inclusions=cpaas-simulate-http/src/main/java/com/xuanwu/cpaas/simulate/http/controller/DingYuController.java,cpaas-msg-hub/src/main/java/com/xuanwu/cpaas/msghub/constant/MessageTaskType.java -Dsonar.modules=cpaas-msg-hub,cpaas-simulate-http
```

## sonar-project.properties
[https://www.devopsschool.com/tutorial/sonarqube/sonarqube-properties.html](https://www.devopsschool.com/tutorial/sonarqube/sonarqube-properties.html)
[https://dev.astrotech.io/sonarqube/sonarscanner.html](https://dev.astrotech.io/sonarqube/sonarscanner.html)
[https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/analysis-parameters/](https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/analysis-parameters/)
-Dsonar.inclusions=项目内的相对路径
 -Dproject.settings=../myproject.properties
使用mvn sonar:sonar仅读取mvn命令行参数或者是pom配置参数
[Sonar-project.properties and maven sonar:sonar goal](https://community.sonarsource.com/t/sonar-project-properties-and-maven-sonar-sonar-goal/3938)
[https://www.tabnine.com/code/java/methods/org.sonar.scanner.scan.ScanProperties/metadataFilePath](https://www.tabnine.com/code/java/methods/org.sonar.scanner.scan.ScanProperties/metadataFilePath)
### sonar.links.scm
[https://community.sonarsource.com/t/how-to-get-sonar-scm-url/26284/8](https://community.sonarsource.com/t/how-to-get-sonar-scm-url/26284/8)
sonar.links.scm is a property for setting the link to sources on Sonarqube project dashboard.
If you want to get this property from a Sonarqube project, you may use the web api
api/project_links/search
For Maven builds this property may be set via pom.xml and <scm><url>.
## sonar-report
sonar-scanner 废弃本地导出报告
[https://community.sonarsource.com/t/sonar-report-json-is-this-file-still-available/5827](https://community.sonarsource.com/t/sonar-report-json-is-this-file-still-available/5827)
[https://community.sonarsource.com/t/not-able-to-generate-sonarqube-report-in-json-format/61119/2](https://community.sonarsource.com/t/not-able-to-generate-sonarqube-report-in-json-format/61119/2)
sonar-gerrit也是基于api获取最新的analyze
[https://plugins.jenkins.io/sonar-gerrit/](https://plugins.jenkins.io/sonar-gerrit/)
sonarlint-插件可以预览结果，但是没有命令行
[https://community.sonarsource.com/t/can-i-run-sonarlint-check-from-command-line-without-sonarqube/35896/8](https://community.sonarsource.com/t/can-i-run-sonarlint-check-from-command-line-without-sonarqube/35896/8)
[https://stackoverflow.com/questions/35888330/how-to-get-the-sonar-report-json-file-created-with-sonarqube](https://stackoverflow.com/questions/35888330/how-to-get-the-sonar-report-json-file-created-with-sonarqube)
jq解析配置
[sonar-report-builder.jq.txt](https://www.yuque.com/attachments/yuque/0/2023/txt/23176849/1695787275917-f315f87d-e23b-4b96-b2e6-7109c4863ccb.txt?_lake_card=%7B%22src%22%3A%22https%3A%2F%2Fwww.yuque.com%2Fattachments%2Fyuque%2F0%2F2023%2Ftxt%2F23176849%2F1695787275917-f315f87d-e23b-4b96-b2e6-7109c4863ccb.txt%22%2C%22name%22%3A%22sonar-report-builder.jq.txt%22%2C%22size%22%3A843%2C%22ext%22%3A%22txt%22%2C%22source%22%3A%22%22%2C%22status%22%3A%22done%22%2C%22download%22%3Atrue%2C%22taskId%22%3A%22u605b4884-794d-4930-8e8c-4528e1fe663%22%2C%22taskType%22%3A%22upload%22%2C%22type%22%3A%22text%2Fplain%22%2C%22__spacing%22%3A%22both%22%2C%22mode%22%3A%22title%22%2C%22id%22%3A%22u0eaa644e%22%2C%22margin%22%3A%7B%22top%22%3Atrue%2C%22bottom%22%3Atrue%7D%2C%22card%22%3A%22file%22%7D)
## sonarqube api
[https://docs.sonarsource.com/sonarqube/9.9/extension-guide/web-api/](https://docs.sonarsource.com/sonarqube/9.9/extension-guide/web-api/)
生成认证token，请求加鉴权信息
[https://docs.sonarsource.com/sonarqube/9.8/user-guide/user-account/generating-and-using-tokens/#expiration-date-in-http-response](https://docs.sonarsource.com/sonarqube/9.8/user-guide/user-account/generating-and-using-tokens/#expiration-date-in-http-response)
[https://docs.sonarsource.com/sonarqube/9.8/extension-guide/web-api/](https://docs.sonarsource.com/sonarqube/9.8/extension-guide/web-api/)
taskid
[https://community.sonarsource.com/t/ant-quality-gate/41655/13](https://community.sonarsource.com/t/ant-quality-gate/41655/13)
sonar后在项目的./target/sonar/report-task.txt

![image.png](https://cdn.nlark.com/yuque/0/2023/png/23176849/1695828443371-e84bf642-735b-4da3-bb0e-6b82bf8b798c.png#averageHue=%232f3338&clientId=ud64b50d3-0e38-4&from=paste&height=367&id=u1a0965d4&originHeight=597&originWidth=264&originalType=binary&ratio=1.625&rotation=0&showTitle=false&size=25536&status=done&style=none&taskId=u48fe192b-3a7a-42da-9793-d85cd57aa99&title=&width=162.46153846153845)
```
projectKey=CPAAS_cpaas_AYq7gWkdcNdOUVRcFiVe
serverUrl=http://10.20.121.41:30205
serverVersion=9.6.0.59041
dashboardUrl=http://10.20.121.41:30205/dashboard?id=CPAAS_cpaas_AYq7gWkdcNdOUVRcFiVe
ceTaskId=AYrXE6SRcNdOUVRcFiZD
ceTaskUrl=http://10.20.121.41:30205/api/ce/task?id=AYrXE6SRcNdOUVRcFiZD
```
## sonar-cli
[SonarScanner CLI](https://docs.sonarcloud.io/advanced-setup/ci-based-analysis/sonarscanner-cli/)
容器中导入sonar-cli
[https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/ci-integration/codemagic-integration/](https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/ci-integration/codemagic-integration/)
[sonar-scanner的使用 - 捷后愚生 - 博客园](https://www.cnblogs.com/Uni-Hoang/p/15207178.html)
[https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/scanners/sonarscanner/](https://docs.sonarsource.com/sonarqube/latest/analyzing-source-code/scanners/sonarscanner/)

## scan Q&A
[https://www.jianshu.com/p/a388252af433](https://www.jianshu.com/p/a388252af433)


# maven 
[超级详细的 Maven 教程（基础+高级）_maven_Ayue、_InfoQ写作社区](https://xie.infoq.cn/article/77c75784ede87b54d30c2dde8) 
获取项目所有模块名字
```shell
 mvn -Dexec.executable='echo' -Dexec.args='${project.artifactId}' exec:exec -q | awk '{print $1}'| tr '\n' ','
```
#  curl

post file with curl
![image.png](https://cdn.nlark.com/yuque/0/2023/png/23176849/1695805297466-573ffca6-9bd1-4968-8139-273ca26a65c2.png#averageHue=%230f0b07&clientId=u857ac977-6269-4&from=paste&height=103&id=ufa32dccb&originHeight=103&originWidth=1490&originalType=binary&ratio=1&rotation=0&showTitle=false&size=22535&status=done&style=none&taskId=ud26246ea-6f0c-4f27-afda-3aab217515f&title=&width=1490)
[https://www.cnblogs.com/weiweirui/p/16930608.html](https://www.cnblogs.com/weiweirui/p/16930608.html)
[https://blog.filestack.com/api/step-step-guide-curl-upload-file/](https://blog.filestack.com/api/step-step-guide-curl-upload-file/)
 
 
 
# git 
## git diff

# 增量扫描
[https://github.com/yangziwen/diff-check/tree/master](https://github.com/yangziwen/diff-check/tree/master)
[Shell中将多行合并成一行的小技巧_shell把多行变成一行_杰瑞26的博客-CSDN博客](https://blog.csdn.net/Jerry_1126/article/details/82262634)
[git查看提交修改的文件列表_git log 查看修改了哪些文件_辛勤的摆渡人的博客-CSDN博客](https://blog.csdn.net/hunter168_wang/article/details/121497595)
[shell 脚本读取文件内容并输出--问题总结(编码问题)_shell脚本读取文件的特定行并输出内容_爱吃臭豆腐、的博客-CSDN博客](https://blog.csdn.net/qq_29473881/article/details/84101403)
waitCheckFiles=`git diff --name-only $PULL_REQUEST_TO_HASH $PULL_REQUEST_FROM_HASH | grep '\.java' | xargs printf '%s,'`

waitCheckFiles=`git diff --name-only $PULL_REQUEST_TO_HASH $PULL_REQUEST_FROM_HASH | grep '\.java' | xargs printf '%s,'`
git show --raw fb4f4deba996a4ff880b6c9b609a514cf2f2710c  | grep '\.java' | awk '{print $6}'| tr '\n' ','



# docker
查看镜像的dockerfile
[【docker】怎么查看docker镜像的dockerfile_docker history weblogic:latest_云川之下的博客-CSDN博客](https://blog.csdn.net/m0_45406092/article/details/119037604)
设置path使用cli 二进制工具
[https://juejin.cn/s/dockerfile%20%E8%AE%BE%E7%BD%AEpath](https://juejin.cn/s/dockerfile%20%E8%AE%BE%E7%BD%AEpath)
[docker环境变量设置_dockerfile env path-CSDN博客](https://blog.csdn.net/a12345676abc/article/details/84651477)
## ci tool image
[Dockerfile · master · GitLab CI Utils / Docker curl jq · GitLab](https://gitlab.com/gitlab-ci-utils/curl-jq/-/blob/master/Dockerfile?ref_type=heads)

# shell
读取文件内容并赋值string变量
[shell读取文件内容并进行变量赋值_shell 读取整个文件-CSDN博客](https://blog.csdn.net/smallnetvisitor/article/details/81285456)
[Linux教程 - 在Shell脚本中声明和使用布尔变量示例-腾讯云开发者社区-腾讯云](https://cloud.tencent.com/developer/article/1770351)
退出状态码
[Shell退出状态码及其应用详解 - 编程教程](http://www.17bigdata.com/study/programming/it-shell/it-shell-201643.html)
[Shell exit命令：退出当前进程](http://c.biancheng.net/view/1145.html)
判断字符串开头
[Shell判断字符串是否以某些字符开头 - 卡洛小豆 - 博客园](https://www.cnblogs.com/tudou1179006580/p/14875527.html)
[shell中if条件字符串、数字比对，[[ ]]和[ ]区别_shell 字符串比较 返回0-CSDN博客](https://blog.csdn.net/qq_28513801/article/details/88979311)
[shell脚本----if（数字条件，字符串条件，字符串为空）-CSDN博客](https://blog.csdn.net/yf210yf/article/details/9207147)
[Linux Shell 之 Shell 基本控制结构（一）（if and case）_shell if and-CSDN博客](https://blog.csdn.net/xy010902100449/article/details/48934423)

shell不同解析器的内置方法函数不同
![image.png](https://cdn.nlark.com/yuque/0/2023/png/23176849/1697095504439-5ef4db1b-2fed-492c-934d-0993b789a440.png#averageHue=%23626261&clientId=u2d890396-e363-4&from=paste&height=181&id=ub531e5eb&originHeight=181&originWidth=632&originalType=binary&ratio=1&rotation=0&showTitle=false&size=8511&status=done&style=none&taskId=u9d67f41a-5587-43d0-b015-7866ef5df72&title=&width=632)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/23176849/1697095513141-0c1d9554-8d44-4b64-8ac1-440ea745022b.png#averageHue=%232b2b2b&clientId=u2d890396-e363-4&from=paste&height=139&id=u1e4db4ed&originHeight=139&originWidth=564&originalType=binary&ratio=1&rotation=0&showTitle=false&size=9515&status=done&style=none&taskId=ufa623658-1eb0-456c-832f-f82426fc14c&title=&width=564)
[https://unix.stackexchange.com/questions/17727/why-does-my-shell-script-give-the-error-declare-not-found](https://unix.stackexchange.com/questions/17727/why-does-my-shell-script-give-the-error-declare-not-found)

字符串、数组变量
[Shell 数组 | 菜鸟教程](https://www.runoob.com/linux/linux-shell-array.html)
[shell脚本——字符串 数组_shell脚本字符串数组-CSDN博客](https://blog.csdn.net/weixin_42167759/article/details/80702517)
[Linux下Shell脚本字符串单引号、双引号、反引号、反斜杠的作用和区别-CSDN博客](https://blog.csdn.net/andyguan01_2/article/details/90901338)
## shell 数值操作
声明数值类型
[shell基础-bash变量-数值运算与运算符-CSDN博客](https://blog.csdn.net/lamp_yang_3533/article/details/70041211)
随机数生成
[shell随机数生成的几种方法 - Gavin的博客 | Gavin Blog](https://gavin-wang-note.github.io/2020/07/01/generate_random_number_in_shell/)
数值运算
[shell学习八-----变量数值计算(())-CSDN博客](https://blog.csdn.net/yujin2010good/article/details/76863183)
## shell字符串
[shell判断一个变量是否为空方法总结-腾讯云开发者社区-腾讯云](https://cloud.tencent.com/developer/article/1721905)
[关于shell条件判断中变量用”″与不用的区别_unknown operand-CSDN博客](https://blog.csdn.net/cao_ni_mei2015/article/details/105945403)
[https://blog.csdn.net/stpeace/article/details/78343547](https://blog.csdn.net/stpeace/article/details/78343547)
[Shell字符串拼接（连接、合并）](http://c.biancheng.net/view/1114.html)
打印文件指定行
[Linux 打印文本部分行内容（前几行，指定行，中间几行，跨行，奇偶行，后几行，最后一行，匹配行） - 叨叨软件测试 - 博客园](https://www.cnblogs.com/daodaotest/p/13277208.html)
替换字符串的分隔符
[Shell_Linux Shell 中实现字符串切割的几种方法_shell split string-CSDN博客](https://blog.csdn.net/u010003835/article/details/80750003)
[2. 详解awk当中的分隔符，输入分隔符，输出分隔符_51CTO博客_awk多个分隔符分隔](https://blog.51cto.com/zaishu/5137309)
删除字符串指定字符
[shell删除字符串中的指定字符-掘金](https://juejin.cn/s/shell%E5%88%A0%E9%99%A4%E5%AD%97%E7%AC%A6%E4%B8%B2%E4%B8%AD%E7%9A%84%E6%8C%87%E5%AE%9A%E5%AD%97%E7%AC%A6)
[Nginx 安装配置 | 菜鸟教程](https://www.runoob.com/linux/nginx-install-setup.html)
判断字符串的包含关系：
[Shell判断字符串包含关系的几种方法_shell 筛选字符串-CSDN博客](https://blog.csdn.net/iamlihongwei/article/details/59484029)
[Shell：判断字符串是否包含某个子串_shell判断字符串是否包含子串_小小平不平凡的博客-CSDN博客](https://blog.csdn.net/sinat_34241861/article/details/121456227)
shell 控制结构退出
[【8】shell：跳出循环 continue、break、continue、return、exit_shell跳出 break-CSDN博客](https://blog.csdn.net/focus_lyh/article/details/112319193)

```shell

string=cpaas-channel-hub/src/main/java/com/xuanwu/cpaas/channelhub/service/SubChannelService.java,cpaas-channel-hub/src/main/java/com/xuanwu/cpaas/channelhub/service/impl/ChannelServiceImpl.java,cpaas-channel-hub/src/main/java/com/xuanwu/cpaas/channelhub/service/impl/SubChannelServiceImpl.java,cpaas-channel-hub/src/main/java/com/xuanwu/cpaas/channelhub/service/thirdparty/config/ChannelConfigAggregationService.java,cpaas-channel-hub/src/main/java/com/xuanwu/cpaas/channelhub/service/thirdparty/config/impl/ChannelConfigAggregationServiceImpl.java,
s=$(echo "$string" | tr ',' ' ')
```

文件名和路径的提取
[Linux shell中提取文件名和路径 - 鲁娜的博客 | Luna’s Blog](https://dulunar.github.io/2019/11/08/Linux-shell%E4%B8%AD%E6%8F%90%E5%8F%96%E6%96%87%E4%BB%B6%E5%90%8D%E5%92%8C%E8%B7%AF%E5%BE%84/)

shell 多行命令需要左空格
[linux参数太长续行，linux shell 参数换行（标准说法：续行）_bash 命令 换行-CSDN博客](https://blog.csdn.net/hunanchenxingyu/article/details/45047813)
## shell睡眠
[Bash Sleep – How to Make a Shell Script Wait N Seconds (Example Command)](https://www.freecodecamp.org/news/bash-sleep-how-to-make-a-shell-script-wait-n-seconds-example-command/)

# linux 
## 磁盘管理-查看
显示当前目录下深度为1文件占用
```shell
du -d 1 -h
```

[df、du、fdisk：Linux磁盘管理 - 莫水千流 - 博客园](https://www.cnblogs.com/zhoug2020/p/5609220.html)
## 文件排序
[https://blog.csdn.net/moudaen/article/details/15813397](https://blog.csdn.net/moudaen/article/details/15813397)
## 文件搜索
[Linux find 命令 | 菜鸟教程](https://www.runoob.com/linux/linux-comm-find.html)

## nfs 相关命令
[linux查看nfs共享目录的内容-掘金](https://juejin.cn/s/linux%E6%9F%A5%E7%9C%8Bnfs%E5%85%B1%E4%BA%AB%E7%9B%AE%E5%BD%95%E7%9A%84%E5%86%85%E5%AE%B9)

## linux标准输入输出
2>&1
[https://segmentfault.com/a/1190000040086046](https://segmentfault.com/a/1190000040086046)
## linux 命令执行顺序
[Linux不管上一条命令成功还是失败都执行下一个命令的方法-CSDN博客](https://blog.csdn.net/suyues/article/details/100062812)
```yaml
              command: [ "/bin/sh" ]
              args: [ "-c",
                      "echo $(kubectl -n cpaas-cicd delete -f /home/cpaas.yaml);kubectl -n cpaas-cicd apply -f /home/cpaas.yaml",
              ]
```
[https://stackoverflow.com/questions/33887194/how-to-set-multiple-commands-in-one-yaml-file-with-kubernetes](https://stackoverflow.com/questions/33887194/how-to-set-multiple-commands-in-one-yaml-file-with-kubernetes)

# curl
[3分钟短文 | Linux 使用curl发起post请求的4个常用方式-腾讯云开发者社区-腾讯云](https://cloud.tencent.com/developer/article/1669557)
[Attention Required! | Cloudflare](https://reqbin.com/req/c-sma2qrvp/curl-post-form-example)
在curl 传输变量需要转义
[https://blog.csdn.net/weixin_42808782/article/details/125296518](https://blog.csdn.net/weixin_42808782/article/details/125296518)
使用curl表单发送文件加请求
[https://blog.csdn.net/fungleo/article/details/80703365](https://blog.csdn.net/fungleo/article/details/80703365)
[https://blog.csdn.net/freedomwjx/article/details/43278157](https://blog.csdn.net/freedomwjx/article/details/43278157)
[https://blog.csdn.net/qq_32743943/article/details/102608101](https://blog.csdn.net/qq_32743943/article/details/102608101)
[https://reqbin.com/req/c-sma2qrvp/curl-post-form-example](https://reqbin.com/req/c-sma2qrvp/curl-post-form-example)
upload文件路径
[https://blog.csdn.net/qq_14997473/article/details/115112189](https://blog.csdn.net/qq_14997473/article/details/115112189)
# iris
接受表单

# vim 
delete 所选范围文本
[在Vim/Vi中删除行、多行、范围、所有行及包含模式的行-腾讯云开发者社区-腾讯云](https://cloud.tencent.com/developer/article/1838332)
# 操作系统环境变量path
[环境变量基本操作及path环境变量_环境变量path_渌玦Leo_J的博客-CSDN博客](https://blog.csdn.net/weixin_45072139/article/details/94987680)

# k8s
使cli工具镜像持续运行
[在Kubernetes集群上如何保持容器一直运行](https://lyyao09.github.io/2019/08/13/stack/How-can-I-keep-a-container-running-on-Kubernetes/)
[docker run 如何让容器启动后不会自动停止](https://jerrymei.cn/docker-container-run-not-stop-automatically/)
否则，启动容器成功，立马就退出
[Exit Codes in Containers & Kubernetes | Complete Guide | Komodor](https://komodor.com/learn/exit-codes-in-containers-and-kubernetes-the-complete-guide/)
pod挂载pvc
[kubernetes系列教程（十）深入学习持久化存储PV和PVC-腾讯云开发者社区-腾讯云](https://cloud.tencent.com/developer/article/1520039)
pod的时间与主机保存一致
[pod时间时区与node主机保持一致_pod时间同步_Locutus的博客-CSDN博客](https://blog.csdn.net/yjk13703623757/article/details/116062676)
修改configmap，配置热更新
[https://jimmysong.io/kubernetes-handbook/concepts/configmap-hot-update.html](https://jimmysong.io/kubernetes-handbook/concepts/configmap-hot-update.html)
cron job的调度cron时区基于k8s api server的时区
容器启动执行script脚本
[https://kubernetes.io/zh-cn/docs/tasks/inject-data-application/define-command-argument-container/](https://kubernetes.io/zh-cn/docs/tasks/inject-data-application/define-command-argument-container/)
网络-域名解析、服务发现、外部访问
[https://marcuseddie.github.io/2021/K8s-Network-Architecture-section-two.html](https://marcuseddie.github.io/2021/K8s-Network-Architecture-section-two.html)
# go 
条件语句switch：
[https://www.runoob.com/go/go-switch-statement.html](https://www.runoob.com/go/go-switch-statement.html)

1. 不需要break
2. 可以type-switch判断类型
3. 增加fallthrough

使用匿名struct
[https://segmentfault.com/a/1190000041102008](https://segmentfault.com/a/1190000041102008)
string <->int互相转换
[golang 中string和int类型相互转换_golang string 转int-CSDN博客](https://blog.csdn.net/iamlihongwei/article/details/79550958)
string截取
[go语言怎么删除字符串字符-Golang-PHP中文网](https://www.php.cn/faq/498921.html)
[strings — 字符串操作 · Go语言标准库](https://books.studygolang.com/The-Golang-Standard-Library-by-Example/chapter02/02.1.html)
const常量
[https://learnku.com/articles/44095](https://learnku.com/articles/44095)
[https://juejin.cn/s/golang%20const%20structure](https://juejin.cn/s/golang%20const%20structure)
xml 解析
1.将xml文件解析为byte数组，直接使用xml解码
[49. XML 解析 |《Go 编程实例 Go by Example 2020》| Go 技术论坛](https://learnku.com/docs/gobyexample/2020/xml-analysis/6300)
[Parse and generate XML easily in golang](https://golangexample.com/parse-and-generate-xml-easily-in-golang/)
[Go解析xml,Go xml struct ,Go xml 转数组-阿里云开发者社区](https://developer.aliyun.com/article/873498)
[Go 入门很简单：读取和解析 XML 文件_51CTO博客_go语言解析xml](https://blog.51cto.com/yuzhou1su/5165546)
[go解析xml的三种方式 - bartggg - 博客园](https://www.cnblogs.com/bartggg/p/13067153.html)
read file to byte array
[Golang program to convert file to byte array](https://www.tutorialspoint.com/golang-program-to-convert-file-to-byte-array)
临时文件、目录
[https://gobyexample-cn.github.io/temporary-files-and-directories](https://gobyexample-cn.github.io/temporary-files-and-directories)
时间戳
[https://www.sdk.cn/details/d591E8oY9X7M67veZz](https://www.sdk.cn/details/d591E8oY9X7M67veZz)
## go 并发
获取go协程Id
[https://hikoqiu.github.io/posts/zh/2016/04/huoqugoroutine_id_tech.html](https://hikoqiu.github.io/posts/zh/2016/04/huoqugoroutine_id_tech.html)
go锁
[https://studygolang.com/articles/11703](https://studygolang.com/articles/11703)
go协程基本使用
[https://www.runoob.com/go/go-concurrent.html](https://www.runoob.com/go/go-concurrent.html)
协程睡眠
[https://blog.csdn.net/whatday/article/details/102637905](https://blog.csdn.net/whatday/article/details/102637905)
[https://www.jb51.net/article/268321.htm](https://www.jb51.net/article/268321.htm)


# java
jvm 参数 g1cg优化
[https://blog.csdn.net/Axela30W/article/details/106307548](https://blog.csdn.net/Axela30W/article/details/106307548)
[https://www.cnblogs.com/redcreen/articles/2037057.html](https://www.cnblogs.com/redcreen/articles/2037057.html)
[https://blog.csdn.net/Dax1n/article/details/77163540](https://blog.csdn.net/Dax1n/article/details/77163540)

# maven
## 多模块打包
指定构建模块
```shell
#仅构建cpaas-msg-hub并跳过测试
mvn install -pl cpaas-msg-hub  -Dmaven.test.skip=true
mvn install -pl cpaas-msg-hub,  -Dmaven.test.skip=true
#构建父项目并构建cpaas-msg-hub,sonar 扫描需要父pom的配置信息
mvn install -pl .,cpaas-msg-hub  -Dmaven.test.skip=true
```
对于顶层pom的第2级的module不可以直接使用-pl打包构建；可以在顶层pom显式申明该module![image.png](https://cdn.nlark.com/yuque/0/2023/png/23176849/1697098016790-1584c10c-6e13-4820-9c3f-8a0a7c5591d7.png#averageHue=%2322272e&clientId=u2d890396-e363-4&from=paste&height=127&id=u5b2bb15c&originHeight=127&originWidth=671&originalType=binary&ratio=1&rotation=0&showTitle=false&size=22530&status=done&style=none&taskId=ue74258ba-1b29-4f3a-a097-57dc46738ad&title=&width=671)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/23176849/1697097706241-c4feae56-63c9-4df0-925e-67d6a3995998.png#averageHue=%23141414&clientId=u2d890396-e363-4&from=paste&height=68&id=u42f75ee8&originHeight=68&originWidth=981&originalType=binary&ratio=1&rotation=0&showTitle=false&size=2606&status=done&style=none&taskId=u0e5cd1c8-ea2c-4f0f-b942-9876a29a732&title=&width=981)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/23176849/1697097724055-0473dfde-73a4-4090-8205-3b178991d5d9.png#averageHue=%231a1717&clientId=u2d890396-e363-4&from=paste&height=157&id=ub84216a5&originHeight=157&originWidth=1005&originalType=binary&ratio=1&rotation=0&showTitle=false&size=9338&status=done&style=none&taskId=u11a5f16b-c62d-461b-87fc-cfbfbeafe37&title=&width=1005)
![image.png](https://cdn.nlark.com/yuque/0/2023/png/23176849/1697098034866-12eb2398-f8ad-4217-95ae-de2d9f7089cd.png#averageHue=%23131313&clientId=u2d890396-e363-4&from=paste&height=143&id=u653976b0&originHeight=143&originWidth=687&originalType=binary&ratio=1&rotation=0&showTitle=false&size=4537&status=done&style=none&taskId=uc8679561-5d27-40b9-986e-b33e669341b&title=&width=687)
其实-pl后跟的项目的对于root的目录而非artifactId
![image.png](https://cdn.nlark.com/yuque/0/2023/png/23176849/1697100077122-b31e05f1-8d62-4964-bad9-e1fc6703c4fe.png#averageHue=%23131313&clientId=u2d890396-e363-4&from=paste&height=66&id=u8bd8d85b&originHeight=66&originWidth=992&originalType=binary&ratio=1&rotation=0&showTitle=false&size=2728&status=done&style=none&taskId=u3fa4530c-7394-45d3-b722-0834037e436&title=&width=992)
[https://segmentfault.com/q/1010000021576084](https://segmentfault.com/q/1010000021576084)

## 获取项目中所有module
```shell
 mvn -Dexec.executable='echo' -Dexec.args='${project.artifactId}' exec:exec -q | awk '{print $1}'| tr '\n' ','
```
![企业微信截图_16957974895563.png](https://cdn.nlark.com/yuque/0/2023/png/23176849/1697098757345-3692fc97-39af-4d55-a32e-a5dd6f8f0ed5.png#averageHue=%230a0806&clientId=u2d890396-e363-4&from=paste&height=150&id=uae6ab551&originHeight=150&originWidth=1037&originalType=binary&ratio=1&rotation=0&showTitle=false&size=15529&status=done&style=none&taskId=ufa89277f-7211-4e48-96bd-c8e2a0d410e&title=&width=1037)

## 结合git 打包更新的module
```shell
mvn package -Dmaven.test.skip=true -pl $( git show --raw commitId| grep '\.java'| awk '{print $6}' | awk -F '/src' '{print $1}' | sort | uniq |tr '\n' ',')

```
