# BrokenSHA-1

两个不同的pdf，计算sha1摘要时，发现sha1摘要是一样的，哈哈，是不是很神奇？

经过精心构造，两个pdf文件： [shattered-1.pdf](https://github.com/mythkiven/SHAttered/raw/master/shattered-1.pdf) 与 [shattered-2.pdf](https://github.com/mythkiven/SHAttered/raw/master/shattered-2.pdf) 的sha1摘要完全一致。

pdf的格式：
![](https://github.com/mythkiven/SHAttered/raw/master/pdf_format.png)

简单的拆分下：
```
- 删除两个pdf中不同的数据之后，得到两个文件：shattered-1-del.pdf、shattered-2-del.pdf，这两个内容自然是一样了，哈希也一样。
- 取出两个pdf中不同的部分：dif1和dif2，哈希是不同的。
```

其实哈希函数的本质是将无限的集合，通过压缩算法一一映射到有限的集合中。根据  鸽巢原理，必然存在碰撞的情况。


相关研究如下：

- 王小云团队提供MD5碰撞实例：

2004年的国际密码讨论年会（CRYPTO）尾声，王小云及其研究同事展示了MD5、SHA-0及其他相关散列函数的散列冲撞[3]。所谓散列冲撞指两个完全不同的消息经散列函数计算得出完全相同的散列值。根据鸽巢原理，以有长度限制的散列函数计算没有长度限制的消息是必然会有冲撞情况出现的。可是一直以来，信息安全专家一直无法给出实际例子，而王小云提供了第一个碰撞示例。

2005年2月，王小云与其同事提出SHA-1散列函数的散列冲撞。由于SHA-1散列函数被广泛应用于现今的主流计算机保安产品，其影响可想而知。王小云所提的散列冲撞算法只需少于269步骤，少于生日攻击所需的280步。同年8月，王小云、姚期智，以及姚期智妻子姚储枫联手于国际密码讨论年会提出SHA-1散列函数散列冲撞算法的改良版。此改良版使破解SHA-1时间缩短为263步。[4]
引自维基百科

-  以及GWI和谷歌的SHA1碰撞性实例(就是本文列举的两个pdf)。

引自 http://shattered.it/


**补充：**
-  实施 MD5碰撞的库： https://github.com/upbit/clone-fastcoll
-  实施SHA1碰撞的库：https://github.com/nneonneo/sha1collider
