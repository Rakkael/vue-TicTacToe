<template>
  <div id="app">
    <div class="game">
      <div class="row">
        <cell @countAdd="countSelfPlus(0, $event)" :data="this.count"></cell>
        <cell @countAdd="countSelfPlus(1, $event)" :data="this.count"></cell>
        <cell @countAdd="countSelfPlus(2, $event)" :data="this.count"></cell>
      </div>
      <div class="row">
        <cell @countAdd="countSelfPlus(3, $event)" :data="this.count"></cell>
        <cell @countAdd="countSelfPlus(4, $event)" :data="this.count"></cell>
        <cell @countAdd="countSelfPlus(5, $event)" :data="this.count"></cell>
      </div>
      <div class="row">
        <cell @countAdd="countSelfPlus(6, $event)" :data="this.count"></cell>
        <cell @countAdd="countSelfPlus(7, $event)" :data="this.count"></cell>
        <cell @countAdd="countSelfPlus(8, $event)" :data="this.count"></cell>
      </div>
    </div>
    <div>{{result}}</div>
  </div>
</template>

<script>
import Cell from './components/Box.vue'

export default {
  name: 'App',
  components: {
    Cell
  },
  data() {
    return {
      count: 0,
      map: [
        [null,null,null],
        [null,null,null],
        [null,null,null]
      ],
      result: false
    }
  },
  computed: {

  },
  methods: {
    countSelfPlus(num, type){
      this.count += 1;
      this.map[Math.floor(num/3)][num%3] = type;
      console.log(`第${num}个被点击，结果为${type}`);
      this.whoWin();
    },
    whoWin(){
      for(let i=0; i<3; ++i){
        if(this.map[i][0] != null && this.map[i][0] == this.map[i][1] && this.map[i][1] == this.map[i][2]){
          this.result = true;
        }
      };
      for(let j=0; j<3; ++j){
        if(this.map[0][j] != null && this.map[0][j] == this.map[1][j] && this.map[1][j] == this.map[2][j]){
          this.result = true;
        }
      if(this.map[0][0] != null && this.map[0][0] == this.map[1][1] && this.map[1][1] == this.map[2][2]){
        this.result = true;
      }
      if(this.map[0][2] != null && this.map[0][2] == this.map[1][1] && this.map[1][1] == this.map[2][0]){
        this.result = true;
      }
      };
    }
  },
}
</script>

<style>
* {
  margin: 0;
  padding: 0;
}
#app {
  display: flex;
  height: 100vh;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}
.row {
  display: flex;
}
</style>
