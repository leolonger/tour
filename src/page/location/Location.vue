<template>
  <div>
    <div class="load" v-if="loading">loading...</div>
  	<location-header :cities="cities"> 
    </location-header>
  	<location-list 
      :letter="letter"
      :cities="cities"
      :hotCities="hotCities"
    >  
    </location-list>
  	<location-alphabet 
      @change="handleLetterChange"
      :alphabetList="alphabetList"
    >
    </location-alphabet>
  </div>
</template>

<script>
import axios from 'axios'
import locationHeader from './components/locationHeader.vue'
import locationList from './components/locationList.vue'
import locationAlphabet from './components/locationAlphabet.vue'
export default {
  name: 'Location',
  components:{
  	locationHeader,
  	locationList,
  	locationAlphabet
  },
  data(){
    return {
      letter:'',
      cities:{},
      hotCities:[],
      alphabetList:[],
      loading:true
    }
  },
  methods:{
    handleLetterChange(letter){
      this.letter = letter;
    },
    getLocationData(){
      axios.get("/api/city.json").then(this.getCityDataSucc);
    },
    getCityDataSucc(res){
      res = res.data;
      // console.log(res)
      if(res.data){
        const data = res.data;
        this.loading = false;
        this.cities = data.cities;
        this.hotCities = data.hotCities;
        this.alphabetList = data.alphabetList;
      }
    }
  },
  mounted(){
    this.getLocationData();
  }
 }
</script>

<style lang="stylus" scoped>
.load
  position:absolute
  top:7rem
  left:3.5rem
  z-index:1011
  width:1.8rem
  height:.5rem
  opacity:.3
  background:#000
  color:#fff
  text-align:center
</style>
