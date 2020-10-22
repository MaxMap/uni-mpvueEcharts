# uni-app mpvue-echarts
### 插件安装
单独新建一个文件夹，打开终端下载 echarts 、mpvue-echarts
npm install echarts mpvue-echarts --save
node_modules 目录，里面的三个目录：echarts、mpvue-echats 、zrender 导入当前项目的根目录
在所需要的组件
import * as echarts from 'echarts'
import mpvueEcharts from 'mpvue-echarts'

view 视图展示
// <mpvue-echarts ref="pieChart2" :echarts="echarts" @onInit="initChart" />

基本流程可以参考网上 [mpvue-echarts安装教程](https://blog.csdn.net/CherryLee_1210/article/details/83016706)

### uniapp小程序中报:this.echarts.setCanvasCreator 找不到响应的函数。
原因：版本不适配
解决：替换最新的 mpvue-echarts 组件 可以直接拿走

### 页面不报错，但是空白展示
原因：1> 数据不对，2> 宽和高未位置 包括嵌套在外层的view
解决：1> 数据形式写对 2>最外层view设置宽和高。逻辑层 的echarts 也插入宽高
### 页面二次刷新或者数据变化 echarts 位置偏移
原因：1>因为组件已经加载过，单纯改变数据，无法实现图表渲染，2>echarts option没有设置x和y ，导致图表位置自动发生改变
解决：1>通过 v-if 重新渲染组件，数据变化是组件也重新显示 2>设置位置和宽度大小


