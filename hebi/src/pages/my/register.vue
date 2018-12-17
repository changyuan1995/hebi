<template>
	<div class="container">
		<div class="title-default">
			<div class="left">
				<i class="fa fa-angle-left" @click="back"></i>
			</div>
			<h3>手机注册</h3>
		</div>

		<div class="submit">
			<div class="warning">
				<p>
					<i class="fa fa-exclamation-circle"></i>
					<span>您输入的手机号格式不正确！</span>
				</p>
			</div>
		</div>

		<div class="growp">
			<div class="item user">
				<i class="fa fa-user"></i>
				<input type="text" placeholder="请输入11位手机号">
			</div>
			<div class="item pass">
				<i class="fa fa-lock"></i>
				<input type="password" placeholder="请输入6-16位数字或字母密码">
				<router-link to="">忘记密码</router-link>
			</div>
		</div>

		<div class="growp">
			<div class="item">
				<i class="fa fa-pencil-square-o"></i>
				<input type="text" class="input-identifying" placeholder="请输入验证码">
			</div>
			<div class="identifying">
				发送验证码
			</div>
		</div>

		<div class="submit">
			<button class="btn">注册</button>
			<div class="protocol">
				<input type="checkbox">
				<router-link to="/register">已阅读并同意用户协议</router-link>
			</div>
		</div>
	</div>
</template>
<script>
	import { mapState } from 'vuex';
	export default {
		name : 'my',
		data (){
			return {
				options : [{
					icon : 'fa-star-o',
					text : '我的收藏',
					url : ''
				},{
					icon : 'fa-commenting-o',
					text : '我的评论',
					url : ''
				},{
					icon : 'fa-bookmark-o',
					text : '我的关注',
					url : ''
				},{
					icon : 'fa-search',
					text : '新闻搜索',
					url : ''
				},{
					icon : 'fa-sun-o',
					text : '设置',
					url : ''
				}]
			}
		},
		methods : {
			back(){
				this.$router.go(-1)
			}
		}
	}
</script>