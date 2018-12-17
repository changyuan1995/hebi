<template>
	<div class="container">
		<div class="swiper-container top-nav" ref="topNav">
		  <div class="swiper-wrapper">
		    <div class="swiper-slide" v-for="text in navData">{{text}}</div>
		  </div>
		</div>
		<div class="swiper-container swiperMain" ref="swiperMain">
		  <div class="swiper-wrapper">
		    <div class="swiper-slide" v-for="row in swiperSlide">
				<div class="wrapper" ref="wrapper">
					<div class="wrap">
						<div class="item" v-for="(item,index) in row" :key="index">
							<router-link :to="{name : 'article', params : {id : item.id}}">
								<img :src="item.pic">
								<div class="news-title">{{item.text}}</div>
								<span class="msgNum"><i class="fa fa-commenting-o"></i>{{item.msgNum}}</span>
							</router-link>
						</div>
					</div>
				</div>
		    </div>
		  </div>
		</div>
	</div>
</template>
<script>
	import BScroll from 'better-scroll'
	import Swiper from 'swiper'
	export default {
		name : 'local',
		data (){
			return {
				navData : ['鹤山区','淇滨区','山城区','淇县','浚县']
			}
		},
		methods : {
			refresh (){
				this.scroll.refresh();
			}
		},
		computed : {
			swiperSlide (){
				return this.$store.state.local
			}
		},
		mounted (){
			this.$refs.wrapper.forEach((v,i) => {
				var bscroll = new BScroll(v,{
					click : true
				})
				window.addEventListener('load',function(){
					bscroll.refresh();
				})
			})

			var topNav = new Swiper(this.$refs.topNav,{
				freeMode : true,
				slidesPerView : 5,
				watchSlidesVisibility: true
			})
			var swiperMain = new Swiper(this.$refs.swiperMain,{
				thumbs : {
					swiper : topNav,
					slideThumbActiveClass : 'cur'
				}
			})
		}
	}
</script>
<style scoped lang="less">
	.top-nav{
		width:100%;
		height:1.28rem;
		line-height: 1.28rem;
		background:#0EACF6;
		color:#fff;
		text-align:center;
		position:absolute;
		z-index:2;
		.cur{
			background:#ff3010;
		}
	}
	.swiperMain{
		height:100%;
		padding-top:1.28rem;
		.wrapper{
			height:100%;
			padding:0 0.32rem;
			overflow:hidden;
			.item{
				padding:0.32rem 0.24rem;
				display:flex;
				position:relative;
				a{
					display:flex;
					color:#333;
				}
				img{
					width:3.2rem;
					height:2.4rem;
				}
				.news-title{
					margin-left:0.32rem;
					font-size:0.48rem;
				}
				.msgNum{
					position:absolute;
					right:0.24rem;
					bottom:0.32rem;
					color:#999;
				}
			}
		}
	}
	
</style>