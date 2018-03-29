##How to destroy bitcoins?
###怎样销毁比特币

![BTCKeychain](https://www.flickr.com/photos/btckeychain/14276700855)
We know [how bitcoins are created](https://en.bitcoin.it/wiki/Mining), but how can they be destroyed?
我们已经了解了[比特币是怎么产生的](https://en.bitcoin.it/wiki/Mining)，但是它们可以被销毁吗？

Burning bitcoins is making them unspendable. This can have several uses, such as bootstraping another crypto-currency (like [Counterparty](http://counterparty.io/) did) or raising (negligibly) the value of the remaining bitcoins by reducing the number of spendable ones. This article will describe three ways that can be used to burn bitcoins.
销毁比特币的含义是使它们变得不可被消费。这种做法可以有几个用途：例如引流到另一种加密货币（像[Counterparty](http://counterparty.io/)所做的），或者通过减少可花费比特币的数量来（微不足道地）提高当前价格。这篇文章将介绍销毁比特币的三种方法。

---
####The simple way
####最简单的方法
Sending bitcoins to a bogus address (an address with no known private key) is an easy way to burn bitcoins. Fortunately, Bitcoin users have very very little chance to unwillingly burn Bitcoins this way as a 4 bytes checksum is present in its string representation hence preventing typos (a [complete guide to how Bitcoin addresses are created](https://en.bitcoin.it/wiki/Technical_background_of_version_1_Bitcoin_addresses) is available on the bitcoin wiki).
把比特币发送到一个（没人知道私钥的）伪造地址是销毁比特币最简单的方法。庆幸的是，由于字符串表示中存在一个 4 字节的校验和来防止拼写错误，比特币用户几乎没有机会通过这种方式来不情愿地销毁比特币（在比特币维基上有一个[创建比特币地址的完整指南](https://en.bitcoin.it/wiki/Technical_background_of_version_1_Bitcoin_addresses)）。

That’s why creating a bogus Bitcoin address requires more effort than just smashing a keyboard. In order to create one, its underlying hash160 is used as it can have any value and this value directly translates into the first characters of the address (the last ones represent the checksum).
这就是为什么创建一个伪造比特币地址需要花费更多的努力，而不是仅仅敲敲键盘就可以完成。为了创建一个伪造地址，会使用到它底层的 hash160 算法，该算法可以取任何值，同时这个值经过运算后直接转化成地址的第一个字符（而最后一个字符代表校验和）。

Known examples of bogus addresses are:
一些已知的伪造地址有：
- [1BitcoinEaterAddressDontSendf59kuE](http://blockchain.info/address/1BitcoinEaterAddressDontSendf59kuE) (2.10556692 BTC received),
- [1CounterpartyXXXXXXXXXXXXXXXUWLpVr](https://blockchain.info/address/1CounterpartyXXXXXXXXXXXXXXXUWLpVr) (2,130.84717717 BTC),
- [1111111111111111111114oLvT2](https://blockchain.info/address/1111111111111111111114oLvT2) (43.2884582 BTC), this address encodes the smallest possible hash160
- [1QLbz7JHiBTspS962RLKV8GndWFwi5j6Qr](https://blockchain.info/address/1QLbz7JHiBTspS962RLKV8GndWFwi5j6Qr) (0.01159201 BTC), and this one is the biggest possible hash160.

- [1BitcoinEaterAddressDontSendf59kuE](http://blockchain.info/address/1BitcoinEaterAddressDontSendf59kuE) (已收到2.10556692 BTC )，
- [1CounterpartyXXXXXXXXXXXXXXXUWLpVr](https://blockchain.info/address/1CounterpartyXXXXXXXXXXXXXXXUWLpVr) (2,130.84717717 BTC)，
- [1111111111111111111114oLvT2](https://blockchain.info/address/1111111111111111111114oLvT2) (43.2884582 BTC), 这个地址编码了最小可能性的 hash160 值，
- [1QLbz7JHiBTspS962RLKV8GndWFwi5j6Qr](https://blockchain.info/address/1QLbz7JHiBTspS962RLKV8GndWFwi5j6Qr) (0.01159201 BTC)，这个地址编码了最大可能性的 hash160 值。

While sending bitcoins to such an address is a pretty sure way to burn them, it is not a provably definitive one as a private key for this address could exist (however [finding out if it exists would require way more energy than our solar system could produce during its lifetime](https://i.imgur.com/fYFBsqp.jpg)).
虽然把比特币发送到这样的一个地址是销毁它们的一种比较确定的方法，但不是一种可证明的终极方法，因为伪造地址的私钥还是有可能存在的（然而发现私密是否存在需要消耗的能量比我们太阳系在其一生产生的能量还多）。

---
####The meaningful way
####有意义的方法
For a very long time, Bitcoin users have been including data in the blockchain whether it is to [prove document ownership](https://www.proofofexistence.com/) or [identity](http://onename.com/), to secure contracts or to [represent real world assets on the blockchain](https://en.bitcoin.it/wiki/Colored_Coins).
在很长一段时间，比特币用户一直向区块链中写入数据，无论是为了[证明文件所有者](https://www.proofofexistence.com/)还是[认证](http://onename.com/)，是为了保证合同还是[在区块链上代表真实世界资产](https://en.bitcoin.it/wiki/Colored_Coins)。

In 2013, an easy way to add data to any Bitcoin transaction was introduced. By making standard a previously invalid script instruction, OP_RETURN, a Bitcoin user could add up to 40 bytes of data to his transactions.
在 2013 年，引入了一种简单的向任意一笔比特币交易添加数据的方法。通过标准化上一区块无效脚本的指令，OP_RETURN，比特币用户可以为他的交易添加多达 40 个字节的数据。

Before the [standardization](https://github.com/bitcoin/bitcoin/pull/2738) this new output type, including data in the blockchain was not a straightforward task and involved using numerous bogus addresses to encode arbitrary data. The introduction this new output type made it easier and allowed Bitcoin nodes to prune this kind of outputs from their memory as they cannot be spent thereby limiting what developers called [blockchain bloat](http://www.coindesk.com/new-forms-spam-bloat-bitcoins-block-chain/).
在标准化这种新输出类型之前，向区块链写入数据不是一个简单的任务，需要使用数个伪造地址来编码任意数据。引入这种新输出类型使得任务更容易，并且允许比特币结点对内存中该种输出类型进行剪枝，因为它们是不可花费的，另一方面也缓解了开发者所说的区块链臃肿问题。

Since its introduction, [more than 3.66 BTC](http://p2sh.info/dashboard/db/op_return-statistics) have been spent in OP_RETURN outputs and the number of these outputs keeps growing, reflecting a move toward a more diverse use of the blockchain.
自从它发明后，超过 3.66 BTC 已经花费在 OP_RETURN 输出，并且这些输出在持续增长，这反映出区块链多元化使用的走向。

---

####The definitive way
####终极的方法
While the previous methods are effective, they do not really destroy bitcoins. You can still see them in the blockchain, it’s just that no one can spend them. However, there’s a way to effectively destroy bitcoins by removing them from the blockchain.
虽然前面所述的方法都是有效的，但是它们并没有真正意义上的销毁比特币。你仍然可以在区块链上看到它们，仅仅是没有人能够使用它们而已。然而，有一种通过把它们从区块链移除的方法能够永久地销毁比特币。

When I was building the new version of [p2sh.info](http://p2sh.info/), I made sure that I had not missed any transaction data so that the database was consistent. As a part of this process, I computed the number of existing bitcoins as the sum of bitcoins held in unspent, but confirmed, outputs. If everything is right, this sum should add up to the number of bitcoins in existence (and this number can be computed only by knowing the number of blocks in the main chain of the blockchain).
当我搭建 [p2sh.info](http://p2sh.info/) 新版本的时候，我需要确认我没有遗漏任何一笔交易数据来保证数据库的一致性。在该步骤的其中一个环节，我计算那些在未消费但已被确认的交易输出中的比特币数量。如果一切都没有问题，这个总和应该等于现有比特币的数量（这个数值只能通过区块链主链中已知的区块数来计算）。

However, I found out that 10.19768818 BTC were missing… At first, I thought I had missed some transactions or that there was a bug in my code. Upon further inspection, I found out that I was right: 1031 blocks did not redeem all of the block reward they were entitled to. The block reward is the combination of the generated coins (50BTC at the beginning of Bitcoin, halving every 210,000 blocks) and the fees contained in the block’s transactions.
然而，我发现 10.19768818 BTC 不见了...一开始，我以为我遗漏了某些交易，不然就是我的代码中有 bug 。经过进一步检查后，我发现我是对的： 有 1031 个区块没有兑现它们应得的所有区块奖励。区块奖励是由产生区块本身（最开始是 50 BTC，以后每产生 210,000 区块减半）和区块交易中包括的费用两部分组成。

These discrepancies may be due to the fact that miners missed some transactions’ fees or that a superfluous transaction fee was paid for the coinbase transaction itself and not included in the miner’s transaction output value or it may even be intentional, who knows.
这些差异可能是由于矿工遗漏了一部分交易费，或者为矿工奖励交易本身支付了多余的交易费用，但该费用没有包含在矿工交易输出的数据里面，或者甚至可能是故意的，鬼知道呢？

The first of these blocks dates back to May 18th, 2011 and the last one occured on August 15th, 2015 (it had only 1 satoshi missing and was apparently mined using [CoiniumServ](http://www.int6ware.com/products/coiniumserv/)). The majority of these blocks was mined between January 2012 and March 2013.
这种区块首次出现的日期可追溯到 2011 年 5 月 18 日，而最新的一次出现在 2015 年 8 月 15 日（只丢失了 1 聪，明显是在[CoiniumServ](http://www.int6ware.com/products/coiniumserv/)挖出的）。大多数这些区块是在 2012 年 1 月到 2013 年 3 月挖出的。

Several pools mined blocks not claiming all of the block reward. According to [Blocktrail](https://www.blocktrail.com/) API, [EclipseMC](https://eclipsemc.com/) and [Eligius](http://eligius.st/) were those that mined more than half of these blocks. What’s interesting to notice is that these two pools started mining them at the same time, suggesting they may have been using the same pool software. However, EclipseMC stopped mining them in September 2012 while Eligius didn’t (they stopped in January 2013) suggesting a split in pool software at that time. Other pools, like Slush, P2Pool, also mined such blocks, but only a few ones.
有好几个矿池挖矿声称不领取区块奖励。据说挖出超过一半这种区块的 [Blocktrail](https://www.blocktrail.com/) API, [EclipseMC](https://eclipsemc.com/) and [Eligius](http://eligius.st/) 就是这类型的矿池。有趣的是，这两个矿池同时开始挖出它们，表明它们可能使用了相同的挖矿软件。然而，EclipseMC 于 2012 年 9 月停止了这样的挖矿，Eligius 没有停止（他们于 2013 年 1 月才停止），表明当时挖矿软件出现分裂。其他矿池如 Slush，P2Pool 也挖出了这种区块，但数量很少。

These missing bitcoins are definitively lost. Sending bitcoins to bogus addresses or spending them in unspendable outputs does not make them disappear, you can still see them in the blockchain. Not redeeming all the block reward makes bitcoins really disappear: there is no way to see them in the blockchain. Looking at the [bitcoin source](https://github.com/bitcoin/bitcoin/blob/54e8bfec8387ee154f8b15b41ae0b29bc2cd9bbc/src/main.cpp#L1873), the only check on the block reward’s value is that it does not exceed its maximum value, thus it seems that you could even destroy all of the block reward, including generated coins, this way.
这些漏掉的比特币是明确性的丢失了。把比特币发送到伪造地址或将其花费在不可靠输出中并不会使它们消失，你仍然可以在区块链中看到它们。但不兑现所有的区块奖励将会使比特币真正地消失：在区块链中你将无法看到它们。来看一下[比特币的源码](https://github.com/bitcoin/bitcoin/blob/54e8bfec8387ee154f8b15b41ae0b29bc2cd9bbc/src/main.cpp#L1873)，对区块奖励值的唯一检查就是该数值没有超过它的最大值，所以看起来你甚至可以通过这种方式销毁所有的区块奖励，包括挖矿产生的比特币。

---

####Conclusion
####结论
There’s more ways to burn bitcoins (for example by using invalid [non standard scripts](https://medium.com/@alcio/a-look-at-bitcoin-non-standard-outputs-c97f65cccbb6)) but the most common ones are using bogus addresses and OP_RETURN scripts. While it’s only speculation from my part, I found it very interesting to be able to see which pools used common software only by looking at the blockchain.
还有一种销毁比特币的方法(例如通过使用无效的 [非标准脚本](https://medium.com/@alcio/a-look-at-bitcoin-non-standard-outputs-c97f65cccbb6)) ，但是最普遍的方法是使用伪造地址和 OP_RETURN 脚本。虽然这只是我的猜测，但我发现仅仅通过查看区块链就能看到哪些矿池使用了通用软件，这一点非常有趣。
