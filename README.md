# 跨模态检索：图像——文本检索
媒体计算实践作业：图像——文本跨模态搜索

## 数据集下载
本项目使用的是[Flickr30k数据集](http://shannon.cs.illinois.edu/DenotationGraph/data/index.html)，你需要自行先下载。
[百度云地址](https://pan.baidu.com/s/10z2LTaQWzIlfBuQOunf7yA)

## 数据预处理

在Preprocessing下:
- `data_split_1.py` 划分训练集、测试集、验证集
- `resize_data_2.py` 长宽比例不变，将短边拉伸为256
- `count_vocab_3.py` 统计每个单词的词频
- `convert_annotations_4.py` 将.txt格式的标注文件转换为.json
- `build_dictionary_5.py` 构建单词编号，即查询字典

## 模型训练

在数据预处理完成后，在`config.py`中配置各文件的路径以及训练的参数，并且下载在谷歌新闻上预训练的[Word2Vec模型](https://pan.baidu.com/s/1Q9Z-Z8qWxCjNbFmXMty8Dw)
- `trainStage1.py` 使用分类损失预训练
- `trainStage2.py` 使用三元组损失和对抗损失微调

## 测试界面

在 QueryApp 下的 [图文互搜.exe](https://pan.baidu.com/s/104cT0qy3rOKkAilVSkYXuw) 提供简单的测试界面。

需要提前下载预训练模型[imgcnn.pth和textcnn.pth](https://pan.baidu.com/s/1vtLcsHwiTqSkLHvKR-oqbA)到`DATA/Checkpoint`下方便自动初始化，

[captions_database.pkl](https://pan.baidu.com/s/1k_csdkpMaJV9bbv0729jpw)和[images_database.pkl](https://pan.baidu.com/s/1b4L51_225vL9pW9EqsusgA)事先提取的图像和文本特征以及其索引到`DATA/`下，

字典[text_info.json](https://pan.baidu.com/s/1dlG067OS_ZKeDKxnVqtc_Q)到`DATA/Flick_10k`，

图片数据到`DATA/Flick_10k/flick_image_256`下。也可以自己选择路径，但是后续检索的时候不支持自动初始化。

测试结果如下：

![](https://github.com/EternallyTruth/Cross-modal-retrieval/blob/master/median_compute/Test/result.png)

## 参考资料
[双路CNN MatConvNet](https://github.com/EternallyTruth/Image-Text-Embedding)

[用于图文搜索的对抗学习 ACM2017](https://dl.acm.org/doi/10.1145/3123266.3123326)
