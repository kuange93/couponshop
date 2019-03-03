<template>
  <div class="goods_list_container">
    <div :class="(index + 1)%2 === 0 ?  'goods_item' : 'goods_item goods_item_margin_right'" v-for="(item, index) in goodsList" :key="index"
         @click="clickHandle (item.id)">
      <div class="goods_image">
        <img :src="item.goods_img" alt="">
      </div>
      <div class="goods_title">
        <img src="../images/taobao.png" alt="">
        <h2>{{item.goods_title}}</h2>
        <div class="clear"></div>
      </div>
      <div class="goods_price">
        <p class="goods_price_after">券后价 <span class="red">￥<span class="red red_big">{{item.rear_price_of_voucher}}</span></span></p>
        <p class="goods_price_before">￥{{item.original_price}}</p>

        <div class="clear"></div>
      </div>
      <div class="goods_item_footer">
        <div class="voucher">
          <p class="voucher_left">领劵</p>
          <p class="voucher_right">减{{item.price_reduction}}</p>

          <div class="clear"></div>
        </div>
        <div class="sold">
          <p>已售</p>
          <p class="green">{{item.sold}}</p>
          <div class="clear"></div>
        </div>
        <div class="clear"></div>
      </div>
    </div>
    <div class="clear"></div>
  </div>

</template>

<script>
export default {
  props: {goodsList: Object},
  methods: {
    clickHandle (id) {
      wx.navigateTo( {
        url: '../detail/main?id=' + id
      })
    }
  },
  onLoad () {
      console.log(this.goodsList)
  }
}
</script>

<style lang="less" scoped>
  .goods_item_margin_right {
    margin-right: 10px;
  }

  .goods_item {
    background-color: white;
    width: 338px;
    border-radius: 10px;
    float: left;
    margin-bottom: 13px;


    .goods_image {
      width: 338px;
      height: 344px;
      overflow: hidden;

      img {
        max-width: 338px;
        text-align: center;
      }
    }
    .goods_title{
      margin-top: 30px;

      img {
        width: 23px;
        height: 23px;
        float: left;
        margin: 6px 10px 0 20px;
      }

      h2 {
        font-size: 26px;
        float: left;
      }
    }

    .goods_price {
      margin-top: 20px;

      p {
        font-size: 22px;
      }

      .goods_price_after {
        float: left;
        margin-left: 15px;

        .red {
          color: #ff4646;
        }

        .red_big {
          font-size: 36px;
        }
      }

      .goods_price_before {
        float: right;
        margin-right: 20px;
        margin-top: 8px;

        color: #666666;
      }
    }

    .goods_item_footer {
      margin-top: 20px;
      padding-bottom: 25px;

      .voucher {
        float: left;
        margin-left: 15px;
        p {
          float: left;
          font-size: 20px;

          width: 55px;
          height: 34px;
          line-height: 34px;
          text-align: center;
        }

        .voucher_left {
          color: white;
          background-color: #ff4646;

          border-top-left-radius: 5px;
          border-bottom-left-radius: 5px;
        }

        .voucher_right {
          color: #ff4646;

          border: 1px solid #ff4646;

          border-top-right-radius: 5px;
          border-bottom-right-radius: 5px;

          box-sizing:border-box;
          -moz-box-sizing:border-box; /* Firefox */
          -webkit-box-sizing:border-box;

          line-height: 32px!important;
        }
      }

      .sold {
        float: right;
        margin-right: 20px;

        p {
          float: left;
          font-size: 22px;
          color: #666666;
        }

        .green {
          color: #14bc88;
          margin-left: 3px;
        }
      }
    }
  }
</style>
