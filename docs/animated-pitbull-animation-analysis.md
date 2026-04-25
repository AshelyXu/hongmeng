# animated_pitbull_dog.glb 动画枚举与接入分析

本文档基于 `models/animated_pitbull_dog.glb` 直接读取出的 119 个动画。目标不是把所有动作都无差别接进主流程，而是把它们整理成可控的动作库，让宠物表现更生动，同时保持动作衔接自然、按钮不遮挡身体。

## 接入原则

- 稳定姿态只保留少量核心状态，作为所有动作链的起点和终点。
- 过渡动作优先于直接淡入淡出，特别是站立、坐下、趴下、嗅闻、走路之间。
- 点缀动作低频插入，播完回到原稳定状态。
- 互动动作由事件触发，不能直接覆盖当前动作；先规划动作链，再播放反馈。
- 跑、冲刺、跳跃、游泳、攻击类动作先不进入日常宠物主流程，除非后续加入空间移动、朝向和碰撞逻辑。

## 全部动画枚举

| 序号 | 动画名 | 时长 | 初步分类 | 接入建议 |
|---:|---|---:|---|---|
| 0 | `idle 50` | 1.96s | 稳定姿态 | 已接入，站立待机主循环 |
| 1 | `atttack 8` | 0.28s | 特殊/攻击 | 暂缓，容易破坏宠物感 |
| 2 | `canter_fwd 53` | 2.08s | 中高速移动 | 第二阶段以后，需位移逻辑 |
| 3 | `canter_fwd_sniff_to_idle_sniff 53` | 2.08s | 移动到嗅闻过渡 | 可作为 canter 接入后的停止动作 |
| 4 | `duck 9` | 0.32s | 特殊姿态 | 暂缓，可用于受惊/躲避 |
| 5 | `fall 1` | 0.00s | 特殊姿态 | 暂缓，pose 类动作 |
| 6 | `hopping_water_fwd 21` | 0.80s | 水中/特殊移动 | 暂缓，需要水域场景 |
| 7 | `idle sniff air 271` | 10.80s | 点缀/警觉 | 可低频接入警觉心情 |
| 8 | `idle_bark_04_warning 47` | 1.84s | 点缀/警觉 | 可低频接入低安全感状态 |
| 9 | `idle_drop_item 51` | 2.00s | 道具互动 | 投喂/叼取系统后接入 |
| 10 | `idle_lay_one_off_02 .201` | 8.00s | 趴卧点缀 | 可低频接入，时长较长 |
| 11 | `idle_lay_one_off_1. 112` | 4.44s | 趴卧点缀 | 可低频接入 |
| 12 | `idle_lay_pose 2` | 0.00s | 稳定姿态 | 已接入，趴卧稳定态 |
| 13 | `idle_lay_to_idle 71` | 2.80s | 过渡 | 已接入，趴到站 |
| 14 | `idle_lay_to_idle_sit 93` | 3.68s | 过渡 | 已接入，趴到坐 |
| 15 | `idle_lay_to_walk_fwd 38` | 1.48s | 过渡 | 已接入，趴到走 |
| 16 | `idle_one_off_chin_drag 151` | 6.00s | 点缀 | 可用于无聊/放松 |
| 17 | `idle_one_off_dig 184` | 7.32s | 点缀/探索 | 第二阶段，低频 |
| 18 | `idle_one_off_shuffle_turn_lft 122` | 4.84s | 转向点缀 | 可接入朝向系统 |
| 19 | `idle_one_off_shuffle_turn_rgt 91` | 3.60s | 转向点缀 | 可接入朝向系统 |
| 20 | `idle_pickup_item 67` | 2.64s | 道具互动 | 投喂/玩具系统后接入 |
| 21 | `idle_pose_to_jump_fwd 15` | 0.56s | 跳跃过渡 | 暂缓，需要落地链 |
| 22 | `idle_rest_pose 22` | 0.00s | 稳定姿态 | 可作为更放松的休息态 |
| 23 | `idle_shake_1. 137` | 5.44s | 点缀 | 已接入，低频甩身 |
| 24 | `idle_shake_2. 81` | 3.20s | 点缀 | 可接入，替换或补充 shake_1 |
| 25 | `idle_sit_one_off_scratch 176` | 7.00s | 坐姿点缀 | 已接入，低频抓痒 |
| 26 | `idle_sit_one_off_step_1. 119` | 4.72s | 坐姿点缀 | 可低频接入 |
| 27 | `idle_sit_one_off_step_2. 119` | 4.72s | 坐姿点缀 | 可低频接入 |
| 28 | `idle_sit_pose 2` | 0.00s | 稳定姿态 | 已接入，坐姿稳定态 |
| 29 | `idle_sit_to_idle 56` | 2.20s | 过渡 | 已接入，坐到站 |
| 30 | `idle_sit_to_idle_lay 113` | 4.48s | 过渡 | 已接入，坐到趴 |
| 31 | `idle_sit_to_walk_fwd 61` | 2.40s | 过渡 | 已接入，坐到走 |
| 32 | `idle_sniff 83` | 3.28s | 嗅闻点缀 | 可接入嗅闻稳定态内部 |
| 33 | `idle_sniff_one_off 83` | 3.28s | 嗅闻点缀 | 已接入 |
| 34 | `idle_sniff_pose` | 0.00s | 稳定姿态 | 已接入，嗅闻稳定态 |
| 35 | `idle_sniff_to_idle 51` | 2.00s | 过渡 | 已接入，嗅闻回站 |
| 36 | `idle_sniff_to_trot_sniff 51` | 2.00s | 过渡 | 第二阶段，接 trot 后使用 |
| 37 | `idle_sniff_to_walk_sniff 34` | 1.32s | 过渡 | 已接入，嗅闻到走 |
| 38 | `idle_step_bwd_long 91` | 3.60s | 位移点缀 | 可用于靠近/避让逻辑 |
| 39 | `idle_step_bwd_short 64` | 2.52s | 位移点缀 | 可用于靠近/避让逻辑 |
| 40 | `idle_to_aggressive_pose 56` | 2.20s | 警觉/攻击过渡 | 暂缓，警觉系统成熟后低频 |
| 41 | `idle_to_canter_fwd_run 35` | 1.36s | 高速移动过渡 | 暂缓 |
| 42 | `idle_to_dodge_backstep 51` | 2.00s | 闪避 | 暂缓 |
| 43 | `idle_to_dodge_lft 31` | 1.20s | 闪避 | 暂缓 |
| 44 | `idle_to_idle_lay 111` | 4.40s | 过渡 | 已接入，站到趴 |
| 45 | `idle_to_idle_sit 57` | 2.24s | 过渡 | 已接入，站到坐 |
| 46 | `idle_to_idle_sniff 46` | 1.80s | 过渡 | 已接入，站到嗅闻 |
| 47 | `idle_to_run_fwd 32` | 1.24s | 高速移动过渡 | 暂缓 |
| 48 | `idle_to_sneak_idle_1. 46` | 1.80s | 潜行动作 | 第二阶段，可做谨慎性格 |
| 49 | `idle_to_sneak_idle_2. 26` | 1.00s | 潜行动作 | 第二阶段，可做谨慎性格 |
| 50 | `idle_to_sprint_fwd 39` | 1.52s | 冲刺过渡 | 暂缓 |
| 51 | `idle_to_sprint_fwd_directional 39` | 1.52s | 冲刺过渡 | 暂缓 |
| 52 | `idle_to_trot_fwd 43` | 1.68s | 小跑过渡 | 第二阶段 |
| 53 | `idle_to_walk_fwd 47` | 1.84s | 过渡 | 已接入，站到走 |
| 54 | `idle_turn_135_rgt` | 3.00s | 转向 | 第二阶段，需朝向系统 |
| 55 | `idle_turn_135_rgt_to_walk_fwd` | 2.88s | 转向到走 | 第二阶段，需朝向系统 |
| 56 | `idle_turn_180_lft` | 2.64s | 转向 | 第二阶段，需朝向系统 |
| 57 | `idle_turn_180_rgt` | 3.80s | 转向 | 第二阶段，需朝向系统 |
| 58 | `idle_turn_180_rgt_to_walk_fwd` | 2.68s | 转向到走 | 第二阶段，需朝向系统 |
| 59 | `idle_turn_45_rgt` | 2.40s | 转向 | 第二阶段，需朝向系统 |
| 60 | `idle_turn_45_rgt_to_walk_fwd` | 2.24s | 转向到走 | 第二阶段，需朝向系统 |
| 61 | `idle_turn_90_rgt` | 2.32s | 转向 | 第二阶段，需朝向系统 |
| 62 | `idle_turn_90_rgt_to_walk_fwd` | 2.24s | 转向到走 | 第二阶段，需朝向系统 |
| 63 | `idlesniff_to_walk_fwd_sniff 79` | 3.12s | 过渡 | 可替换 `idle_sniff_to_walk_sniff`，更长更自然 |
| 64 | `idleTOaggressive_pose 4` | 0.12s | 警觉/攻击过渡 | 暂缓，太短 |
| 65 | `interact_bed_elmer_pet 31` | 0.00s | 床上互动 | 暂缓，需要床/场景 |
| 66 | `interact_bed_lay_exist 270` | 10.76s | 床上趴卧 | 暂缓，需要床/场景 |
| 67 | `interact_bed_sleep_exist 221` | 8.80s | 床上睡眠 | 暂缓，需要床/场景 |
| 68 | `interact_elmer_pet_1. 31` | 1.20s | 用户互动 | 已接入，摸摸反馈 |
| 69 | `interact_elmer_pet_2` | 0.00s | 用户互动/姿态 | 已在候选中，需观察是否像 pose |
| 70 | `interact_elmer_treat` | 1.20s | 用户互动 | 已接入，投喂反馈 |
| 71 | `jump 22` | 0.84s | 跳跃 | 暂缓，需要起跳和落地链 |
| 72 | `land 7` | 0.24s | 落地 | 跳跃系统后接入 |
| 73 | `land2. 5` | 0.16s | 落地 | 跳跃系统后接入 |
| 74 | `no 10` | 0.36s | 表情/头部反馈 | 可接入呼唤失败或低亲密 |
| 75 | `pee 43` | 1.68s | 特殊生理 | 暂缓，除非做养成事件 |
| 76 | `playbow 1` | 0.00s | 玩耍姿态 | 已在候选中，需作为 pose 或短反馈谨慎使用 |
| 77 | `poop 75` | 2.96s | 特殊生理 | 暂缓 |
| 78 | `push 61` | 2.40s | 特殊互动 | 暂缓，需要对象 |
| 79 | `run_fwd 13` | 0.48s | 快跑循环 | 暂缓，需要位移系统 |
| 80 | `run_fwd carry item 13` | 0.48s | 快跑携物 | 暂缓，需要道具与位移 |
| 81 | `run_fwd_to_idle` | 2.60s | 快跑停止 | run 接入后使用 |
| 82 | `sit_carry 2` | 0.00s | 携物坐姿 | 道具系统后接入 |
| 83 | `sneak_fwd 61` | 2.40s | 潜行移动 | 第二阶段，警觉性格很好用 |
| 84 | `sneak_fwd_bank_lft 61` | 2.40s | 潜行转向 | 第二阶段 |
| 85 | `sneak_fwd_bank_rgt 61` | 2.40s | 潜行转向 | 第二阶段 |
| 86 | `sneak_idle_to_idle 41` | 1.60s | 过渡 | 第二阶段，潜行回站 |
| 87 | `sneak_idle_to_sneak_fwd 81` | 3.20s | 过渡 | 第二阶段 |
| 88 | `sneak_pose` | 0.00s | 稳定姿态 | 第二阶段，可做警觉稳定态 |
| 89 | `sneak_to_idle 31` | 1.20s | 过渡 | 第二阶段 |
| 90 | `sneak_to_sneak_idle 86` | 3.40s | 过渡 | 第二阶段 |
| 91 | `sprint_fwd 11` | 0.40s | 冲刺循环 | 暂缓 |
| 92 | `sprint_fwd_to_idle 62` | 2.44s | 冲刺停止 | sprint 接入后使用 |
| 93 | `sprint_fwd_to_idle_sharp 59` | 2.32s | 冲刺急停 | sprint 接入后使用 |
| 94 | `sprint_jump_to_swim 42` | 1.64s | 跳入水 | 暂缓，需要水域 |
| 95 | `sprint_retrieve item_108degree . 19` | 0.72s | 取物冲刺 | 暂缓，需要道具 |
| 96 | `sprint_retrieve_item directional 19` | 0.72s | 取物冲刺 | 暂缓，需要道具 |
| 97 | `swim_bank_lft 34` | 1.32s | 游泳转向 | 暂缓，需要水域 |
| 98 | `swim_bank_rgt 34` | 1.32s | 游泳转向 | 暂缓，需要水域 |
| 99 | `swim_carry item_fwd 23` | 0.88s | 游泳携物 | 暂缓，需要水域和道具 |
| 100 | `swim_fwd 34` | 1.32s | 游泳 | 暂缓，需要水域 |
| 101 | `track_bark_harvest 75` | 2.96s | 警觉/叫声 | 可低频用于警觉/看家性格 |
| 102 | `trot_carry item 17` | 0.64s | 小跑携物 | 道具系统后接入 |
| 103 | `trot_fwd 17` | 0.64s | 小跑循环 | 第二阶段，活泼性格 |
| 104 | `trot_fwd_nervous 19` | 0.72s | 紧张小跑 | 第二阶段，警觉/无聊 |
| 105 | `trot_fwd_sniff 18` | 0.68s | 嗅闻小跑 | 第二阶段，活泼探索 |
| 106 | `trot_fwd_to_idle 56` | 2.20s | 小跑停止 | trot 接入后必须使用 |
| 107 | `trot_sniff_to_idle_sniff 51` | 2.00s | 小跑嗅闻停止 | trot sniff 接入后使用 |
| 108 | `walk_fwd 29` | 1.12s | 走路循环 | 可补充普通走路 |
| 109 | `walk_fwd_bank_lft 29` | 1.12s | 走路转向 | 第二阶段，需朝向系统 |
| 110 | `walk_fwd_bank_rgt 29` | 1.12s | 走路转向 | 第二阶段，需朝向系统 |
| 111 | `walk_fwd_sniff 46` | 1.80s | 探索循环 | 已接入，主探索 |
| 112 | `walk_fwd_sniff_bank_lft 46` | 1.80s | 探索转向 | 第二阶段，需朝向系统 |
| 113 | `walk_fwd_sniff_bank_rgt 46` | 1.80s | 探索转向 | 第二阶段，需朝向系统 |
| 114 | `walk_fwd_sniff_multi_cycle 61` | 2.40s | 探索循环 | 可替换主探索，更自然 |
| 115 | `walk_fwd_sniff_to_idle_sniff 53` | 2.08s | 过渡 | 已接入，探索到嗅闻 |
| 116 | `walk_fwd_to_idle 59` | 2.32s | 过渡 | 已接入，走路停下 |
| 117 | `wave 18` | 0.68s | 用户反馈 | 已在候选中，高亲密使用 |
| 118 | `yes 8` | 0.28s | 用户反馈 | 已接入，轻反馈 |

