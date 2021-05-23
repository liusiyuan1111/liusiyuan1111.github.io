---
title: 论文翻译：Deep Image Retrieval  A Survey
date: 2021-02-05 19:53:38
tags:
- 论文翻译
- 图像检索
- 深度学习
- Paper
- CV
---

# Deep Image Retrieval: A Survey

深度图像检索综述

**Abstract**—In recent years a vast amount of visual content has been generated and shared from various fields, such as social media platforms, medical images, and robotics. This abundance of content creation and sharing has introduced new challenges. In particular, searching databases for similar content, i.e., content based image retrieval (CBIR), is a long-established research area, and more efficient and accurate methods are needed for real time retrieval. Artificial intelligence has made progress in CBIR and has significantly facilitated the process of intelligent search. In this survey we organize and review recent CBIR works that are developed based on deep learning algorithms and techniques, including insights and techniques from recent papers. We identify and present the commonly-used benchmarks and evaluation methods used in the field. We collect common challenges and propose promising future directions. More specifically, we focus on image retrieval with deep learning and organize the state of the art methods according to the types of deep network structure, deep features, feature enhancement methods, and network fine-tuning strategies. Our survey considers a wide variety of recent methods, aiming to promote a global view of the field of instance-based CBIR.
**Index Terms**—Content based image retrieval, Deep learning, Convolutional neural networks, Literature survey

**摘要**—近年来，从社交媒体平台、医学图像和机器人技术等各个领域产生并共享了大量视觉内容。这种丰富的内容创建和共享带来了新的挑战。特别是，在数据库中搜索相似的内容，即基于内容的图像检索(CBIR)，是一个由来已久的研究领域，实时检索需要更有效和更准确的方法。人工智能在CBIR取得了进展，极大地促进了智能搜索的进程。在这篇综述中，我们组织和回顾了CBIR最近的工作，这些工作是基于深度学习算法和技术开发的，包括来自最近论文的算法和技术。我们确定并介绍了该领域常用的基准和评估方法。我们收集共同的挑战，并提出有前景的未来研究方向。更具体地说，我们关注具有深度学习的图像检索，并根据深度网络结构、深度特征、特征增强方法和网络微调策略的类型来组织最先进的方法。我们的综述考虑了各种各样的最新方法，旨在促进基于实例的CBIR领域的全球视野。

**索引**—基于内容的图像检索、深度学习、卷积神经网络、文献综述

## **1 INTRODUCTION**

## **1 引言**

CONTENT based image retrieval (CBIR) is the problem of searching for semantically matched or similar images in a large image gallery by analyzing their visual content, given a query image that describes the user’s needs. CBIR has been a longstanding research topic in the computer vision and multi-media community [1], [2]. With the present, exponentially increasing, amount of image and video data, the development of appropriate information systems that efficiently manage such large image collections is of utmost importance, with image searching being one of the most indispensable techniques. Thus there is nearly endless potential for applications of CBIR, such as person re-identification [3], remote sensing [4], medical image search [5], and shopping recommendation in online markets [6], among many others.

基于内容的图像检索(CBIR)是通过分析图像的视觉内容，在大型图像库中搜索语义匹配或相似的图像的问题，给出描述用户需求的查询图像。CBIR一直是计算机视觉和多媒体领域的一个长期研究课题。随着当前图像和视频数据量的指数级增长，开发能够有效管理如此大的图像集合的信息系统是至关重要的，其中图像检索是不可缺少的技术之一。因此，CBIR的应用潜力几乎是无穷无尽的，如行人重识别，遥感图像，医学图像检索，以及在线商城的购物推荐等等。

A broad categorization of CBIR methodologies depends on the level of retrieval, i.e., instance level and category level. In instance level image retrieval, a query image of a particular object or scene (e.g., the Eiffel Tower) is given and the goal is to find images containing the same object or scene that may be captured under different conditions [7], [8]. In contrast, the goal of category level retrieval is to find images of the same class as the query (e.g., dogs, cars, etc.). Instance level retrieval is more challenging and promising as it satisfies specific objectives for many applications. Notice that we limit the focus of this survey to instance-level image retrieval and in the following, if not further specified, “image retrieval” and “instance retrieval” are considered equivalent and will be used interchangeably. 

CBIR方法的广泛分类取决于检索的级别，即实例级和类别级。在实例级图像检索中，给出特定对象或场景(例如，埃菲尔铁塔)的查询图像，并且目标是找到包含在不同条件下可能被捕获的相同对象或场景的图像。相比之下，类别级检索的目标是找到与查询相同类别的图像(例如，狗、汽车等))。实例级检索更具挑战性和前景，因为它满足了许多应用程序的特定目标。注意我们将本次综述的重点限于实例级图像检索，在下文中，如果没有进一步说明，“图像检索”和“实例检索”被认为是等效的，将可互换使用。

