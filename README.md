# 线性拟合的不同做法：
① 直接使用LSM最小二乘法进行多项式拟合——效果很差，W参数分布在较高次幂系数上  
② 使用岭回归正则项约束——W参数分布在较低次幂系数上，且集中分布在二次幂  
③ 使用SGD隐含正则进行实验——W参数经过调参后，同样能够做到集中在较低次幂系数上，且集中分布在二次幂  
④ 使用dropout W参数做（类似于S3COMP，但是dropout的对象为W），从结构上等同于岭回归（有部分区别），在dropout 参数p较小（drop维度较少）时具有性能，主要为具有一个岭回归求解结构。  
当dropout 参数p较大时，性能下降（因为可能drop掉低次幂，此时模型并非为欠拟合，导致高次幂系数过高的欠拟合现象）  
