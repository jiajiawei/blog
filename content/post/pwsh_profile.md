---
title: "pwsh中使用zsh的git插件"
date: 2022-09-14T23:00:30+08:00
draft: false
categories: ["杂技浅尝"]
---

用过一段时间 **zsh**， 里面的 **git** 插件简写实在太好用。 后来想 **pwsh** 能不能也干这个事， 其实可以的！

## 1. **pwsh** 中执行`code $profile`

该命令会通过 **vscode** 打开 **C:\Users\\{username}\Documents\PowerShell\Microsoft.PowerShell_profile.ps1** 文件，没有的话会自动创建。 里面内容粘贴如下：

```pwsh
function gaa{
    git add --all
}

function gcam($msg){
    git commit -a -m $msg
}
```

## 2. 保存文件并测试

重新在原来的 **pwsh** 窗口，使用 `gaa`， `gcam "修改配置文件"` 即可像zsh中是git插件一样， 快速git。。。


### 以下附上我常用的一些命令

```pwsh
function proxy {
    $env:HTTP_PROXY = "http://localhost:10809"
    $env:HTTPS_PROXY = "http://localhost:10809"
}
function noproxy {
    $env:HTTP_PROXY = ""
    $env:HTTPS_PROXY = ""
}
function glum{
    git pull upstream master
}
function gcmm{
    git checkout master
    git pull upstream master
}
function gco($branch_name){
    git checkout $branch_name
}
Remove-Item alias:\gcb
function gcb($branch_name){
    git checkout -b $branch_name
}
function grbm{
    git rebase master
}
function grbc{
    git rebase --continue
}
function grba{
    git rebase --abort
}
function gaa{
    git add --all
}
function gl{
    git pull
}
function gp{
    git push
}
function glo{
    git log --oneline --decorate
}
function glog{
    git log --oneline --decorate --graph
}
function gloga{
    git log --oneline --decorate --graph --all
}
function gst{
    git status
}
function gstu{
    git stash --include-untracked
}
function gstp{
    git stash pop
}
function ggf{
    $current_branch = git rev-parse --abbrev-ref HEAD
    git push --force origin $current_branch
}
function grv{
    git remote -v
}
function gcn!{
    git commit -v --no-edit --amend
}
function gcam($msg){
    git commit -a -m $msg
}
function gcamm(){
    git commit -a -m "暂存"
}
function grh1(){
    git reset HEAD~1
}
function grh2(){
    git reset HEAD~2
}
function grh3(){
    git reset HEAD~3
}
function ggg($branch_name， $msg){
    git checkout -b $branch_name
    git add --all
    git commit -a -m $msg' #'$branch_name
    
    $current_branch = git rev-parse --abbrev-ref HEAD
    git push --force origin $current_branch
}
function gggr(){
    $current_branch = git rev-parse --abbrev-ref HEAD
    git checkout master
    git pull upstream master
    git checkout $current_branch
    git rebase master
}
function flpg{
    flutter pub get
}
function flbw{
    flutter build windows
}
function flc{
    flutter clean
}
```