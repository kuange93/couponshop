<template>
  <section class="tabBar-wrap">
    <article class="tabBar-box">
      <ul class="tabBar-nav" v-if="navList.length > 0">
        <li class="item" v-for="(item, index) in navList"
            @click="selectNavItem(index,item.pagePath)"
            :key="index">
          <p class="item-images">
            <img :src="selectNavIndex === index ? item.selectedIconPath : item.iconPath" alt="iconPath">
          </p>
          <p :class="selectNavIndex === index ? 'item-text item-text-active' : 'item-text' ">
            {{item.text}}
          </p>
        </li>
      </ul>
    </article>
  </section>
</template>

<script>


export default {
    props: {selectNavIndex: Number },
    data () {
        return {

          navList: [
            {
              "pagePath": "../index/main",
              "text": "首页",
              "iconPath": "../../images/navigation_1.png",
              "selectedIconPath": "../../images/sel_1.png"
            },
            {
              "pagePath": "../catalogue/main",
              "text": "分类",
              "iconPath": "../../images/navigation_2.png",
              "selectedIconPath": "../../images/sel_2.png"
            },
            {
              "pagePath":"../list/main",
              "text":"实时榜",
              "iconPath": "../../images/navigation_3.png",
              "selectedIconPath": "../../images/sel_3.png"
            },
            {
              "pagePath":"../personal/main",
              "text":"我的",
              "iconPath": "../../images/navigation_4.png",
              "selectedIconPath": "../../images/sel_4.png"
            }
          ]
        }
    },
    methods: {
      /**
       * 点击导航栏
       * @param index
       */
      selectNavItem(index, pagePath) {

        if (index === this.selectNavIndex) {
          return false;
        }


        if (index == 0 && this.selectNavIndex == -1) {
          this.$emit("fetch-index");
        }
        this.bindViewTap(pagePath);
      },

      /**
       * 路由跳转
       */
      bindNavigateTo(url) {
        wx.navigateTo({
          url
        })
      },

      /**
       * tabBar路由跳转
       */
      bindViewTap(url) {
        // 回到顶部

        wx.switchTab({
          url,
          success: function (res) {

          },
          fail: function (res) {
            console.log(res)
          }
        })
      }
    }
}
</script>

<style lang="less" scoped>
  .tabBar-box {
    position: fixed;
    bottom: 0;
    width: 100%;
    height: 100px;
    border-top: 1px solid #c3c3c3;
    background-color: #fff;
    padding-top: 15px;
  }

  .tabBar-nav {
    width: 100%;
    display: flex;

    .item {
      flex: 1;
      text-align: center;
    }
    .item-text {
      color: #666;
      font-size: 22px;
      transition: .24s linear;
      margin-top: 12px;
    }
    .item-text-active {
      color: #27a79a;
    }

    .item-images {
      width: 48px;
      height: 48px;
      margin: 0 auto;
      text-align: center;
      transition: .24s linear;

      & img {
        display: inline;
        width: 100%;
        height: 100%;
      }
    }
  }
</style>
