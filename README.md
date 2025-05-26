# 教师成果管理系统

## 项目概述
这是一个基于前后端分离架构开发的教师成果管理系统，用于管理教师的各类科研成果，包括论文、专利、著作、项目等。系统支持多角色管理，包括普通教师、教研室主任和管理员。

## 技术栈
### 前端技术栈
- 前端框架：Vue 3
- 开发语言：TypeScript
- UI 框架：Element Plus
- 状态管理：Pinia
- 路由管理：Vue Router
- 图表库：ECharts
- 构建工具：Vite
- HTTP 客户端：Axios

### 后端技术栈
- 核心框架：Spring Framework
- Web框架：SpringMVC
- ORM框架：MyBatis
- 数据库：MySQL
- 项目管理：Maven
- 接口文档：Swagger
- 权限认证：Spring Security + JWT

## 项目结构
```
├── frontend/                # 前端项目目录
│   ├── src/
│   │   ├── assets/         # 静态资源
│   │   ├── components/     # 公共组件
│   │   ├── router/         # 路由配置
│   │   ├── store/          # 状态管理
│   │   ├── types/          # TypeScript 类型定义
│   │   ├── views/          # 页面组件
│   │   └── App.vue         # 根组件
│   ├── package.json        # 前端依赖配置
│   └── vite.config.ts      # Vite 配置文件
│
└── backend/                # 后端项目目录
    ├── src/
    │   ├── main/
    │   │   ├── java/      # Java 源代码
    │   │   │   ├── controller/    # 控制器层
    │   │   │   ├── service/       # 服务层
    │   │   │   ├── dao/          # 数据访问层
    │   │   │   ├── entity/       # 实体类
    │   │   │   ├── dto/          # 数据传输对象
    │   │   │   ├── config/       # 配置类
    │   │   │   └── utils/        # 工具类
    │   │   └── resources/        # 配置文件
    │   └── test/          # 测试代码
    └── pom.xml            # Maven 配置文件
```

## 功能模块

### 1. 用户认证与权限控制
- 支持多角色登录（教师、教研室主任、管理员）
- 基于 Token 的身份验证
- 登录状态持久化
- 根据用户角色和选择自动跳转对应页面
- 数据访问权限控制：
  * 教师：仅可查看和管理自己的数据
  * 教研室主任：可查看和管理本教研室所有教师数据
  * 管理员：可查看和管理所有数据

### 2. 教师端功能
#### 2.1 页面概览
- 成果总数统计（个人）
- 本年度成果统计（个人）
- 待审核成果数量（个人）
- 总积分统计（个人）
- 最近成果展示（个人）
- 系统信息展示（管理员发布）

#### 2.2 成果管理
- 成果列表展示（仅显示当前教师成果）
- 成果筛选功能：
  * 上传者
  * 成果类型
  * 审核状态
  * 时间范围
- 成果操作权限控制：
  * 待审核状态：可查看、删除、编辑
  * 未通过状态：可查看、删除、编辑
  * 已通过状态：仅可查看
- 新增成果功能
- 导出清单功能（待实现）

#### 2.3 成果上传
支持多种类型的成果上传：
- 论文成果
- 专利成果
- 项目成果
- 著作成果
- 软件著作权
- 个人获奖
- 科研指导
- 社会服务
- 其他成果

#### 2.4 统计分析
- 成果类型分布统计（个人）
- 年度成果趋势分析（个人）
- 数据可视化展示（使用 ECharts）

#### 2.5 个人中心
- 个人信息展示
- 密码修改功能

### 3. 教研室主任端功能
#### 3.1 成果审核
- 查看待审核成果（本教研室）
- 审核操作：
  * 审核通过：更新教研室审核状态
  * 驳回：更新成果状态为未通过
- 成果筛选功能：
  * 上传者
  * 成果类型
  * 审核状态
  * 时间范围
- 导出清单功能（待实现）

#### 3.2 本教研室
- 查看本教研室所有教师成果
- 成果筛选和搜索
- 数据导出功能

#### 3.3 统计分析
- 本教研室成果统计
- 教师成果对比分析
- 数据可视化展示

### 4. 管理员端功能（待开发）
- 系统管理
- 用户管理
- 成果管理
- 统计分析
- 系统信息发布

## 业务逻辑

### 1. 用户角色权限
- 教师：可以上传和管理自己的成果
- 教研室主任：可以审核本教研室的成果，查看本教研室所有教师成果
- 管理员：可以管理所有成果和用户，发布系统信息

### 2. 成果管理流程
1. 教师上传成果
2. 教研室主任审核
3. 管理员审核
4. 成果状态更新（需教研室主任和管理员都通过）
5. 成果统计和分析

### 3. 数据验证
- 表单验证
- 贡献率计算（确保总贡献率为100%）
- 文件上传验证
- 角色权限验证
- 审核状态验证

## 开发规范
- 使用 TypeScript 进行类型检查
- 遵循 Vue 3 组合式 API 规范
- 使用 ESLint 进行代码规范检查
- 使用 Prettier 进行代码格式化

## 部署要求
### 前端环境要求
- Node.js 环境 (推荐 v16+)
- 现代浏览器支持
- npm 或 yarn 包管理器

### 后端环境要求
- JDK 1.8+
- Maven 3.6+
- MySQL 5.7+
- Tomcat 8.5+

## 开发环境搭建
### 前端开发环境
```sh
# 进入前端项目目录
cd frontend

# 安装依赖
npm install

# 启动开发服务器
npm run dev
```

### 后端开发环境
```sh
# 进入后端项目目录
cd backend

# 编译项目
mvn clean install

# 运行项目
mvn spring-boot:run
```

## 数据库配置
1. 创建 MySQL 数据库
2. 执行数据库初始化脚本
3. 修改 `application.yml` 中的数据库连接配置

## 待优化项
1. 后端 API 集成
2. 文件上传功能完善
3. 数据导出功能实现
4. 性能优化
5. 单元测试补充

这个系统采用了现代化的前端技术栈，具有良好的可扩展性和维护性。通过模块化的设计和清晰的代码结构，使得系统易于开发和维护。

## Recommended IDE Setup

[VSCode](https://code.visualstudio.com/) + [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) (and disable Vetur).

## Type Support for `.vue` Imports in TS

TypeScript cannot handle type information for `.vue` imports by default, so we replace the `tsc` CLI with `vue-tsc` for type checking. In editors, we need [Volar](https://marketplace.visualstudio.com/items?itemName=Vue.volar) to make the TypeScript language service aware of `.vue` types.

## Customize configuration

See [Vite Configuration Reference](https://vite.dev/config/).

## Project Setup

```sh
npm install
```

### Compile and Hot-Reload for Development

```sh
npm run dev
```

### Type-Check, Compile and Minify for Production

```sh
npm run build
```

### Run Unit Tests with [Vitest](https://vitest.dev/)

```sh
npm run test:unit
```

### Run End-to-End Tests with [Playwright](https://playwright.dev)

```sh
# Install browsers for the first run
npx playwright install

# When testing on CI, must build the project first
npm run build

# Runs the end-to-end tests
npm run test:e2e
# Runs the tests only on Chromium
npm run test:e2e -- --project=chromium
# Runs the tests of a specific file
npm run test:e2e -- tests/example.spec.ts
# Runs the tests in debug mode
npm run test:e2e -- --debug
```

### Lint with [ESLint](https://eslint.org/)

```sh
npm run lint
```
