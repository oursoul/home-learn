### 一、项目搭建

#### 1.editorConfig

> 背景：windows 回车和 mac 回车可能不一样，编辑器不一样（vscode,webstorm 默认缩进)，
> 提交到代码仓库的风格也不一致，

新建.editroconfig 文件(**参考 vue 项目**)

```
# https://editorconfig.org

root = true

[*]
charset = utf-8
indent_style = space
indent_size = 2
end_of_line = lf
insert_final_newline = true
trim_trailing_whitespace = true

[*.md]
insert_final_newline = false
trim_trailing_whitespace = false

```

#### 2.prettier 工具

> 即使不用 vscode 也可以用*prettier*，可以使用一个 prettier 包

-D 表示是开发时依赖

```
npm i prettier -D
```

新建 .prettierrc 文件 添加一下代码：

```
{
  "useTabs": false,
  "tabWidth": 2,
  "printWidth": 80,
  "singleQuote": true,
  "trailingComma": "none",
  "semi": false
}
```

新建.prettierignore 文件，忽略一些文件

```
# Ignore artifacts:
/dist/*
.local
.output.js
/node_modules/**

**/*.svg
**/*.sh

/pubilc/*
```

vscode 添加 prettier 插件，为了解决每个文件都需要 ctrl+s 保存后格式化很繁琐的问题，在 package.json 文件，添加命令行：

```
"prettier" : prettier --write
```

#### 3.兼容 eslint 和 prettier

> 安装 eslint

```
npm i eslint-config-prettier eslint-plugin-prettier -D
```

在.eslintrc.js 中 extends 项 添加
plugin:prettier/recommended

#### 4.git 提交代码前的 eslint fix

> git commit -m "" 这一步之前做一些校验操作

使用 git husky 工具(需要初始化 git 仓库)

```
npx husky-init
npm i
```

查看 pre-commit 文件
