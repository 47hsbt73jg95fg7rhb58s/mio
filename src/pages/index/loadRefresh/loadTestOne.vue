<template>
	<view style="height: 100%">
		<scroll-view scroll-y style="position: fixed;top: 0;bottom: 0;">
			<!--这是顶部测试-->
			<view class="cu-list menu" :class="[false?'sm-border':'', true?'card-menu margin-top':'']">
				<view v-for="(item, index) in lists" :key="index" class="cu-item">
					<view class="content padding-tb-sm">
						<view>
							<text class="fa text-blue margin-right" :class="['fa-' + item.icon]"></text>
							<text>{{ item.name }}</text>
						</view>
					</view>

					<view v-show="false" class="action">
						<button :class="['cu-btn', 'bg-blue', 'shadow']" @tap="detail(item.url)">
							操作
						</button>
					</view>
					<view v-show="true" class="fa fa-angle-right fa-2x margin-left text-gray"></view>
				</view>
			</view>
			<!--实际滚动-->
			<view class="padding">
				<swiper-tab ref="mytab" v-model="tabClick" :tabLists="tabLists"></swiper-tab>
				<swiper style="height: 700rpx" :current="tabClick" @change="swiperChange">
					<swiper-item>
						<mescroll-item :i="0" :index="tabClick" :tabs="tabLists"></mescroll-item>
					</swiper-item>

					<swiper-item>
						<mescroll-item :i="1" :index="tabClick" :tabs="tabLists"></mescroll-item>
					</swiper-item>

					<swiper-item>
						<mescroll-item :i="2" :index="tabClick" :tabs="tabLists"></mescroll-item>
					</swiper-item>

					<swiper-item>
						<mescroll-item :i="3" :index="tabClick" :tabs="tabLists"></mescroll-item>
					</swiper-item>

					<swiper-item>
						<mescroll-item :i="4" :index="tabClick" :tabs="tabLists"></mescroll-item>
					</swiper-item>

					<swiper-item>
						<mescroll-item :i="5" :index="tabClick" :tabs="tabLists"></mescroll-item>
					</swiper-item>
				</swiper>
			</view>

			<!--底部测试-->
			<view class="cu-list menu" :class="[false?'sm-border':'', true?'card-menu margin-top':'']">
				<view v-for="(item, index) in lists" :key="index" class="cu-item">
					<view class="content padding-tb-sm">
						<view>
							<text class="fa text-blue margin-right" :class="['fa-' + item.icon]"></text>
							<text>{{ item.name }}</text>
						</view>
					</view>

					<view v-show="false" class="action">
						<button :class="['cu-btn', 'bg-blue', 'shadow']" @tap="detail(item.url)">
							操作
						</button>
					</view>
					<view v-show="true" class="fa fa-angle-right fa-2x margin-left text-gray"></view>
				</view>
			</view>
		</scroll-view>
	</view>

</template>

<script>
    import MescrollItem from './mescroll-swiper-item-two'
    import SwiperTab from '@/components/swiper-tab/swiper-tab'

    export default {
        components: {
            SwiperTab,
            MescrollItem,
        },
        data() {
            return {
                lists: [{name: '列表一', icon: 'video-camera'},
                    {name: '列表一', icon: 'user'},
                    {name: '列表一', icon: 'user'},
                    {name: '列表一', icon: 'user'},
                    {name: '列表一', icon: 'user'},
                    {name: '列表一', icon: 'user'},
                    {name: '列表一', icon: 'user'},
                    {name: '列表一', icon: 'user'},
                    {name: '列表一', icon: 'user'},
                    {name: '列表一', icon: 'user'},
                    {name: '列表一', icon: 'user'},
                    {name: '列表一', icon: 'user'},
                    {name: '列表一', icon: 'user'},
                    {name: '列表一', icon: 'user'},
                    {name: '列表一', icon: 'user'},
                    {name: '列表一', icon: 'user'},
                    {name: '列表一', icon: 'user'},
                    {name: '列表一', icon: 'phone'}
                ],
                tabLists: [
                    {name: '前端', type: 'frontend'},
                    {name: '后端', type: 'backend'},
                    {name: '安卓', type: 'Android'},
                    // {name: '苹果', type: 'iOS'},
                    // {name: 'Flutter', type: 'Flutter'},
                    // {name: '应用程序', type: 'app'},
                ],
                tabClick: 0 // 当前tab的下标
            }
        },
        methods: {
            swiperChange(e) { // 轮播菜单
                this.tabClick = e.detail.current
                this.$refs.mytab.longClick(e.detail.current)
            },
        },
        onLoad() {
            // #ifdef H5
            document.body.addEventListener('touchmove', function (evt) { // 禁止微信浏览器拖动
                evt.preventDefault()
            }, {passive: false})
            // #endif
        }
    }
</script>
