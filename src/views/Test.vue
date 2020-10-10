<template>
	<div>
		<el-radio v-model="radio" label="1">备选项</el-radio>
		<el-radio v-model="radio" label="2">备选项</el-radio>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				radio: '1'
			}
		},
		created() {
			this.$axios({
				method: 'get',
				url: 'https://api.coindesk.com/v1/bpi/currentprice.json'
			}).then((response) => { //这里使用了ES6的语法
				console.log(response) //请求成功返回的数据
			})
		}
	}
</script>
