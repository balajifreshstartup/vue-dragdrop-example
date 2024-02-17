<template>
    <div>
      <li v-for="list, index in listing" :key="list.id" 
      draggable="true" 
      @dragstart="handleDragover(list, index)"
      @dragover.prevent @drop="drop(list,index)">{{ list.item }}</li>
    </div>
</template>

<script>
export default {
  name: 'DragDrop', 
  data:function(){
    return{
      dragStartItem:Object,
      dragStartIndex:Number,
    }
  },
  props:{
    listing: Array
  },
  methods:{
    handleDragover(list, index) {
      this.dragStartItem = list;
      this.dragStartIndex = index;
    },
    drop(targetList,index) {
      const dropItem = targetList;
      if(dropItem !== this.dragStartItem){
        let newItems = [];
        newItems = [...this.listing];
        newItems.splice(this.dragStartIndex, 1)
        newItems.splice(index,0,this.dragStartItem)
        this.$emit('update-listing', newItems)
      }
      
    }
  },
  emits: ['update-listing'],
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h3 {
  margin: 40px 0 0;
}
ul {
  list-style-type: none;
  padding: 0;
}
li {
  display: inline-block;
  margin: 0 10px;
}
a {
  color: #42b983;
}
</style>
