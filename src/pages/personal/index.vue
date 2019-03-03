<template>
  <div class="container">
    <div class="personal-top">
      <!--<button open-type="getUserInfo" lang="zh_CN" @getuserinfo="onGotUserInfo">获取用户信息</button>-->
      <div class="information-wrap">
        <div class="info-top">
          <img :src="userInfo.avatarUrl" alt="">
          <p>{{userInfo.nickName}}</p>
        </div>
        <ul>
          <li>
            <p class="gold">1347</p>
            <p>我的金币</p>
          </li>
          <li>
            <img class="evaluate" src="../../images/evaluate.png" alt="">
            <p>我的评价</p>
          </li>
          <li>
            <img class="footprint" src="../../images/footprint.png" alt="">
            <p>我的足迹</p>
          </li>
        </ul>
      </div>
    </div>
    <div class="goods-wrap">
      <div class="remind-goods">
        <div class="title">
          <p>提醒商品</p>
          <img src="../../images/right-icon.png" alt="">
          <div class="clear"></div>
        </div>
        <scroll-view  :style="{'height': '336rpx'}" :scroll-x="true">
          <div class="scroll-x">
            <div class="r-goods-item" v-for="(item, index) in r_goods_list" :key="index">
              <image class="r-goods-img"  mode="aspectFill" :src="item.goods_img"></image>
              <div class="goods-title">
                <img class="taobao" src="../../images/taobao.png" alt="">
                <h2>{{item.goods_title}}</h2>
              </div>
              <p class="price">￥<span>{{item.rear_price_of_voucher}}</span></p>
            </div>
          </div>
        </scroll-view>
      </div>
      <div class="submit-goods">
        <h2>提交商品</h2>
        <div class="add-goods">
          <img src="../../images/add.png" alt="">
        </div>
      </div>
      <div class="personal-bottom">

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
      selectNavIndex: 3,
      userInfo: {
          avatarUrl: 'https://wx.qlogo.cn/mmopen/vi_32/Budy1Ogf3pGNBnY0eibfkWlYkMpYwXfGN6wYiaPBps3EssOsvg7EuWwGqicyNuPs8icGsDrZ7Uttx4TT3aValfCK6A/132',
          nickName: 'Action...'
      },
      r_goods_list: [
        {
          "id": 1,
          "goods_img": "../../images/recommend_list_1.jpg",
          "goods_title": "大V领套头宽松毛衣...",
          "rear_price_of_voucher": "39.5"
        },
        {
          "id": 2,
          "goods_img": "../../images/recommend_list_2.jpg",
          "goods_title": "粉色印花套头宽松毛...",
          "rear_price_of_voucher": "115"
        },
        {
          "id": 3,
          "goods_img": "../../images/recommend_list_3.jpg",
          "goods_title": "无袖纯白色蕾丝性感...",
          "rear_price_of_voucher": "108",
          "original_price": "138",
        },
        {
          "id": 4,
          "goods_img": "../../images/recommend_list_4.jpg",
          "goods_title": "大V领纯白色职业商...",
          "rear_price_of_voucher": "96"
        }
      ]
    }
  },

  components: {
    vueTabBar
  },

  methods: {
    onGotUserInfo (e) {
        this.userInfo = JSON.stringify(e.mp.detail.userInfo);

        wx.setStorageSync('userInfo', this.userInfo)
    },
    getSetting() {
      wx.getSetting({
        success: function(res){
          if (res.authSetting['scope.userInfo']) {
            wx.getUserInfo({
              success: function(res) {
                this.userInfo = res.userInfo

              }
            })
          }else{

          }
        }
      })
    }
  },
  onLoad () {
    wx.setNavigationBarTitle({
      title:'个人中心'
    })

    wx.setNavigationBarColor({
      frontColor: '#ffffff',
      backgroundColor: '#dbedc9'
    })

    wx.getStorage({
      key: 'userInfo',
      success: function (res) {
        this.userInfo = JSON.parse(res.data)

        console.log(this.userInfo)
      }
    })
  }

}
</script>

<style lang="less">
.personal-top {
  height: 310px;
  background: #dbedc9;

  .information-wrap {
    width: 690px;
    height: 292px;

    background: #fff;
    border-radius: 20px;

    position: relative;
    left: 50%;
    margin-left: -345px;

    bottom: -140px;

    .info-top {
      display: flex;

      img {
        width: 145px;
        height: 145px;
        border-radius: 50%;
        border: 1px solid #fff;

        position: relative;

        top: -36px;
        margin-left: 70px;
        margin-right: 36px;
      }

      p {
        font-size: 36px;
        margin-top: 20px;
      }
    }

    ul {
      display: flex;

      li {
        text-align: center;
        width: 33.3333333333333333%;

        p {
          font-size: 24px;
          margin-top: 6;
        }
      }
    }

    .evaluate {
      width: 50px;
      height: 50px;

      margin-top: 5px;
    }

    .footprint {
      width: 45px;
      height: 55px;
    }

    .gold {
      color: #f1545c;
      font-size: 40px!important;
      line-height: 64px;
    }
  }
}
.goods-wrap {
  background: #f2f2f2;

  .remind-goods {
    padding-top: 179px;
    .title {
      padding: 0 33px 0 30px;
      margin-bottom: 14px;

      p {
        float: left;
        font-size: 28px;
      }

      img {
        float: right;
        width: 16px;
        height: 28px;
      }
    }

    .scroll-x {
      display: flex;
      margin-left: 30px;

      .r-goods-item {
        width: 237px;
        margin-right: 10px;
        background: #fff;
        border-radius: 5px;

        .r-goods-img {
          max-width: 100%;
          max-height: 240px;
        }

        .goods-title {
          display: flex;

          margin-top: 2px;

          .taobao {
            width: 19px;
            height: 19px;
            margin: 6px 8px 0 12px;
          }

          h2 {
            font-size: 24px;
            width: 180px;
            overflow: hidden;
            text-overflow:ellipsis;
            white-space: nowrap;
          }
        }

        .price {
          font-size: 22px;
          color: #fe446a;
          text-align: center;
          margin-top: 7px;
          margin-bottom: 12px;

          span {
            font-size: 26px;
          }
        }
      }
    }

  }

  .submit-goods {
    height: 260px;
    h2 {
      font-size: 28px;
      margin-left: 30px;
      margin-top: 28px;
    }

    .add-goods {
      width: 690px;
      height: 300px;
      background: #fff;
      position: absolute;
      left: 50%;
      margin-left: -345px;
      bottom: -60px;

      border-radius: 5px;

      img {
        position: absolute;
        width: 129px;
        height: 129px;

        top: 50%;
        margin-top: -64.5px;
        left: 50%;
        margin-left: -64.5px;
      }
    }
  }

  .personal-bottom {
    height: 235px;
    background: #ffeeee;
  }
}
</style>


