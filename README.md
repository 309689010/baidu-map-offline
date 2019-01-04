# baidu-map-offline

## 项目介绍：

1. 离线地图不是万能的, 有些依赖在线的功能是无法使用的, 请自行扩展
2. 请查看 离线地图示例demo.html 里面的示例，或者查看地图API在线示例：
    <http://developer.baidu.com/map/jsdemo.htm>
3. 地图API请查看百度官方说明：
    <http://developer.baidu.com/map/reference/index.php>
4. ECharts 实现地图散点图：
    <http://echarts.baidu.com/blog/2016/06/13/echarts-map-tutorial.html>

### 注意：

1. 默认普通地图，瓦片图放到 tiles 目录下（已有最大级别至16级的福州市地图）
2. 支持显示卫星混合地图，瓦片图放到 tiles_hybrid 目录下
3. 支持支定义混合图，瓦片图放到 tiles_self 目录下
4. 增加根据城市名称设置地图中心, 请自行扩展 map_city.js
5. 增加鼠标测距示例
6. 增加鼠标绘制线面示例

#### 增加新的瓦片图：

1. 使用瓦片下载工具下载你要的地区和级别：瓦片下载\BaiDuMapDownloadByThreadPool.java
2. 按需要修改map_load.js，指定瓦片图的路径，或者按默认的来
3. 目录说请看图片： 目录说明.jpg

#### 基本的使用方法：

1. 加载离线地图必须的文件：

```html
<script type="text/javascript" src="offlinemap/map_load.js"></script>
<link rel="stylesheet" type="text/css" href="offlinemap/css/map.css"/>
```

2. 增加一个容器用来显示地图：

```html
<div id="map_demo"></div>
```
    
3. 写JS脚本：

```javascript
<script type="text/javascript">  
    // 创建Map实例
    var map = new BMap.Map("map_demo");
    // 初始化地图,设置中心点坐标和地图级别
    map.centerAndZoom(new BMap.Point(116.404, 39.915), 7);
    // 设置地图中心显示的城市
    map.setCurrentCity("武汉");
    // 开启鼠标滚轮缩放
    map.enableScrollWheelZoom(true);
    // 缩放按钮
    map.addControl(new BMap.NavigationControl());
    // 添加地图类型控件 离线只支持普通、卫星地图; 三维不支持
    map.addControl(new BMap.MapTypeControl({
        mapTypes: [
            BMAP_NORMAL_MAP,
            BMAP_HYBRID_MAP
        ]
    }));
</script>
```
