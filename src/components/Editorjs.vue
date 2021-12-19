
<template>
  <div >
    <div >
      <h1 style="text-align:center">This is vue editor.js</h1>
    </div>

    <div class="editorx_body">
      <!--editorjs id-->
      <!-- style="pointer-events: none;" -->
      <div class id="codex-editor" />
    </div>
    <button style="margin-left: 30%;" type="button" name="button" @click="save()">save</button>
    <div class="editorx_body">
      <pre>{{value}}</pre>
    </div>
  </div>
</template>

<script>
import EditorJS from "@editorjs/editorjs";
import Header from "@editorjs/header";
import Paragraph from "@editorjs/paragraph";
import List from "@editorjs/list";
//import ImageTool from '@editorjs/image';
import Embed from '@editorjs/embed';
import Raw from '@editorjs/raw';
import Table from '@editorjs/table';
import Marker from '@editorjs/marker';
import {SimpleImage} from './editorjs/simple-image'
import './editorjs/simple-image.css'

export default {
  data() {
    return {
      value: null
    };
  },
  methods: {
    save: function() {
      window.editor.save().then(savedData => {
        console.log(savedData);
        this.value = savedData;
      });
    },
    myEditor: function() {
      window.editor = new EditorJS({
        holder: "codex-editor",
        autofocus: true,
        placeholder: 'Let`s write an awesome story!',
        /**
         * This Tool will be used as default
         */
        defaultBlock: "paragraph",
        hideToolbar:true,
        //tunes:['test1', 'test2'],
        inlineToolbar:['bold'],
        tools: {
          header: {
            class: Header,
            shortcut: "CMD+SHIFT+H",
            inlineToolbar:false,
            readOnly:true,
            config: {
              placeholder: ".",
              readOnly:true
            }
          },
          list: {
            inlineToolbar: false,
            class: List
          },
          paragraph: {
            class: Paragraph,
            readOnly:true,
            config: {
              placeholder: 'Let`s write an awesome story!',
              readOnly:true
            }
          },
          embed: {
            class: Embed,
            config: {
              services: {
                youtube: true,
                coub: true
              }
            }
          },
          raw: Raw,
          table: {
            class: Table,
            inlineToolbar: true,
            config: {
              rows: 2,
              cols: 3,
            },
          },
          Marker: {
            class: Marker,
            shortcut: 'CMD+SHIFT+M',
          },
          image: {
            class: SimpleImage,
            inlineToolbar: true,
            config: {
              placeholder: 'Paste image URL',
              readOnly:true
            },
            readOnly:true
          }
        },
         
        onReady: function() {
          console.log("ready");
        //   let tool = document.querySelectorAll(".ce-toolbar");
        // for (let i = 0; i < tool.length; i++) {
        //     tool[i].style.display = "none"
        // }
        },
        onChange: function() {
          console.log("change");
        }
      },
      );
    }
  },
  mounted: function() {
    this.myEditor();
  }
};
</script>

<style lang="css" scoped >
.editorx_body {
  /* width: 62%;
  margin-left: 15%; */
  width: 60%;
  margin-left: 20%;
  border: 2px solid #f1f3f5;
  box-sizing: border-box;
}
.ce-block--focused {
  background: linear-gradient(
    90deg,
    rgba(2, 0, 36, 1) 0%,
    rgba(9, 9, 121, 0.5438550420168067) 35%,
    rgba(0, 212, 255, 1) 100%
  );
}
</style>