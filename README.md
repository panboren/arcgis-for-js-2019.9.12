一： 入门

1，MapView创建2D地图
2，SceneView创建3D地图
3，TileLayer创建两个图层，并在图层上指定url属性。url属性必须指向托管的缓存地图服务。
	map.layers.add（）将传输层添加到地图。
              图层在视图不可见，仍然可以访问。
4，  view.popup.open({})弹出窗口
5，小部件的基本概念：
      创建并实例化小部件
      设置窗口小部件的属性
     小部件添加 view.ui.add(toggle, "top-right");


二： 最新样式

1，编辑器”窗口小部件 new Editor( )  
   添加 view.ui.add(editor, "top-right");
2，不希望编辑器创建任何新功能，通过allowedWorkflows: ['update']在editingConfig属性中进行设置来限制此操作。
  限制显示和如何显示，通过fieldConfig[]在editingConfig属性中设置属性
3，必须设置小部件引用的视图
4，过滤功能，创建新的FeatureFilter并指定其where
5，SketchViewModel绘制用于过滤的多边形，折线或点。
6,自定义搜索源以使用搜索小组件。
7,FeatureForm小部件通过applyEdits在用户选择视图上的要素时调用该函数来更新现有要素的属性
8,DotDensityRenderer。点密度
9,WebGL 缩放器
10，SceneView中的hitTest返回一个与这些图层中鼠标位置相交的所有对象的数组
11，castShadows控制单个3D对象上阴影的属性
12，将glTF模型添加到SceneView。SketchViewModel。

6，DistanceMeasurement2D小部件测量两个或多个点之间的直线距离
     AreaMeasurement2D小部件测量区域。
     小于100 km时，默认模式为planar
7，FeatureLayer.applyEdits（）解析为包含编辑结果的对象。如果编辑失败，则编辑结果包含错误。
      Update Feature Attributes 编辑属性
