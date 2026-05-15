# 各各他林对话

## .yarn文件命名标准
- `global`：游戏全局通用的所有变量
- `NPC_*`：NPC
- `Ally_*`：队友
- `Mission_*`：任务，一般只定义与该任务有关的变量
- `Dream_*`：梦境
- `Site_*`：某地点

## 节点命名标准
- `init`：用于定义临时变量的节点
- `encounter`：遭遇该物品/NPC
- `discover`：进入某地点

## 扩展函数
- `flag(标志名)`: 获取标志,默认为false
- `set_flag(标志名,true/false)`: 修改标志
- `ch(角色名)`: 获取当前情景是否有指定角色

## 检定扩展
- 暗骰
`check(检定名, 检定角色, 骰子面数, 掷骰次数, 难度)`
返回布尔值
- 表骰
`<<uicheck 检定名 检定角色 难度>>`
结果储存在变量`$dice_result`中, 若成功则为true, 否则为false.
