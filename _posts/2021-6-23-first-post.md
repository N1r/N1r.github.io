[TOC]



---

layout: post 

title:  "first-post" 

---

# Dialectology for computational linguists

## Computational work in dialectology

> 主要参考：
>
> Nerbonne J, Heeringa W, Prokic J, et al. Dialectology for computational linguists. 2019.
>
> Wieling, Martijn, and Nerbonne, John. 2015. Advances in dialectometry. *Annual* Review of Linguistics*, **1**, 243–264.
>
> Heeringa, Wilbert, and Proki´c, Jelena. 2018. Computational dialectology. Pages 330–347 of: Boberg, Charles, Nerbonne, John, and Watts, Dominic (eds), *The* *handbook of dialectology*. Hoboken, New Jersey: Wiley-Blackwell.

## Dialectology

定义： a **geographically restricted** language variety,

Focus on this sort of variety, ignoring the other dimensions of variation, including social, situational and temporal.

## Research questions and research perspectives

>  what makes them up, and where they are spoken.

 The two main questions – what is special about a given dialect and where is it spoken ?

Aim : to provide compact characterizations with defensible assumptions

## Data collection

传统数据收集：

Dialectologists have experimented not only with questionnaires (Llamas, 2018) and other written surveys (Chambers, 2018), which better guarantee that responses are comparable, but also with personal interviews (Bailey, 2018)

新兴数据收集：

1. world-wide web as a means of conducting surveys
2. smart phone apps and crowd sourcing

方言数据的特点：

​	1. cherished！

​	2. collecting notably it in the form of dialect atlases

> KEY: Collaboration with one of the many dialect atlases across the world.

# 方言计量学--**Dialectometry**

Primary data analysis steps in traditional dialectology involved decorating a map with codes corresponding to the different ways of expressing the same thing in the language area under study.

Draw an **isogloss** (同言线，同语线) separating the area

小缺陷：Areas were normally drawn with sharp borders, even while dialectologists conceded that they often witnessed gradual, unsharp boundaries.	

*Note1: 从离散，绝对的分界线，到可能的连续变体*

实践难度：Traditional dialectology often relied on extremely knowledgeable practitioners – both field workers and project managers.

> 研究者的权威性是传统方言学成果的保证。

Goebl: clustering as a means of detecting dialect areas,

Goebl noted further that dialect areas are often hierarchically organized, means shared features that distinguish them from others.

层级聚类 --***hierarchical clustering***

Goebl’s work on clustering pushed the discussion concerning the determination of dialect boundaries to a new, more replicable level.

## 聚类算法的一些问题

1. 非常的不稳定，输入的微小变化对于输出影响大。

一些改进，类似BOOTSTRAP类型的重采样手段；此类方法增加了聚类过程的稳定性.

> These procedures indeed solve the stability problem when parameters are chosen judiciously (Nerbonne et al., 2008)

2. 进一步的方法，层级模型，算法的使用；

例如：WPGMA amd UPGMA

非加权组平均法(unweighted pair-group method with arithmetic means, UPGMA或average linkage) 主要思路应该是对特定feature的一些加权； 同时，提供了一些可行的聚类有效性评估参数

Modified Rand index, entropy, and purity

3. 更有效的聚类算法的研究依然是焦点之一。

# 距离相关的研究 -- Distance related research

不同于传统的方言研究，计算语言学的研究的中心之一为距离的计算；可以包括以下三个部分：

1. phonetics (mainly)
2. morphology
3. lexicology and syntax 

为什么计算距离：

>  a very simple, yet efficient way commonly used in dialectometry to infer pronunciation differences between language varieties.

It has successfully been applied to many languages in aggregate analysis of dialect varieties: Dutch (Nerbonne et al., 1996; Heeringa, 2004; Wieling et al., 2007), Sardinian (Bolognesi and Heeringa, 2002), Norwegian (Gooskens and Heeringa, 2004), German (Nerbonne and Siedle, 2005), American English (Nerbonne, 2015b), and Bulgarian (Osenova et al., 2009).

