# 网易云听歌排行词云
本项目使用 Python 和 jieba 分词，收集用户的听歌排行中的所有歌词信息，使用 WordCloud 词云展示

效果展示：

![https://github.com/lijiext/myc_music_cloud/blob/main/word_cloud.png?raw=true](https://github.com/lijiext/myc_music_cloud/blob/main/word_cloud.png?raw=true)

## 文档
### 先决条件
1. anaconda 环境
2. 浏览器调试工具的使用
3. 网易云 nodeJs 版 API
### 步骤
1. 首先在浏览器中获取到用户的听歌排行界面 (你需要将 id 替换成你需要的)

    使用 [https://music.163.com/#/user/home?id=1469645xxx](https://music.163.com/#/user/home?id=1469645xxx)
    
    可以进入用户的主页，点击更多可以到用户的听歌排行主页
    ![image.png](https://s3.maocdn.cn/img/2022/04/26/image.png)

    进入用户的听歌排行主页:
    [https://music.163.com/#/user/songs/rank?id=1469645xxx](https://music.163.com/#/user/songs/rank?id=1469645xxx)
    ![image686351765e53a532.png](https://s3.maocdn.cn/img/2022/04/26/image686351765e53a532.png)

2. 打开浏览器调试窗口
    ![imagee24ac4a4e9b926bd.png](https://s3.maocdn.cn/img/2022/04/26/imagee24ac4a4e9b926bd.png)

    复制如下内容，替换 music_rank 中的 data
    ![imagea4a31272e95e8dea.png](https://s3.maocdn.cn/img/2022/04/26/imagea4a31272e95e8dea.png)

    请求头中的 Referer 也可以替换成自己的

3. 运行 music_rank.ipynb 中的内容，将会保存歌单到 csv 或者 xlsx 文件

4. 歌词处理

    需要运行 [https://github.com/Binaryify/NeteaseCloudMusicApi](https://github.com/Binaryify/NeteaseCloudMusicApi)，你需要按照文档部署好该服务

    运行 music_lyrics.ipynb 中的内容

    运行完成好之后，在 lyrics.txt 中包含的就是歌单的所有歌词，你可能需要根据自己的需要自定义 stop_words 列表，排除不需要的例如作曲、作词这样的歌词内容

    ![image74df44a2e82b4934.png](https://s3.maocdn.cn/img/2022/04/26/image74df44a2e82b4934.png)

    请注意本处可能存在的问题：

    1. 停止词列表：由于网易云歌词数据非规格化，需要手动的生成停止词列表文件
    
    2. 多语种识别：本项目主要针对与中文语种的音乐分词，没有考虑日韩英等多语种
    3. 重复度：某些歌曲中的歌词完全重复了几遍，高度影响统计结果

5. 生成歌词

    运行 word_cloud.ipynb 生成词云图片，请注意，同样需要忽略歌词中的无意义词汇例如：啊，的，吗，了等词汇

    另外 针对中文需要指定中文字体的路径


### TODO
1. 使用云函数或 github actions 自动化程序流程
2. 分语言与权重
3. 词汇情感分析
4. 列表展示
5. 用户相似度