

Transformer:

##### 总览：

![image-20220518212949139](./图片/:Users:zhangpengfei:PycharmProjects:interview:图片:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518212949139.png)



![image-20220518213145664](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518213145664.png)

![image-20220518213254304](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518213254304.png)



1. 6个encoder的结构相同，6个decoder的结构相同，但是参数并不相同，每个encoder和decoder单独训练

##### 拆解：

![image-20220518213847347](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518213847347.png)

![image-20220518214029434](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518214029434.png)

下面首先介绍一下RNN:

隐含层共享权重参数

2. RNN的梯度梯度消失：

由于连乘导致远距离梯度接近为0，总梯度被近距离梯度主导

3. 因为transformer的输入不是像RNN一样按序列顺序输入，而是序列中的所有字一起输入，忽略了顺序，所以需要位置编码

![image-20220518214132079](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518214132079.png)



![image-20220518215955584](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518215955584.png)

![image-20220518220216899](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518220216899.png)

##### 注意力机制

![image-20220518220503279](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518220503279.png)

self-attention原理：

![image-20220518220834718](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518220834718.png)

![image-20220518221526314](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518221526314.png)

![image-20220518221636255](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518221636255.png)

![image-20220518221804272](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518221804272.png)

![image-20220518222126043](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518222126043.png)

##### 残差和LayNorm

![image-20220518222238488](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518222238488.png)

![image-20220518222733956](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518222733956.png)

Batch notmalization: 

针对样本特征的同一纬度进行处理，在NLP任务中效果很差

优点：1. 解决内部协变量偏移，2. 缓解梯度饱和问题，加快收敛，但不会挺高精度。

缺点： batch size比较小的话，效果比较差；在RNN中效果比较差(因为BN是在对batch中相同位置的单词做BN, 但是相同位置的单词并不代表相同的语义信息，而LN是对每个输入序列做LN，在相同的语义空间里)；



![image-20220518223904358](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518223904358.png)

##### Decoder

![image-20220518224035400](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518224035400.png)

Masked Multi-Head Attention: 需要对当前词和之后的词做mask

![image-20220518224457152](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518224457152.png)

![image-20220518224555158](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518224555158.png)

![image-20220518224629626](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518224629626.png)

注意： decoder时，q来自于本身，k和v来自于encoder

![image-20220518224929120](./图片/:Users:zhangpengfei:Library:Application Support:typora-user-images:image-20220518224929120.png)















































