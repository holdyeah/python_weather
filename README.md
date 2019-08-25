# python_weather
个人

## 题目 天气数据平台系统设计与实现(python)                       
       
完稿日期：   2018.5.3           
## ［摘要］
在大数据时代，我们面对海量数据时，有时难免显得无所适从，一方面，数据复杂繁多，另一方面，人类大脑无法从堆积如山的数据中快速发现核心问题，因此就需要数据可视化，通过丰富的视觉效果，把数据以直观、生动、易理解的方式呈现给用户，可以有效提升数据分析的效率和效果。一目了然地天气数据可以更加直观,准确快速地洞察天气变化和影响,合理的交互设计、精美的界面体验,能够快速地知晓天气,提前做好出行计划。
## ［关键词］
天气;python;
## [Summary]
In the era of big data, when faced with massive data, it is sometimes difficult for us to be at a loss. On the one hand, the data is complex and numerous. On the other hand, the human brain cannot quickly find core problems in mountainous data. Therefore, data visualization is needed. The visual effects of the data presented to the user in an intuitive, vivid and easy-to-understand manner can effectively improve the efficiency and effectiveness of data analysis. At a glance, the weather data can be more intuitive, accurate and rapid insight into the weather changes and impacts, reasonable interaction design, exquisite interface experience, can quickly know the weather, make travel plans in advance.
## [Key words]
Weather;python3.6;mysql;
## 目 录
* [1.系统概述](#系统概述)

    * 1.1流程分析
    * 1.2数据
    * 1.3开发环境
    
* [2.系统分析](#系统分析)

    * 2.1流程分析
    * 2.2数据
    * 2.3开发环境

* [3.系统设计](#系统设计)

    * 3.1功能设计
    * 3.2模块设计
    
* [4.系统实现](#系统实现)

    * 4.1界面实现

* [结论](#结论)
* [参考文献](#参考文献)

****************

### 系统概述

 * 1.1天气平台系统概述
 
 **天气系统通常指引起天气变化和分布的高压、低压和高压脊、低压槽等具有典型特征的大气运动系统，影响天气的原因有很多种，比如气压，维度等等的原因。通过科学的分析，以及信息的搜集和处理架构下，客观引化下统计出个时间段的天气并且分析出而后的天气，在平台上更加直观的展现出来的系统。
      天气平台系统是为了提前为出行做好准备能够更好地预防做出人性化服务。
      
 * 1.2平台形状
 
 **天气是影响人们出行的一个重要的因数之一。17世纪以前，人们通过观测天象、物象的变化，编成天气谚语，以此预测当地未来几天的天气，尤其是“看云识天气“的常识得到了广泛应用。17世纪以后，温度表和气压表等气象观测仪器相继出现，地面气象站陆续建立，这时主要根据气压、气温、风、云等要素的变化来预报天气。但用天气图来预报天气只有100多年的历史。
1820年，德国莱比锡大学教授布兰蒂斯绘制出世界上最早的天气图，它为切实可行的天气预报创造了条件。19世纪中期，英法两国与沙皇俄国为了争夺黑海海峡而发生了克里木战争，英法两国派出了大批舰队前往参战。1854年11月14日，黑海上刮起了狂风，卷起巨浪，把停泊在海上的英法联合舰队军舰猛烈摔向礁石、海岸，使联合舰队蒙受到巨大的损失。 法国皇帝拿破仑三世很震惊，立即命令巴黎天文台调查这场风暴的起因。天文学家勒威耶通过搜集、分析欧洲各地11月14日前后几天的气象资料，终于弄清了这场风暴的来龙去脉，并写出了调查报告。勒威耶认为，只要各地的气象观测网用电报迅速传递气象情况，便可即时绘制天气图，进行天气预报了。
    根据勒威耶的建议，法国、英国先后开始了天气预报，并很快普及到世界各地。后来，观测天气的手段不断增多，尤其是气象卫星的发射，大大提高了天气预报的准确度。
    以往天气数据收集通过各个地方气象站近年来，随着人们出行区域扩大化，不在早上当当的一个小区域，可能是一个县市区，可能是一个省，可能是全球各地。当前的天气系统内容比较多，用户无法一目了然的看到自己需要的东西，某些因素可能给用户带来一定干扰。一些不必要的广告占据了系统一部分的面积，给用户带来负面的体验。同时浪费了不必要的流量，虽然开发者受益，但可能导致用户体验降低，导致产品开始下滑，不利于共赢。
    
 * 1.3需求分析
 
 **通过大数据分析采集个平台天气筛选出需要的信息整合优化信息，更人性化的给出合理的出行指南。根据地理位置为前提，不断推送实时的天气环境。数据采用百度api，以及气象局数据为背景，整合了两个平台的优势，从百度api中获取出今天的天气状况，及出行指南，回调气象局未来七天天气状况，通过大数据发现出未来天气的演化，提早的反馈给用户未来的信息变化。当遇到大风、大雨、、、及时的告知用户。
     不同用户查看天气预报可能会有各不相同的原因，但是总结起来其本质都是一样的，即通过天气预报信息来指导自己的行为。从这个本质的需求可以得到一些常见的具体场景。想在未来某一天安排一项活动，看看天气是否适合。晚上睡觉前看看天气来决定第二天穿什么衣服。去某个地方出差或者旅游，根据当地天气情况来选择携带合适的行李。想了解一下当天不同时段的天气情况，最高温度有多少，是否会下雨。看看未来几天天气的趋势，是会凉快一点还是会更热，有没有降雨等。看看室外的空气状况，是否适合进行户外活动。
以上是一些比较常见的场景，由于不同用户的生活习惯不同，所以可能还会有很多其他使用场景。但是这些基础的使用场景基本上可以涵盖了大多数用户的使用情况，从这些场景中可以抽象出用户一些基本需求，进一步得到一款天气预报需要具有的一些基本功能。
     有未来几日的天气预报信息、一天中不同时段的温度以及晴雨情况、可以查看多个城市的天气情况、能够查看空气质量。
     其中温度和晴雨情况是用户最为关注的信息。由于天气预报类的数据都是调用气象局的信息，因此在数据源上各类应用并未太大差异。要想赢得用户的青睐，就需要在信息的处理以及界面设计上下功夫。因此天气预报的任务就是让用户用最直观的方式获取最有效的信息，并且在这个过程中有很好的体验，产生愉悦的心情。
 
### 系统分析
   
   **系统分析是开发流程中必不可少的过程之一，在整个流程过程中起了至关重要的一个环节。一个好的分析思路可以给系统开发带来时间上的合理安排，让系统能够更加全方位，深度的明白系统的搭建。
   
 * 2.1流程分析
 
 **天气系统主要是把信息直关的体现给用户，让用户一目了然的通过这个系统获取自己的需要数据。
 这一套天气系统特点是通过大数据分析出用户的需求，在数据上进行比对分析出天气的变化。在开发过程中，为了解决这些困难
 （1）.标准化
 （2）.合理化
 （3）.添加注释，解析
 
 
 * 2.2数据
 
    **数据是天气系统中必不可少的给人提供信息，没有数据就没有天气系统
    温度、日期、落差温度、天气状况
 
 * 2.3开发环境
 
    **硬件要求：云服务器、1核2G，1M带宽、系统盘（Ubuntu 14.04.5 LTS（Trusty Tahr） 50G）
      软件要求：pyhon3.6、pycham2017.2、mysql
 
### 系统设计

 * 3.1功能设计
 
    **为了用户能够更快的、更方便的获取天气数据。为用户提供一种更科学的服务系统。于是开始设计出由云计算的工作的一种信息化服务，在可行的基础上添加自己的设计方案，依托大数据平台的信息化程度已经数据共享为保障，提供云计算的分析，来给用户提供有效的数据。天气系统主要的实现功能板块
 
 * 3.2模块设计

 
### 系统实现

 * 4.1界面实现
 
### 结论

### 参考文献
