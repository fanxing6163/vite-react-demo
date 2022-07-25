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