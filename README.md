### 克隆网站
做 RSS 阅读器的时候想到的东西，代码东拼西凑实现的功能，没优化。

### 配置
`_config.yml`
```yml
# reader：生成订阅/克隆网站
reader:
  # 配置文件地址，支持本地文件 和 url
  # path: source/_data/rss.yml # 指定本地文件（如果未指定配置文件路径，默认读取这个文件）
  rss:
    enable: false
    # path: source/_data/rss.yml
    path: https://cdn.jsdelivr.net/gh/cxvh/cxvh@main/yml/rss.yml # 配置 url
  menu:
    path: source/_data/menu.yml
    icon: icon # 指定图标name
    name: name # 指定标题name
    url: url # 指定链接name
  clone: # 克隆配置
    enable: true
    # path: source/_data/clone.yml
    path: https://cdn.jsdelivr.net/gh/cxvh/cxvh@main/yml/clone.yml
```

`clone.yml`
```yml
- name: BARAN的小站🔥🔥🔥
  host: https://cxvh.com # host 是必须的，入口文件
  output: Baran/ # 输出目录，非必须
  waittime: 0 # 链接请求间隔，默认 500，设置 0 无间隔容易出错
  rule: # 规则非必须，以下为默认规则
    content: $('#article-container') # 文章内容
    title: $('[property="og:title"]').attr('content') # 标题
    auther: $('[name="author"]').attr('content') # 作者
    subtitle: $('[name="description"]').attr('content') # 描述
    pubDate: $('[datetime].post-meta-date-created').attr('datetime') # 发布时间
    tags: $('.post-meta__tag-list a') # 标签
    categories: $('.post-meta-categories a') # 分类
    cover: $('[property="og:image"]').attr('content') # 封面
- name: butterfly主题
  host: https://butterfly.js.org
  output: butterfly/
  waittime: 500 # 等待时间 + 等待时间 × 随机数(0-1)
```

### 安装依赖
`npm install hexo-reader -D`

### 生成命令
`hexo reader`
