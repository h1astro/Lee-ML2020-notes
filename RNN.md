# RNN      LSTM

循环神经网络（Recurrent Neural Network，RNN）是一种用于处理序列数据的神经网络。相比一般的神经网络来说，他能够处理序列变化的数据。比如某个单词的意思会因为上文提到的内容不同而有不同的含义，RNN就能够很好地解决这类问题。

![image-20200413100626953](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413100626953.png)

![image-20200413100722870](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413100722870.png)

![image-20200413100749878](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413100749878.png)

RNN不一定传中间的，还可以将$y^t$的权重传入到下一层

![image-20200413100823291](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413100823291.png)

此外还有双向的循环神经网络 Bidirectional RNN

![image-20200413100956805](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413100956805.png)



## LSTM

长短期记忆（Long short-term memory, LSTM）是一种特殊的RNN，主要是为了解决长序列训练过程中的梯度消失和梯度爆炸问题。简单来说，就是相比普通的RNN，LSTM能够在更长的序列中有更好的表现。

有四个输入和一个输出

三个门gate，输入门(Input Gate), 遗忘门(Forget Gate), 输出门(Output Gate)

记忆单元(Memory Cell)

![image-20200413101054555](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413101054555.png)

![image-20200413120523842](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413120523842.png)

LSTM举例

这里x2=1时表示输入门允许输入的相加，

当x2=-1时，遗忘门进行清零，

当x3=1的时候，输出门输出。 

![image-20200413103359142](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413103359142.png)

举例两个实际运算，每个门假设是固定的这四个权重，第一个输入门趋向为关闭，如果第二个输入值为正且＞1/10，会选择允许进入，否则输入为0；第二个遗忘门趋向不遗忘...

![image-20200413120352935](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413120352935.png)

![image-20200413115239868](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413115239868.png)

![image-20200413115308796](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413115308796.png)

分别输入到四个输入出

![image-20200413120600533](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413120600533.png)



![image-20200413121347006](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413121347006.png)

![image-20200413121502698](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413121502698.png)



![image-20200413121439621](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413121439621.png)

RNN存在梯度消失梯度爆炸

![image-20200413121706286](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413121706286.png)

如果一个权重只比1多了一点点，累计下去会导致输出很大

如果一个权重只比1小了一点点，累计下去会导致输出为0

![image-20200413121548484](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413121548484.png)

但是LSTM可以通过门来解决梯度消失和梯度爆炸

![image-20200413121625666](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413121625666.png)

## 语音识别

如果对向量序列识别出多个好好好棒棒棒棒棒，然后进行重复字删除，那么会出现一个问题：如果识别“好棒棒”呢

![image-20200413124055619](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413124055619.png)

出现了CTC的方法，对有些取null，提取的时候删除null，可解决这个问题

![image-20200413125411649](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413125411649.png)

需要这样训练，全部的可能性？

![image-20200413125529777](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413125529777.png)

![image-20200413125729323](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413125729323.png)



![image-20200413125810376](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413125810376.png)



![image-20200413125756162](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413125756162.png)

![image-20200413125841870](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413125841870.png)

## ATTENTION 注意力



![image-20200413121912818](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413121912818.png)

![image-20200413125919748](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413125919748.png)



![image-20200413130018731](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413130018731.png)

![image-20200413130038828](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413130038828.png)

![image-20200413130057491](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413130057491.png)

![image-20200413130132569](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413130132569.png)

可进行融合

![image-20200413130154271](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413130154271.png)

![image-20200413130215077](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413130215077.png)

![image-20200413130243667](C:\Users\10653\AppData\Roaming\Typora\typora-user-images\image-20200413130243667.png)