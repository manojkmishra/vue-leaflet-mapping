<template>
    <div class="card brew-list">
          <ul class="list-group list-group-flush">
            <li @mouseover="mo(index)" @mouseleave="ml(index)"
                v-bind:key="index" v-for="(brew,index) in brews" class="list-group-item">
              {{index}}:{{brew.name}},{{brew.state}}
            </li>
          </ul>
        </div>
</template>
<script>
export default {
    props:{brews:Array},
    methods:{
        mo(i){ this.$emit('mouse-over-brew',i)},
        ml(i){this.$emit('mouse-leave-brew',i)}
    }
}
</script>
<style lang="scss" scoped>
 .brew-list{
   overflow-y:scroll;
   height:95vh;
   li{&:hover{background-color: darkgrey}}
 }

</style>
