<template>
  <div class="container">
    <div class="row">
      <div class="col-12">
        <h1 class="text-center text-info">Brewery List</h1>
      </div>
    </div>
    <div class="row">
      <div class="col-6 brew-list">
        <h2 class="text-center">left</h2>
        <div class="card">
          <ul class="list-group list-group-flush">
            <li v-bind:key="index" v-for="(brew,index) in brews" class="list-group-item">
              {{index}}:{{brew.name}},{{brew.state}}
            </li>
          </ul>
        </div>
      </div>
      <div class="col-6">
        <h2 class="text-center">right</h2>
      </div>
    </div>
   </div>
</template>

<script>
import axios from 'axios'
export default {
  name: 'Brew',
  data: function() {  return {  brews:[]  }   },
  mounted:function(){  axios.get('https://api.openbrewerydb.org/breweries')
                            .then((r)=>{console.log('res=',r)
                                        this.brews=r.data})    
                    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang="scss" scoped>
 .brew-list{
   overflow-y:scroll;
   height:95vh;
   li{&:hover{background-color: darkgrey}}
 }

</style>
