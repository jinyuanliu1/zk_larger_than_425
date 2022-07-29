# 零知识证明
证明六级分数大于425
# 零知识证明简介
我们一提到零知识证明，首先想到的一定是阿里巴巴的故事，这个生动的小故事给我留下了深刻的印象：


![image](https://user-images.githubusercontent.com/75195549/181715985-00638ed2-729b-4362-b1f7-1c80656d3214.png)




![image](https://user-images.githubusercontent.com/75195549/181716050-67dd6164-d26d-41a8-b9b1-156430db539a.png)





![image](https://user-images.githubusercontent.com/75195549/181716094-e007a488-7e6e-4d82-9088-83404d91b385.png)



经过学习我们知道，零知识证明是一种能力，这种能力能够让一方（the prover, 证明者）可以向另一方（the verifier, 证明者）证明他们知道值x，而无需传达任何信息，除了他们知道值x。零知识证明的本质是，通过简单地揭示信息来证明某人具有某些信息的知识是微不足道的。面临的挑战是在不透露信息本身或任何其他信息的情况下证明拥有这种财产。


​		根据零知识证明的定义可以得知零知识证明具有以下三个重要的性质：

1. 完备性（`Completeness`）：只要证明者拥有相应的知识，那么就能通过验证者的验证，即证明者有足够大的概率使验证者确信。；
2. 可靠性（`Soundness`）：如果证明者没有相应的知识，则无法通过验证者的验证，即证明者欺骗验证者的概率可以忽略。
3. 零知识性（`Zero-Knowledge`）：证明者在交互过程中仅向验证者透露是否拥有相应知识的陈述，不会泄露任何关于知识的额外信息。

​		根据零知识证明的定义可以得知零知识证明具有以下三个重要的性质：

1.高效性：该过程计算量小，双方交换的信息量少。

2.安全性：其依赖于未解决的数学难题，如离散对数、大整数因子分解、平方根等。

3.许多零知识证明相关的技术避免了直接使用有政府限制的加密算法，这就给相关产品的出口带来了优势。


​		根据零知识证明的方式，可以分为交互式和非交互式。交互式一般是通过挑战响应的方式，非交互式一般通过承诺方案来实现。








# 符号简介


本人实在没有解决这个符号书写的问题，故在此说明一下符号的意义：




ECC曲线参数P: 大素数


ECC曲线参数G：基点

g：成绩

m：moe


id：i

# ECC方法构造方案

**成绩发布：**

2. 生成随机数k，计算$R=(g+k)*G$，考生保存$kG$，也就是说，考生可以计算得到$(k+1)G,(k+2)G...(k+g)G$
3. 使用MoE的私钥sk进行签名：$sig\_by\_m = signature_{sk}(cn\_i||year||R)$



**零知识证明：**

假如此时正在面试，考官要求学生提供零知识证明CET6成绩超过425（如果没超过，就当考官没说）

1. 考生向考官提供$sig\_by\_m$，考官通过验证平台或其他方式，使用MoE的公钥验证签名，得到$R=(g+k)*G$
2. 考官发起挑战，要求学生提供$r=(g+k-425)*G$
3. 如果学生成绩大于425，那么$g+k-425>k$，即学生可以提供$r'=(g+k-425)*G$，考官验证 $r==r'$，如果相等则通过验证。



**合理性说明：**

​		两个方案中都是利用成绩和随机数k做了一个计算链，同时允许考生知道其中的g个值，因为是单向函数，所以考生也只能提供这g个值。在零知识证明时，向考生请求g+k-425，那么考生的g必须大于425才能提供正确的值，因此可以实现正确性证明。
