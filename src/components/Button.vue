<template>
  <button class="bg-violet-500 font-sans" v-on:click="onClick" >{{ textButton }}</button>
</template>
<script>
export default {
  props: ["textButton", "onClick"]
}
</script>
<script setup>

defineProps({
  textButton: { 
    type: String,
    required: true
  },
  onClick: {
    type: Function,
    required: true
  }
})

</script>

<style lang="">
  
</style>