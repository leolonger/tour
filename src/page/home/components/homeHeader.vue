<template>
  <div class="header" :class="[showHeader]">
  	<div class="header-back" :class="[showBack]">
  		<span class="iconfont">&#xe641;</span>
  	</div>
  	<div class="header-search" :class="[showSearch]">
  	  <span class="iconfont">&#xe7b7;</span>上海海昌海洋公园
  	</div>
    <router-link to="/location">
  	<div class="header-city" :class="[showCity]">
  	{{this.city}}
  	<span class="iconfont">&#xe651;</span></div>
    </router-link>
  </div>
</template>

<script>
export default {
  name: 'homeHeader',
  props:['city'],
  methods:{
    scrollChange(){
      let height = document.documentElement.scrollTop;
      if(height>10){
        this.showHeader = 'showHeader';
        this.showBack = 'showBack';
        this.showSearch = 'showSearch';
        this.showCity = 'showCity';
      }else {
        this.showHeader = '';
        this.showBack = '';
        this.showSearch = '';
        this.showCity = '';
      }
    }
  },
  data(){
    return {
      showHeader:'',
      showBack:'',
      showSearch:'',
      showCity:''
    }
  },
  mounted(){
    window.addEventListener('scroll',this.scrollChange)
  }
 }
</script>

<style lang="stylus" scoped>
.showHeader
  background:#fff
.header
  line-height:.88rem
  text-align:center
  display:flex
  .showBack
    color:#000
  .header-back
    float:left
    width:.9rem
  .showSearch
    color:#aaa
    background:#eee
  .header-search
    flex:1
    height:.6rem
    line-height:.6rem
    margin-top:.2rem
    margin-left:.2rem
    margin-right:.2rem
    border-radius:.5rem
    box-shadow:0 0 .01rem .02rem #ccc
  .showCity
    color:#000
  .header-city
    float:right
    width:1.4rem
</style>
