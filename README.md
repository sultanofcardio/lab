# Lab

[![CI](https://github.com/Ackerr/lab/workflows/CI/badge.svg)](https://github.com/Ackerr/lab)
[![Go Report Card](https://goreportcard.com/badge/github.com/ackerr/lab)](https://goreportcard.com/report/github.com/ackerr/lab)
[![release](https://img.shields.io/github/v/release/ackerr/lab.svg)](https://github.com/ackerr/lab/releases)

关于GitLab的命令行工具

## 功能

```
lab config   快捷打开lab的配置文件
lab sync     同步gitlab项目至本地
lab browser  模糊搜索项目名, 回车后，默认浏览器中打开项目地址
lab open     快捷在默认浏览器中打开当前所在项目的web地址
lab clone    模糊搜索项目名, 如果设置了codespace, 会将项目clone至codespace，
             否则在当前目录，当然也可以通过--current(-c)，clone至当前路径
lab ci       获取当前项目指定远端分支的ci日志
```

> 通过 `lab help` 查看lab更多命令及其参数

## 安装

### homebrew

```bash
$ brew install ackerr/tap/lab
```

### scoop

```bash
$ scoop bucket add ackerr https://github.com/Ackerr/scoop-bucket
$ scoop install ackerr/lab
```

### go get

```bash
$ go get -u "github.com/ackerr/lab"
```

## 配置

在首次使用`lab config`时，会默认生成配置文件，配置文件如下

```
[gitlab]
base_url  = $GITLAB_BASE_URL
token     = $GITLAB_TOKEN

codespace = ""
name      = ""
email     = ""

[main]
fzf       = 0    # 是否使用系统fzf
theme_color      = "79" # 主题色，支持hex值或0-256
tail_line_number = "30" # 默认tail number
```

> 根据功能分为 gitlab 与 main 两个部分，添加时需要注意


base_url 与 token 为必填项，其余配置均为选填。token获取方式可参考[链接](https://docs.gitlab.com/ee/user/profile/personal_access_tokens.html#creating-a-personal-access-token)。

在使用`lab clone`时
- 设置name和email，会默认为项目设置git user.name以及user.email
- 设置codespace，会将项目clone至codespace路径中，并使用结构化目录展示, 例如clone ackerr/ackerr 则会克隆至`$CODESPACE/$GITLAB_BASE_URL/ackerr/ackerr`
