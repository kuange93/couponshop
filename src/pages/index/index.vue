<template>
  <div class="container">
      <div class="home-top">
        <input type="text" placeholder="请输入商品名称">
      </div>
      <div class="banner">
        <img src="../../images/banner.jpg" alt="">
      </div>
      <div class="classification">
        <ul>
          <li @click="skipPage('9dot9')">
          <img src="../../images/9dot9.png" alt="">
          <p>9.9包邮</p>
        </li>
          <li @click="skipPage('preferential')">
            <img src="../../images/discount.png" alt="">
            <p>实时优惠</p>
          </li>
          <li @click="skipPage('hotlist')">
            <img src="../../images/hot.png" alt="">
            <p>热销榜</p>
          </li>
          <li @click="skipPage('praiselist')">
            <img src="../../images/good.png" alt="">
            <p>好评榜</p>
          </li>
          <li @click="skipPage('notice')">
            <img src="../../images/preview.png" alt="">
            <p>预告</p>
          </li>
          <li @click="skipPage('friedfood')">
            <img src="../../images/delicacy.png" alt="">
            <p>爆款美食</p>
          </li>
          <li @click="skipPage('departmentstore')">
            <img src="../../images/general-merchandise.png" alt="">
            <p>居家百货</p>
          </li>
          <li @click="skipPage('grainandoil')">
            <img src="../../images/grain-and-oil.png" alt="">
            <p>粮油调味</p>
          </li>
        </ul>
        <div class="clear"></div>
      </div>
      <div class="goods_list">
        <h1>热销商品</h1>


        <GoodsList :goodsList=goods_list></GoodsList>


      </div>
    <VueTabBar :selectNavIndex=selectNavIndex></VueTabBar>
  </div>
</template>

<script>
import VueTabBar from "../../components/vueTabBar.vue"
import GoodsList from "../../components/goods.vue"

export default {
  data () {
    return {
      userInfo: {},
      selectNavIndex: 0,
      goods_list: [
        {
            "id": 1,
            "goods_img": "../../images/recommend_list_1.jpg",
            "goods_title": "大V领套头宽松毛衣...",
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
    VueTabBar,
    GoodsList
  },

  methods: {
    bindViewTap () {
      const url = '../logs/main'
      wx.navigateTo({ url })
    },
    skipPage (str) {
      const url = '../' + str + '/main'
      wx.navigateTo({ url })
      console.log(url)
    }
  },
  onLoad () {
    wx.setNavigationBarColor({
      frontColor: '#ffffff',
      backgroundColor: '#14bc88'
    })
  },
  onReachBottom () {
    wx.showLoading({
      title: '加载中',
    })

    setTimeout(function () {
      wx.hideLoading()
      wx.showToast({
        title: '商品就这么多了...',
        duration: 2000
      })
    }, 2000)
  }
}
</script>

<style lang="less">
  .home-top {
    background: #14bc88;
    padding: 10px 30px 18px 30px;

    input {
      position: relative;
      color: #afafaf;
      border-radius: 10px;
      background: #FFFFFF;
      padding-left: 56px;
      height: 60px;
      font-size: 26px;
    }

    input::after {
      content:"";
      position: absolute;

      width: 28px;
      height: 29px;
      left: 20px;
      top: 16px;
      background: url("../../images/search.png") no-repeat;
      background-size: 100%;
    }


  }


  .banner {
    width: 750px;
    height: 374px;

    img {
      width: 100%;
      height: 100%;
    }
  }

  .classification {
    padding-bottom: 38px;
    li {
      width: 25%;
      float: left;
      text-align: center;
      margin-top: 38px;
    }
    img {
      width: 84px;
      height: 84px;
    }
    p {
      font-size: 26px;
    }
  }

  .goods_list {
    padding: 0 30px 122px 30px;
    background-color: #f9f9f9;


    h1 {
      font-size: 30px;
      text-align: center;
      padding: 30px 0;
    }

  }

</style>


