---
layout:     post
title:      主题阅读|Wolfram Engine
subtitle:   梳理与总结
date:       2021-05-17
author:     Jinga
header-img: img/grey.jpg
catalog: true
tags:
    - Computational Intelligence


---
# Wolfram Engine

* [1.安装](#1)
* [2.奇技淫巧](#2)
* [3.数学领域](#3)

<h2 id="1">1.安装</h2>

在网站[Free Wolfram Engine for Developers](https://www.wolfram.com/engine/?source=nav)找到对应自己电脑系统的安装包  

我选择的是linux版本，这个是免费的开发者版本     

然后会跳到一个注册界面，注册完成后记住账号密码，后续有用  

下载完WolframEngine_12.2.0_LIN_CN.sh文件后，再命令行bash进行安装，注意需要sudo获得权限  

`
sudo bash WolframEngine_12.2.0_LIN_CN.sh   
`  

接下来会提示安装的路径:   

`
Enter the installation directory, or press ENTER to select
/usr/local/Wolfram/WolframEngine/12.2:
`   

安装成功后，cd到这个安装路径   

按照[How do I specify which kernel WolframScript should use?](https://support.wolfram.com/47243)操作进行配置   

`
wolframscript -config WOLFRAMSCRIPT_KERNELPATH="/usr/local/Wolfram/WolframEngine/12.2/Executables/WolframKernel"  
`  

然后输入 
`
wolframscript 
`  


此时需要输入Wolfram ID和Password，这就是之前注册的信息  

完成后就来到Wolfram的计算环境，现在可以尽情探索了  

输入`Quit[]`可退出   

---

安装jupyterlab   
`sudo pip3 install jupyterlab`   

运行jupyter-lab   

这时终端会弹出网址   

```
http://localhost:8888/lab?token=9b7513e72a26836335c16e5f3d1ae1323117e5516ffeb2e0
http://127.0.0.1:8888/lab?token=9b7513e72a26836335c16e5f3d1ae1323117e5516ffeb2e0
```

在浏览器上登陆网址，就可以访问到jupyterlab   



在[WolframLanguageForJupyter](https://github.com/WolframResearch/WolframLanguageForJupyter/releases)中下载WolframLanguageForJupyter-0.9.2.paclet   

在WolframEngine中输入wolframscript后   

```mathematica
In[7]:= PacletInstall["./Downloads/WolframLanguageForJupyter-0.9.2.p
aclet"]                                                                         

Out[7]= PacletObject[WolframLanguageForJupyter, 0.9.2, <>]

In[8]:= Needs["WolframLanguageForJupyter`"]                                     

In[9]:= ConfigureJupyter["Add"]                                                 


```


这时再刷新http://127.0.0.1:8888/lab   

就可以看到wolfram入口了   

<h2 id="2">2.奇技淫巧</h2>  

---

出现报错   

```
No valid password found.
Connection closed by WolframKernel.
The Wolfram Engine exited because of a license error: single machine process limit reached.
```

说明已经有引擎在运行了，需要先退出来原来的引擎，只允许单个的进程运行   

---

可在命令行直接运行，如   
`wolframscript -code 2+2`   

也可通过Wolfram Cloud来计算   
`wolframscript -cloud -code 2+2`    

---

[Mathematica 比起 Python 如今还有什么优势？](https://www.zhihu.com/question/265383707)    

---

[MathematicaForPrediction](https://github.com/antononcube/MathematicaForPrediction)   

This open source project is for Mathematica (Wolfram Language) implementations of statistical and Machine Learning algorithms that can be used for data analysis, forecast, prediction, and recommendation systems.   

---

如果输出表达式，可以在后面加上//TeXForm, 生成比较美观的输出,tex格式   

```mathematica
In[15]:= x+1/y//TeXForm                                                         

Out[15]//TeXForm= x+\frac{1}{y}
```

---

输入  

`Entity["Lamina", "SmileyFaceLamina"]["Diagram"]`   

可以看到输出有表情的图片了  

![smileyface.png](/img/20210517smileyface.png)

---

检测一段文本的情感   

```mathematica
wolframscript -code 'Classify[ "Sentiment", "That is too bad" ]'
```

---

**用 Python 运行Wolfram 语言代码**

安装
sudo pip3 install wolframclient   

```python
from wolframclient.evaluation import WolframLanguageSession
from wolframclient.language import wl, wlexpr
session = WolframLanguageSession()
```

---

计算列表的最小最大值  
`session.evaluate(wl.MinMax([1, -3, 0, 9, 5]))`    

---

运行脚本文件    

mimmax.wls
```mathematica
l = {1, -3, 0, 9, 5};
y = MinMax[l];
Print[y];
```

运行wls文件
`$ wolframscript -file mimmax.wls`   

output:   
`{-3, 9}`   

---

[Cartoonise people in videos with neural networks, image/video processing ](https://community.wolfram.com/groups/-/m/t/2253071?source=frontpage-latest-news)   



---

自动构建列表   
Table函数：按照指定次数和指定值，生成某个函数的列表。例如，Table[x,5]，生成{x,x,x,x,x}；Table[a[n],{n,5}]，生成{a[1], a[2], a[3], a[4], a[5]}。这个函数的用途很广泛，使用频率很高。   









##### 参考:

1. [TeXForm Output in JupyterLab](https://github.com/WolframResearch/WolframLanguageForJupyter/issues/83)  
2. [给Anaconda的Jupyter notebook笔记本安装Wolfram engine核心](https://zhuanlan.zhihu.com/p/79730978)   
3. [Smiley Face using parametric equations](https://mathematica.stackexchange.com/questions/137669/smiley-face-using-parametric-equations)    
4. [Ubuntu 18.04 服务器安装 JupyterLab](https://wangxin1248.github.io/linux/2018/11/python3-data-science-01.html#:~:text=%E5%8F%AF%E4%BB%A5%E9%80%9A%E8%BF%87%E5%BE%88%E5%A4%9A%E7%A7%8D%E6%96%B9%E6%B3%95%E6%9D%A5%E5%AE%89%E8%A3%85%20JupyterLab%EF%BC%8C%E5%8F%AF%E4%BB%A5%E9%80%9A%E8%BF%87%20conda%2C%20pip%2C%20%E6%88%96%E8%80%85%20pipenv.,%E8%BF%99%E9%87%8C%E6%88%91%E9%80%89%E6%8B%A9%E7%9A%84%E6%98%AF%E9%80%9A%E8%BF%87%20pip%20%E6%9D%A5%E5%AE%89%E8%A3%85%20juputerlab.%20pip%20install%20jupyterlab.)    
5. [Wolfram Engine使用+Jupyter协作](https://zhuanlan.zhihu.com/p/115381177)   
6. [用于命令行的 WolframScript](https://cloud.tencent.com/developer/article/1140198)   
7. [Wolfram Language (Mathematica) 学习笔记 ](http://blog.sciencenet.cn/blog-241374-1042212.html)   
8. [如何学习mathematica](https://www.zhihu.com/question/346321384)  
9. [Project Euler 1~50](https://zhuanlan.zhihu.com/p/109730792)  
10. [Mathematica中的约束最优化问题/遗传算法/退火算法](https://blog.csdn.net/weixin_43632421/article/details/106871744)    
11. [你的爱，用数学公式告诉她(他) ](http://www.360doc.com/content/20/1009/18/71872132_939616057.shtml)    











