<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <h1>{{ msgfromfather }}</h1>
    <button v-on:click="onClickMe">open mouse!</button>
  </div>
</template>

<script>
export default {
  data () {
    return {
      msg: 'hello from component a'
    }
  },
  props: ['msgfromfather'],
  methods: {
    onClickMe: function () {
//      console.log(this.msgfromfather)
//      debugger
      this.$emit('child-tell-me-something', this.msg)
// dispatch v-on 监听不到 使用events
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
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
</style>
