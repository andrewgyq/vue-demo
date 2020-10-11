<template>
	<div id="app">
		<el-tabs type="border-card">
			<el-tab-pane label="批量保全申请"></el-tab-pane>

			<el-steps :space="500" :active="0" align-center>
				<el-step title="受理"></el-step>
				<el-step title="处理"></el-step>
				<el-step title="确认"></el-step>
			</el-steps>

			<el-divider></el-divider>
			<div style="text-align:left;"><span>保全类型</span></div>
			<el-divider></el-divider>

			<div style="text-align:left;">
				<el-radio disabled label="禁用">被保险人替换</el-radio>
				<el-radio label="2">新增被保险人</el-radio>
				<el-radio disabled label="禁用">减少保险人</el-radio>
				<el-radio disabled label="禁用">账户资金转移</el-radio>
				<el-radio disabled label="禁用">团单退保</el-radio>

				<el-radio disabled label="禁用">其它</el-radio>
				<el-select disabled placeholder=""></el-select>
				<el-button type="primary">下载单证</el-button>
			</div>

			<el-divider></el-divider>
			<el-form :inline="true">
				<el-form-item label="团单号">
					<el-input v-model="a"></el-input>
				</el-form-item>

				<el-form-item label="投保单号">
					<el-input v-model="b"></el-input>
				</el-form-item>

				<el-form-item label="单位代码">
					<el-input v-model="c"></el-input>
				</el-form-item>
			</el-form>
			<el-button type="primary">查询</el-button>

			<el-table style="width: 100%" border>
				<el-table-column prop="date" label="单位/投保人代码" width="180">
				</el-table-column>
				<el-table-column prop="name" label="投保人" width="180">
				</el-table-column>
				<el-table-column prop="address" label="投保人地址">
				</el-table-column>
			</el-table>
			
			<el-divider></el-divider>
			
			<el-table style="width: 100%" border>
				<el-table-column type="selection" width="55">
				</el-table-column>
				<el-table-column prop="name" label="团单号" width="180">
				</el-table-column>
				<el-table-column prop="address" label="主险名称">
				</el-table-column>
				<el-table-column prop="address" label="责任起期">
				</el-table-column>
				<el-table-column prop="address" label="责任终期">
				</el-table-column>
				<el-table-column prop="address" label="保单状态">
				</el-table-column>
				<el-table-column prop="address" label="出单方式">
				</el-table-column>
				<el-table-column prop="address" label="保单归属地">
				</el-table-column>
			</el-table>

			<el-divider></el-divider>

			<el-button-group>
				<el-button type="primary" icon="el-icon-arrow-left">上一步</el-button>
				<el-button type="primary">下一步<i class="el-icon-arrow-right el-icon--right"></i></el-button>
			</el-button-group>
		</el-tabs>
	</div>
</template>

<script>
	export default {
		data() {
			return {
				a: '',
				b: '',
				c: ''
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
