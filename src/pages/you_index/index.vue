<template>
  <div class="index-container">
    <!-- 搜索框 -->
    <div class="search-box">
      <input type="text" placeholder="搜索">
      <icon class="icon-search" type=" search" size="12" color="#eb4450"></icon>
    </div>
    <!-- 轮播图 -->
    <swiper
      class="swiper"
      indicator-dots
      autoplay
      circular
      indicator-color="rgba(255,255,255,.3)"
      indicator-active-color="#fff"
    >
      <swiper-item class="swiper-item" v-for="item in swiperList" :key="item.image_src">
        <img mode="aspectFill" :src="item.image_src">
      </swiper-item>
    </swiper>
    <!-- 分类按钮区域 -->
    <div class="category-box">
      <div class="category-item" v-for="item in categoryList">
        <img :src="item.image_src" alt>
        <p>{{item.name}}</p>
      </div>
    </div>
    <!-- 楼层区域 -->
    <div class="floor-box">
      <!-- 每一层 -->
      <div class="floor-item" v-for="(item, index) in floorList">
        <h3 class="tit">{{item.floor_title.name}}</h3>
        <div class="content">
          <img :src="it.image_src" v-for="(it, i) in item.product_list">
        </div>
      </div>
    </div>
    <!-- 底线 -->
    <div class="bottom">
      <i class="iconfont icon-xiao"></i>
      我是有底线的!
    </div>
    <!-- 返回顶部 -->
    <div class="return-top" v-show="isShow" @click="toTop">
      <i class="iconfont icon-jiantoushang"></i>
      顶部
    </div>
  </div>
</template>

<script>
// 导入封装的haxios
import haxios from "../../utils/index.js";

export default {
  data() {
    return {
      // 轮播图数据
      swiperList: [],
      //分类按钮数据
      categoryList: [],
      // 楼层数据
      floorList: [],
      // 显示返回顶部
      isShow: false
    };
  },
  // 页面滚动事件
  onPageScroll(object){
    // console.log(object);
    // 页面滚动超过170，显示返回顶部
    if(object.scrollTop > 170){
      this.isShow = true;
    }else {
      this.isShow = false;
    }
  },
  methods: {
    // 返回顶部
    toTop() {
      wx.pageScrollTo({
        scrollTop: 0,
        duration: 300
      });
    }
  },
  async created() {
    // 发送获取轮播图的请求 (依次)
    // let swiperRes = await haxios.get({
    //   url: 'api/public/v1/home/swiperdata'
    // })
    // console.log(swiperRes);
    // this.swiperList = swiperRes.data.message;

    // //发送获取分类按钮的请求
    // let categoryRes = await haxios.get({
    //   url: 'api/public/v1/home/catitems'
    // })
    // console.log(categoryRes);
    // this.categoryList = categoryRes.data.message;

    // //获取楼层数据
    // let floorRes = await haxios.get({
    //   url: 'api/public/v1/home/floordata'
    // })
    // console.log(floorRes);
    // this.floorList = floorRes.data.message;

    //一次性请求三个
    let p1 = haxios.get({
      url: "api/public/v1/home/swiperdata"
    });
    let p2 = haxios.get({
      url: "api/public/v1/home/catitems"
    });
    let p3 = haxios.get({
      url: "api/public/v1/home/floordata"
    });
    let totalRes = await Promise.all([p1, p2, p3]);
    console.log(totalRes);
    this.swiperList = totalRes[0].data.message;
    this.categoryList = totalRes[1].data.message;
    this.floorList = totalRes[2].data.message;
  }
};
</script>

<style lang='scss'>
$uRed: #eb4450;
.index-container {
  padding-top: 100rpx;
  // 搜索框
  .search-box {
    position: fixed;
    top: 0;
    left: 0;
    padding: 20rpx 30rpx;
    width: 100%;
    background-color: $uRed;
    box-sizing: border-box;
    z-index: 999;
    input {
      width: 100%;
      padding-left: 300rpx;
      height: 60rpx;
      font-size: 24rpx;
      border-radius: 20rpx;
      background-color: #fff;
      box-sizing: border-box;
    }
    .icon-search {
      position: absolute;
      top: 50%;
      left: 50%;
      transform: translate(-50%, -50%);
    }
  }
  // 轮播图
  .swiper {
    height: 340rpx;
    .swiper-item {
      height: 100%;
      img {
        width: 100%;
        height: 100%;
      }
    }
  }
  //分类按钮
  .category-box {
    display: flex;
    padding: 25rpx 0;
    background-color: #fff;
    .category-item {
      flex: 1;
      text-align: center;
      img {
        width: 100rpx;
        height: 100rpx;
      }
      p {
        margin-top: 10rpx;
        font-size: 24rpx;
        color: #333;
      }
    }
  }
  //楼层样式
  .floor-box {
    .floor-item {
      .tit {
        padding: 25rpx;
        height: 90rpx;
        color: #ef8093;
        background-color: #eee;
        box-sizing: border-box;
      }
      .content {
        overflow: hidden;
        padding: 20rpx;
        padding-right: 0;
        box-sizing: border-box;

        img {
          float: left;
          margin-right: 10rpx;
          width: 230rpx;
          &:first-child {
            height: 378rpx;
          }
          &:nth-child(n + 2) {
            height: 185rpx;
          }
          &:nth-child(n + 4) {
            margin-top: 10rpx;
          }
        }
      }
    }
  }
  // 底线
  .bottom {
    display: flex;
    justify-content: center;
    // align-items: center;
    padding-top: 15rpx;
    height: 150rpx;
    font-size: 25rpx;
    color: #aaa;
    background-color: #f4f4f4;
  }
  .return-top {
    position: fixed;
    bottom: 20rpx;
    right: 20rpx;
    padding-top: 10rpx;
    width: 100rpx;
    height: 90rpx;
    font-size: 25rpx;
    text-align: center;
    border-radius: 50%;
    color: #747474;
    background-color: #fafafa;
  }
}
</style>
