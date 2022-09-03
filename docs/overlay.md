# Overlay-遮罩层

## 使用
```
 <Overlay :isShow="isShow" @click="isShow = false"></Overlay>
```

## 属性
|  名称   | 描述              | 是否必选 | 数据类型    | 默认值 |
|  ----  | ----             | ----    |   ----    | ----  | 
| isShow  | 控制蒙层显示与否    | 否       |  Boolean  |  false  | 
| opacity  | 控制蒙层透明度    | 否       |  Number   | 0.5  | 
| zIndex  | 控制蒙层层级       | 否       |  Number   | 1  | 
| lockScroll  | 是否禁止滚动穿透     | 否      |  Boolean   | true  | 
| soltPosition  | solt插入的位置     | 否      |  String('bottom','top','center')   | "center"  | 
