<template>
  <div class="container">
    <div class="list-wrap">
      <div class="top-nav">
        <ul>
          <li>
            <p>综合</p>
            <div class="nav-right"></div>
          </li>
          <li>
            <p>好评</p>
            <div class="nav-right"></div>
          </li>
          <li>
            <p>价格</p>
            <div class="nav-right"></div>
          </li>
          <li>
            <p>销量</p>
          </li>
        </ul>
      </div>

      <div class="goods_list">
        <GoodsList :goodsList=goods_list></GoodsList>
      </div>

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
      selectNavIndex: 2,
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

  },

  onLoad () {
    wx.setNavigationBarTitle({
      title:'实时榜'
    })

    wx.setNavigationBarColor({
      frontColor: '#000000',
      backgroundColor: '#ffffff',
    })
  }
}
</script>

<style lang="less">
.container {
  background: #f2f2f2;
  padding-top: 3px;

  .top-nav {
    height: 80px;
    background: #ffffff;

    ul {
      display: flex;

      li {
        flex: 1;
        position: relative;

        p {
          font-size: 28px;
          text-align: center;
          line-height: 80px;
        }

        .nav-right {
          position: absolute;


          width: 1px;
          height: 40px;

          background: #c2c2c2;
          right: 0;
          top: 20px;
        }
      }
    }
  }

  .goods_list {
    padding: 22px 30px 122px 30px;
    background-color: #f2f2f2;
  }
}
</style>