Finding a desired image can require a search among thousands, millions, or even billions of images. Hence, searching efficiently is as critical as searching accurately, to which continued efforts have been devoted [7], [8], [9], [10], [11].To enable accurate and efficient retrieval of massive image collections,compact yet rich feature representations are at the core of CBIR.

找到想要的图像可能需要在数千、数百万甚至数十亿张图像中进行搜索。因此，有效的搜索和精确的搜索一样重要，对此人们一直在努力，参考文献7-11。为了准确高效地检索大量图像集合，紧凑而丰富的特征表示是CBIR的核心。

In the past two decades, remarkable progress has been made in image feature representations, which mainly consist of two important periods: feature engineering and feature learning (particularly deep learning). In the feature engineering era (i.e., pre-deep learning), the field was dominated by milestone hand-engineered feature descriptors, such as the Scale-Invariant Feature Transform (SIFT) [19]. The feature learning stage, the deep learning era since 2012, begins with artificial neural networks, particularly the breakthrough ImageNet and the Deep Convolutional Neural Network (DCNN) AlexNet [20]. Since then, deep learning has impacted a broad range of research areas, since DCNNs can learn powerful feature representations with multiple levels of abstraction directly from data. Deep learning techniques have attracted enormous attention and have brought about considerable breakthroughs in many computer vision tasks, including image classification [20], [21], [22], object detection [23], and image retrieval [10], [13], [14].

在过去的二十年里，图像特征表示取得了显著的进展，主要包括两个重要阶段:特征工程和特征学习(特别是深度学习)。在特征工程时代(即深度学习前)，该领域由里程碑式的手工工程特征描述符主导，如尺度不变特征变换(SIFT) 。特征学习阶段，自2012年以来的深度学习时代，始于人工神经网络，特别是突破性的ImageNet和深度卷积神经网络(DCNN) AlexNet  。从那以后，深度学习影响了广泛的研究领域，因为数据挖掘神经网络可以直接从数据中学习具有多层次抽象的强大特征表示。深度学习技术已经引起了极大的关注，并在许多计算机视觉任务中带来了相当大的突破，包括图像分类、对象检测和图像检索。

Excellent surveys for traditional image retrieval can be found in [1], [2], [8]. This paper, in contrast, focuses on deep learning based methods. A comparison of our work with other published surveys [8], [14], [15], [16] is shown in Table 1. Deep learning for image retrieval is comprised of the essential stages shown in Figure 1 and various methods, focusing on one or more stages, have been proposed to improve retrieval accuracy and efficiency. In this survey, we include comprehensive details about these methods, including feature fusion methods and network fine-tuning strategies etc. , motivated by the following questions that have been driving research in this domain:

传统图像检索的方法可以在综述[1]、[2]、[8]中找到。相比之下，本文侧重于基于深度学习的方法。我们的工作与其他已发表的综述[8]、[14]、[15]、[16]的比较见表1。图像检索的深度学习由图1所示的基本阶段组成，并且已经提出了各种方法，集中在一个或多个阶段，以提高检索的准确性和效率。在本篇综述中，包括了这些方法的综合细节，特征融合方法和网络微调策略等，其动机是推动该领域研究的以下问题:

1) By using off-the-shelf models only, how do deep features outperform hand-crafted features?
2) In case of domain shifts across training datasets, how can we adapt off-the-shelf models to maintain or even improve
retrieval performance?
3) Since deep features are generally high-dimensional, how can we effectively utilize them to perform efficient image
retrieval, especially for large-scale datasets?

1)仅使用现成的模型，深度特征如何胜过手工制作的特征？

2)在跨训练数据集的领域转移的情况下，我们如何适应现成的模型来保持甚至提高检索性能？

3)由于深度特征通常是高维的，我们如何有效地利用它们来执行高效的图像检索，尤其是对于大规模数据集。

TABLE 1: A summary and comparison of the primary surveys in the field of image retrieval.

表1:图像检索领域主要综述文献的总结和比较。

![image-20210205203313875](https://i.loli.net/2021/02/05/bM8DLriRHAEPGvU.png)

![image-20210205203545671](https://i.loli.net/2021/02/05/U36pBOD87Ckujrd.png)

Fig. 1: In deep image retrieval, feature embedding and aggregation methods are used to enhance the discrimination of deep features. Similarity is measured on these enhanced features using Euclidean or Hamming distances.

图1:在深度图像检索中，使用特征嵌入和聚集方法来增强深度特征的区分度。使用欧几里德距离或汉明距离来测量这些增强特征的相似性。

