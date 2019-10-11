---
title: 工作笔记-通过REST API创建Jenkins Credentials
date: 2019-10-11 23:48:30
category: 工作笔记
tags:
- Jenkins
- credential
- REST API
---

1. 准备创建Credential的模板

    创建文件credential.xml，内容如下：

    ```(xml)
    <com.cloudbees.plugins.credentials.impl. UsernamePasswordCredentialsImpl>
        <scope>GLOBAL</scope>
        <id>my-credentials-example-id</id>
        <description>This is an example from REST API</description>
        <username>admin</username>
        <password>
            <secret-redacted/>
        </password>
    </com.cloudbees.plugins.credentials.impl. UsernamePasswordCredentialsImpl>
    ```

2. 将模板通过POST请求发从到 `$JENKINS_URL/<path to context>/credentials/store/<store id>/domain/<domain name>/createCredentials` 
3. 准备更新Credential的模板

    创建文件updateCredential.xml，内容如下：

    ```(xml)
    <com.cloudbees.plugins.credentials.impl.UsernamePasswordCredentialsImpl>
        <scope>GLOBAL</scope>
        <id>my-credentials-example-id</id>
        <description>This is an example from REST API (updated)</description>
        <username>admin</username>
        <password>newsupersecret</password>
    </com.cloudbees.plugins.credentials.impl.UsernamePasswordCredentialsImpl>
    ```

4. 发送POST请求更新Credential

    ```(shell)
    curl -X POST \
    -u $JENKINS_USER:$JENKINS_PASSWORD_OR_API_TOKEN \
    -H "Jenkins-Crumb:${JENKINS_CRUMB}" \
    -H 'content-type:application/xml' \
    -d @updatedCredential.xml \
    "$JENKINS_URL/<path to context>/credentials/store/<store id>/domain/<domain name>/credential/my-credentials-example-id/config.xml"
    ```

参考：<https://support.cloudbees.com/hc/en-us/articles/360030526992-How-to-manage-Credentials-via-the-REST-API>
