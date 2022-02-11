# 迁移数据

无需引继，仅需第一次迁移即可实现类似BGO的多设备(iOS, Android, 模拟器)、多客户端(FGO,BFGO)登陆。支持在iOS和Android之间任意迁移。
仅适用于使用引继码方式的日服和美服。

## 导出存档

### 导出Android存档

Android系统的FGO**存档目录**为: `/sdcard/Android/data/<package>/files/data/`，d713等子文件夹为资源文件，可忽略。

`/sdcard/`即为打开文件管理的默认根目录, 对于内部储存此处`/sdcard/`=`/storage/emulated/0/`

`<package>`包名如下
- 日服: `com.aniplex.fategrandorder`
- 美服: `com.aniplex.fategrandorder.en`
- 日服BetterFGO: `io.rayshift.betterfgo`
- 美服BetterFGO: `io.rayshift.betterfgo.en`

### 导出iOS存档

iOS采用备份还原的方式导出或还原存档，首先需要通过**iMazing**软件备份“整个iPhone”至电脑（往往会有几到几十GB），然后从备份中导出某个应用存档。
若存档已过期，则需重新备份整个手机再导出存档，若上次备份的存档仍有效，则可以从上次备份导出存到，后续导出选项有这一项。

iMazing的使用图文教程网上很多，就不细说。备份较大，若希望删除备份，在iMazing对应设备中查看选项设置，会显示备份位置，可手动删除对应备份文件夹（默认路径可能为隐藏文件夹）。

0. 安装[iMazing](https://imazing.com/zh)软件（支持Windows和macOS，试用版就够用）。数据线连接iPhone与电脑，若手机有弹窗点击信任此电脑，iMazing将显示所连接的手机。
1. 在iMazing中选择`管理应用`，(可能需要登录苹果账号)，显示应用列表，有两个标签页(设备Device和资料库Library)，在设备这一页找到Fate/GO。
2. 右键`导出应用数据`，选择保存目录，下面有两选项：`备份并导出`和`尝试从上一次备份导出`。初次使用无差别，否则见此处第一部分描述。
3. 导出成功后，在目标文件夹下生成`Fate GO.imazingapp`(Windows)或`Fate/GO.imazingapp`(macOS)，注意字符`/`在Windows中是非法文件夹，若需要从mac复制文件到Windows，建议先修改文件名（~~仅仅是个人各种试错经历~~）。
4. imazingapp类型文件相当于zip压缩包，可使用WinRAR打开，若需替换文件，建议直接在WinRAR中替换。
5. 压缩包内`Container/Documents`即为存档目录。

iOS与Android存档目录下文件对应关系如下，还原到不同系统时记得修改文件名。

| iOS                | Android    | 备注          |
| ------------------ | ---------- | ------------ |
| authsave(2).dat*   | 54cc790    | 引继主文件，唯一指定登陆凭据               |
| friendcodesave.dat | e1a9f8     | 用户id，若不更新，登录页将仍旧显示旧的id，虽然实际登陆是新的 |
| signupsave.dat     | 644b05     | 可能是用户名啥的                         |
| user**save.dat     | 未知        | 一些页面或战斗的配置，删除此文件           |
| /                  | 其他文件    | 删除Android存档下所有其他文件，防止验证冲突 |

> 在iOS中可能同时存在`authsave.dat`和`authsave2.dat`两个文件，内容一样，复制一份即可

## 还原存档

### 还原至Android存档

删除data存档目录下所有其他文件，子目录可保留，然后复制上述`54cc790`等3个文件。万事大吉。在Android<->Android时即为简单的复制粘贴。

### 还原至iOS存档

iOS需在设置中关闭**查找我的手机**功能才能使用还原功能。还原结束可重新开启。

1. WinRAR打开imazingapp文件后，将重命名的`authsave.dat`等4个文件直接拖进去覆盖。(虽为zip压缩，但未尝试过先解压再重新压缩是否可行)
2. 回到iMazing的管理应用的应用列表，右键`还原应用存档`，手机将重启。
3. 重启后会需要id验证、安全隐私设置。**有一项从何处恢复数据的选项，选择不要恢复！** 万事大吉。