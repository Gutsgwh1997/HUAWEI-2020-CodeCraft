## HUAWEI 2020 Code Craft
### 1、前言
京津东北赛区小问号的女朋友队，初赛第9名，复赛A榜第10名，复赛B榜无分数
![image](https://github.com/Gutsgwh1997/HUAWEI-2020-CodeCraft/blob/master/image/Screenshot%20from%202020-05-28%2009-06-45.png)
非科班出身，能和这么多优秀的Coder同台竞技，初赛取得这个成绩实属欣慰。
![image](https://github.com/Gutsgwh1997/HUAWEI-2020-CodeCraft/blob/master/image/Screenshot%20from%202020-05-28%2008-38-25.png)
这一路走来充满了艰辛，曾被小号搞到心态爆炸，曾因为连续几天0.0x的优化想要放弃，还好我们坚持下来了。
#### 2、找环算法
主体使用双向DFS算法，我们开源了初赛、复赛最快以及最鲁棒的版本，差异主要在数据结构上：
1. 鲁棒的版本使用vector套娃存邻接表、vector套娃存结果；
2. 最快的版本使用静态数组存取对应的信息；

初赛IO的优化占比较大，复赛对数据结构、算法细节的优化提升较大，我们的存图数据结构从vector套娃-->静态数组-->类前向星结构的优化取得了不错的时间上的提升。

算法大体使用的技术：
1. topo排序进行（线上提升不大）
2. 强连通分量减枝（线上无提升）
3. 多线程负载均衡（%4）
4. 双向DFS搜索
5. 多线程memcpy构造结果字符串，IO使用mmap加速等

### 3、总结
第一次正式参与这种比赛，一个半月还是学到不少东西的，对C/C++的内存、STL的认识进步了一个台阶，当然也发现了自身和团队协作中的不足：
1. 代码版本管理
2. 代码规范
3. 自己心急时听不进队友的建议

这些都是日后学习、工作中需要改进的地方。关于为什么复赛B榜没分数，还不是因为自己菜，B榜改了一些需求，我们的双向DFS扩展性、可阅读性很强，主要死在了浮点数金额上：   
1. 采用long long存储金额*100后的数值，转换时没有定位到出错点，一个临时变量的类型未改变，在这花费了大量时间；
2. 没有意识到.x与0.xx乘100倍后的差别；
3. 处理第二个问题时被`\r\n`坑了一把；
4. 代码合并时策略出了问题；

最后一分钟我们改好了代码，但是提交通道关闭了。这次比赛与其他同学经验交流的收获要远远大于比赛的奖品，其他大佬的解决方案如下，大家共同学习进步：

- 京津东北赛区1504b：https://github.com/WavenZ/CodeCraft2020
- 上合赛区但使龙城飞将在，六宫粉黛无颜色：https://github.com/hai371591695/2020CodeCraft
- 武长赛区左家垅反洗钱小分队：https://github.com/yoghurt-lee/HuaWeiCodeCraft2020
- 赛粤港澳赛区以上团队均未获奖：https://github.com/cxq80803716/2020codecraft
