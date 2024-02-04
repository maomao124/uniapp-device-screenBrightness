<template>
	<view>
		<button type="primary" @click="set(1)" >设置屏幕亮度- 1</button>
		<button type="primary" @click="set(0.5)" >设置屏幕亮度- 0.5</button>
		<button type="primary" @click="set(0)" >设置屏幕亮度- 0</button>
		<button type="primary" @click="get()" >读取屏幕亮度</button>
		<button type="primary" @click="button1()" >保持屏幕常亮</button>
		<button type="primary" @click="button2()" >取消保持屏幕常亮</button>
	</view>
</template>

<script>
	export default {
		data() {
			return {
				
			}
		},
		methods: {
			set(number)
			{
				uni.setScreenBrightness({
					value:number,
					success: () => {
						uni.showToast({
							title:'设置成功'
						})
					},
					fail: () => {
						uni.showToast({
							title:'设置失败'
						})
					}
				})
			},
			get()
			{
				uni.getScreenBrightness({
					success: (res) => {
						uni.showToast({
							title:'当前亮度值：'+res.value
						})
					},
					fail: () => {
						uni.showToast({
							title:'读取失败'
						})
					}
				})
			},
			button1()
			{
				uni.setKeepScreenOn({
					keepScreenOn: true,
					success: () => {
						uni.showToast({
							title:'设置成功'
						})
					},
					fail: () => {
						uni.showToast({
							title:'设置失败'
						})
					}
				});
			},
			button2()
			{
				uni.setKeepScreenOn({
					keepScreenOn: false,
					success: () => {
						uni.showToast({
							title:'设置成功'
						})
					},
					fail: () => {
						uni.showToast({
							title:'设置失败'
						})
					}
				});
			}
		}
	}
</script>

<style>
button{
	margin: 5px;
}
</style>
