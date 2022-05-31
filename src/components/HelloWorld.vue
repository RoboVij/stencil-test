<template>
  <div class="hello">
    <h1 style="padding: 20px">Test @Watch() decorator compatibility with Vue</h1>
    <p>Selecting items1, items2 works. But when both are not selected, watch isn't rendering</p>

    <input type="checkbox" id="items1" v-model="showItems1">
    <label for="items1">Items1</label>
    <input type="checkbox" id="items2" v-model="showItems2">
    <label for="items2">Items2</label>

    <div style="padding-top: 40px; font-weight: bold">Prop value being passed from Vue: </div>
    <p>{{items}}</p>

    <div style="padding-top: 40px; font-weight: bold">Value in Stencil component: </div>
    <my-component id='component' first="It is:" :tester.prop="items"></my-component>
  </div>
</template>

<script>
import 'stencil-tester-watch';
export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      items1: [{x: 23, y:74}, {x: 6, y:14}],
      items2: [{x: 3, y:6}, {x: 16, y:2}],
      showItems1: true,
      showItems2: true,
    };
  },
  computed: {
    items() {
      let list = [];
      if (this.showItems1) {
        list.push(...this.items1);
      }
      if (this.showItems2) {
        list.push(...this.items2);
      }
      return list;
    },
  }
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
