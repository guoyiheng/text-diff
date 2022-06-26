<script setup lang="ts">
const lhsResponse = 'the quick red fox\njumped over the hairy dog'
const rhsResponse = 'the quick brown fox\njumped over the lazy dog'
// const mergelyRef: any = ref(null)
// onMounted(() => {

//   // initialize mergely of vue
//   nextTick(() => {
//     // initialize mergely
//     mergely.value.init()

//     // get async lhsResponse, then set lhs value
//     mergely.value.setLhs(lhsResponse)

//     // get async rhsResponse, then set rhs value
//     mergely.value.setRhs(rhsResponse)
//   })
// })
</script>

<template>
  <div class="mergely-full-screen-8">
    <div class="mergely-resizer">
      <div id="mergely" ref="mergelyRef" />
    </div>
  </div>
</template>

<style scoped>
</style>
