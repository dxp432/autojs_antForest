# （一）下载地址：
### auto.js下载
这个app（autoJs-V4.1.1.Alpha2-common-armeabi-v7a-debug下载地址：
来自https://github.com/Ericwyn/Auto.js/releases
### 打包插件下载
如果你需要把自己编写好的脚本打包成app，就需要用到打包插件，
Auto.js打包插件_4.1.0 Alpha5来自下面的百度云：
打包插件4.1.0.alpha5
https://pan.baidu.com/s/1NTGBKW9mlWHkf0IkXUshFQ ?提取码:8j57

# （二）使用方法

 1. 在vs code上安装 AutoJS 插件：点击 扩展 搜索 Auto.js 或 hyb1996 即可找到Auto.JS插件。
    
 2.  按 Ctrl+Shift+P 或点击"查看"->"命令面板"可调出命令面板，输入 Auto.js可以看到几个命令，移动光标到命令Auto.js: Start Server，按回车键执行该命令。
   
 3.  在Auto.js的侧拉菜单中启用调试服务，并输入电脑IP地址，等待连接成功。
  
 4. 在电脑上编辑JavaScript文件并通过命令Run或者按键F5在手机上运行。

# （三）蚂蚁森林偷能量
简单脚本实例： 蚂蚁森林偷能量

步骤：

 1. 打开支付宝app
 2. 点击蚂蚁森林图标
 3. 点击指定坐标（写死的坐标），点击很多坐标进行收自己的能量
 4. 点击“偷能量”按钮进行偷其他人的能量。

代码示例：

```javascript
"auto";
var width = device.width;//1080
var height = device.height;//2280

function myFunction() {
    // // 收集自己能量
    log("收能量")
    sleep(1000) //能量球生成需要一秒钟时间
    for(var myx = 229;myx < 810; myx += 70){
        for(var myy = 439;myy < 736; myy += 70){
            click(myx, myy)
            sleep(10)
        }
    }
    click(828, 801)
    sleep(50)
    click(252, 832)
    sleep(4000)
}

function doit() {

    //打开支付宝App
    launch("com.eg.android.AlipayGphone");
    waitForPackage("com.eg.android.AlipayGphone", 200);

    while (!className("android.widget.TextView").text("蚂蚁森林").exists()) {
        sleep(1000);
    }
    toast("进入蚂蚁森林");
    click("蚂蚁森林");
    while (!text("种树").findOnce()) {
        sleep(500);
    }


    for(var my_loop = 1;my_loop < 5; my_loop += 1){
        for(var my_index = 1;my_index < 3; my_index += 1){
            myFunction()

            log('点击找能量按钮')
            click(949, 1555)
            sleep(4000)
        }
        
        log('返回')
        click(56, 144)
        sleep(4000)
    }

}


// 时间判断
function time() {
    var now = new Date();
    // var minutes = now.getMinutes();
    var hours = now.getHours();
    // var time = hours * 60 + minutes - 400; //6点50
    if (hours >= 0 && hours <= 99) { //6点50到7点50
        log('时间符合，再次收取');
        return true
    } else {
        return false
    }
}


// 时间判断
function time_ant() {
    var now = new Date();
    // var minutes = now.getMinutes();
    var hours = now.getHours();
    // var time = hours * 60 + minutes - 400; //6点50
    if (hours >= 0 && hours <= 99) { //6点50到7点50
        log('时间符合，再次收取');
        return true
    } else {
        return false
    }
}



// 请求截图权限
if (!requestScreenCapture()) {
    toast("请求截图失败");
}

log('开始运行程序')
while (time())
{
    log('我还没醒，帮我检测')
    sleep(1000)
    if (time_ant()) {
        log('is time!')
        doit()
        sleep(5000)
    }
    else{
        log('wait....')
        sleep(2000)
    }
}
log('out')

```
