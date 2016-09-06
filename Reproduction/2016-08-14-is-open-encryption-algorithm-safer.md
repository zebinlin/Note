# 在有限专家间评议加密算法是不是比直接公开更安全？

这是一个经典问题了，常常被问起。其他回答有些已经从专业角度进行了阐述。我尝试从通俗的角度再补充一下。

**一、应用于大众领域的密码学却要实现算法保密？一个不可能的任务**

一提起密码学，大家第一反应是联想到战争、军事，但如今的世界，密码学最广泛也是最基本的用途却是在保护普通人的通信安全——比如让你在使用网银的时候密码不会被其他人截获进而偷走你的钱。

站在这个角度看，很快就会发现，要想让全世界70亿人口仰仗一种不公开的加密算法隐约存在一些障碍。不过，在开始讨论之前，我们还是先做一些非常非常理想（而不切实际的）假设：

1. 算法的缔造者是顶级专家具有深入的知识
2. 算法没有包含任何的后门，不会被特殊的政治集团利用
3. 算法的保密性极佳没有任何机构有能力窃取
4. 全世界一致同意接受这一算法

在如此乌托邦般理想的背景下，全世界满心欢喜，翘首以待，希望立刻使用这一算法来保障全世界的通信安全！（此处应有BGM，世界500强CEO欢聚一堂纷纷竖起大拇指对提出这一算法天才致以最高的敬意——虽然并没有人知道他是怎么做到的——而且我也不清楚大家怎么就能如此单纯的相信他说的是真的……）

就在这欢声笑语一片祥和，世界大同的瞬间，有一个工程师突然发现了一个问题——怎么才能把这个算法用起来呢？另一个工程师也恍然大悟，一拍大腿脱口而出：是啊，算法他妈的根本没公开啊！

全世界都愣住了，光忙着庆祝，却忽略了一个问题——除了算法的作者谁也不知道怎么去加密和解密，没人能写出算法！怎么办？

这时候隔壁老王提提裤子站了起来，提议由算法的发明人，定制一种硬件芯片，秘密制造，然后在不公开其硬件构造的情况下，统一分发给大家！

热烈的掌声，经久不息。但老张不乐意了，老张站起来缓缓道：硬件好是好，但是我们公司的几亿台嵌入式设备已经在运行，要升级硬件难度太大。首先你的芯片有多大，尺寸太大肯定不行，我们的设备体积有限；耗电多少，太耗电那也行不通；速度呢，能达到每秒处理 X Mbit 吗？我们的系统是硬实时系统，响应时间不能超过 Y ms……如果可以，还有个问题，价格呢？如果太贵，我们怕是要破产。而且硬件的东西，做上去就无法更改了，你们最好一次做对，要是出问题想改那也是难呐……

会场陷入了一片沉默……一些工程师开始交头接耳。老张顿了顿，说道：可以搞软件的嘛，提供一个预编译好的二进制库给我们就行了，这样我们不用升级硬件，也能用上这项伟大的发明！

算法的发明人经过短暂的考虑，微笑着点点头表示了同意。笑容又出现在每个人的脸上。除了会场角落的一群人……

他们轻蔑的看着狂欢的人群，为他们的天真报以最深的同情——这是一群安全研究人员，就在上个月，他们破解了一个被认为“绝对安全”的芯片，完全逆向出了其中的算法。在他们眼中，这场闹剧虽然可笑，但却也是一个闷声发大财的绝佳机会……

讲这个段子只是为了提醒你：

1. 任何保密的算法一旦变成了硬件，就有可能被逆向还原
2. 同上，任何保密算法一旦变成了软件，就有可能被逆向还原（实际上不是有可能而是一定可以）
3. 上述两条在可以预见的未来依然成立

所以结论：算法的保密性在现实世界行不通。甚至可以说，任何想要大规模广泛应用保护几十亿人的密码学算法，都根本无法实现保密，最终不管是你愿意还是不愿意都会公开。原因是，算法要给人用，就要变为硬件或者软件，而这二者都不安全，可以通过研究它们逆向还原出算法。

**二、通过严密的管理措施在军事上实现算法保密？另一种幻想**

上面聊完了民用，我们知道一点，一旦需要［广泛］应用一种加密算法，那么保密就是不可能的。接下来我们考虑军事环境下，能否实现加密算法的保密呢？

