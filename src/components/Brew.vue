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
        <div class="card" style="width: 18rem;">
          <ul class="list-group list-group-flush">
            <li class="list-group-item">Cras justo odio</li>
            <li class="list-group-item">Dapibus ac facilisis in</li>
            <li class="list-group-item">Vestibulum at eros</li>
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
export default {
  name: 'Brew',
  props: {
    msg: String
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