对于汉语方言的研究： （similar)  digging

Typological variation across Mandarin dialects: An areal perspective with a quantitative approach

Applying Functional Partition in the Investigation of Lexical Tonal-Pattern Categories in an Under-Resourced Chinese Dialect

Funny topic: 

Mutual intelligibility and similarity of Chinese dialects

## 距离计算的主要方法

### Edit distance, known as Levenshtein distance

例子： Dutch word *hart* – [hArt] and [ært@], the algorithm produces the following alignment:

![image-20210122235919504](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20210122235919504.png)

可以用来比较 phonetic transcription的差异：

### Automatically Induced Segment Distances

data-driven solution to segment comparison

frequencies-based model 

They then weighted the edit operation costs using (an inverse of) point wise mutual information (PMI) with edit distance algorithm in order to let operation costs reflect the likelihood of two segments being involved in a substitution.

 PMI can gauge how similar or distant two phones are; the more often they are aligned, the bigger the similarity between them and vice versa. 

:deciduous_tree: 具体的实践操作需调研： 

Wieling et al. (2012) found that PMI induced segment distances correlate well with acoustic distances in formant space (0*.*61 *< r <* 0*.*76) measured on six dialect data sets.

PMI-weighted alignments (Jager, 2013, 2015)

此类研究方法已有较为完备的python包： :package: *LingPy library,*([Python Library for Historical Linguistics — LingPy](https://lingpy.org/))

:deciduous_tree: worth to try ! 

###  Criticism

> Edit distance has often been criticized as linguistically naive and too simple.

问题一：The criticism arises because linguists are interested not only in determining main dialect areas, but also in discovering linguistic details behind those divisions

分类，聚类算法的问题之一是难以同时保证准确性和完备的可解释性，即模型并没有提供知识。

问题二：  this approach based on manually prepared phonetic transcriptions, Heavily rely on phonetic transcriptions.

过高的依赖高准确度的转写数据是此类方法的一个弊端，acoustic phonetics 或者 articulography 可进行一定克服。

## 区别特征 -- Distinctive elements

In order to identify distinctive characteristics of dialect areas

目标是确认该区域内，最具有差异性的特质，有如下相关研究和方法。（基于统计 mainly) 

Prokic suggested  Fisher’s linear discriminant that seeks features which differ little within the group in question and a great deal outside that group. 

（特定特征的内部差异性小 和外部比较的差异性大 :scroll:重要）

:grey_question:  Good questions : which individual variables are most characteristic for a given variety.

1. principle component analysis (PCA) 
2.  factor analysis

:thought_balloon: 关于区别特征的选择，一方面，feature的数量是决定是否可以成功聚类的关键，数量越大，即可能的参数量越大，分类聚类的效果应该更好，另一方面，在较少的feature情况下，特定明显区分的feature可有效区分，其他feature可能比较冗余。

无论是基于判别分析，降维算法，因子分析，目的是寻找是否存在明显区别特征的feature，同时在分类，聚类中占据较大的权重。此类feature的提取，最好是本身具有强解释性，这样可以同时提供高分类准确度和人类所需要的知识。

# 分布的研究 -- **Geography of distributions**

最基础，最普遍的问题 ：Location of dialects 

在传统的方言研究中，已经得到较为完整的回答。是否可以更加的reliable？ 

:notebook: 传统方言研究和计算方言学的结合，若基于人类知识和基于数据驱动的方式得出类似的结论，说明其结果更有一定的可靠性。

部分研究： 使用不同的聚类（降维）方法。

1. multi-dimensional scaling (MDS)

使用此类方法的好处：, MDS does not assume that varieties are aligned with discrete sets of data collection sites which then project to dialect areas. Instead, dialect continua can likewise be detected. 

distributed continuously, not categorically,

从离散到连续。**alect continua**

![image-20210123155240371](C:\Users\LENOVO\AppData\Roaming\Typora\typora-user-images\image-20210123155240371.png)

Wieling and Nerbonne (2015) 关于荷兰方言的研究

:notebook:  从离散到连续，可以间接的体现出特定的方言之间的互相影响，尤其方言区域之间边界位置的特定。

:thought_balloon: 思考： 无论是离散还是连续，多特征的降维是此类研究的关键，同时，是否可以解读降维后的结果也非常重要。

除去熟悉的PCA MDS 之外，还有一些高效的降维手段可以实践，例如 [t-sne]( **t-SNE(t-distributed stochastic neighbor embedding)**) 、[umap](Uniform Manifold Approximation and Projection for Dimension Reduction，一致的流形逼近和投影以进行降维) 在复杂数据上取得更好的效果。然而需要注意的是，降维的效果和结果的可解释性之间的关系，一些无监督的降维手段后，2 3 维中的距离并不完全反应其实际的差别，使得对其的解读更具有挑战性。

### Additional research：  Geo statistics and Topography**

方言的分布和地区本身的epidemiology, geology, ecology and environmental protection

# 研究结果的验证 -- **Validation**

Computational linguistics has emphasized the need to validate putative means of measuring linguistic features and linguistic difference.

## 人类对于相似度的评价 -- Human judgments of similarity

和前人的研究相互证明，同时需要高水平的听者进行判断。

此部分可归类为 主观评价。听者的听辨结果应该被认定为golden standard，不过听辨者需要认真的选取，例如

The subjects in Wieling et al.’s experiment were predominantly linguists, or at least linguistically informed listeners, as they had responded to an appeal in the *Language Log* (http://languagelog.ldc.upenn.edu/) to participate as subjects. 

主观评价是验证结果有效性的关键，不过听者的选择是较为困难的问题。

## 声学特征 -- Acoustic characterizations

除了听觉上的评价，另一种有效的方法为声学特征的评价，此部分可归类为 客观评价。

伴随着技术的进步，音频文件的存贮和获取更加的方便，而非仅仅关注与转写上的差异，可以进一步的比较和使用音频来验证试验的结果。

更加鲁棒的研究方法 ：transcription-based work  that does not rely on transcription only .

例如 研究 使用试验语音学的方法研究音段的差异，例如共振峰（Format-based) 

最新的一篇文章 比较了 MFCC-based 和 transcription-based 的距离比较，结论证明了 especially speaker-based cepstral mean and variance normalization 对于距离的影响较大。 

>  Bartelds, M., Richter, C., Liberman, M., & Wieling, M. (2020). **A New Acoustic-based Pronunciation Distance Measure.** *Frontiers in Artificial Intelligence.*

 :question:虽然该论文取名为new measure，但粗略的阅读下感觉此方法是在语音识别或发音偏误检测中非常常用的一种，还需要再仔细读一下 note！关于音段距离的研究，剑桥大学的研究者 也有相应的成果，若此方向有效，有诸多可以推进的点。

## Articulography

a new direction of research in dialectology is focusing on the underlying movements of the tongue and lips.

调音器官的运动轨迹是方言研究的一个新方向。使用特定的仪器，例如 Electropalatography 可以得出相当有说服力的结论。

例如：Wieling 2016  Espinosa 2007 

调音器官的运动轨迹，本身也是一种运动曲线，使用线性/非线性回归模型，GAM模型等 方法拟合后可以进行有效的分析。

# 可能的研究课题 -- **Emerging opportunities and issues**

1. 主要的研究还集中于语音方向，对于 形态学 句法等研究较少，但其结论本身应该很有价值。取决于方言本身的差异性仅仅体现在音段，而非其他语言学相关领域。
2. 从类别categorical 到连续 continuum
3. 基于频率的研究 ，应该是方法论的改进，数据中，对于高频率的词应该给予更高权重，一些特定的低频率词可能可以舍弃。
4. 方言和社会语言学的交互。
5. improvements in the linguistic characterization of the dialect differences. 



- 调研中的额外有趣课题： 
  - 互相理解度研究：大多数中国人可以使用普通话和方言，并且较为熟练的转换。不同方言之间，和方言和普通话之间，存在着可能的Mutual intelligibility （Tang 2007)



