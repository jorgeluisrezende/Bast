<template>
  <div id="titlebar">
    <header v-on:dblclick="maximize" class="toolbar toolbar-header">
      <span class="left-buttons" href="#" v-if="!isWin">
        <span class="icon icon-record" @click="close" style="color:#fc605b">
           <span class="icon icon-cancel title-bar-minus title-bar-icon"></span>
        </span>
        <span class="icon icon-record" @click="minimize" style="color:#fdbc40">
          <span class="icon icon-minus title-bar-minus title-bar-icon"></span>
        </span>
        <span class="icon icon-record" @click="maximize" style="color:#34c84a">
          <span class="icon icon-resize-full title-bar-max title-bar-icon"></span>
        </span>
      </span>

      <h1 class="title">Bast Music Player</h1>
      
      <span class="right-buttons" href="#" v-if="isWin">
      
        <span class="icon icon-record" @click="minimize" style="color:#fdbc40">
           <span class="icon icon-minus title-bar-minus title-bar-icon"></span>
        </span>
        <span class="icon icon-record" @click="maximize" style="color:#34c84a">
          <span class="icon icon-resize-full title-bar-max title-bar-icon"></span>
        </span>
        <span class="icon icon-record" @click="close" style="color:#fc605b">
          <span class="icon icon-cancel title-bar-minus title-bar-icon"></span>
        </span>
      </span>
    </header>
  </div>
</template>

<script>
const { ipcRenderer } = window.require('electron');

export default {
  name: 'titlebar',
  data() {
    return {
      isWin: process.platform === 'win32',
    };
  },
  methods: {
    maximize() {
      ipcRenderer.send('windowChange');
    },
    close() {
      ipcRenderer.send('close');
    },
    minimize() {
      ipcRenderer.send('minimize');
    },
  },
};
</script>

<style>
#titlebar .toolbar{
  background: #000;
}
.left-buttons{
  font-size: 22px;
  padding-left: 8px;
  position: absolute;
}
.right-buttons{
  position: absolute;
  font-size: 22px;
  right: 0;
  top: 0;
  padding-right: 8px;
}
.left-buttons> .icon, .right-buttons> .icon{
  cursor: pointer;
}
.left-buttons> .icon:hover .title-bar-icon, .right-buttons> .icon:hover .title-bar-icon{
  display:inline-block;
}
.title{
  width: 100%;
  padding: auto;
  height: 25px;
  margin: auto;
  display: inline-block;
  font-size: 13px;
  line-height: 29px;
}
.title-bar-max {
  color: rgba(0, 0, 0, 0.5);
  display: none;
  cursor: pointer;
  font-weight: 600;
  font-size: 11px;
  margin-left: -18%;
  top: 25%; 
  position: absolute;
}
.title-bar-minus {
  color: rgba(0, 0, 0, 0.5);
  display: none;
  cursor: pointer;
  font-weight: 600;
  font-size: 12px;
  margin-left: -16%;
  top: 25%; 
  position: absolute;
}
</style>