## 当前已接入动作

当前页面的主逻辑在 `pages/webgl_animation_dog.html` 的 `CLIP_PLAN` 中。已接入的核心动作如下：

- 稳定态：`idle 50`、`idle_sit_pose 2`、`idle_lay_pose 2`、`idle_sniff_pose`、`walk_fwd_sniff 46`
- 姿态过渡：`idle_to_idle_sit 57`、`idle_to_idle_lay 111`、`idle_to_idle_sniff 46`、`idle_sit_to_idle 56`、`idle_sit_to_idle_lay 113`、`idle_lay_to_idle 71`、`idle_lay_to_idle_sit 93`
- 移动过渡：`idle_to_walk_fwd 47`、`idle_sit_to_walk_fwd 61`、`idle_lay_to_walk_fwd 38`、`idle_sniff_to_walk_sniff 34`、`walk_fwd_to_idle 59`、`walk_fwd_sniff_to_idle_sniff 53`
- 互动反馈：`interact_elmer_pet_1. 31`、`interact_elmer_pet_2`、`interact_elmer_treat`、`yes 8`、`wave 18`、`playbow 1`
- 点缀动作：`idle_shake_1. 137`、`idle_sniff_one_off 83`、`idle_sit_one_off_scratch 176`、`idle_lay_one_off_1. 112`、`idle_lay_one_off_02 .201`、`idle sniff air 271`

