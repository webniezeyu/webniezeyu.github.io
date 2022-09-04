# Overlay-弹出框

## 使用
```
 <n-dialog :isShow="isShow" @click="isShow = false"></n-dialog>
```

## 属性
|  名称   | 描述              | 是否必选 | 数据类型    | 默认值 |
|  ----  | ----             | ----    |   ----    | ----  | 
| isShow  | 控制蒙层显示与否    | 否       |  Boolean  |  false  | 
| opacity  | 控制蒙层透明度    | 否       |  Number   | 0.5  | 
| zIndex  | 控制蒙层层级       | 否       |  Number   | 1  | 
| lockScroll  | 是否禁止滚动穿透     | 否      |  Boolean   | true  | 
| soltPosition  | solt插入的位置     | 否      |  Str   ing('bottom','top','center')   | "center"  | 
| dialogStyle  | 弹出框的自定义样式     | 否      |  Object   | {height: "200px"}  | 
| title  | 标题     | 否      |  String   | "标题"  | 
| content  | 内容     | 否      |  String   | "这是一个非常好用的基于Vue3的H5移动端组件Dialog"  | 
| isShowButton  | 是否显示底部按钮     | 否      |  Boolean   | true  | 
| cancelCallback  | 取消按钮回调函数     | 在isShowButton=true时，必选      |  Function   | () => {}  | 
| confirmCallback  | 确认按钮回调函数     | 在isShowButton=true时，必选      |  Function   | () => {}  | 
