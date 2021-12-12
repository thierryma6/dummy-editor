<template>
  <div>
    <div>
      <span @click="selected=1" class="title" :class="{selected:selected==1}">Editorjs</span>
      <span @click="selected=2" class="title" :class="{selected:selected==2}">Slatejs</span>
      <span @click="selected=3" class="title" :class="{selected:selected==3}">Ckeditor</span>
      <span @click="selected=4" class="title" :class="{selected:selected==4}">Draftjs</span>
      <span @click="selected=5" class="title" :class="{selected:selected==5}">Quill</span>
      <span @click="selected=6" class="title" :class="{selected:selected==6}">Tinymce</span>
      <Editorjs v-show="selected===1" />
      <Slatejs v-show="selected===2" />
      <Ckeditor v-show="selected===3" />
      <Draftjs v-show="selected===4" />
      <Quill v-show="selected===5" />
      <Tinymce v-show="selected===6" />
    </div>
  </div>
</template>

<script>
import Editorjs from './components/Editorjs.vue'
import Slatejs from './components/Slatejs.vue'
import Ckeditor from './components/Ckeditor.vue'
import Draftjs from './components/Draftjs.vue'
import Quill from './components/Quill.vue'
import Tinymce from './components/Tinymce.vue'

export default {
  name: 'App',
  components: {
    Editorjs,Slatejs,Ckeditor,Draftjs,Tinymce,Quill
  },
  data(){
    return{
      selected:1
    }
  }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
.title{
  margin:20px;
}
.selected{
  color:blue;
}
</style>