## 更生动的接入路线

### 第一阶段：补强日常生命感

这一阶段风险最低，适合马上接入。

- 加入 `idle_rest_pose 22`，作为安全感高、精力低时的放松稳定态。
- 将 `walk_fwd_sniff_multi_cycle 61` 替换或轮换当前 `walk_fwd_sniff 46`，让探索循环少一点重复感。
- 将 `idle_shake_2. 81`、`idle_one_off_chin_drag 151`、`idle_sit_one_off_step_1. 119`、`idle_sit_one_off_step_2. 119` 加入点缀池。
- 将 `idle_sniff 83` 加入嗅闻稳定态内部的小动作，而不是单独作为稳定态。

建议触发方式：

- 平静：更常 `sit`、`lay`、`rest`
- 无聊：更常 `sniff`、`walk_fwd_sniff_multi_cycle`
- 开心：更常 `yes`、`wave`、`interact_elmer_pet_1`
- 警觉：低频 `idle sniff air 271`

### 第二阶段：加入朝向和巡游

这一阶段能显著增加生动感，但需要一个简单的朝向系统。

- 转向动作：`idle_turn_45_rgt`、`idle_turn_90_rgt`、`idle_turn_135_rgt`、`idle_turn_180_lft`、`idle_turn_180_rgt`
- 转向后移动：`idle_turn_45_rgt_to_walk_fwd`、`idle_turn_90_rgt_to_walk_fwd`、`idle_turn_135_rgt_to_walk_fwd`、`idle_turn_180_rgt_to_walk_fwd`
- 走路转弯：`walk_fwd_bank_lft 29`、`walk_fwd_bank_rgt 29`
- 嗅闻转弯：`walk_fwd_sniff_bank_lft 46`、`walk_fwd_sniff_bank_rgt 46`

