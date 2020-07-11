# 1. 通信电子线路课程设计

**[The Author's E-mail](http://www.thdong.top/index.php/start-page.html)**

>注意我这里来使用的是Multisim 13.0.1，如果使用这里的资源也需要使用对应的软件版本。该设计使用的工程文件如下：

![](https://ythdong.gitee.io/blog_image/%E4%B8%93%E4%B8%9A%E8%AF%BE/%E9%AB%98%E9%A2%91.PNG)



## 1.1. 设计任务及主要技术指标

调频发射机的主要任务是完成有用的低频信号的频率放大,将其变为易于天线发射的高频电磁波。调频发射机的实现需要用电路仿真软件Multisim仿真，验证试验结果。验证结果包括：示波器测量的主要点的波形、电路实现的参数(输入信号波特率、幅度，发射机部分供电电压、电流；接收机部分供电电压、电流，发射机输出信号幅度、中心频率、带宽，接收机灵敏度，接收机输出电压幅度等)。

### 1.1.1. 设计任务

* 确定调频发射机的设计方案，根据设计指标对既定方案进行理论设计分析，并给出各单元电路的理论设计方法和实用电路设计细节，其中包括元器件的具体选择、参数调整。
* 利用multisim仿真软件，对设计电路进行仿真和分析，依据设计指标对电路参数进行调整直至满足设计要求。

### 1.1.2. 主要技术指标

* 中心频率：10.7MHz 
* 调制信号：1KHz
* 频偏：20KHz

## 1.2. 设计方案及原理

### 1.2.1. 调频原理

![](https://ythdong.gitee.io/blog_image/%E4%B8%93%E4%B8%9A%E8%AF%BE/%E9%AB%98%E9%A2%911.png)

如图， 调频发射机原理框图所示，首先我们使用震荡器产生载波频率，对于振荡器的选择我们这里使用的是克拉坡振荡器，之所以选择它是因为它的频率比较稳定，有了载波信号之后再使用低频调制信号去控制变容二极管的电容实现调频，其中调频电路使用的是电容二极管调频，因为它的电容会随着反向电压的改变而改变，所以当它的电容加到克拉珀振荡器上，会改变总的电容而实现调频，最后将已调信号通过缓冲器加载到高频功率放大器上，进行功率放大，便于发射，缓冲级使用的是射极跟随器，缓冲级在此处起着隔离的作用，因为放大器和调频电路之间寻在这相互的干扰，缓冲级的存在可以让放大器和调频电路隔离开避免我们不想要且可以排除的干扰。

### 1.2.2. 结构框图

![](https://ythdong.gitee.io/blog_image/%E4%B8%93%E4%B8%9A%E8%AF%BE/%E9%AB%98%E9%A2%912.png) 

## 1.3. 结果展示

### 1.3.1. 振荡器

![](https://ythdong.gitee.io/blog_image/%E4%B8%93%E4%B8%9A%E8%AF%BE/%E9%AB%98%E9%A2%913.png)

### 1.3.2. 调频电路

![](https://ythdong.gitee.io/blog_image/%E4%B8%93%E4%B8%9A%E8%AF%BE/%E9%AB%98%E9%A2%914.png)

### 1.3.3. 缓冲级

![](https://ythdong.gitee.io/blog_image/%E4%B8%93%E4%B8%9A%E8%AF%BE/%E9%AB%98%E9%A2%915.png)

### 1.3.4. 高频功率放大器

![](https://ythdong.gitee.io/blog_image/%E4%B8%93%E4%B8%9A%E8%AF%BE/%E9%AB%98%E9%A2%916.png)

### 1.3.5. 总电路

![](https://ythdong.gitee.io/blog_image/%E4%B8%93%E4%B8%9A%E8%AF%BE/%E9%AB%98%E9%A2%917.png)

## 1.4. 系统性能分析及改进措施

|           要求            | 完成情况 |
| :-----------------------: | :------: |
| 中心频率维持在10.7MHz左右 |   达标   |
|      频偏维持在20KHz      |   达标   |
|  输入调制信号频率为1KHz   |   达标   |

经过性能分析，这个电路各方面都是达标的。
有克拉珀振荡器产生载频，通过射极跟随器加载到放大电路上，为了
改善振荡频率稳定度，从根本上来说就是力求减小振荡频率收温度、负载、电源等外界因素影响的程度，振荡级是主要部件，因此改善振荡频率稳定度的重要措施是提高振荡回路在外界因素变化是保持频率不变的能力。

高频功率放大器也就是射随器利用集电极的直流分量在基极偏置电阻上产生所需要的负偏压，使其工作在丙类状态。输出回路采用变压器耦合式谐振回路，利用电感抽头实现阻抗匹配，调整末级功放的工作状态，从而达到有效的集电极调幅，有最佳的功率输出。

同时通过查询资料我还发现起振器和振荡器之间会产生一定的频率干扰，从而影响整个电路，所以在实际操作时我们应该把二者隔离开来，从我这个原理图上看，感觉有一些不合理，一是基极电压不好保证，建议在基极和地之间加一电阻，基极上拉电阻暂时做成可调节的，然后调整上拉电阻值，找到合适工作点。另外注意相应的震荡电容要使用瓷片电容或者是瓷管电容 3点 这个三极管的放大倍数不能太小。
