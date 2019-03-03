<template>
  <div class="container">
    <VueTabBar  :selectNavIndex=selectNavIndex></VueTabBar>
  </div>
</template>

<script>
import VueTabBar from "../../components/vueTabBar.vue"
export default {
  data () {
    return {
      selectNavIndex: 5
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
      title:'实时优惠'
    })
  }
}
</script>

<style lang="less">
.container {
  border-top: 1px solid #f2f2f2;
}
</style>


