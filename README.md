[🎮 点击在线试玩](https://zzy-star-d.github.io/a-game/)
[🎮 点击在线试玩](https://zzy-star-d.github.io/a-game/)
# 荒域幸存者 v1.0

一款单文件、离线可玩的俯视角波次生存射击游戏。双击 `index.html` 即可开始，不需要安装依赖，也不请求网络资源。

[🎮 点击在线试玩](https://zyy-star-d.github.io/a-game/)

## 玩法

- 共 20 波，每波 30 秒；活动时长约 10 分钟，加上商店与选卡通常为 10–15 分钟。
- 角色自动攻击最近敌人，鼠标决定朝向。
- 击杀敌人会掉落绿色经验球与金色材料。
- 每波结束进入商店。材料在波末结算，可购买武器或属性，也可花 5 材料重掷。
- 武器槽共 6 个，满槽购买新武器时会要求选择替换位置。
- 第 5、10、15、20 波出现 Boss。Boss 会交替使用冲锋和环形弹幕。

## 操作

| 操作 | 键位 |
| --- | --- |
| 移动 | `WASD` 或方向键 |
| 朝向 | 鼠标 |
| 自动攻击 | 无需按键；有敌人时自动锁定最近目标 |
| 冲刺 | `空格` 或 `Shift`，冷却 1 秒，带 0.2 秒无敌 |
| 属性面板 | `Tab`，或鼠标悬停左下区域 |
| 暂停/继续 | `Esc` |
| 升级选卡 | 鼠标点击或 `1` / `2` / `3` |
| 商店购买 | 鼠标点击商品或 `1`–`4` |
| 商店重掷 | `R` 或点击“重掷” |
| 下一波 | `N` 或点击“下一波” |
| 满槽替换 | 按 `1`–`6` 选择要替换的武器 |
| 测试面板 | `F1`，可跳波、开关无敌、查看 FPS 与实体数量 |
| 重新开始 | 结束界面按 `R` |

移动端建议横屏游玩：左下虚拟摇杆控制移动，点击画面可立即触发一次自动瞄准射击。

## 已知问题

- 浏览器要求用户先点击或按键，之后才会初始化 WebAudio；因此第一次交互前不会播放音效，这是浏览器安全限制。
- 手机竖屏下 16:9 游戏区域会显得较小，建议横屏。
- 最高波次保存在浏览器 `localStorage`；隐私模式或禁用本地存储时不会跨刷新保留。
- `F1` 测试面板属于调参工具，会记录跳转到的最高波次。
- 极端低配设备在 200 敌人、Boss 弹幕和大量粒子同时出现时可能低于 60 FPS。

## 数值调整入口

所有主要可调数值集中在 `index.html` 顶部的 `CONFIG` 对象中。升级卡数值位于 `CONFIG.upgrades`，Boss 位于 `CONFIG.boss`，武器位于 `CONFIG.weapons`。

## 数值表

| 配置项 | 默认值 | 调大后的影响 | 调小后的影响 |
| --- | ---: | --- | --- |
| `waves.duration` | 30 秒 | 单波更长，整局更久，成长和刷怪总量更高 | 波次更快，单局更短，后期压力来得更快 |
| `waves.maxEnemies` | 200 | 允许更多同屏敌人，压力与性能成本上升 | 降低上限，画面更轻松，后期压迫感下降 |
| `waves.healRatio` | 0.2 | 每波回血更多，容错率上升 | 回血更少，续航压力上升 |
| `waves.startingMaterials` | 16 | 开局更容易买到第一件商品 | 前期构筑成型更慢 |
| `waves.spawnIntervals` | 0.90 → 0.11 秒 | 数值越大刷怪越慢；越小越快 | 全部调小会迅速堆怪 |
| `waves.enemyCaps` | 40 → 200 | 每波同屏上限提高，后期数量增多 | 单波同屏数量减少 |
| `player.baseHp` | 100 | 初始生存能力提高 | 更容易被连续命中击杀 |
| `player.baseSpeed` | 225 | 基础走位更灵活 | 更依赖移速升级 |
| `player.contactDamage` | 10 | 基础接触伤害更高 | 敌人碰撞威胁降低 |
| `player.hitCooldown` | 0.65 秒 | 受击后无敌更久，更宽容 | 敌人可更快连续造成伤害 |
| `player.dashSpeed` | 620 | 冲刺距离更远 | 冲刺更短 |
| `player.dashInvulnerability` | 0.2 秒 | 冲刺无敌窗口更长 | 更容易在冲刺中受伤 |
| `player.dashCooldown` | 1 秒 | 可冲刺频率降低 | 冲刺更频繁，机动性更强 |
| `enemies.baseHp` | 1 | 所有敌人在第 1 波更硬 | 前几波击杀更快 |
| `enemies.hpPerWave` | 0.58 | 后期血量增长更快，更吃武器成型 | 后期更依赖数量而不是血量施压 |
| `enemies.chaser.speedBase` | 70 | 追击者更快，更难甩开 | 更容易风筝 |
| `enemies.chaser.contactDamage` | 8 | 单次碰撞伤害更高 | 追击者威胁降低 |
| `enemies.tank.hpMultiplier` | 3.6 | 坦克更耐打 | 坦克更容易被快速处理 |
| `enemies.tank.speedBase` | 32 | 坦克推进更快 | 坦克更容易被拉开 |
| `enemies.shooter.preferredDistance` | 235 | 射手躲得更远 | 射手更靠近玩家 |
| `enemies.shooter.shootInterval` | 1.8 秒 | 射手发弹更慢 | 弹幕压力明显增加 |
| `enemies.shooter.projectileSpeed` | 185 | 射手弹更难躲 | 更容易通过走位避开 |
| `enemies.bomber.fuseTime` | 0.5 秒 | 玩家有更多时间离开爆炸圈 | 停顿更短，爆炸更突然 |
| `enemies.bomber.explosionRadius` | 92 | 爆炸范围更大 | 自爆兵更容易规避 |
| `enemies.bomber.explosionDamage` | 30 | 爆炸伤害更高 | 爆炸只负责打断走位 |
| `weapons.pistol.cooldown` | 0.58 秒 | 手枪射得更慢 | 手枪输出提高 |
| `weapons.pistol.damage` | 1 | 手枪单发伤害更高 | 手枪更依赖数量与其他武器 |
| `weapons.shotgun.pellets` | 5 | 单次弹丸更多，近战爆发更高 | 近距离爆发下降 |
| `weapons.shotgun.spread` | 23° | 扇形更宽、覆盖更大但单目标命中率下降 | 弹丸更集中，远距离命中增加 |
| `weapons.smg.cooldown` | 0.115 秒 | 射速降低 | 射速进一步提高，子弹数量上升 |
| `weapons.smg.spread` | 5.5° | 精度下降 | 远距离更稳定 |
| `weapons.laser.damage` | 3.1 | 激光爆发更高 | 激光更偏向辅助削血 |
| `weapons.laser.cooldown` | 1.35 秒 | 激光更慢 | 瞬时伤害频率提高 |
| `shop.itemCount` | 4 | 每轮商品更多，成型更快 | 选择空间减少 |
| `shop.rerollCost` | 5 | 重掷成本更高 | 更容易反复刷新商品 |
| `shop.statPriceMin/Max` | 8–12 | 属性商品更贵 | 属性更容易购买 |
| `weapons.*.price` | 12–26 | 武器成型更慢 | 更早获得多武器构筑 |
| `boss.baseHp` | 240 | 第一个 Boss 更耐打 | 第一个 Boss 更快被击杀 |
| `boss.hpPerBoss` | 100 | 后续 Boss 血量增长更快 | 后续 Boss 与第一个差距缩小 |
| `boss.chargeSpeed` | 430 | 冲锋更难躲 | 更容易横向移开 |
| `boss.chargeCooldown` | 3.8 秒 | 冲锋间隔更长 | Boss 更频繁冲锋 |
| `boss.barrageInterval` | 3.2 秒 | 弹幕更稀疏 | 弹幕更密集，封路能力增强 |
| `boss.barrageBulletCount` | 14 | 每轮弹幕更多 | 每轮弹幕更少 |
| `upgrades.damageMultiplier` | 1.1 | 每次伤害升级收益更高 | 伤害成长放缓 |
| `upgrades.attackSpeedMultiplier` | 1.1 | 所有武器攻击更快 | 攻速成长放缓 |
| `upgrades.moveSpeedMultiplier` | 1.08 | 移速升级收益更高 | 更依赖走位基础功底 |
| `upgrades.critChanceGain` | 0.05 | 暴击更常出现 | 暴击流派成型更慢 |
| `upgrades.dodgeGain` | 0.03 | 闪避成长更快，但仍受上限和递减约束 | 闪避属性更难堆 |
| `upgrades.dodgeCap` | 0.6 | 闪避上限提高；不建议超过 0.6 | 闪避上限降低，生存更依赖护甲与走位 |
| `upgrades.armorGain` | 1 | 每次护甲升级减伤更明显 | 护甲成长更慢 |
| `effects.hitFlashDuration` | 0.1 秒 | 受击闪白更久，反馈更强但可能刺眼 | 闪白更短 |
| `effects.deathParticleMax` | 10 | 死亡反馈更华丽，性能成本增加 | 粒子更少，画面更干净 |

## 验收记录

- Edge 实际运行：控制台无报错。
- 1366×768：16:9 画面无变形，HUD 不重叠。
- 844×390 触屏模拟：虚拟摇杆移动、触屏点射正常。
- 压力测试：200 敌人 + 300 子弹同屏，实测约 60 FPS。
- 当前 `index.html`：约 99.5 KB，3148 行；零外部依赖，断网可玩。
