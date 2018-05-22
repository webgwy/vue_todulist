<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <button v-on:click='onClickme'>open</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      msg: 'this is my child',
    }
  },
  props:["msgfromfather"],
  methods:{
    onClickme:function(){
      //  console.log(this.msgfromfather);
       this.$emit('child-tell-me',this.msg)
    }
  }
}
</script>
<style scoped>
h1, h2 {
  font-weight: normal;
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
