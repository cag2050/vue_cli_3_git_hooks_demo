### vue-cli 3 安装选项:
1. Babel, Router（history mode）, Vuex, CSS Pre-processors（Stylus）, Linter（ESLint + Standard config、Lint and fix on commit），placing config（In dedicated config files）
2. `Lint and fix on commit`不是我喜欢的，我更喜欢`lint on save`
3. 此项目选择的：`ESLint + Standard config`，没有选择`ESLint + Prettier`，

### 此项目实现的功能：
1. git commit 时，进行代码格式化。比如：js中用了双引号，commit 时，会被修改为符合 eslint 规范的单引号。
2. 检查 commit 信息文案是否合规。不符合规则，无法提交代码；commit 信息文案规范，commitlint.config.js 中 rules.type-enum 指定的关键字加上英文冒号再加空格，然后写具体文案，比如：`fix: 具体文案`

### 实现步骤
1. 安装所需模块：
`npm install lint-staged @commitlint/cli @commitlint/config-conventional --save-dev`
2. package.json 添加如下代码：
```
    "gitHooks": {
        "commit-msg": "commitlint -E GIT_PARAMS",
        "pre-commit": "lint-staged"
    }
```
3. 添加文件：.lintstagedrc、commitlint.config.js。

### vue cli 3 查看项目 vue.config.js 的默认配置信息
1. 运行命令，在终端输出：
```npx vue-cli-service inspect```
2. 运行命令，将输出导入到文件：`vue.config.detail.js`：
```npx vue-cli-service inspect >> vue.config.detail.js```
3. 在文件：`vue.config.detail.js` 开头，添加：`module.exports = `，然后格式化即可查看。

### .lintstagedrc 配置
`prettier-eslint --write`含义：
1. https://github.com/okonet/lint-staged#reformatting-the-code
```Tools like Prettier, ESLint/TSLint, or stylelint can reformat your code according to an appropriate config by running prettier --write/eslint --fix/tslint --fix/stylelint --fix. After the code is reformatted, we want it to be added to the same commit.```
2. https://prettier.io/docs/en/cli.html#write
```--write：This rewrites all processed files in place. This is comparable to the eslint --fix workflow.```
3. https://github.com/prettier/prettier-eslint-cli#--write
```
By default prettier-eslint will simply log the formatted version to the terminal. If you want to overwrite the file itself (a common use-case) then add --write.
```

### [prettier-eslint](https://github.com/prettier/prettier-eslint) 与 [prettier-eslint-cli](https://github.com/prettier/prettier-eslint-cli) 区别：
1. prettier-eslint [只能处理字符串](https://github.com/prettier/prettier-eslint-cli#the-problem)
2. prettier-eslint-cli [能处理一个或多个文件](https://github.com/prettier/prettier-eslint-cli#this-solution)
3. [默认情况下，prettier-eslint-cli 先运行 prettier，再运行`eslint --fix`](https://github.com/prettier/prettier-eslint-cli#--write)

# vue_cli_3_git_hooks_demo

## Project setup
```
npm install
```

### Compiles and hot-reloads for development
```
npm run serve
```

### Compiles and minifies for production
```
npm run build
```

### Run your tests
```
npm run test
```

### Lints and fixes files
```
npm run lint
```

### Customize configuration
See [Configuration Reference](https://cli.vuejs.org/config/).
