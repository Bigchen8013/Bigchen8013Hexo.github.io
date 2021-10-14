---
layout: name
title: 使用Stanford NER进行中文文本的分词
date: 2020-12-08 22:02:45
tags:
---

# 使用Stanford NER进行中文文本的分词

### 一、在Standford 官网下载stanford的包

​		，在斯坦福官网（https://nlp.stanford.edu/software/CRF-NER.shtml#Download）下载所需要的包后解压。对于中文文本的分析处理，还需要下载中文处理的模型stanford-chinese-corenlp-2222-11-14-models.jar，此处你下载下来的包的名字不一定和我的名字相同，若是直接使用下载时的包名，使用时会报没有中文处理模型的文件，最好是改成我的这种命名方式。

注意：下载下来的中文模型需要放到stanford-corenlp这个文件的根目录下，要不然在调用的时候找不到路径。

### 二、本地环境配置

**1、** java环境配置

​		Stanford的NLP工具需要有java环境的支持，并且jdk的版本需要1.8以上。此处我使用的JDK版本是jdk-8u211-windows-x64.exe，以下是安装时的配置。

+ 我的jdk是安装在I:\eclipse\JDK install目录下，所以创建系统变量的时候，JAVA_HOME的值为I:\eclipse\JDK install
+ CLASSPATH的值：.;%JAVA_HOME%\lib\dt.jar;%JAVA_HOME%\lib\tools.jar
+ PATH的值：%JAVA_HOME%\bin和%JAVA_HOME%\jre\bin

**2、**验证java环境

  +  win+r  键入cmd
  +  分别输入java -version、java、javac都能出现正确信息即配置成功

![image-20201208211810980](C:\Users\13778\AppData\Roaming\Typora\typora-user-images\image-20201208211810980.png)

**3、**python环境配置并验证

​		在python官网选择python版本下载并进行安装，最好下载.exe文件安装，这样可以在安装时自动配置系统变量。

验证：

+ win+r键入cmd
+ 输入python，此时终端会输出你的python版本并进入python环境，即![image-20201208212248188](C:\Users\13778\AppData\Roaming\Typora\typora-user-images\image-20201208212248188.png)
+ 若是有多个python版本还可以使用where python查看python版本的位置，即![image-20201208212352782](C:\Users\13778\AppData\Roaming\Typora\typora-user-images\image-20201208212352782.png)

### 三、使用corenlp进行中文分词

```python
from stanfordcorenlp import StanfordCoreNLP
#I:/standford NER/stanford-corenlp-4.2.0/这个是本地模型的位置，zh表示中文模型处理
nlp = StanfordCoreNLP(r'I:/standford NER/stanford-corenlp-4.2.0/', lang='zh')

sentence = "小明是斯坦福大学的一名研究生，他的专业是计算机科学与技术。"

print("------word_tokenize分词-----")
print(nlp.word_tokenize(sentence))
print("------pos_tag进行分词并进行词性标注-----")
print(nlp.pos_tag(sentence))
print("------ner命名实体识别-----")
print(nlp.ner(sentence))
```

运行结果：

![image-20201208214826438](C:\Users\13778\AppData\Roaming\Typora\typora-user-images\image-20201208214826438.png)

​		总的来说，该工具的分词效果确实确实挺不错，但有一个缺点是在加载模型的时候比较慢，这就导致在处理数据时需要花费更多的时间。