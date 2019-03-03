<template>
  <div class="container">
    <div class="detail-top">
      <img mode="aspectFill" :src="goods_list[id].goods_img"></img>
      <p>券</p>
    </div>
    <div class="detail-goods-info">
      <div class="info-title">
        <img src="../../images/taobao.png" alt="">
        <h2>{{goods_list[id].goods_title}}</h2>
      </div>
      <div class="info-price">
        <div class="rear-price">
          <p>券后价 <span class="red">￥<span class="red-and-big">{{goods_list[id].rear_price_of_voucher}}</span></span></p>
        </div>
        <div class="original-price">
          <p>￥{{goods_list[id].original_price}}</p>
        </div>
        <div class="clear"></div>
      </div>
      <div class="reduction-and-sold">
        <div class="price-reduction">
          <p class="left-box">领劵</p>
          <p class="right-box">减{{goods_list[id].price_reduction}}</p>
        </div>
        <div class="gold">
          <p>已售<span>{{goods_list[id].sold}}</span></p>
        </div>
        <div class="clear"></div>
      </div>
      <div class="remind">
        <p class="tip-text">新劵提醒</p>

        <div class="buttons" :tipStatus="tipStatus">
          <p @click="isOpenTip ('on')">开启</p>
          <p @click="isOpenTip ('off')">关闭</p>
          <img :class="tipPos" src="../../images/button-active.png" alt="">
        </div>

      </div>
      <div class="clear"></div>
    </div>

    <div class="entrance" @click="">
      <img src="../../images/entrance.png" alt="">
    </div>

    <div class="evaluate">
      <div class="evaluate-more">
        <p>用户评价 (1329)</p>
        <img src="../../images/right-icon.png" alt="">
        <div class="clear"></div>
      </div>

      <div class="evaluate-detail">

      </div>
    </div>

    <vue-tab-bar :selectNavIndex=selectNavIndex></vue-tab-bar>
  </div>
</template>

<script>
import vueTabBar from "../../components/vueTabBar.vue"

export default {
  data () {
    return {
      selectNavIndex: 4,
      id: 0,
      tipStatus: 'on',
      tipPos: 'on',
      goods_list: [
        {
          "id": 1,
          "goods_img": "../../images/recommend_list_1.jpg",
          "goods_title": "大V领套头宽松毛衣大V领套头宽松毛衣大衣 宽松毛衣大衣",
          "rear_price_of_voucher": "39.5",
          "original_price": "89.5",
          "price_reduction": "50",
          "sold": "245"
        },
        {
          "id": 2,
          "goods_img": "../../images/recommend_list_2.jpg",
          "goods_title": "粉色印花套头宽松毛...",
          "rear_price_of_voucher": "115",
          "original_price": "125",
          "price_reduction": "10",
          "sold": "245"
        },
        {
          "id": 3,
          "goods_img": "../../images/recommend_list_3.jpg",
          "goods_title": "无袖纯白色蕾丝性感...",
          "rear_price_of_voucher": "108",
          "original_price": "138",
          "price_reduction": "20",
          "sold": "245"
        },
        {
          "id": 4,
          "goods_img": "../../images/recommend_list_4.jpg",
          "goods_title": "大V领纯白色职业商...",
          "rear_price_of_voucher": "96",
          "original_price": "106",
          "price_reduction": "10",
          "sold": "245"
        }
      ]
    }
  },

  components: {
    vueTabBar
  },

  methods: {
    isOpenTip (key) {
      switch (key) {
        case 'on':
            if (this.tipStatus !== key) {
              this.tipStatus = key;
              this.tipPos = key;
            }
            break;
        case 'off':
            if (this.tipStatus !== key) {
              this.tipStatus = key;
              this.tipPos = key;
            }
            break;
      }
    }
  },

  created () {
  },
  onLoad (option) {
    this.id = option.id - 1;
    wx.setNavigationBarTitle({
      title:'商品详情'
    })
  }
}
</script>

<style lang="less">
.container {
  background: #f2f2f2;
}
.detail-top {
  height: 750px;
  img {
    width: 100%;
    height: 750px;
  }

  p {
    position: absolute;
    width: 99px;
    font-size: 48px;
    color: #fff;
    text-align: center;
    line-height: 113px;

    background: url("../../images/coupon-bg.png") no-repeat;
    background-size: 99px 113px;

    top: 0;
    left: 28px;
  }
}

.detail-goods-info {
  padding: 11px 30px 0 32px;
  background: #fff;

  .info-title {
    img {
      width: 32px;
      height: 32px;
      display: block;

      float: left;

      margin-top: 7px;
      margin-right: 17px;
    }

    h2 {
      font-size: 30px;
      color: #333333;
    }
  }

  .info-price {
    margin-top: 15px;
    .rear-price {
      float: left;

      p {
        font-size: 28px;
      }

      .red {
        color: #ff4646;
      }

      .red-and-big {
        font-size: 44px;
      }
    }

    .original-price {
      float: right;

      p {
        font-size: 26px;
        color: #666666;
        margin-top: 12px;
      }
    }
  }

  .reduction-and-sold {
    margin-top: 3px;
    .price-reduction {
      float: left;
      display: flex;

      p {
        text-align: center;
        line-height: 34px;
        height: 34px;
        font-size: 20px;
        padding: 0 9px 0 8px;
      }

      .left-box {
        color: #fff;
        background: #ff4646;
        border-top-left-radius: 6px;
        border-bottom-left-radius: 6px;
      }

      .right-box {
        border: 1px solid #ff4646;
        box-sizing: border-box;
        color: #ff4646;

        border-top-right-radius: 6px;
        border-bottom-right-radius: 6px;
      }
    }

    .gold {
      float: right;

      p {
        font-size: 24px;
        color: #666666;

        span {
          color: #14bc88;
        }
      }
    }
  }

  .remind {
    margin-top: 16px;
    padding-bottom: 24px;
    .tip-text {
      float: left;
      font-size: 26px;
      color: #666666;

      line-height: 46px;
      margin-right: 30px;
    }

    .buttons {
      position: relative;
      width: 140px;
      height: 46px;
      display: flex;
      background: #cdcdcd;
      border-radius: 5px;


      p {
        width: 70px;
        color: #ffffff;
        line-height: 46px;
        font-size: 22px;
        text-align: center;
        z-index: 9999;
      }

      img {
        width: 70px;
        height: 46px;

        position: absolute;

        top: 0;
        z-index: 0;
      }

      .on {
        left: 0;
      }

      .off {
        right: 0;
      }
    }
  }
}

.entrance {
  width: 100%;
  height: 352px;

  text-align: center;
  margin-top: 24px;

  img {
    width: 583px;
    height: 310px;
    margin-top: 30px;
  }
}

.evaluate {
  .evaluate-more {
    height: 70px;
    background: #fff;

    p {
      float: left;
      font-size: 26px;
      color: #999999;
      line-height: 70px;
      margin-left: 33px;
    }

    img {
      float: right;
      width: 16px;
      height: 28px;

      margin: 23px 29px 0 0;
    }
  }

  .evaluate-detail {
    width: 100%;
    height: 178px;
    background: #fff;
    margin-top: 1px;
  }
}
</style>


