<template>
  <div>
      <input type="text" placeholder="Cerca" v-model="inputText">
      <button @click="$emit('search', inputText)" >CERCA</button>
  </div>
</template>

<script>
export default {
    name: 'MyHeader',
  data(){
    return {
        inputText: ''
    }
  }
}
</script>

<style>

</style>
