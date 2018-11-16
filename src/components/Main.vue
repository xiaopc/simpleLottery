<template>
  <div id="main-panel">
    <h2 class="main-description" contenteditable>大奖得主为</h2>
    <p class="content">
      第 <span class="res-num">{{ curX }}</span> 行
      <span class="res-num">{{ curY }}</span> 列
    </p>
    <button class="start-btn" :class="(this.status == 1)?'active':''" @click="handleBtnClick">{{ btnWord }}</button>
  </div>
</template>

<script>
export default {
  name: 'Main',
  props: {
    settings: Object
  },
  data: function() {
    return {
      curX: "00",
      curY: "00",
      status: 0,  // 0 for resseted, 1 for running, 2 for done
      interval: null,
    }
  },
  computed: {
    btnWord: function() {
      if (this.status == 0){
        return "抽"
      } else if (this.status == 1){
        return "停"
      } else {
        return "重"
      }
    },
  },
  methods: {
    handleBtnClick: function(){
      if (this.status == 0){
        this.status = 1
        var vm = this
        this.interval = window.setInterval(function(){
          var xMax = vm.settings.totalX
          var yMax = vm.settings.totalY
          var xCur = Math.ceil(xMax * Math.random())
          var yCur = Math.ceil(yMax * Math.random())
          vm.curX = (xCur/100).toFixed(2).substr(2)
          vm.curY = (yCur/100).toFixed(2).substr(2)
        }, vm.settings.interval)
      } else if (this.status == 1){
        this.status = 2
        window.clearInterval(this.interval)
      } else {
        this.status = 0
        this.curX = "00"
        this.curY = "00"
      }
    },
  },
  mounted: function() {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import url('https://fonts.loli.net/css?family=VT323');

#main-panel {
  text-align: center;
}
.res-num {
  font-family: 'VT323', monospace;
  font-size: 64pt;
  margin: 0.5em;
  padding: 0.1em 0.2em;
  background: rgba(0,0,0,0.7);
  color: #faFafa;
  border-radius: 5px;
}
.content {
  font-size: 32pt;
}
.start-btn {
  border: none;
  outline: none;
  font-size: 32pt;
  text-align: center;
  padding: 0;
  width: 80pt;
  height: 80pt;
  border-radius: 40pt;
  border: 2px solid rgba(0,0,0,0.2);
  background-color: rgba(255,255,255,0.8);
  transition: 1s cubic-bezier(0.075, 0.82, 0.165, 1) all;
}
.start-btn:hover, .start-btn.active {
  background-color: rgba(0,0,0,0.2);
}
a {
  color: #42b983;
}
@media (max-width: 750px) {
  .content {
    font-size: 0;
    line-height: 70pt;
  }
  .res-num {
    margin: 0.2em;
  }
}
</style>
