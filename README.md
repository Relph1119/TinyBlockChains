# 记录自己学习《从零开始自己动手写区块链》这本书的全部过程 #

本书上传的所有代码都是可以运行的，在此附上本书源码的github地址：
[https://github.com/YaoyaoBae/simchain](https://github.com/YaoyaoBae/simchain)<br/>
在此向本书作者表示感谢

## 运行环境 ##
Python 版本：3.7.2  
PyCharm 版本：PyCharm 2018.3.5 (Professional Edition)

## 代码结构 ##
<pre>
note
|    +----ch2.3_SimchainIntroduction.ipynb----------------Simchain简介
|    +----ch3.2.1_HashAlgorithm.ipynb---------------------哈希算法
|    +----ch3.2.2_PrivateKeyPublicKeyAddress.ipynb--------私钥、公钥和地址
|    +----ch3.2.3_EllipticCurve.ipynb---------------------椭圆曲线
|    +----ch3.2.5_EllipticCurveCryptography.ipynb---------椭圆曲线加密
|    +----ch3.2.6_Wallet.ipynb----------------------------钱包
|    +----ch3.4.2_BasicLattice.ipynb----------------------格基础知识
|    +----ch3.4.3_LatticeProblem.ipynb--------------------格问题
|    +----ch3.4.6_GGH&Lyubashevshy.ipynb------------------GGH数字签名
|    +----ch4.1_CreateTransactions.ipynb------------------创建交易
|    +----ch4.3_VerifyingTransactions.ipynb---------------验证交易
|    +----ch4.5_ProgrammableTransactions.ipynb------------可编程的交易
|    +----ch5.1_Block.ipynb-------------------------------区块
|    +----ch5.2_BlockChain.ipynb--------------------------区块链
|    +----ch6.1_ConsensusAlgorithm.ipynb------------------常见的共识算法
|    +----ch6.2_CreateCandidateBlocks.ipynb------------创建候选区块、挖矿、打包、广播
|    +----ch6.4_VerifyBlock.ipynb----------------------验证区块
|    +----ch6.6_AddtoBlockChain.ipynb---------------------添加到区块链
src
</pre>

## 运行截图 ##
区块链运行的截图，全部都来自于[模拟器的GUI游戏](https://github.com/YaoyaoBae/Blockchain-simulator-exe)，非常感谢作者创建了这个模拟器，能更好的理解区块链原理。
1. 点击开始按钮  
![image](https://github.com/Relph1119/TinyBlockChains/blob/master/pics/begin.png)
2. 创建随机交易  
![image](https://github.com/Relph1119/TinyBlockChains/blob/master/pics/random.png)  
在共识之前都是未确认的交易    
![image](https://github.com/Relph1119/TinyBlockChains/blob/master/pics/unconfirmed.png)
3. 创建共识  
![image](https://github.com/Relph1119/TinyBlockChains/blob/master/pics/mining.png)  
我们可以看到交易在达成共识后得到确认。获胜者得到了奖励和交易费。  
![image](https://github.com/Relph1119/TinyBlockChains/blob/master/pics/reached.png)

4. 执行定向交易  
我们可以让英雄与他人交易。但最多只有1000分。  
![image](https://github.com/Relph1119/TinyBlockChains/blob/master/pics/one.png)  
之后，我们只能看到网络中的一个交易，达成共识后将交易写入区块链。  
![image](https://github.com/Relph1119/TinyBlockChains/blob/master/pics/onedone.png)  
5个随机交易将持续进行并达成共识。  
![image](https://github.com/Relph1119/TinyBlockChains/blob/master/pics/five.png)

5. 添加新的节点  
![image](https://github.com/Relph1119/TinyBlockChains/blob/master/pics/add.png)  
![image](https://github.com/Relph1119/TinyBlockChains/blob/master/pics/last.png)

## 个人总结 ##
&emsp;&emsp;看完整本书前后用了3个月，由于本书的代码示例采用的都是Python Shell，于是笔者把代码示例都搬到了Jupyter Notebook上，书中有一些代码漏写了，在本次学习中都已经补写了，需要区块链入门的小伙伴可以参考。  
&emsp;&emsp;本书主要讲了区块链相关的原理，主要还是创币和、发币、交易、加密和共识。作为区块链入门，还是一本很不错的书，书中的代码示例还是很详细的，比一般的介绍区块链的书籍要好很多。笔者敲完了书中所有的示例代码，对于区块链的原理有了一定的理解。  
&emsp;&emsp;上传的git代码中note文件夹下面是笔者在练习时的Jupyter NoteBook笔记，里面包括了书中所有的Python Shell的代码示例，由于生成区块链网络的随机性，生成的网络和书中不一样，但是并不影响本书的代码练习和原理理解。

## 区块链原理总结 ##
&emsp;&emsp;系统由对等节点构成P2P网络，为交易和区块的传播提供基本条件，交易和区块又由节点创建和负责传播。区块链系统采用的是分布式存储，为了保证所有节点数据的一致性，需要一个分布式共识过程。UTXO是指用户资产存储在交易的未消费输出但愿你中，加密算法对UTXO进行锁定，应用梅克尔树根哈希值对交易数据进行归纳。采用工作量证明算法进行对“挖矿”的奖励。分布式存储的区块链要保证数据一直，必须要达成全网共识，采用工作量证明的共识算法。  
&emsp;&emsp;健康的区块链系统必须具备四要素：P2P网络、连续的交易、足够多的存储节点，以及足够多的共识节点。当P2P网络搭建完成后，节点发起的交易通过泛洪路由协议在网络中传播，其他节点对照自己的区块链数据独立验证交易的有效性，有效交易被存放在各自的交易池中，然后打包之后，将区块广播到网络中，其他节点对照自己的区块链数据独立验证区块的有效性，如果有效且符合添加原则，则会扩展自己的链条，从而保证了全网数据的一致。以上就是区块链系统的工作过程。