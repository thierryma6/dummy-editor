<template>
  <div>
    <div id="editor"></div>
    <div id="insert-table" @click="insertTable()">insert table</div>
  </div>
</template>

<script>
import Quill from 'quill'
import 'quill/dist/quill.snow.css'
import QuillBetterTable from 'quill-better-table'

Quill.register({
  'modules/better-table': QuillBetterTable
}, true)



export default {
  name: 'editor',
  props: {
    value: Object
  },
  methods:{

      insertTable(){
          let tableModule = this.quill.getModule('better-table')
      tableModule.insertTable(3, 3)
      }
  },
  data() {
    return {
      quill:null,
      options: {
        theme: 'snow',
        modules: {
            toolbar: [
              ['bold', 'italic', 'underline', 'strike'],
              ['blockquote', 'code-block'],
              [{ 'header': 1 }, { 'header': 2 }],
              [{ 'list': 'ordered' }, { 'list': 'bullet' }],
              [{ 'script': 'sub' }, { 'script': 'super' }],
              [{ 'indent': '-1' }, { 'indent': '+1' }],
              [{ 'direction': 'rtl' }],
              [{ 'size': ['small', false, 'large', 'huge'] }],
              [{ 'header': [1, 2, 3, 4, 5, 6, false] }],
              [{ 'color': [] }, { 'background': [] }],
              [{ 'font': [] }],
              [{ 'align': [] }],
              ['clean'],
              ['link', 'image', 'video'],
              ['table']
            ],
                  table: false,  // disable table module
      'better-table': {
        operationMenu: {
          items: {
            unmergeCells: {
              text: 'Another unmerge cells name'
            }
          }
        }
      },
      keyboard: {
        bindings: QuillBetterTable.keyboardBindings
      }
          },
          placeholder: 'Insert text here ...',
      }
    }
  },
  mounted() {
    // let dom = this.$el.querySelector('.editor')
    // this.quill = new Quill(dom, this.options);
    // this.quill.setContents(this.value)
    // this.quill.on('text-change', () => {
    //   this.$emit('input', this.quill.getContents())
    // });
     this.quill = new Quill('#editor', this.options);
  }
}
</script>
