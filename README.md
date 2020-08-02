## legado阅读3.0自动构建

> 默认从最新发布的tag构建,每次构建会自动清空18PlusList.txt

> 当前最新tag:3.20.072917
  
1. fork到你自己的仓库
2. 去你自己的仓库,点一下右上角star就会自动开始构建,已经star的点unstar,再点一下star就会进行新的构建,你的[Actions](https://github.com/10bits/gedoor-Build/actions)列表会有显示的
3. 构建完,apk会自动打包,去你自己的[Actions](https://github.com/10bits/gedoor-Build/actions)列表里找
4. 每次构建大概十几分钟,请耐心等待
5. 为什么要去自己的仓库构建,因为很多人一起构建,Actions列表会显的乱七八糟

## 如果你安装apk遇到以下问题

1. `安装失败(-102)`问题,给release apk增加了签名,已解决
2. `与已安装应用签名不同`问题,请卸载重新安装,已解决
3. `与已安装程序共存`问题,通过修改`applicationIdSuffix='.releaseA'`,已解决,不用卸载重装了
4. 使用过程中遇到问题,请到这里解决[gedoor/legado](https://github.com/gedoor/legado/issues)
## 如何定制你自己的APP(举例)
请在`custom.sh`脚本里进行定制
```bash
#!/bin/sh
#设置搜索界面浮动按钮颜色
sed '/id\/fb_stop/a\        android:backgroundTint="#389099"' /opt/legado/app/src/main/res/layout/activity_book_search.xml -i
#缩小apk体积
sed '/minifyEnabled/i\            shrinkResources true' /opt/legado/app/build.gradle -i
sed 's/minifyEnabled false/minifyEnabled true/'         /opt/legado/app/build.gradle -i
```
## 定时更新脚本
`schedule.sh`脚本会定时更新本页面里`当前最新tag`的显示
## 免责声明

* 使用github actions自动构建,不会对原仓库代码程序进行任何修改
* 如果你使用了自动打包的apk对你的设备产生伤害,与本人无关,一切都是自动构建的