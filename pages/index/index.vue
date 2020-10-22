<template>
	<view class="content">
		<view class=""  style="height: 40vh;width: 100%;">
			<mpvue-echarts  ref="pieChart" :echarts="echarts" @onInit="initChartSix" />
		</view>
		<view class=""  style="height: 40vh;width: 100%;">
			<mpvue-echarts ref="pieChart2" :echarts="echarts" @onInit="initChart" />
		</view>
	</view>
</template>

<script>
	import * as echarts from 'echarts'
	import mpvueEcharts from 'mpvue-echarts'
	export default {
		data() {
			return {
				echarts,
				sexlist:[60,40],
				userlist:[
					 ['Matcha Latte',43.3, 85.8, 93.7],
					  ['Milk Tea',83.1, 73.4, 55.1]
				]
			}
		},
		onLoad() {

		},
		components: {
			mpvueEcharts
		},
		methods: {
			//男女比例
			initChartSix(e) {
				let {
					canvas,
					width,
					height
				} = e;
				width = width;
				//直接定义宽和高图表再次渲染不在脱离位置
				//let canvas = this.$refs.pieChart.canvas;
				echarts.setCanvasCreator(() => canvas);
				const chart = echarts.init(canvas, null, {
					width: 400,
					height: 300
				})
			
				canvas.setChart(chart)
				var option = {
					right:"0%",
					bottom:"0%",
					width: "90%", // 宽度
					height: "90%", // 高度
					color: ['rgba(131, 142, 240, 1)', 'rgba(230, 108, 152, 1)'],
					series: [{
						name: '访问来源',
						type: 'pie',
						radius: ['0', '60%'],
						center: ['55%', '50%'],
						hoverAnimation: false,
						clickable: false, //是否开启点击
						silent: true,
						label: {
							normal: {
								formatter: '{b}: {d}%',
								textStyle: {
									fontWeight: 'normal',
									fontSize: 10
								},
							}
						},
						data: this.sexlist,
						itemStyle: {
							emphasis: {
								shadowBlur: 10,
								shadowOffsetX: 0,
								shadowColor: 'rgba(0, 0, 0, 0.5)'
							}
						}
					}],
					itemStyle: { // 此配置
						normal: {
							borderWidth: 30,
							borderColor: '#ffffff',
						},
						emphasis: {
							borderWidth: 0,
							shadowBlur: 10,
							shadowOffsetX: 0,
							shadowColor: 'rgba(0, 0, 0, 0.5)'
						}
					}
				};
			
				chart.setOption(option)
				this.$refs.pieChart.setChart(chart);
			},
			initChart(e) {
				let {
					canvas,
					width,
					height
				} = e;
				width = width;
				//let canvas = this.$refs.pieChart.canvas;
				echarts.setCanvasCreator(() => canvas);
				const chart = echarts.init(canvas, null, {
					width: width,
					height: height
				})
			
				canvas.setChart(chart)
				var option = {
					color: ['rgba(106, 173, 237, 1)', 'rgba(131, 142, 240, 1)', 'rgba(59, 209, 159, 1)'],
					legend: {
						show:false
					},
					tooltip: {},
					dataset: {
						source: this.userlist
					},
					xAxis: {
						type: 'category',
						axisLine:{
							lineStyle:{
								color:'rgba(230, 230, 230, 1)'
							}
						}
					},
					yAxis: {
						axisLine:{
							show: false,
							lineStyle:{
								color:'rgba(230, 230, 230, 1)'
							}
						}
					},
					// Declare several bar series, each will be mapped
					// to a column of dataset.source by default.
					series: [{
							type: 'bar',
							z: 12,
							name:' ',
							// "barWidth": "0",
							"label": {
								"normal": {
									"show": true,
									"position": "top",
									// "formatter": "{c}%"
									fontSize: 10,
									color: '#333'
								}
							}
						},
						{
							type: 'bar',
							z: 12,
							// "barWidth": "0",
							"label": {
								"normal": {
									"show": true,
									"position": "top",
									// "formatter": "{c}%"
									fontSize: 10,
									color: '#333'
								}
							}
						},
						{
							type: 'bar',
							z: 12,
							// "barWidth": "0",
							"label": {
								"normal": {
									"show": true,
									"position": "top",
									// "formatter": "{c}%"
									fontSize: 10,
									color: '#333'
								}
							}
						}
					]
				};
			
				chart.setOption(option)
				this.$refs.pieChart2.setChart(chart);
				//return chart
			}
		}
	}
</script>

<style>
	.content {
		display: flex;
		flex-direction: column;
		align-items: center;
		justify-content: center;
	}

	.logo {
		height: 200rpx;
		width: 200rpx;
		margin-top: 200rpx;
		margin-left: auto;
		margin-right: auto;
		margin-bottom: 50rpx;
	}

	.text-area {
		display: flex;
		justify-content: center;
	}

	.title {
		font-size: 36rpx;
		color: #8f8f94;
	}
</style>
