# yt-dlp 常用命令
yt-dlp 常用命令组合

yt-dlp 是 youtube-dl 的增强版，功能非常强大，支持丰富的命令组合，适合下载 YouTube、Bilibili、Twitter、Twitch、抖音等各种平台的视频、音频、字幕、元数据等内容。

下面是常用命令组合和功能分类介绍：

✅ 基础命令组合
bash
复制
编辑
yt-dlp URL
例如：

bash
复制
编辑
yt-dlp https://www.youtube.com/watch?v=dQw4w9WgXcQ
🔑 登录/身份认证
1. 从浏览器获取 Cookie（推荐）
bash
复制
编辑
yt-dlp --cookies-from-browser chrome URL
2. 手动加载 cookies.txt
bash
复制
编辑
yt-dlp --cookies cookies.txt URL
3. 登录用户名/密码（不推荐用于 Google）
bash
复制
编辑
yt-dlp -u 用户名 -p 密码 URL
🎧 下载音频
1. 提取音频（默认为 m4a）
bash
复制
编辑
yt-dlp -x URL
2. 转为 mp3
bash
复制
编辑
yt-dlp -x --audio-format mp3 URL
3. 指定音频质量
bash
复制
编辑
yt-dlp -x --audio-format mp3 --audio-quality 0 URL
🎞️ 下载视频+音频
1. 下载最高画质（带音频合并）
bash
复制
编辑
yt-dlp -f "bv*+ba/b" URL
解释：

bv*：最佳视频

ba：最佳音频

/b：如果只有一个流（包含音视频）也可用

2. 指定清晰度（如 1080p）
bash
复制
编辑
yt-dlp -f "bestvideo[height<=1080]+bestaudio/best[height<=1080]" URL
📥 指定输出目录与文件名
bash
复制
编辑
yt-dlp -o "~/Downloads/%(title)s.%(ext)s" URL
占位符常用项：

%(title)s：标题

%(id)s：视频ID

%(uploader)s：作者

%(upload_date)s：上传日期

%(resolution)s：分辨率

%(ext)s：扩展名

🌐 下载字幕/元数据
下载字幕（默认语言）
bash
复制
编辑
yt-dlp --write-subs --sub-lang en --sub-format srt URL
下载视频信息 JSON
bash
复制
编辑
yt-dlp --write-info-json URL
💾 批量下载
从文本读取多个 URL
bash
复制
编辑
yt-dlp -a urls.txt
⏱️ 只下载某个时间段
bash
复制
编辑
yt-dlp --download-sections "*00:01:00-00:02:30" URL
🚀 加速下载（多线程）
bash
复制
编辑
yt-dlp -N 8 URL  # 8个线程并发
🧹 自动跳过已下载
bash
复制
编辑
yt-dlp --download-archive downloaded.txt URL
用于避免重复下载（将已下载ID写入 downloaded.txt）

💻 使用代理
bash
复制
编辑
yt-dlp --proxy "socks5://127.0.0.1:1080" URL
🎮 其他进阶组合示例
下载 Bilibili 分P
bash
复制
编辑
yt-dlp --yes-playlist "https://www.bilibili.com/video/BVxxx"
下载抖音无水印视频（部分支持）
bash
复制
编辑
yt-dlp "https://www.douyin.com/video/xxxxxx"
🧩 常用组合汇总（推荐收藏）
功能	命令
自动获取 Cookie	--cookies-from-browser chrome
音频转 MP3	-x --audio-format mp3
指定清晰度下载	-f "bestvideo[height<=1080]+bestaudio"
下载字幕	--write-subs --sub-lang en
多线程加速	-N 8
指定输出模板	-o "%(title)s.%(ext)s"
下载某段时间	--download-sections "*00:01:00-00:02:00"
避免重复下载	--download-archive archive.txt
