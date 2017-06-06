<template>
  <div id="app">
    <!--<h1>{{ title }}</h1>-->
    <!--<h1 v-text="title"></h1>-->
    <h1 v-html="title"></h1> <!-- title: '<span>?</span>this is a todo list'-->
  	<input v-model="newItem" v-on:keyup.enter="addNew">
  	</input>
  	<ul>
  		<!--<li v-for="item in items" v-bind:class="[liClass]">-->
  		<li v-for="item in items" v-bind:class="{finished: item.isFinished}" v-on:click="toggleFinish(item)">
  			{{item.label}}
  		</li>
  	</ul>
  	<component-a msgfromfather='yayaya'></component-a>
  </div>
</template>

<script>
import Store from './store'
import ComponentA from './components/componentA'
// console.log(Store)
export default {
// name: 'app'
  data: function () {
    return {
      title: 'this is a todo list',
      items: Store.fetch(),
//    [
//        {
//          label: 'coding',
//          isFinished: false
//        },
//        {
//          label: 'walking',
//          isFinished: true
//        }
//    ],
      newItem: ''
    }
  },
  components: { ComponentA },
  watch: {
    items: {
      handler: function (items) {
        Store.save(items)
      },
      deep: true
    }
  },
  methods: {
    toggleFinish: function (item) {
      item.isFinished = !item.isFinished
//    console.log(item.isFinished)
    },
    addNew: function () {
      this.items.push({
        label: this.newItem,
        isFinished: false
      })
//    console.log(this.newItem)
      this.newItem = ''
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
  .finished {
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
