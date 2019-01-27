<template>
  <div class="mine-container">
    <!-- 顶部 -->
    <div class="top-box">
      <div class="avatar">
        <i class="iconfont icon-shezhi"></i>
        <img src="/static/icon/icon.png" alt>
        <i class="iconfont icon-xiaoxi"></i>
      </div>
      <p>登录/注册</p>
    </div>
    <div class="body-wrap">
      <!-- 历史记录 -->
      <div class="history-box">
        <div class="history-item">
          <p>0</p>
          <p>收藏的店铺</p>
        </div>
        <div class="history-item">
          <p>0</p>
          <p>收藏的商品</p>
        </div>
        <div class="history-item">
          <p>0</p>
          <p>关注的商品</p>
        </div>
        <div class="history-item">
          <p>0</p>
          <p>我的足迹</p>
        </div>
      </div>
      <!-- 订单 -->
      <div class="order-box">
        <div class="tit">我的订单</div>
        <div class="content">
          <div class="item">
            <i class="iconfont icon-daifukuan"></i>
            <p>待付款</p>
          </div>
          <div class="item">
            <i class="iconfont icon-daishouhuo"></i>
            <p>待收货</p>
          </div>
          <div class="item">
            <i class="iconfont icon-tuikuan"></i>
            <p>退款/退货</p>
          </div>
          <div class="item">
            <i class="iconfont icon-dingdan"></i>
            <p>全部订单</p>
          </div>
        </div>
      </div>
      <!-- 选项卡 -->
      <div class="option-box">
        <div class="option">
          收货地址管理
          <i class="iconfont icon-jiantouyou"></i>
        </div>        
      </div>
      <div class="option-box">
        <div class="option">
          联系客服
          <i>400-618-40000</i>
        </div>
        <div class="option">
          意见反馈
          <i class="iconfont icon-jiantouyou"></i>
        </div>
        <div class="option">
          关于我们
          <i class="iconfont icon-jiantouyou"></i>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      // 记录用户名字
      username: ""
    };
  }
};
</script>

<style lang='scss'>
$uRed: #eb4450;
.mine-container {
  // 顶部头像区
  .top-box {
    padding-top: 100rpx;
    height: 420rpx;
    color: #fff;
    background-color: $uRed;
    box-sizing: border-box;
    .avatar {
      display: flex;
      justify-content: center;
      align-items: center;
      font-size: 30rpx;
      img {
        margin: 0 65rpx;
        width: 135rpx;
        height: 135rpx;
        border: 5rpx solid #fff;
        border-radius: 50%;
      }
    }
    p {
      margin-top: 20rpx;
      font-size: 30rpx;
      text-align: center;
    }
  }
  // 下方内容区域
  .body-wrap {
    padding: 0 20rpx;
    background-color: #f4f4f4;
    // 历史记录
    .history-box {
      display: flex;
      height: 120rpx;
      background-color: #fff;
      transform: translateY(-30rpx);
      .history-item {
        flex: 1;
        display: flex;
        flex-direction: column;
        justify-content: center;
        align-items: center;
        height: 100%;
        font-size: 25rpx;
        color: #626363;
      }
    }
    // 我的订单
    .order-box {
      background-color: #fff;
      .tit {
        padding: 20rpx 30rpx;
        font-size: 35rpx;
        border-bottom: 1px solid #dddddc;
      }
      .content {
        display: flex;
        height: 160rpx;
        .item {
          flex: 1;
          display: flex;
          flex-direction: column;
          justify-content: center;
          align-items: center;
          height: 100%;
          i {
            font-size: 55rpx;
            color: $uRed;
          }
          p {
            margin-top: 10rpx;
            font-size: 30rpx;
            color: #292929;
          }
        }
      }
    }
    // 选项卡区域
    .option-box {
      margin-top: 25rpx;
      padding-left: 30rpx;
      background-color: #fff;
      .option {
        display: flex;
        justify-content: space-between;
        padding: 20rpx 30rpx 20rpx 0;
        font-size: 35rpx;
        border-bottom: 1px solid #dddddc;
        &:last-child {
          border: none;
        }
        i {
          color: #aaa;
        }
      }
    }
    
  }
}
</style>
