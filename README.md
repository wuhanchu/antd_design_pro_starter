# antd_design_pro_starter

这个项目主要是在[fr-schema](https://github.com/wuhanchu/fr-schema.git),[antd_design_pro](https://github.com/ant-design/ant-design-pro.git),[fr-schema-antd-utils](https://github.com/wuhanchu/fr-schema-antd-utils.git)的基础上，组建出一个快速的开发模版。

## 目录结构

    |-- config                                # umi 配置，包含路由，构建等配置
    |-- mock                                  # 本地模拟数据
    |-- public
    |   |-- favicon.png                       # favicon
    |-- src                                   #
    |   |-- assets                            # 本地静态资源
    |   |-- components                        # 业务通用组件
    |   |-- layout                            # 通用布局
    |   |-- models                            # 全局 dva model
    |   |-- services                          # 后台接口服务
    |   |-- pages                             # 业务页面入口和常用模板
    |   |-- e2e                               # 集成测试用例
    |   |-- global.less                       # 全局样式
    |   |-- global.tsx                         # 全局 JS
    |   |-- theme.js
    |-- tests                                 # 测试工具
    |-- .gitignore                            # git忽略文件
    |-- .editorconfig                         # 编辑器代码风格配置
    |-- .eslintignore                         # eslint忽略文件
    |-- .eslintrc                             # eslint规则
    |-- .prettierignore                       # 代码风格配置忽略文件
    |-- .prettierrc                           # 代码风格配置文件
    |-- .stylelintrc                          # 样式风格配置文件
    |-- package.json
    |-- README.md

## 安装环境

Install `node_modules`:

```bash
npm install
```

or

```bash
yarn installe
```

### 运行

```bash
npm start
```

### 编译

```bash
npm run build
```

### 检查代码规范

```bash
npm run lint
```

你可以运行下面的代码来修改代码规范问题:

```bash
npm run prettier
```

### 运行单元测试

```bash
npm test
```

## 部署

### 编译镜像

```docker
docker build  -t antd_design_pro_starter --file docker/Dockerfile.hub  .
docker build  -t server.aiknown.cn:31003/z_ai_frame/node:antd_4 --file docker/Dockerfile.node  . && docker push server.aiknown.cn:31003/z_ai_frame/node:antd_4
```

### 运行容器

```docker
docker run --rm  -p 8000:80 --name antd_design_pro_starter -e SERVER_URL='http://192.168.1.150:5002' antd_design_pro_starter
```

-   端口 80: web 访问端口
-   SERVER_URL: 后端服务地址

### 导入导出镜像

-   导出镜像：docker save -o ./antd_design_pro_starter.docker antd_design_pro_starter
-   导入镜像：docker load ‒‒input antd_design_pro_starter.docker

## More

使用到的一些组件可以在[official website](https://pro.ant.design)中找到. 如果你不喜欢我开发的模版，你可以访问[github](https://github.com/ant-design/ant-design-pro)是一个很优秀的脚手架.

## 初始化

在使用之前需要配置一下认证的信息，来保证用户的登录。

-   proxy.js： 配置一下后端接口的代理
-   config：配置一下 Oauth 信息。

## jenkins 依赖镜像编译
