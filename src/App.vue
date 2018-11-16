<template>
  <div id="app">
    <button class="btn-switcher" :class="curPanel.toLowerCase()" @click="handleBtnClick"/>
    <h1 contenteditable class="title-inline">飞扬专用抽奖系统</h1>
    <h2 contenteditable class="title-inline">就这么炫酷</h2>
    <component v-bind:is="curPanel" :settings="settings" @setSettings="onGetSettings"
      style="padding: 2rem 0;"></component>
  </div>
</template>

<script>
import Main from './components/Main.vue'
import Settings from './components/Settings.vue'

export default {
  name: 'app',
  components: {
    Main, Settings
  },
  data: function(){
    return {
      curPanel: "Main",  // "Main" "Settings"
      settings: {
        totalX: 10,
        totalY: 10,
        interval: 50,  
      },
    }
  },
  methods:{
    onGetSettings: function(e){
      this.settings = e
    },
    handleBtnClick: function(){
      if (this.curPanel == "Main"){
        this.curPanel = "Settings"
      } else {
        this.curPanel = "Main"
      }
    },
  },
}
</script>

<style>
/*! normalize.css v5.0.0 | MIT License | github.com/necolas/normalize.css */
html{font-family:sans-serif;line-height:1.15;-ms-text-size-adjust:100%;-webkit-text-size-adjust:100%}body{margin:0}article,aside,footer,header,nav,section{display:block}h1{font-size:2em;margin:.67em 0}figcaption,figure,main{display:block}figure{margin:1em 40px}hr{box-sizing:content-box;height:0;overflow:visible}pre{font-family:monospace,monospace;font-size:1em}a{background-color:transparent;-webkit-text-decoration-skip:objects}a:active,a:hover{outline-width:0}abbr[title]{border-bottom:none;text-decoration:underline;text-decoration:underline dotted}b,strong{font-weight:inherit}b,strong{font-weight:bolder}code,kbd,samp{font-family:monospace,monospace;font-size:1em}dfn{font-style:italic}mark{background-color:#ff0;color:#000}small{font-size:80%}sub,sup{font-size:75%;line-height:0;position:relative;vertical-align:baseline}sub{bottom:-.25em}sup{top:-.5em}audio,video{display:inline-block}audio:not([controls]){display:none;height:0}img{border-style:none}svg:not(:root){overflow:hidden}button,input,optgroup,select,textarea{font-family:sans-serif;font-size:100%;line-height:1.15;margin:0}button,input{overflow:visible}button,select{text-transform:none}[type=reset],[type=submit],button,html [type=button]{-webkit-appearance:button}[type=button]::-moz-focus-inner,[type=reset]::-moz-focus-inner,[type=submit]::-moz-focus-inner,button::-moz-focus-inner{border-style:none;padding:0}[type=button]:-moz-focusring,[type=reset]:-moz-focusring,[type=submit]:-moz-focusring,button:-moz-focusring{outline:1px dotted ButtonText}fieldset{border:1px solid silver;margin:0 2px;padding:.35em .625em .75em}legend{box-sizing:border-box;color:inherit;display:table;max-width:100%;padding:0;white-space:normal}progress{display:inline-block;vertical-align:baseline}textarea{overflow:auto}[type=checkbox],[type=radio]{box-sizing:border-box;padding:0}[type=number]::-webkit-inner-spin-button,[type=number]::-webkit-outer-spin-button{height:auto}[type=search]{-webkit-appearance:textfield;outline-offset:-2px}[type=search]::-webkit-search-cancel-button,[type=search]::-webkit-search-decoration{-webkit-appearance:none}::-webkit-file-upload-button{-webkit-appearance:button;font:inherit}details,menu{display:block}summary{display:list-item}canvas{display:inline-block}template{display:none}[hidden]{display:none}

#app {
  position: absolute;
  top: 0;
  right: 0;
  bottom: 0;
  left: 0;
  max-width: 80vw;
  max-height: 26rem;
  margin: auto;
  padding: 3rem;
  box-shadow: 2px 2px 25px rgba(0,0,0,0.1);
  overflow: hidden;
}

.title-inline {
  outline: none;
  margin: 0 1rem 0 0;
  display: inline-block;
}

.btn-switcher {
  outline: none;
  width: 150px;
  height: 150px;
  position: absolute;
  right: -25px;
  top: -25px;
  border-radius: 75px;
  border: 2px solid rgba(0,0,0,0.2);
  background-color: rgba(255,255,255,0.8);
  transition: 1s cubic-bezier(0.075, 0.82, 0.165, 1) all;
}

.btn-switcher:hover {
  background-color: rgba(0,0,0,0.2);
}

.btn-switcher.main {
  background-image: url(assets/setting.svg);
  background-position: center;
  background-repeat: no-repeat;
}

.btn-switcher.settings {
  background-image: url(assets/home.svg);
  background-position: center;
  background-repeat: no-repeat;
}

@media (max-width: 750px) {
  #app {
    max-height: 100%;
    max-width: 100%;
    padding: 2rem;
  }
  .btn-switcher {
    width: 80px;
    height: 80px;
    top: -15px;
    right: -15px;
    background-size: 40px;
  }
}

</style>
