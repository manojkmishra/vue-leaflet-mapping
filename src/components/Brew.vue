<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h1 class="text-center text-info">Brewery List</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-6 ">        
          <BrewList @mouse-over-brew="moverb" @mouse-leave-brew="mleaveb"  
                    v-bind:brews="brews"/>
      </div>
      <div class="col-6">
        <BrewMap v-bind:brews="brews"/>
      </div>
    </div>
   </div>
</template>

<script>
import axios from 'axios'
import BrewList from './BrewList'
import BrewMap from './BrewMap'
export default {
  name: 'Brew',
  data: function() {  return {  brews:[] , normalIcon:[30,30],largeIcon:[60,60] }   },
  mounted:function(){  axios.get('https://api.openbrewerydb.org/breweries')
                            .then((r)=>{console.log('res=',r)
                                        //this.brews=r.data
                                        this.brews=r.data.filter(r=>r.state=='Arizona')
                                                          .map(r=>{r.iconSize=this.normalIcon; return r;})
                                        console.log('brews=',this.brews)
                                        })    
                    },
  components:{BrewList, BrewMap},
  methods:{
    moverb(a){console.log('moverb-index=',a); this.brews[a].iconSize=this.largeIcon;
            },
    mleaveb(a){console.log('mleaveb-index=',a); this.brews[a].iconSize=this.normalIcon;}
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>


</style>
