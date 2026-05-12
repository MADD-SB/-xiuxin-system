# 修心系统

这是《修心系统》的单文件版本。

## 文件

```text
index.html
```

所有 HTML、CSS、JavaScript、默认数据、localStorage 逻辑和图表都已经写在 `index.html` 里，不需要 React、Tailwind、npm、Vite 或任何构建命令。

## 本地使用

直接双击打开 `index.html` 即可使用。

也可以用任意静态服务器打开，例如：

```bash
python -m http.server 4173
```

然后访问：

```text
http://localhost:4173
```

## 部署到 GitHub Pages

1. 新建一个 GitHub 仓库。
2. 上传 `index.html`。
3. 进入仓库 `Settings -> Pages`。
4. Source 选择 `Deploy from a branch`。
5. 分支选择 `main`，目录选择 `/root`。
6. 保存后访问 GitHub Pages 给出的地址。

## 数据说明

数据保存在浏览器 `localStorage` 中。换浏览器、清缓存或换设备时，数据不会自动同步。页面右上角有“数据”按钮，可以导出和导入 JSON 备份。
