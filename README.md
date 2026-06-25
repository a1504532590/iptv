IPTV-AutoUpdate 项目说明 README.md
项目介绍
本项目基于 GitHub Actions 实现全自动定时抓取、校验、合并 IPTV 直播源，自动生成可用 m3u 播放文件。内置两套公共源地址：央视频道合集、全国卫视 + 地方频道 + 赛事回放合集，每日自动检测链接存活、剔除失效线路，无需服务器，全程云端自动维护，TVBox、VLC、各类电视盒子均可直接订阅播放。
源文件说明
仓库内置两套完整 m3u8 直播源文件：
cctv.m3u8：全央视频道
包含 CCTV1~17、CGTN 多语种、老故事、发现之旅等央视频道，每条频道配备多线路备用地址，降低卡顿失效概率
quanpindao.m3u8：全频道合集
覆盖各大省级卫视、全国地方市县频道、体育赛事回放、篮球 / 羽毛球 / 足球赛事录像，频道分类清晰，自带多备用线路
订阅播放地址（国内 CDN 加速，推荐）
央视专用源
plaintext
https://cdn.jsdelivr.net/gh/a1504532590/iptv@main/cctv.m3u8
全频道综合源（卫视 / 地方 / 赛事）
plaintext
https://cdn.jsdelivr.net/gh/a1504532590/quanpindao.m3u8
GitHub 原生直链（海外使用）
plaintext
# CCTV
https://raw.githubusercontent.com/a1504532590/iptv/blob/main/cctv.m3u8
# 全频道
https://raw.githubusercontent.com/a1504532590/iptv/blob/main/quanpindao.m3u8
自动化功能说明
定时自动更新
GitHub Actions 每日定时执行更新脚本，批量检测所有直播链接连通性，删除失效地址，保留可用多线路。
多线路冗余
每个频道内置 4 组不同服务器地址，一条卡顿自动切换其他线路，提升播放稳定性。
自动分类整理
源文件采用标准 #genre 分组标签，播放器可自动区分「央视」「卫视」「地方台」「赛事回放」分类。
支持自定义源扩展
可在项目内新增自定义私有源文件，脚本会自动合并进最终播放列表。
部署使用步骤
Fork 本仓库至自己 GitHub 账号
开启仓库读写权限：Settings → Actions → Workflow permissions 选择 Read and write permissions
按需修改 .github/workflows 定时 cron 表达式，自定义更新频率
等待定时任务自动运行，或手动触发 Actions 立即更新直播源
将上方 CDN 链接复制到播放器即可订阅观看
支持播放器
TVBox、VLC、PotPlayer、MX 播放器、各类安卓电视盒子、智能电视直播软件、Kodi
常见问题
链接加载缓慢 / 打不开
优先使用 cdn.jsdelivr.net 加速地址，raw 原生链接国内网络访问易超时。
部分频道无法播放
公共服务器线路存在时效性，等待下一轮自动更新脚本刷新可用地址。
Actions 更新失败
检查仓库 Actions 读写权限是否开启。
免责声明
本项目仅聚合互联网公开可访问直播链接，不存储、不转发任何音视频内容，所有直播地址来源于网络公开资源。如有版权侵权内容，请提交 Issues 联系删除对应频道源。
