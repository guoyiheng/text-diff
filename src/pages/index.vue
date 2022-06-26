<script setup lang="ts">
import TextDiff from '~/components/TextDiff.vue'

const lhsResponse = `I'm Nobody! Who are you?
Are you – Nobody – too?
Then there's a pair of us!
Don't tell! they'd advertise – you know!

How dreary – to be – Somebody!
How public – like a Frog –
To tell one's name – the livelong June –
To an admiring Bog!`
const rhsResponse = lhsResponse.replaceAll('Nobody', 'The One')
  .replace('Frog', 'Frog-Lord')

const collapse = ref(false)
const contentAlign = ref(true)
</script>

<template>
  <div flex mb2 op30 text-xs>
    <button flex="~ gap1" items-center @click="collapse = !collapse">
      <div :i="collapse ? 'carbon-checkbox-checked' : 'carbon-checkbox'" />
      Collapse
    </button>
    <button flex="~ gap1" items-center ml-2 @click="contentAlign = !contentAlign">
      <div :i="contentAlign ? 'carbon-checkbox-checked' : 'carbon-checkbox'" />
      Content Align
    </button>
  </div>
  <TextDiff :old-value="lhsResponse" :new-value="rhsResponse" :collapse="collapse" :content-align="contentAlign" />
</template>
