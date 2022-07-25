https://juejin.cn/post/7123612981895626760

# start

## init

`yarn create vite`  
+ input project name
+ select react
+ select react-ts

## run
`yarn`  
`yarn dev`

# 代码规范

## ESlint

用于检测代码风格代码规范

`npm init @eslint/config`  
会创建`.eslintrc.cjs`文件，配置自己lint规则可以在rules中添加

## Prettier

用于对代码进行格式化

+ 安装依赖`yarn add prettier -D`
+ 在根目录创建`.prettierrc.cjs`配置文件
+ 在Eslint中引入Prettier，安装相关依赖`yarn add eslint-config-prettier eslint-plugin-prettier -D`
+ 在Eslint配置文件`.eslintrc.cjs`中加入Prettier相关配置
+ 在`package.json`的script中添加命令：`"lint": "eslint --ext .js,.jsx,.ts,.tsx --fix --quiet ./"`
+ 在React17中，已经不需要显式引入React了，在`.eslintrc.cjs`的extends中添加`'plugin:react/jsx-runtime'`

## Vite中引入ESlint

在vite中引入ESlint插件，以便在开发阶段发现问题（yarn dev的时候会在控制台输出错误）

+ `yarn add vite-plugin-eslint -D`
+ 在`vite.config.ts`引入插件

# Husky + lint-staged

## Husky

通过Husky在git commit时进行代码校验

+ `yarn add husky -D`
+ 在`package.json`中添加脚本`prepare`：`npm pkg set scripts.prepare="husky install" & yarn prepare`，运行命令后会创建`.husky`文件夹
+ 添加一个Hook：`npx husky add .husky/pre-commit "npm run lint"`，添加这个hook之后，每次`git commit`之前都会先运行`npm run lint`，通过之后才会提交代码

## lint-staged

每次提交都检测所有的代码并不好，通过lint-staged只对暂存区的代码进行检验

+ `yarn add lint-staged -D`
+ 在`package.json`中添加（非scripts）
```
"lint-staged": {
    "*.{js,jsx,tsx,ts}": ["npm run lint"]
}
```
+ 在`.husky/pre-commit`中替换`npm run lint`为`npx lint-staged`