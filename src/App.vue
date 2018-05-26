<template>
  <div id="app">
    <h1>{{title}}</h1>
    <input v-model="newItem" v-on:keyup.enter="addNew">
    <ul>
      <li v-for="item in items" v-bind:class="{finished:item.isFinished}" v-on:click="toggleFinished(item)">
        {{item.label}}
      </li>
    </ul>
  </div>
</template>

<script>
export default {
  /* 等价：
  data:function(){
    return{
      msg:"hello world!"
    }
  }


  */
  data(){
    return{
      title:"This is a todolist~",
      items:[
      ],
      newItem:''
    }
  },
  methods:{
    toggleFinished:function(item){
      item.isFinished = !item.isFinished;
    },
    addNew:function(){
      // console.log(this.newItem);
      this.items.push({
        label:this.newItem,
        isFinished:false
      })
      this.newItem = ""
    }
  }
}
</script>

<style>
.finished{
  text-decoration: underline;
}

#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
