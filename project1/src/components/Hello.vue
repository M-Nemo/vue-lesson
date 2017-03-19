<template>
  <div class="hello">
    <h1 v-text="title"></h1>
    <input v-model="addItem" v-on:keyup.enter="submit">
    <ul>
      <li v-for="item in items" v-bind:class="{flag:item.flag}" @click="setStatus(item)"> {{item.lable}} </li>
    </ul>
  </div>
</template>

<script>
import Store from '../store.js'
export default {
  name: 'hello',
  data: function () {
    return {
      title: 'ToDo List',
      items:Store.fetch(),
      addItem:""
    }
  },
  methods:{
    setStatus:function(item){
      item.flag=!item.flag
    },
    submit:function() {
      this.items.push({
        lable:this.addItem,
        flag:false
      })
      this.addItem = ''
      Store.save(this.items)
    }
  },
  watch:{
    items:{
      handler:function(items){
        Store.save(items)
      },
      deep:true
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  margin: 20px 10px;
}

a {
  color: #42b983;
}
.flag{
  text-decoration: line-through;
}
</style>
