<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h1 class="text-center text-info">Brewery List</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-6 ">
        
          <BrewList v-bind:brews="brews"/>
      </div>
      <div class="col-6">
        <BrewMap/>
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
  data: function() {  return {  brews:[]  }   },
  mounted:function(){  axios.get('https://api.openbrewerydb.org/breweries')
                            .then((r)=>{console.log('res=',r)
                                        this.brews=r.data})    
                    },
  components:{BrewList, BrewMap}
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>


</style>
