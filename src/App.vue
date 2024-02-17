<template>
  <DragDrop v-bind:listing="lists" v-on:update-listing="newListing"/>
</template>

<script>
import DragDrop from './components/DragDrop.vue'

export default {
  name: 'App',
  components: {
    DragDrop
  },
  data:function(){
    return{
      lists:[
        {
          id:1,
          item:'List 1'
        },
        {
          id:2,
          item:'List 2'
        },
        {
          id:3,
          item:'List 3'
        },
        {
          id:4,
          item:'List 4'
        }
      ]
    }
  },
  methods:{
    newListing(newListData){
      this.lists = newListData;
    }
  },
  emits: ['update-listing'],
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
