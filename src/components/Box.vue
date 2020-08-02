<template>
  <div>
    <div class="box" @click="changeState">{{ a }}</div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      state: true,
      a: ''
    }
  },
  props:['data'],
   methods: {
      changeState(){
        if(this.state !== true) return
        if(this.data%2 === 0){
          this.a = '×';
          this.$emit('countAdd',this.a);
        }else{
          this.a = '○';
          this.$emit('countAdd',this.a);
        }
        this.state = false;
      }
    },
}
</script>

<style scoped>
.box {
  display: flex;
  justify-content: center;
  align-items: center;
  width: 100px;
  height: 100px;
  border: 1px solid black;
  font-size: 80px;
  color: black;
}
</style>