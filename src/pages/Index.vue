<template>
	<div class="Index">
		<el-row class="Index-row">
			<el-col :span="5" :offset="2" class="Index-col">
				<el-menu mode="vertical" class="Index-menu" :default-active="defaultActive" @select="selectMenu">
					<el-submenu :index="menu.index" v-for="menu in menus" :key="menu.index">
						<span slot="title">{{ menu.title}}</span>
						<el-menu-item :index="submenu.index" v-for="submenu in menu.submenu" :key="submenu.index">
							{{ submenu.title }}
						</el-menu-item>
					</el-submenu>
				</el-menu>
			</el-col>
			<el-col :span="15" class="Index-col">
				<div class="menu-content">
					<div v-for="(content, index) in currentContent" :key="index">
						<h2>例 {{ index + 1}}</h2>
						<iframe width="100%" height="300" :src="content.src" allowpaymentrequest allowfullscreen="allowfullscreen" frameborder="0">
						</iframe>
						<div class="content-tips" v-if="content.tips.length > 0">
							<p v-for="tip in content.tips">{{ tip }}</p>
						</div>
					</div>
				</div>
			</el-col>
		</el-row>
	</div>
</template>

<script>
	import Chapter from '@/const/index'
	export default {
		data () {
			return {
				jsfiddle: '',
				defaultActive: '1-1',
				menus: [
					{
						index: '1',
						title: '第2章 背景与边框',
						submenu: [
							{ index: '1-1', title: '1. 半透明边框' },
							{ index: '1-2', title: '2. 多重边框' },
							{ index: '1-3', title: '3. 灵活的背景定位' },
							{ index: '1-4', title: '4. 边框内圆角' },
							{ index: '1-5', title: '5. 条纹背景' },
							{ index: '1-6', title: '6. 复杂的背景图案' },
							{ index: '1-7', title: '7. 伪随机背景' },
							{ index: '1-8', title: '8. 连续的图像边框' }
						]
					},
					{
						index: '2',
						title: '第3章 形状',
						submenu: [
							{ index: '2-1', title: '1. 自适应的椭圆' },
							{ index: '2-2', title: '2. 平行四边形' },
							{ index: '2-3', title: '3. 菱形图片' },
							{ index: '2-4', title: '4. 切角效果' },
							{ index: '2-5', title: '5. 梯形标签页' },
							{ index: '2-6', title: '6. 简单的饼图' }
						]
					},
					{
						index: '3',
						title: '第4章 视觉效果',
						submenu: [
							{ index: '3-1', title: '1. 单侧投影' },
							{ index: '3-2', title: '2. 不规则投影' },
							{ index: '3-3', title: '3. 染色效果' },
							{ index: '3-4', title: '4. 毛玻璃效果' },
							{ index: '3-5', title: '5. 折角效果' }
						]
					}
				],
				menuContents: Chapter,
				currentContent: [],
			}
		},
		methods: {
			selectMenu (index) {
				this.currentContent = this.menuContents[index] || []
			}
		},
		created () {
			this.currentContent = this.menuContents[this.defaultActive]
		},
		updated () {
			console.log('updated')
		}
	}
</script>

<style scoped lang="scss">
	@import './Index.scss';
</style>
