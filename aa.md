

# git规范

## 分支管理

### master/main 分支

> 主分支，永远处于稳定状态，对应当前线上版本
>
> 以 `tag` 标记一个版本，因此 `master/main` 分支上看到的每一个 `tag` 都应该对应一个线上版本
>
> master/main 分支一般由`develop`和`hotfix`分支合并，任何时间都不允许在该分支上直接提交代码

### develop分支

> 开发分支，始终保持最新完成以及bug修复后的代码，包含了项目最新的功能和代码，所有开发都依赖`develop`分支进行, 一般开发新功能时， `feature分支都是基于develop分支创建`。
>
> 推荐：`develop`分支作为开发主分支，也不允许直接提交代码，小改动也应该以`feature/`分支提 `merge request` 合并，目的是保证每个改动都经过了强制代码 review，降低代码风险

### feature 分支

> 分支名称以`feature/`开头的为特性分支，例如：`feature/user_module`、`feature/cart_module`  
>
> 开发新功能时，以`develop`为基础切出`feature`分支  ，开发完成后合并回`develop`分支，并且删除`feature`分支

### release 分支

> 发布分支，新功能合并到 develop 分支，准备发布新版本时使用的分支, **预发布**
>
> 准备发布新版本时或者进入提测时，会创建release分支如果测试过程中若存在bug需要修复，则直接由开发者在release分支修复并提交。当测试完成之后，合并release分支到master和develop分支，此时master为最新代码，用作上线

## commit message规范

**commit message格式：**  

>\<type\>(<scope>): \<subject\> 
>
>// 空一行 
>
>\<body\> 
>
>// 空一行
>
>\<footer\>
>
>分别对应 Commit message 的三个部分：`Header`，`Body` 和 `Footer`；其中，`Header` 是必需的，`Body` 和 `Footer` 可以省略。

**Header:** Header 部分只有一行，包括三个字段：`type`（必需）、`scope`（可选）和`subject`（必需）。

| type     | 说明                                        |
| -------- | ------------------------------------------- |
| feat     | 新功能(feature)                             |
| fix      | 修复bug                                     |
| docs     | 仅仅修改了文档，如：readme.md               |
| style    | 格式(不影响代码运行的变动)                  |
| refactor | 重构(不是新增功能，也不是修改bug的代码变动) |
| perf     | 优化相关，如提升性能、用户体验相关          |
| test     | 测试用例，包括单元测试、集成测试            |
| chore    | 改变构建流程、或者添加依赖库、工具等        |

**scope:** 用于 commit 影响的范围，比如 数据层、控制层、视图层等等，视项目不同而不同  

**subject:** commit 目的的简短描述  

**body:** 对本次commit 修改内容的具体描述，可以分为多行，要求在72个字符以内，主要包括：

- 为什么需要此更改
- 怎么解决这个问题
- 是否对项目有其他副作用
- 提交次数

**footer:** 只用于两种情况：

- 一些备注，通常是 `BREAKING CHANGE(当前代码与上个版本不兼容)`
- 修复的bug(关闭 Issue) 的链接