在理想的世界里，好人和坏人泾渭分明；英雄的意志如同钢铁般从不会被诱惑；每一个兢兢业业的军人如同机器般准确，从不犯错……

可惜现实世界里的军队绝非如此，光是间谍问题就解决不了。间谍也许偷不走你的算法设计文档，但他/她可以偷走你安装了相应加解密芯片的设备，于是问题又回到和前述类似的情况，你的算法很可能被逆向还原……

而更实际的情况其实是，在军事领域，直接收买/绑架/威胁相关人员更加方便，破解芯片有时候反而纯属多余。这方面二战中已经数不胜数。都是血泪教训。

**三、可是，如果公开的是安全的，那么我将其再做保密不是［更加］安全么？一个思维陷阱**

这可能是提问者最困惑的问题。这就相当于，如果你们口口声声说公开的最安全，那么我把它再做一层保护，也就是保密起来，那不是双保险？！

这样的想法，其实是一种**变相的循环论证**：
一个算法，敢叫安全的，一个专家说了不算，十个也不算，所有专家都这么说才算，所以你得［公开］了，最后才敢叫安全
你都保密了，就没有人知道它到底安全不安全，只有一小撮人［认为］它安全，所以你保密的是一个［安全］的算法吗？也许是，也许不是
历史经验证明，发明安全的算法难度之高，远超想象，由此可知，在 2 的情况下，你小心翼翼维护的所谓［安全］算法 99.99％ 其实是个不堪一击的东西

所以，根本原因是，安全不是［天生］属性，而是公开后［实践］赋予的衍生属性。你无法在保密一个东西的同时确定它是安全的，你只能［自认为］它是。


**四、别忘了，公开挑战全世界并获胜是现代密码学胆敢声称安全的唯一标准**

现实世界的任何加密算法赋予的安全性都是［有限］的，实际上加密算法只是在不断的抬升［破解的代价］而已，主要是时间代价
因此完美的，绝对的加密算法在现实世界不存在
由上可知，几乎没有人真正能够判定一个加密算法是否［安全］，只能以有限的知识对其进行估计，但经过大众的参与，一些久经考验的加密算法被发现［很难］破解，我们才可以谨慎认为它们相对安全
仔细想想就会发现，其实现代密码学最大的进步就是承认了不完美，这一点可以说是经典密码学到现代密码学精神内核上最本质的区别，也改变了密码学研究的方向。究竟需要多大的胆量，才可以把自己的算法公之于众的同时，声称它是安全的？同时当全世界绞尽脑汁都无法将其撼动分毫时，作者内心会感受到多高的荣誉？

这是一种极致的挑战精神。也是人类智慧的极致体现。

**五、反常提示**

无需知道加密算法，也可能构造出解密算法，这一点可能让很多人意外：

加密算法本质都是一个函数 F。而与其相对的解谜算法可以称为 F'。这很好理解。问题是，构造 F' 一定要知道 F 吗？能否在不知道原始加密算法的情况下，直接构造一个函数来实现和 F' 相同的解密功能？实际上是有可能的，如果有大量的明文和密文对（这个条件通常很容易满足），然后 F 满足特定的数学性质，那么就可以找到一个 U 函数，实现 F' 的功能。

重复加密多次，或者混用多种不同的加密算法，可能降低安全性：

如果加密一次会变得安全的话，那么加密两次、三次、四次呢？是否更加安全？事实上可能恰恰相反，安全性有可能反而降低。混用加密算法也会带来此类问题。这一点也常常让人意外。

密钥长度越长越安全？不一定：

特定的加密算法，某些长度的密钥有助于增强安全性，而另一些则会削弱，这实际是一个很复杂的问题。实际上好的加密算法至少保证密钥长度增长的同时安全性增强，但许多算法并不能在这方面给予保证，让人很意外。

同一个加密算法，选择两个相同长度的密钥 X 和 Y，它们加密出来的结果一样安全吗？不一定：

存在弱密钥，不幸选中这些密钥会导致安全性下降，有时问题可能会很严重。

其它各种坑就不说了，请参考专业书籍……你了解的越多，你终将会发现，密码学真的非常非常复杂，因此如果谁胆敢声称安全，即使是这个行业的顶级人员，也常常被打脸。一般只敢提出一些新想法启发思路。而证明其安全性是一个很漫长的过程。

没有哪个小圈子强大到提问者想象的那个理想程度。 