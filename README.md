# 各各他林对话

## .yarn文件命名标准
- `global`：游戏全局通用的所有变量
- `NPC_*`：NPC
- `Ally_*`：队友
- `Mission_*`：任务，一般只定义与该任务有关的变量
- `Dream_*`：梦境
- `Site_*`：某地点
- `Item_*`：可放入背包的物品
- `Entity_*`：可直接互动的物品

## 节点命名标准
- `encounter`：遭遇物品/NPC
- `discover`：进入地点

## 命令扩展
- `combat`: 进入战斗

## 函数扩展
- `ch(角色名)`: 指定角色是否在场
- `at(地点名)`: 当前是否位于指定地点

- `moveto(区域名,位置标记名)`: 切换位置

## 检定扩展
- 暗骰
`check(检定名, 检定角色, 骰子面数, 掷骰次数, 难度)`
返回布尔值
- 表骰
`<<uicheck 检定名 检定角色 难度>>`
结果储存在变量`$dice_result`中, 若成功则为true, 否则为false.

## 其它扩展
- 未初始化变量的值是false.

```yarn spinner
title: encounter
---
旁白
you: 测试暗骰
<<if check("dex","you",1,20,10)>>
    检定成功
<<else>>
    检定失败
<<endif>>
allytest: 我也检定一下
<<if check("dex","allytest",1,20,10)>>
    检定成功
<<else>>
    检定失败
<<endif>>
you: 表骰
<<uicheck dex you 10>>
<<uicheck dex allytest 10>>
<<jump node2>>
===

title: node2
---
-> 水母1:让水母1说话...
    水母1:水母1说话
    -> 再问一遍?
        <<jump node2>>
    -> 不了
-> 水母2:让水母2说话
    水母2: 水母2说话
-> you:我再说话
    you: 我再说话
-> allytest:队友说话
    allytest: 队友说话
===
```
