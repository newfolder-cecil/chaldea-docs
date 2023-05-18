# Bugs

以下信息截至 v2.3.6

## 已知问题

- 宫本武藏（Saber）的强化后宝具的特攻总是生效
- 概念礼装技能先于所有从者被动触发。这会导致当卡莲（Ruler）装备付与自身弱化无效的礼装时，友方的复仇者被动可能会因为队伍顺序无法正确付与卡莲弱化耐性下降

## 未实现

- damageNpCounter - 安哥拉曼纽宝具
- counterFunction - 巴泽特宝具

## 已于v2.3.6版本修复

- 为修复回合结束时效果可能提前一回合消失的问题重构 buff 回合数计数方式
- gainNpIndividualSum 现在正确地从指定的目标进行特性计数

## 已于v2.3.5版本修复

- 〔毒〕回复化 - 洛库斯塔二技能
- 攻击后效果未在宝具攻击后触发 - 超级班杨宝具
- 兽尼禄宝具特攻不生效
  - 添加了一个当兽尼禄在队伍中时自动为敌方从者添加兽尼禄特攻特性的选项

## 已于v2.3.3版本修复

- 部分检查目标或自身的 buff 的特性的 buff 不会生效。例：纹章 77（天帝的贵妃）检测目标具有灼烧 buff。
- 当一个从者有复数的宝具类型变更 buff 时，首个 buff 会错误地覆盖之后的 buff。
- 当一个从者有复数的改变职阶相性的 buff 且数值更改皆为强制性（overwriteForce）时，之后的 buff 会错误地覆盖首个 buff。例：迦摩三技能&莱妮斯宝具 vs
  AE 阶敌人。
- 七周年之后选项开启后，无效的首卡(如封印/眩晕)实际能提供染色，但目前模拟器为未染色。