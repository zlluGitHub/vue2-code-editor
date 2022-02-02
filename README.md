vue2-code-editor
====================
[![npm](https://img.shields.io/npm/v/vue2-code-editor)](https://www.npmjs.com/package/vue2-code-editor)


A packaging of 
Vue2-code-editor is a front-end code editor for vue development based on [ACE](https://ace.c9.io/).

<!-- Demo here: https://github.com/chairuosen/vue-ace-editor-demo/tree/vue2 -->

## How to use

#### 1. Install
```
npm install vue2-code-editor --save
```
    
#### 2. Require it in `components` of Vue options
```js
import VueCodeEditor from 'vue2-code-editor';
export default {
    ...
    components: {
        VueCodeEditor
    },
    ...
}
```
 
#### 3. Require the editor's mode/theme module in custom methods
```js
export default {
    ...
    methods: {
        dataSumit() {
            //code here
        },
        editorInit: function () {
            require('vue2-code-editor/node_modules/brace/ext/language_tools') //language extension prerequsite...
            require('vue2-code-editor/node_modules/brace/mode/html') //language 
            require('vue2-code-editor/node_modules/brace/mode/javascript')   
            require('vue2-code-editor/node_modules/brace/mode/less')
            require('vue2-code-editor/node_modules/brace/theme/monokai')
            require('vue2-code-editor/node_modules/brace/snippets/javascript') //snippet
        }
    },
    ...
}
```
    
#### 4. Use the component in template
```html
<VueCodeEditor 
    v-model="content" 
    @init="editorInit" 
    @dirty="editorDirty"
    @blur="editorBlur"
    :lazymodel="false"
    lang="javascript" 
    theme="monokai" 
    width="100%" 
    height="200px"
    :options="{
        enableBasicAutocompletion: true,
        enableLiveAutocompletion: true,
        fontSize: 14,
        highlightActiveLine: true,
        enableSnippets: true,
        showLineNumbers: true,
        tabSize: 2,
        showPrintMargin: false,
        showGutter: true,
    }"
    :commands="[
        {
            name: 'save',
            bindKey: { win: 'Ctrl-s', mac: 'Command-s' },
            exec: null,
            readOnly: true,
        },
    ]"
    />
```

prop `v-model`  is required

prop `lang` and `theme` is same as [ace-editor's doc](https://github.com/ajaxorg/ace)

prop `height` and `width` could be one of these:  `200`, `200px`, `50%`, `60vh`

prop `lazymodel` true : will only update the v-model on blur

    
