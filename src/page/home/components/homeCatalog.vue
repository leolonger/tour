<template>
  <div class="wrapper">
  	<div
     class="icon"
     v-for="item of iconList"
     :key="item.id"
     >
      <div class="icon-img">
        <img class="img" :src="item.imgUrl" :class="[item.color]">
      </div>
      <div class="icon-desc">{{item.desc}}</div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'homeCatalog',
  data(){
    return {
      blue:'blue',
      orange:'orange',
      green:'green',
      red:'red',
      iconList:[
        {
          id:'00001',
          imgUrl:'https://pic5.40017.cn/02/001/6d/e2/rBLkCFmEG8eALBI8AAAEA1xXmqI793.png',
          desc:'本地热推',
          color:'blue'
        },
        {
          id:'00002',
          imgUrl:'https://pic5.40017.cn/02/001/6d/e2/rBLkCFmEG8eALBI8AAAEA1xXmqI793.png',
          desc:'亲子游',
          color:'orange'
        },
        {
          id:'00003',
          imgUrl:'https://pic5.40017.cn/01/001/6d/8f/rBANC1mEG1aAU0Q6AAAHyLUGdmU162.png',
          desc:'主题乐园',
          color:'green'
        },
        {
          id:'00004',
          imgUrl:'https://pic5.40017.cn/01/001/9d/a8/rBANC1rPFcWAaF5sAAAIHYwRlQQ791.png',
          desc:'宜兴竹管',
          color:'red'
        }
      ]
    }
  }
 }
</script>

<style lang="stylus" scoped>
.wrapper
  background:#fff
  padding-top:.2rem
  .icon
    float:left
    width:25%
    .img
      display:block
      margin:0 auto
      width:50%
      background:red
      border-radius:1rem
    .blue
      background:#6dcf16
    .orange
      background:#fda424
    .green
      background:#41a9f2
    .red
      background:#fd6266
    .icon-desc
      text-align:center
      padding-top:.2rem
      padding-bottom:.5rem
</style>
