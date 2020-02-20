<template>
  <TabBar>
    <TabBarItem path="/home">
      <img slot="item-icon" src="../assets/images/tabbar/主页.png" alt="">
      <img slot="item-icon-active" src="../assets/images/tabbar/主页_活跃.png" alt="">
      <div slot="item-text">首页</div>
    </TabBarItem>
    <TabBarItem path="/category">
      <img slot="item-icon" src="../assets/images/tabbar/商城.png" alt="">
      <img slot="item-icon-active" src="../assets/images/tabbar/商城_活跃.png" alt="">
      <div slot="item-text">商城</div>
    </TabBarItem>
    <TabBarItem path="/cart">
      <img slot="item-icon" src="../assets/images/tabbar/购物车.png" alt="">
      <img slot="item-icon-active" src="../assets/images/tabbar/购物车_活跃.png" alt="">
      <div slot="item-text">购物车</div>
    </TabBarItem>
    <TabBarItem path="/profile">
      <img slot="item-icon" src="../assets/images/tabbar/我的.png" alt="">
      <img slot="item-icon-active" src="../assets/images/tabbar/我的_活跃.png" alt="">
      <div slot="item-text">我的</div>
    </TabBarItem>
  </TabBar>
</template>

<script>
  import TabBar from '../components/tabbar/TabBar'
  import TabBarItem from "../components/tabbar/TabBarItem";

  export default {
    name: "MainTabBar",
    components:{
      TabBar,
      TabBarItem
    }
  }
</script>

<style scoped>

</style>