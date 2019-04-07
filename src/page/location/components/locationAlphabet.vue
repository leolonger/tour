<template>
  <div>
    <ul class="list">
      <li 
        v-for="item of alphabetList"
        :key="item.id"
        @click="handleLetterClick"
      >
        {{item.content}}
      </li>
    </ul>
    <div 
      class="connect" 
      ref="distance"
      :style="hidden"
    >
      {{this.content}}
    </div>
  </div>
</template>

<script>
export default {
  name: 'locationAlphabet',
  data(){
    return {
      content:'',
      hidden:{
        display:'none'
      },
      alphabetList:[
        {
          id:'50011',
          content:'当前'
        },
        {
          id:'50012',
          content:'热门城市'
        },
        {
          id:'50013',
          content:'A'
        },
        {
          id:'50014',
          content:'B'
        },
        {
          id:'50015',
          content:'C'
        },
      ]
    }
  },
  methods:{
    handleLetterClick(e){
      this.content = e.target.innerText;
      // console.log(this.content)
      this.$emit("change",this.content);
      for(let i=0;i<this.alphabetList.length;i++){
        if(this.content ===this.alphabetList[i].content){
          let distance = 0.8 + ((i+1)*0.38);
          const showElement = this.$refs.distance;
          showElement.style = "display:block";
          showElement.style = "top:"+distance+"rem";
          setTimeout(function(){
              showElement.style = "display:none";
            },500);
        }
      }
    }
  }
 }
</script>

<style lang="stylus" scoped>
.list
  position:fixed
  top:1.15rem
  right:0
  z-index:100
  text-align:center
  width:15%
  background:#eff1f5
  padding-bottom:100rem
  opacity:.7
  color:#53cabf
.list>li
  margin:.1rem 0
  font-weight:bold
.connect
  position:absolute
  top:1.1rem
  right:1.1rem
  z-index:100
  text-align:center
  background:rgba(80,180,0,.7)
  border-radius:.07rem
  color:#fff
  padding:.1rem .1rem
  margin-right:.2rem
</style>
