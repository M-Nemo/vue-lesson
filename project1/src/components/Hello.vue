<template>
  <div class="hello">
    <h1 v-text="title"></h1>
    <ul>
      <li v-for="item in items" v-bind:class="{flag:item.flag}" @click="setStatus(item)"> {{item.lable}} </li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'hello',
  data: function () {
    return {
      title: 'ToDo List',
      items:[
        {
          lable:"test1",
          flag: true
        },
        {
          lable:"test2",
          flag:false
        }
      ]
    }
  },
  methods:{
    setStatus:function(item){
      item.flag=!item.flag
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
  margin: 0 10px;
}

a {
  color: #42b983;
}
.flag{
  text-decoration: line-through;
}
</style>
