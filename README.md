# base-js

通用 js base 部分, 由 @common-ui 组维护

## changelog

1.考虑 1.9 太多 API 的改变, IE6-8 仍然基于 1.8.3; 其他浏览器基于最新稳定版 2.0.3

# Modules

[jQuery 2.0.3](https://github.com/jquery/jquery/tree/2.0.3)(-sizzle)[size: 67101] / [jQuery 1.8.3](https://github.com/jquery/jquery/tree/1.8.3)(full)

jQuery-ui

[UT](http://gitlab.pro/common-ui/ut) @liangdongjie @yuji

[helper](http://gitlab.pro/common-ui/helper) @liangdongjie @yuji

[localstorage](http://gitlab.pro/common-ui/localstorage) @liangdongjie @fengkun

[localcookie](http://gitlab.pro/common-ui/localcookie) @liangdongjie @fengkun

[eventcenter](http://gitlab.pro/common-ui/eventcenter) @liangdongjie @yuji (待补...)

# USAGE

clone 项目代码:

```shell
# clone 
git clone http://gitlab.pro/common-ui/base-js.git
cd base-js

# 初始化子模块
git submodule init

# 更新子模块
git submodule update
```

在页面中使用:

```
<!--[if lt IE 9]>
    <script src="base.ie.js"></script>
<![endif]-->
<!--[if gte IE 9]><!-->
    <script src="base.js"></script>
<!--<![endif]-->
```

## base-js 库维护

1. 新增子模块

`git submodule add http://gitlab.pro/common-ui/helper.git src/helper`

2. 移除子模块

`git rm src/helper`

3. 更新子模块

`git pull && git submodule update`

4. 重新编译输出

`grunt build`

> 涉及到子模块增减时, 修改 Gruntfile.js 以得到正确打包输出

## 相关模块维护

建议模块归属于 common-ui 组, 独立 `repo`, 由专人维护

common-ui owner 组成员可以直接 `commit` -> `master`

其余同学需要 `fork` -> `pull request` 到 common-ui 后, 由 owner 组成员审核 merge

**note** master 分支永远是 `deploy` 状态, 每次升级前创建 tag, 以便回滚

### owner 组成员职责

- 跟进 `issues` assignee 到相关责任人

- 审核 `pull request`

- 收录 / 移除 `submodule`

### 其他研发同学职责

- `fork` 进行开发, `pull request`

- 提交 `issues`

### jQuery BUILD

`cd src/jquery`

`git checkout 2.0.3`

`npm i`

`grunt custom:-sizzle dist:../../dist/2.0.3`

all: 83649

-sizzle: 16727

依赖 sizzle:

css/hiddenVisibleSelectors, effects/animatedSelector

其他模块, 可能被移除的模块收益都很小, 故全部保留:

-exports/amd: 54
-core/ready: 617
--deprecated: 83606

> ref
http://projects.jga.me/jquery-builder/