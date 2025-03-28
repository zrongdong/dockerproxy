# Docker代理

这里主要解决的问题是在国内经常pull docker很慢或者直接失败。

国内又没有稳定的代理工具，动不动就被封了。

这里通过github的Actions打包image，推送到你的阿里云账号，然后你再从阿里云账号拉取镜像。

虽然过程有点繁琐，但是好在全自动，而且稳定。


## 你需要配置一下变量

| 变量名           | 示例                              | 说明                     |
| ---------------- | --------------------------------- | ------------------------ |
| DOCKER_REGISTRY  | registry.cn-shenzhen.aliyuncs.com | 阿里云镜像仓库地址       |
| DOCKER_IMAGENAME | you_name/docker_proxy             | 阿里云镜像名称           |
| DOCKER_USERNAME  | user_name                         | 阿里云镜像仓库登录用户名 |
| DOCKER_PASSWORD  | paxxxxx                           | 阿里云镜像仓库登录密码   |

## 步骤一

修改Dockerfile文件

```dockerfile
# 拉取镜像
FROM xuxueli/xxl-job-admin:2.5.0
```



## 步骤二

打tag并推送(以下是示例)

```sh
# 提交文件修改
git add . && git commit -m "deploy" && git push origin master
# 提交tag
git tag xxl-job-admin-v2.5.0 && git push origin xxl-job-admin-v2.5.0
```

## 步骤三

等待运行完成
