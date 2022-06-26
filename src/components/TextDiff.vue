<script lang="ts" setup>
import CodeMirror from 'codemirror'
import 'codemirror/lib/codemirror.css'
import 'codemirror/addon/merge/merge.js'
import 'codemirror/addon/merge/merge.css'
import DiffMatchPatch from 'diff-match-patch'
const props = defineProps({
  oldValue: {
    type: String,
    default: '',
  },
  newValue: {
    type: String,
    default: '',
  },
  collapse: {
    type: Boolean,
    default: false,
  },
  contentAlign: {
    type: Boolean,
    default: true,
  },
  isReadOnly: {
    type: Boolean,
    default: false,
  },
})

window.diff_match_patch = DiffMatchPatch
window.DIFF_DELETE = -1
window.DIFF_INSERT = 1
window.DIFF_EQUAL = 0

const diffInstance: any = ref(null)
const codeMirror: any = ref(null)

onMounted(() => {
  initTextDiff()
})

watch(() => [props.collapse, props.contentAlign], () => {
  initTextDiff()
})

function initTextDiff() {
  if (props.newValue == null)
    return
  codeMirror.value.innerHTML = ''
  diffInstance.value = CodeMirror.MergeView(codeMirror.value, {
    value: props.oldValue,
    origLeft: undefined,
    orig: props.newValue,
    lineNumbers: true,
    mode: 'text/html',
    // @ts-expect-error - typescript doesn't know about this
    highlightDifferences: true,
    allowEditingOriginals: true,
    connect: props.contentAlign ? 'align' : undefined,
    collapseIdentical: props.collapse,
    readOnly: props.isReadOnly,
  })
}
</script>

<template>
  <div ref="codeMirror" class="h-800px" />
</template>

<style>
.CodeMirror-merge,
.CodeMirror-merge .CodeMirror {
  height: 88vh;
  border-bottom: 1px solid #ddd;
}
</style>
