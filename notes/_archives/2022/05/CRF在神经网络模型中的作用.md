BERT + CRF
===

CRF层可以为最后预测的标签添加一些约束来保证预测的标签是合法的。在训练数据训练过程中，这些约束可以通过CRF层自动学习到。

这些约束可以是：

I：句子中第一个词总是以标签“B-“ 或 “O”开始，而不是“I-”

II：标签“B-label1 I-label2 I-label3 I-…”,label1, label2, label3应该属于同一类实体。例如，“B-Person I-Person” 是合法的序列, 但是“B-Person I-Organization” 是非法标签序列.

III：标签序列“O I-label” is 非法的.实体标签的首个标签应该是 “B-“ ，而非 “I-“, 换句话说,有效的标签序列应该是“O B-label”。

有了这些约束，标签序列预测中非法序列出现的概率将会大大降低。

- [相关资料](#相关资料)

## 相关资料
https://www.dounaite.com/article/625768fcae87fd3f795f7035.html
