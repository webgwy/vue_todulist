<template>
  <div id="app">
    <h1>{{title}}</h1>
  <input v-model="newItem" v-on:keyup.enter="addNew">
    <ul>
      <li v-for="item in items" :key="item.id" v-bind:class="{Finished:item.isFinished}"
       v-on:click="toogleFinish(item)">
           {{item.label}}
      </li>
    </ul>
    <componentA msgfromfather='you die' v-on:child-tell-me='listentomyboy'></componentA>
    <p>{{childwords}}</p>
  </div>
</template>
<script>
import store from './store.js';
import componentA from './components/HelloWorld';
export default {
  data:function(){
    return{
      title:'添加选项',
      items:store.fetch(),
      newItem:'',
      childwords:''
    }
  },
  components:{componentA},
  watch:{
      items:{
        handler:function(items){
           store.save(items)
        },
        deeps:false
      }
  },
  methods:{
      toogleFinish:function(item){
           item.isFinished=!item.isFinished;
      },
      addNew:function(){
          this.items.push({
             label:this.newItem,
             isFinished:false
          })
          this.newItem=''
          store.save();
      },
      listentomyboy:function(msg){
          this.childwords=msg;
      }
  }
}
</script>

<style>
html{text-align: center;}
.Finished{color: red;}
</style>
