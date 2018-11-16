<template>
  <div id="settings-panel">
    <h2 class="settings-title">设置</h2>
    <form :input="$emit('setSettings', settings)">
      <div class="control-group">
        <label class="control-label">总行数</label>
        <input type="number" v-model.number="settings.totalX">
      </div>
      <div class="control-group">
        <label class="control-label">总列数</label>
        <input type="number" v-model.number="settings.totalY">
      </div>
      <div class="control-group">
        <label class="control-label">刷新速度</label>
        <input type="number" v-model.number="settings.interval">
      </div>
    </form>
  </div>
</template>

<script>
export default {
  name: 'Settings',
  props: {
    settings: Object
  },
/*  data: function() {
    return {
      settings: {
        totalX: 10,
        totalY: 10,
        interval: 50,        
      }
    }
  },*/
  computed: {
  },
  methods: {
  },
  mounted: function() {
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
.control-group{
  padding: 0.5rem;
}
.control-label {
  padding: 1rem 1rem 1rem 0;
  min-width: 60pt;
  display: inline-block;
}

input {
  outline: none;
  border: none;
  border-bottom: 2px solid #ddd;
  font-size: 20pt;
  transition: 0.5s all;
}

input:focus {
  border-bottom: 2px solid #999;
}

@media (max-width: 750px) {
  input {
    max-width: 280px;
  }
}

</style>