建议触发方式：

- 自主探索不再只是“走和停”，而是“先转头/转身，再走两步，再停下嗅闻”。
- 只在 `StandIdle` 或 `SniffIdle` 触发转向，避免坐姿和趴姿硬接转向。

### 第三阶段：加入性格差异

这一阶段可以让三种性格更明显。

- 温顺型：增加 `idle_rest_pose 22`、`idle_one_off_chin_drag 151`、`idle_lay_one_off_1. 112`
- 活泼型：增加 `walk_fwd 29`、`trot_fwd 17`、`trot_fwd_sniff 18`、`idle_to_trot_fwd 43`、`trot_fwd_to_idle 56`
- 警觉型：增加 `sneak_pose`、`idle_to_sneak_idle_1. 46`、`sneak_idle_to_idle 41`、`sneak_fwd 61`、`track_bark_harvest 75`

注意事项：

- `trot` 必须配套 `idle_to_trot_fwd` 和 `trot_fwd_to_idle`。
- `sneak` 必须配套 `idle_to_sneak_idle_*` 和 `sneak_to_idle`。
- 警觉叫声类动作要低频，否则会显得焦躁。

### 第四阶段：道具和玩具系统

这些动作只有在页面出现“食物、玩具、球、床”等对象后才自然。

- 投喂链：`interact_elmer_treat`、`idle_pickup_item 67`、`idle_drop_item 51`
- 携物姿态：`sit_carry 2`
- 携物移动：`run_fwd carry item 13`、`trot_carry item 17`
- 取物：`sprint_retrieve item_108degree . 19`、`sprint_retrieve_item directional 19`
- 床上动作：`interact_bed_elmer_pet 31`、`interact_bed_lay_exist 270`、`interact_bed_sleep_exist 221`

