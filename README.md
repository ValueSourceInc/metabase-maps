# 生成城市地图的GeoJSON

## 第一步：下载地图数据
- 访问 [Highcharts Map Collection](https://code.highcharts.com/mapdata/) 下载特定城市的地图数据（JSON格式）。

## 第二步：转换为EPSG:4326格式（如果需要）
- 为确保兼容性，将下载的地图数据的坐标系转换为 `EPSG:4326` 格式。
- 如果尚未安装 `GDAL`，请先安装它。
- 使用以下命令进行坐标转换：


```bash
ogr2ogr -f "GeoJSON" -t_srs EPSG:4326 output.4326.json input.json
ogr2ogr -f "GeoJSON" -s_srs ESRI:102004 -t_srs EPSG:4326 output.4326.json input.json
```

## 也可以使用GADM（与上面区别与地图样式） 
-	从 [GADM](https://gadm.org/download_country.html) 下载特定国家的地图数据。
=	如果需要，可以使用 [Mapshaper](https://mapshaper.org) 压缩和简化数据。

## 注意事项

- 确保最终的GeoJSON文件是 EPSG:4326 格式，以便与大多数地图库兼容。