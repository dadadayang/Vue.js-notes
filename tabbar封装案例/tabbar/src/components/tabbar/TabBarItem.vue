<template>
  <div class="tab-bar-item" @click="itemClick">
    <div v-if='!isActive'><slot name="item-icon"/></div>
    <div v-else><slot name="item-icon-active"/></div>
    <div :class="{active: isActive}"><slot name="item-text"/></div>
  </div>
</template>

<script>
  export default {
    name: "TabBarItem",
    props:{
      path:String
    },
    data(){
      return{
        // isActive:false,
      }
    },
    computed:{
      isActive(){
        return this.$route.path.indexOf(this.path) !== -1
      }
    },
    methods:{
      itemClick(){
        if (this.$route.path !== this.path){
          this.$router.replace(this.path)
        }
      }
    }
  }
</script>

<style scoped>
  .tab-bar-item{
    flex: 1;
    text-align: center;
    height: 49px;
    font-size: 14px;
  }
  .tab-bar-item img{
    width: 24px;
    height: 24px;
    margin-top: 3px;
    vertical-align: middle;
  }
  .active{
    color:red;
  }
</style>