8，草图小部件 Sketch
9，Slice小部件构建BuildingSceneLayer（真实建筑）
10，加载基本Web地图 new WebMap({ }）
11，填充 view.padding.right = 320;
12，BasemapToggle小部件，nextBasemap切换地图。
13，改变地图，切换map就可以了。 view.map = webmap;
14，SceneView.environment中的background属性可用于设置自定义颜色。
       改变底色 Ground.surfaceColor ground:{surfaceColor: [226, 240, 255]}
15，navigationConstraint以none将允许用户在地面下导航
       map.ground.navigationConstraint = {type: "none"};
17，SceneView.takeScreenshot（）截图。

图层：
2，VectorTileLayer 矢量数据
18，StreamLayer 流动地图
19，IntegratedMeshLayer完整的网格图层
2， new WebTileLayer({}）map.add(tiledLayer);平铺
2， new KMLLayer({}）播放   WMSLayer  也是播放
2，OpenStreetMapLayer  街道
2，WMTSLayer  登峰造极
2，GeoJSONLayer，GeoJSON的文件（.geojson）
2，Portal 门户切换地图
2，eoRSSLayer 有播放按钮的
2，BuildingSceneLaye 建筑
2，
2，

SceneLayer

2，FillSymbol3DLayer.material的colorMixMode在纹理建筑物上更改颜色，replace 将用新颜色替换纹理，multiply将初始纹理颜色与新颜色相乘。
2，边缘也使用SolidEdges3D或SketchEdges3D渲染，stops属性通过将最小值和最大值映射到特定颜色并插入中间值来设置颜色渐变。
2，
2，SceneView中使用Point几何图形化SceneLayer。
2，SceneLayer图层的definitionExpression中设置SQL查询来完成过滤
2，使用视图的hitTest（）方法获取用户单击的功能的目标。我们使用结果创建一个查询对象：
2，Esri办公室的SceneLayer中的功能，
2，

MapImageLayer

2， permitsLayer = new MapImageLayer({}） layers: [permitsLayer]
2，MapImageLayer的子图层并切换其可见性
2，MapImageLayer更新definitionExpression一个的子层。
2，MapImageLayer的子图层属性允许您动态地为地图服务中的图层设置渲染器
2，标记MapImageLayer子图层中的要素。
2，MapImageLayer中创建动态地图图层。
2，
2，CSVLayer允逗号分隔值的文本文件



Symbol

//面
par:Symbol3DLayer 
 ExtrudeSymbol3DLayer：type: "polygon-3d",  type: "extrude",用于通过从地面向上挤出多边形几何来渲染它们，从而创建一个3D体积对象。这是通过做PolygonSymbol3D在SceneView。MapView不支持3D符号。

Subclasses: PictureFillSymbol，SimpleFillSymbol
FillSymbol： type: "simple-fill", 填充符号用于在GraphicsLayer中绘制多边形图形或在2D MapView中绘制FeatureLayer。要创建新的填充符号，请使用SimpleFillSymbol或PictureFillSymbol。

par:Symbol3DLayer
FillSymbol3DLayer： type: "polygon-3d",用于在SceneView中渲染平面2D 多边形几何和3D体网格的曲面。MapView不支持3D符号。

//字体
Font：type: "text", 用于显示2D文本符号和3D文本符号的字体。此类允许开发人员设置字体的族，装饰，大小，样式和权重属性。请注意每个属性的“已知限制”，以了解它们如何根据图层类型而有所不同，以及是否使用MapView或SceneView。

//图标
par:Symbol3DLayer
IconSymbol3DLayer： type: "point-3d",用于在SceneView中使用带有PointSymbol3D的平面2D图标（例如圆形）渲染Point几何。MapView不支持3D符号。也可以使用IconSymbol3DLayers渲染多边形要素，但图标符号图层必须包含在PolygonSymbol3D中，而不是该场景中的PointSymbol3D。



//Line
par:Symbol 
Subclasses: SimpleLineSymbol
LineSymbol：线符号用于在2D MapView中的FeatureLayer中绘制折线要素。



par:Symbol3DLayer
LineSymbol3DLayer： type: "line-3d", type: "line", 在3D SceneView中使用带有LineSymbol3D的平面2D线渲染折线几何。MapView不支持3D符号。

//point
par:Symbol
Subclasses: PictureMarkerSymbol , SimpleMarkerSymbol
MarkerSymbol,标记符号用于在FeatureLayer中绘制Point图形或在2D MapView中绘制单个图形。要创建新的标记符号，请使用SimpleMarkerSymbol或PictureMarkerSymbol。标记符号可用于3D SceneView。但是，建议您使用PointSymbol3D。


par:Symbol3DLayer
ObjectSymbol3DLayer: type: "point-3d",type: "object",用于在SceneView中使用带有PointSymbol3D的体积3D形状（例如，球体或圆柱体）渲染点几何。MapView不支持3D符号。也可以使用ObjectSymbol3DLayers渲染多边形要素，但对象符号图层必须包含在PolygonSymbol3D中，而不是此场景中的PointSymbol3D。

par:Symbol3DLayer
PathSymbol3DLayer :type: "line-3d",type: "path", 在SceneView中使用带有LineSymbol3D的体积3D管渲染折线几何。MapView不支持3D符号。

par:FillSymbol
PictureFillSymbol: type: "picture-fill",  使用重复图案中的图像来对2D MapView中的面要素进行符号化。一个URL必须指向有效的图像。此外，符号可以有一个可选的轮廓，由SimpleLineSymbol定义。PictureFillSymbols可以应用于FeatureLayer或单个Graphic中的面要素。3D SceneView不支持PictureFillSymbol 。仅在使用MapView时使用它。

par:MarkerSymbol
PictureMarkerSymbol :type: "picture-marker",  使用图像在2D MapView或3D SceneView中渲染Point图形。一个URL必须指向有效的图像。PictureMarkerSymbols可以应用于FeatureLayer中的点要素或单个图形。下图描绘了一个FeatureLayer，其点要素使用PictureMarkerSymbol进行样式设置。


par:FillSymbol 
SimpleFillSymbol:type: "simple-fill", 用于在MapView或SceneView中渲染2D多边形。它可以填充固体颜色或图案。此外，符号可以有一个可选的轮廓，由SimpleLineSymbol定义。

par:LineSymbol 
SimpleLineSymbol:type: "simple-line", 用于在2D MapView中渲染2D 折线几何。SimpleLineSymbol还用于渲染标记符号和填充符号的轮廓。

par: MarkerSymbol
SimpleMarkerSymbol: type: "simple-marker",用于在MapView或SceneView中使用简单的形状和颜色渲染2D Point几何。它可以填充有固体颜色和具有可选的轮廓，其具有限定的SimpleLineSymbol。


Subclasses: FillSymbol , LineSymbol , MarkerSymbol , Symbol3D , TextSymbol , WebStyleSymbol
Symbol是所有符号的基类。符号将点，线，多边形和网格几何表示为视图中的矢量图形。符号只能在个别直接设置图形的GraphicsLayer或View.graphics。否则，它们将分配给应用于FeatureLayer或SceneLayer的渲染器。




Subclasses: ExtrudeSymbol3DLayer , FillSymbol3DLayer , IconSymbol3DLayer , LineSymbol3DLayer , ObjectSymbol3DLayer , PathSymbol3DLayer , TextSymbol3DLayer
Symbol3DLayer用于定义使用3D符号渲染的点，折线，多边形和网格几何的可视化。3D符号仅可用于在3D SceneView中的FeatureLayer，SceneLayer或独立图形中渲染要素。2D MapViews中不支持3D符号。

par:Symbol
TextSymbol: type: "text",用于定义用于在2D MapView中的FeatureLayer，CSVLayer，Sublayer和StreamLayer上显示标签的图形。如果几何类型是点或多点，则文本符号也可用于定义Graphic的符号属性。使用此类，您可以更改标签图形的颜色，字体，光晕和其他属性。

 par:Symbol3DLayer
TextSymbol3DLayer: type: "label-3d",用于为任何几何类型的要素绘制文本标签。这通常通过将其添加到3D SceneView中的LabelSymbol3D来完成。MapView不支持3D符号。

par:Symbol
WebStyleSymbol:type: "web-style",是一个用于方便地创建逼真和主题3D符号的类。它是创建PointSymbol3D对象的包装器，指向API中可用的Web样式资源。2D MapViews不支持此符号类型。




******************************************************
par:Symbol
Subclasses: LabelSymbol3D , LineSymbol3D , MeshSymbol3D , PointSymbol3D , PolygonSymbol3D
Symbol3D是所有3D符号的基类。它用于在FeatureLayer中渲染2D 点，折线和多边形要素以及在SceneLayer中渲染 3D网格要素。必须在SceneView实例中使用所有3D符号; MapViews中不支持3D渲染。


//标签
par:Symbol3D  Symbol
LabelSymbol3D： type: "label-3d", 用于为3D SceneView中的FeatureLayer渲染要素的标签。2D MapViews不支持此符号类型。

par:Symbol3D  Symbol
LineSymbol3D： type: "line-3d",  type: "path",用于在3D SceneView中渲染具有折线几何的要素。2D MapViews不支持此符号类型。

par:Symbol3D  Symbol 
MeshSymbol3D:  type: "simple", type: "mesh-3d",用于在3D SceneView中的SceneLayer中渲染3D网格特征。2D MapViews不支持此符号类型。


par:Symbol3D 
PointSymbol3D:type: "point-3d", type: "object",用于在3D SceneView中使用Point几何体渲染要素。2D MapViews不支持此符号类型。

par:Symbol3D 
PolygonSymbol3D: type: "polygon-3d",type: "extrude", 用于在3D SceneView中渲染具有多边形几何体的要素。2D MapViews不支持此符号类型。多边形特征也可以呈现为在每个多边形的质心处具有图标或对象的点。




























