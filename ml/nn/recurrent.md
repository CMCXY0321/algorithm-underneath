#### 循环神经网络
循环神经网络的提出便是基于记忆模型的想法，期望网络能够记住前面出现的特征，并依据特征推断后面的结果，而且整体的网络结构不断循环，因为得名循环神经 
网络

#### 循环神经网络的基本结构
循环神经网络的基本结构特别简单，就是将网络的输出保存在一个记忆单元中，这个记忆单元和下一次的输入一起进入神经网络中。

#### 自然语言处理的应用

- 词嵌入
对于每个词，可以使用一个高维向量去表示它，这里的高维向量和one-hot 的区别在于，这个向量不再是0 和1 的形式，向量的每一位都是一些实数，而这些实数隐含着这个单词的某种属性

- 词嵌入的PyTorch 实现
  - N Gram 模型
  - 单词预测的PyTorch 实现

#### 词性判断
- 基本原理
定义好一个LSTM 网络，然后给出一个由很多个词构成的句子，根据前面的内容，每个词可以用一个词向量表示，这样一句话就可以看做是一个序列，序列中的每个元素都是一个高维向量，将这个序列传入LSTM，可以得到与序列等长的输出，每个输出都表示为对词性的判断
- 字符增强
就是说一些单词存在着前缀或者后缀，比如-ly 这种后缀很可能是一个副词，这样我们就能够在字符水平上对词性进行进一步判断，把两种方法集成起来，能够得到一个更好的结果
