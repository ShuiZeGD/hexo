---
title: OSPF-路由计算
date: 2025-01-12 17:09:49
tags:
    - Datacome
    - OSPF
categories:
    - Datacome
    - OSPF
---
# OSPF 路由计算

1. ## LSA的更新机制

   1. ### 周期性更新

      1. 为什么要周期性更新？
         1. 能够让LSDB**始终描述当前某段时间内网络中真实状态信息**，防止LSDB中LAS的存活时间的差异带来的不确定性。
         2. **每隔30分****钟**周期性 更新自己身产生的LSA，谁产生谁负责对它进行刷新。
         3. 当一条LSA在3600s得不到刷新，则在LSDB中删除。
         4. **刷新过程中，LSA seq 加1， LSA age  置0， check sum 重新计算。**

   2. ### 触发更新

      1. 当LSA中 **描述链路状态参数取值** 发生变化，则立即产生新的LSA，  并在邻居间泛红。

   3. ### LSA的新旧判断机制

      1. 新的LSA要替换掉LSDB 中的 旧的LSA。
      2. 比较LSA seq, 越大越新。
      3. LSA seq相同， 比较checksum， cheksum越大越新。
      4. 如果 seq 相同， checksum 相同， 则判断 LSA age 是否等于 3600s,   **等于的3600S则认为 最新的LSA。**(**LS age 3600s是用于主动删除一条LSA的方法。**)
      5. 如果 LSA age 不等于 3600, 则比较 LS age 的差值，  **差值大于900s, 则Ls age 小的最优**。 **差值小于 900s，则认为是一致。**

   4. `ospf trans-delay 300`  // 修改opsf 传输延迟，默认为1s
   5. ![](/img/Datacome/OSPF-路由计算.png)



