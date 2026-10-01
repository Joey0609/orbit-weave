# Orbit Weave · 轨道织图

星座轨道面与相对相位的历史回放网页，支持星网、千帆、OneWeb、Starlink、Amazon Leo 和时空道宇。

- 按星座和倾角切换，拖动时间轴回放；空格暂停或继续。
- 悬停查看卫星信息，点击锁定；支持图片与当前视图 CSV 导出。
- 仅加载当前视图的数据，切换回来复用缓存。

## 本地打开

双击 `start.cmd`，在浏览器打开启动时提示的地址。不要直接双击 HTML：历史数据需要通过 HTTP 加载。

## GitHub Pages

本目录 `raan_explorer` 就是仓库根目录，建议仓库名 `orbit-weave`。

1. 创建 GitHub 仓库并把本目录推送到 `main` 或 `master` 分支。
2. 在仓库 Settings → Pages → Build and deployment 中，选择 **GitHub Actions**。
3. 推送网页或历史数据的更新，即可自动部署；也可在 Actions 中手动运行 **Deploy Orbit Weave**。

部署仅包含 `index.html`、`switcher.css`、`.nojekyll` 和 `history/`。历史数据约 335 MB，保持普通 Git 文件，不使用 Git LFS。

## 数据与显示

历史数据截至 2026 年 9 月。`history/manifest.json` 是清单，其余数据为浏览器解压的 gzip JSON。

卫星位置采用 TLE 要素的近似传播与通过质量检查的历史区间平滑重建，不是完整 SGP4。共同相位参考在离线建立，网页实时计算位置并减去平滑参考；共同抵消保持卫星间的相对相位差。新发射或不稳定卫星不参与参考速度统计。

本项目是历史数据回放，不会自动获取新的 TLE。

## 本地处理文件

`.gitignore` 采用允许列表，仅提交网页运行文件、历史数据、说明和部署配置。处理脚本、模板、目录缓存及原始目录保留在本地，但不会进入仓库。
