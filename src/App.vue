<template>
  <div id="app">
    <!--<h1>{{ title }}</h1>-->
    <!--<h1 v-text="title"></h1>-->
    <h1 v-html="title"></h1> <!-- title: '<span>?</span>this is a todo list'-->
  	<ul>
  		<li v-for="item in items">
  			{{item.label}}
  		</li>
  	</ul>
  </div>
</template>

<script>
export default {
// name: 'app'
  data: function () {
    return {
      title: 'this is a todo list',
      items: [
        {
          label: 'coding',
          inFinished: false
        },
        {
          label: 'walking',
          inFinished: true
        }
      ]
    }
  }
// data () {
//   return {
//   msg: 'Welcome to Your Vue.js App'
//  }
// }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
