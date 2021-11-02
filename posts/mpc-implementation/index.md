# MPC 实现方案归纳

 
之前做MPC相关的基本都是理论上的东西，效率很差，感觉也没有实现的必要。
最近几年基于秘密分享的MPC方案效率很高，有很多人用这个来做机器学习框架(PPML)，实际的实现方案变多了。
但还是想吐槽一些有些论文不给出代码实现:angry:。

## 两方实现方案(2 PC)
- [ABY DNSS15](https://github.com/encryptogroup/ABY) - "ABY – A Framework for Efficient Mixed-Protocol Secure Two-Party Computation"
通用安全多方计算框架，基于算数分享(arithmetic)，二进制分享(binary)，混淆电路(garble circuit)三者之间的转换，解决非线性函数的计算问题。


## 三方实现方案(3 PC)
- [ABY3 CCS18](https://github.com/ladnir/aby3) - "ABY3: A Mixed Protocol Framework for Machine Learning"
基于ABY方案的转换思想，诚实方占多数的安全假设，半诚实安全的乘法无需乘法triple，性能提升很大。
- [SecureNN (PETS 2019)](https://github.com/snwagh/securenn-public) - "SecureNN: 3-Party Secure Computation for Neural Network Training" 
由两方完成计算过程，引入协作参与方进行triple等随机量的生成，方案中比较协议比较复杂，存在可优化余地。
- [Falcon (PETS 2021)](https://github.com/snwagh/falcon-public) - "Falcon: Honest-Majority Maliciously Secure Framework for Private Deep Learning" 
SecureNN方案与ABY3方案的结合，应该是目前最好的三方计算框架。
- [TF-encrypted](https://github.com/tf-encrypted/tf-encrypted) - "Private Machine Learning in TensorFlow using Secure Computation"
基于TensorFlow实现PPML中常见的各种运算。
- [CrypTen](https://github.com/facebookresearch/CrypTen) - "CRYPTEN: Secure Multi-Party Computation Meets Machine Learning" 
Facebook基于Pytorch实现的PPML机器学习框架，支持机器学习中常见的各种运算，学习成本低。

## SPDZ方案实现
- [SPDZ family](https://github.com/data61/MP-SPDZ) - "Multiparty Computation from Somewhat Homomorphic Encryption"
实现了SPDZ及其衍生出的多种协议，支持各种安全性假设

## 常用密码学工具
- [libOTe](https://github.com/osu-crypto/libOTe) - 
基于C++实现的OT协议库，包含各种常用的OT协议及OT扩展协议
- [EMP-tookit](https://github.com/emp-toolkit) - 
包含MPC中常用的密码学工具：OT，zero knowledge proof等，以及一些两方计算协议的实现



