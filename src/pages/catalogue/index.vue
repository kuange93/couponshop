<template>
  <div class="container">
    <scroll-view  :style="{'height': '1105rpx','width': '200rpx'}" :scroll-y="true">
      <div class="scroll-y">
        <ul class="class-item">
          <li v-for="(item, index) in classifyList" :key="index" :class="selectClassIndex === (index + 1) ? 'class-active': ' '"
              @click="handleClassItem (index)">
            <p>{{item.name}}</p>
          </li>
        </ul>
      </div>
    </scroll-view>
    <VueTabBar  :selectNavIndex=selectNavIndex></VueTabBar>
  </div>
</template>

<script>
import VueTabBar from "../../components/vueTabBar.vue"
export default {
  data () {
    return {
      selectNavIndex: 1,
      selectClassIndex: 1,
      classifyList: [
        {
            tag: 'nvzhuang',
            name: '女装'
        },
        {
          tag: 'nanzhang',
          name: '男装'
        },
        {
          tag: 'nanzhang',
          name: '男装'
        },
        {
          tag: 'nanzhang',
          name: '男装'
        },
        {
          tag: 'nanzhang',
          name: '男装'
        },
        {
          tag: 'nanzhang',
          name: '男装'
        },
        {
          tag: 'nanzhang',
          name: '男装'
        },
        {
          tag: 'nanzhang',
          name: '男装'
        },
      ]
    }
  },

  components: {
    VueTabBar
  },

  methods: {
    handleClassItem (index) {
        this.selectClassIndex = index + 1
    }
  },
  onLoad () {
    wx.setNavigationBarTitle({
      title:'商品分类'
    })
  }
}
</script>

<style lang="less">
.container {
  border-top: 1px solid #f2f2f2;

  .class-item {
    li {
      background: #f7f7f7;
      margin-bottom: 1px;

      text-align: center;
      box-sizing: border-box;
    }
    p {
      font-size: 28px;
      line-height: 110px;
    }

    .class-active {
      background: #fff;

      border-left: 6px solid #ff4646;

      p {
        color: #ff4646;
        margin-left: -6px;
      }
    }
  }
}
</style>


