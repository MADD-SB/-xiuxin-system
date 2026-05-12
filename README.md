# 修心系统

一个本地优先的个人情绪管理、每日复盘、欲望控制、执行力训练系统。数据保存在浏览器 `localStorage`，不需要后端。

## 项目结构

```text
修心系统/
├─ index.html          # 应用入口，加载 React、Tailwind、图标库
├─ package.json        # 可选 npm 脚本
├─ server.mjs          # 零依赖本地静态服务器
├─ README.md           # 运行、部署、扩展说明
└─ src/
   ├─ data.js          # 默认文案、默认规则、字段选项、空白表单模型
   ├─ main.js          # React 页面、6 个核心模块、CRUD 与图表
   ├─ storage.js       # localStorage 读写、迁移、导入导出
   ├─ styles.css       # 全局样式、滚动条、滑块控件
   └─ utils.js         # 积分、等级、连续天数、图表数据等计算逻辑
```

## 如何运行

当前项目不依赖 npm 安装包，直接用 Node 启动静态服务器：

```bash
node server.mjs
```

然后打开：

```text
http://localhost:4173
```

如果要换端口：

```bash
node server.mjs 5173
```

如果你的电脑有 npm，也可以运行：

```bash
npm run dev
```

## 如何部署

### GitHub Pages

1. 把整个目录推到 GitHub 仓库。
2. 进入仓库 `Settings -> Pages`。
3. `Build and deployment` 选择 `Deploy from a branch`。
4. 分支选 `main`，目录选 `/root`。
5. 保存后访问 GitHub Pages 给出的地址。

这是纯静态应用，不需要构建命令。

### Vercel

1. 在 Vercel 新建项目并导入仓库。
2. Framework 选择 `Other`。
3. Build Command 留空。
4. Output Directory 填 `.`。
5. 部署即可。

## 后续扩展为手机 PWA

可以新增：

```text
manifest.webmanifest
service-worker.js
icons/
```

然后在 `index.html` 中加入：

```html
<link rel="manifest" href="./manifest.webmanifest" />
```

并注册 Service Worker。这样可以实现“添加到主屏幕”、离线缓存、启动页图标和沉浸式显示。

## 后续加入云同步

推荐保持当前数据模型不变，只替换存储层：

1. 保留 `src/storage.js` 的本地读写作为离线缓存。
2. 新增账号系统，可选 Supabase、Firebase、LeanCloud 或自建 API。
3. 以 `updatedAt` 为同步依据，把 `dailyReviews`、`dailyPlans`、`rules`、`desires` 等集合分别同步。
4. 冲突策略建议先用“最新更新时间覆盖”，后续再做逐字段合并。
5. 导入导出 JSON 继续保留，作为云同步前后的保险。
