# AWTRIX-Standalone

Awtrix 独立版 | 无需服务器端 | 覆盖基本常用功能 | 像素钟

## 食用提醒

1. 需自行配置相关参数后编译下载固件
2. 仅支持HTU21DF 温湿度传感器，其他型号需自行修改代码
3. 留意设备管脚信息，WS2812B像素屏的数据管脚与原Awtrix的不同，已修改为 D5

## 已有功能
1. 时间日期
2. 室内温湿度
3. 室外天气温湿度
4. 室外空气质量
5. B站粉丝数
6. 油管粉丝数

## 设备信息
1. 主控：ESP8266 NodeMCU开发板
2. 像素屏：WS2812B
3. 温湿度传感器：HTU21DF
4. LDR：光敏电阻+1k电阻

## 管脚信息
1. WS2812B		Data_PIN：D5
2. LDR			ADC_PIN：A0
3. HTU21DF		SDA_PIN：D2	SCL_PIN：D1

## 参数信息
```C
String UserKey = "your_apikey"; 		// 和风天气API私钥 https://dev.heweather.com/docs/start/ 需要自行申请
String Location = "your_locationID";	// 和风天气城市代码 https://github.com/qwd/LocationList/blob/master/China-City-List-latest.csv Location_ID 需要自行查询
#define BILIBILI_UID "0000000"			// B站用户ID 需要自行获取填写
#define YOUTUBE_CHANNEL "0000000"		// Youtube 频道ID 需要自行获取填写
#define YOUTUBE_APIKEY "your_apikey"	// Youtube APIKEY 需要自行获取填写
// 可供选择的任务列表
void showTime();		// 时间日期
void showTempSenor();	// 室内温湿度
void showWeather();		// 室外天气温湿度
void showAQI();			// 室外空气质量
void showBilibili();	// Bilibili粉丝数
void showYoutube();		// Youtube粉丝数
void (*taskList[])() = {showTime, showTempSenor, showWeather, showAQI, showBilibili, showYoutube}; // 在此处根据需求自行调节任务开关和顺序
String zeroTime = "00:00:00"; // 日期更新周期 每天零点 此处不要修改
String updateTime = "0:00";   // 天气、AQI、粉丝数据更新周期 0:00 表示每10 min更新 格式可以泛化 根据需求修改 默认10 min
int showTimes = 10;           // 每个任务展示时间 10 s 根据需求修改 默认10 s
int timeShowType = 0;         // 时间显示类型 0-HH:MM  1-HH:MM:SS 根据需求修改 默认HH:MM
bool nightModeEnable = true; // 夜间模式功能开启标志位 根据需求修改 默认开
int nightBeginHours = 22;    // 夜间模式开启时间-小时 根据需求修改 默认22点
int nightBeginMinutes = 30;  // 夜间模式开启时间-分钟 根据需求修改 默认30分
int nightEndHours = 7;       // 夜间模式结束时间-小时 根据需求修改 默认7点
int nightEndMinutes = 0;     // 夜间模式结束时间-分钟 根据需求修改 默认0分
```
## 致谢
1. [awtrix/AWTRIX2.0-Controller](https://github.com/awtrix/AWTRIX2.0-Controller)
2. [Ldufan/ESP8266_Heweather](https://github.com/Ldufan/ESP8266_Heweather)
3. [yinbaiyuan/AWTRIX2.0-Controller](https://github.com/yinbaiyuan/AWTRIX2.0-Controller)
