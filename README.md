# android_SmallestWidth
## android  sw限定符适配即smallestWidth适配,也叫最小宽度限定符适配,这是对smallestWidth 的一个总结



px = density * dp;

density = dpi / 160;

dpi=density*160

px = dp * (dpi / 160);

dp= px / (dpi / 160) 

名称	密度区间
mdpi	120dpi~160dpi
hdpi	160dpi~240dpi
xhdpi	240dpi~320dpi
xxhdpi	320dpi~480dpi
xxxhdpi	480dpi~640dpi
通常情况下每个目录对应的屏幕分辨率如下

名称	代表分辨率
mdpi	320x480
hdpi	480x800
xhdpi	720x1280
xxhdpi	1080x1920
xxxhdpi	1440x2960

# 举个栗子：
假如APP运行在一款1920x1080分辨率的手机上，DPI是400；可以得出该手机的最小宽度是1080px，
dp值:1080 / (400/160) = 432，这样系统就会匹配到values-sw432dp目录下的dimens文件，

选取一个最小宽度作为基准值，假如我选取360dp作为最小宽度基准值，也就是说将屏幕宽度等分为360份，从1到360 份所占的dp值的计算如下：
dp = ( 实际最小宽度 / 最小宽度基准值 ) * X

X是份额，我们是以360dp作为基准，那X就是从1到360

## 适配的最小宽度，320
dp=(320/360)*1=0.8889
dp=(320/360)*2==1.7779
dp=(320/360)*3=2.6667
dp=(320/360)*4=3.5556
dp=(320/360)*5=4.4444


## 适配的最小宽度，sw360 dp
dp=(360/360)*1=1
dp=(360/360)*2=2
dp=(360/360)*3=3


## 适配的最小宽度，sw420 dp
dp=(420/360)*1=1.1667
dp=(420/360)*2=2.3333
dp=(420/360)*3=3.5


## 适配的最小宽度，sw480 dp
dp=(480/360)*1=1.3333
dp=(480/360)*2=2.6667
dp=(480/360)*3=4.0000
dp=(480/360)*4=5.3333


 ## 模拟器上的机子
 
Pixel 4 XL 1440*3040  dpi=560 ,dp值 = 1440 / (560/160) = sw411.4285 约

Pixel 6 Pro  1440*3120 dpi=560 ,dp值 = 1440 / (560/160) = sw411.4285 约

Galaxy Nexus 720*1280 dpi=320 ,dp值 = 720 / (320/160) = sw360 

# 最后获取最小宽度值

    fun isXHIGH(context: Context): Boolean {
        val config = context.resources.configuration
        return config.smallestScreenWidthDp <= DisplayMetrics.DENSITY_XHIGH
    }
 备注：区分smallestScreenWidthDp compatSmallestScreenWidthDp 区别