建议等 UI 中出现实际道具或床，再接入这些动作。

## 不建议现在接入的动作

这些动作不是不能用，而是需要额外系统支撑。现在直接接入，会让整体变得突兀。

- 攻击/闪避：`atttack 8`、`idle_to_aggressive_pose 56`、`idleTOaggressive_pose 4`、`idle_to_dodge_backstep 51`、`idle_to_dodge_lft 31`
- 跳跃/落地：`idle_pose_to_jump_fwd 15`、`jump 22`、`land 7`、`land2. 5`
- 冲刺：`idle_to_sprint_fwd 39`、`sprint_fwd 11`、`sprint_fwd_to_idle 62`、`sprint_fwd_to_idle_sharp 59`
- 游泳：`hopping_water_fwd 21`、`sprint_jump_to_swim 42`、`swim_*`
- 生理动作：`pee 43`、`poop 75`

## 第一阶段接入结果

以下低风险增强已经接入到 `pages/webgl_animation_dog.html`：

- 新增 `RestIdle` 稳定态，使用 `idle_rest_pose 22`，在低精力、高安全感时更容易触发。
- 扩展点缀池，加入 `idle_shake_2. 81`、`idle_one_off_chin_drag 151`、`idle_sit_one_off_step_1. 119`、`idle_sit_one_off_step_2. 119`、`idle_sniff 83`。
- 探索循环从单一 `walk_fwd_sniff 46` 扩展为 `walk_fwd_sniff 46` 与 `walk_fwd_sniff_multi_cycle 61` 轮换。
- 点缀动作会根据心情做轻量排序：开心更容易甩身/回应，无聊更容易拖下巴或挪步，警觉更容易闻空气。

## 推荐的下一步实现

为了继续增强生动感，下一轮建议进入朝向和巡游阶段：

1. 接入 `idle_turn_45_rgt`、`idle_turn_90_rgt`、`idle_turn_180_*` 作为站立状态下的低频转向。
2. 接入 `walk_fwd_sniff_bank_lft 46`、`walk_fwd_sniff_bank_rgt 46`，让探索时可以轻微左右调整。
3. 为三种性格配置不同的转向概率：温顺低、活泼中、警觉高。

这一步会让它不只是原地循环，而是更像在观察和巡视环境。
