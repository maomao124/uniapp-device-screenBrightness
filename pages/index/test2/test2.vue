<template>
	<view>
		<button type="primary" @click="set(1)" >设置屏幕亮度- 1</button>
		<button type="primary" @click="set(0.5)" >设置屏幕亮度- 0.5</button>
		<button type="primary" @click="set(0)" >设置屏幕亮度- 0</button>
		<button type="primary" @click="get()" >读取屏幕亮度</button>
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
			}
		}
	}
</script>

<style>
button{
	margin: 5px;
}
</style>
