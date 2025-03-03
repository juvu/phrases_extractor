# phrases_extractor

一个从**自然语言文本**   中抽取**关键短语**的工具
简单但是可以运用于生产

## 应用场景

- 在很多关键词提取任务中，使用tfidf等方法提取得到的仅仅是若干零碎词汇。
- 这样的零碎词汇无法真正的表达文章的原本含义，我们并不想要它。  
例如：
```
>>> text = '朝鲜确认金正恩出访俄罗斯 将与普京举行会谈...'
>>> keywords = ['俄罗斯', '朝鲜', '普京', '金正恩', '俄方']
```

- 在很多时候，我们往往需要更细化的短语描述，来作为文本的关键信息展示。这样的需求在生成词云、提供摘要阅读、关键信息检索等任务中都非常重要。  
例如：
```
>>> phrases = ['俄罗斯克里姆林宫', '邀请金正恩访俄', '最高司令官金正恩', 
               '朝方转交普京', '举行会谈']
```

## 功能介绍

为解决以上问题，我基于 jieba 工具，开发了一个关键短语抽取器，它可以方便地从文本中找出表达完成意思的关键短语。


## 使用方法

#### 安装
- 仅支持 python3
- 自动安装 jieba 依赖包

```
$ git clone https://github.com/dongrixinyu/phrases_extractor
$ cd ~/phrases_extractor
$ pip install .
```


#### 调用

- 输入必须为 **utf-8** 编码字符串
- 具体函数参数见代码
```
import phrases_extractor as pe

text = '法国媒体最新披露，巴黎圣母院火灾当晚，第一次消防警报响起时，负责查验的保安找错了位置，因而可能贻误了救火的最佳时机。...'
phrases = pe.extract_phrases(text)
print(phrases)
```

## 原理

首先基于jieba工具的 tfidf 关键词提取算法找出碎片化的关键词，然后再根据相邻关键碎片词进行融合，重新计算权重，去除相似词汇。得到的融合的多个关键碎片即为关键短语。

## 我的窝

如果觉得方便好用，请 follow 我一波：https://github.com/dongrixinyu


