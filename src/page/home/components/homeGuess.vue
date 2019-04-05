<template>
  <div class="guess">
  	<div 
      class="guess-desc"
      :class="[guessDescChange]"
      >
      <div>猜你喜欢</div> 
    </div>
    <div class="guess-content" v-for="item of guessList" :key="item.id">
      <div class="guess-content-img">
        <img :src="item.imgUrl">
        <div>{{item.rank}}</div>
      </div>
      <div class="guess-content-desc">
        {{item.desc}}
      </div>
      <div class="guess-content-prise">
        <div class="guess-content-prise-left">
          {{item.distance}}
        </div>
        <div class="guess-content-prise-right">
          <span>￥</span>{{item.prise}}<span>起</span>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: 'homeGuess',
  props:{
    guessList:Array
  },
  data(){
    return{
      guessDescChange:''
      /*,
      guessList:[
      {
        id:'2001',
        imgUrl:'https://pic4.40017.cn/scenery/destination/2017/02/08/18/ZTe8Qb_420x228_00.jpg',
        rank:'1176点评 99%满意度',
        desc:'宿宜兴帕佛伦斯酒店，自选宜兴竹海风景区等，尊享60楼“云端”自助早餐，免费泳池健身房【踏青赏花】',
        distance:'酒店距景点19.9km',
        prise:'569'
      },
      {
        id:'2002',
        imgUrl:'https://pic5.40017.cn/02/000/02/22/rBLkCVlkdDqAP4NzAAMCZSYX5mY633_420x228_00.jpg',
        rank:'1711点评 99%满意度',
        desc:'【景区内】无锡拈花客栈1晚，游拈花湾，自选酒店自助晚餐/禅食餐等【灵山胜境】【亲子精选】【踏青赏花】',
        distance:'酒店距景点15.6km',
        prise:'944'
      },
      {
        id:'2003',
        imgUrl:'https://pic5.40017.cn/03/000/c0/08/rB5oQFwtas2AFxj6AAQXQp0zUm8624_420x228_00.jpg',
        rank:'79点评 97%满意度',
        desc:'常州中华恐龙园恐龙人俱乐部酒店 1晚+2日无限次恐龙园门票',
        distance:'酒店距景点22.39km',
        prise:'1038'
      },
      {
        id:'2004',
        imgUrl:'https://pic3.40017.cn/zzy/rimage/2015/07/02/18/132BKj_420x228_00.jpg',
        rank:'2349点评 99%满意度',
        desc:'无锡国际饭店1晚，自选美洲豹自助餐/灵山大佛/鼋头渚/三国、水浒城/拈花湾等【太湖度假精选】',
        distance:'酒店距景点28.89km',
        prise:'399'
      },
      {
        id:'2005',
        imgUrl:'https://pic4.40017.cn/scenery/destination/2016/07/19/17/lziIen_420x228_00.jpg',
        rank:'667点评 98%满意度',
        desc:'常州明都枫泽山庄大酒店1晚，自选淹城野生动物园景点/常州明都枫泽山庄大酒店自助晚餐套餐',
        distance:'酒店距景点13.3km',
        prise:'299'
      }]*/
    }
  },
  methods:{
    scrollChange(){
      let height = document.documentElement.scrollTop;
      if(height>600){
        this.guessDescChange = 'guessDescChange';
      }else {
        this.guessDescChange = '';
      }
    }
  },
  mounted(){
    window.addEventListener('scroll',this.scrollChange)
  }
 }
</script>

<style lang="stylus" scoped>
.guess
  border-top:.2rem solid #eee
  background:#fff
  .guess-desc
    overflow:hidden
    height:0
    padding-bottom:10%
    text-align:center
    color:#23beae
  .guessDescChange
    position:fixed
    top:.9rem
    left:0
    width:100%
    background:#fff
    z-index:100
  .guess-desc > div
    overflow:hidden
    width:25%
    height:0
    padding-bottom:6%
    margin:0 auto
    padding-top:.23rem
    border-bottom:.1rem solid #23beae
  .guess-content
    overflow:hidden
    width:92%
    height:0
    padding-bottom:64%
    margin:0 auto
    padding-top:.2rem
    border-top:.05rem solid #eee
    .guess-content-img
      position:relative
      overflow:hidden
      height:0
      padding-bottom:48.3%      
    .guess-content-img >img
      max-width:100%
    .guess-content-img >div
      position:absolute
      bottom:.2rem
      left:.1rem
      color:#fff
    .guess-content-desc
      overflow:hidden
      height:0
      padding-bottom:12%
      text-align:left
      padding-top:.1rem
      text-indent:.1rem
      font-size:.28rem
      font-weight:bold
      letter-spacing:.01rem
      line-height:.35rem
    .guess-content-prise
      overflow:hidden
      height:0
      padding-bottom:10%
      .guess-content-prise-left
        float:left
        color:#aaa
      .guess-content-prise-right
        float:right
        margin-right:.1rem
      .guess-content-prise-right > span
        color:red
        font-weight:bold
        font-size:.4rem
</style>
