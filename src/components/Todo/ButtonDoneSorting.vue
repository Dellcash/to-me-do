<template>
<v-btn class="button-done-sorting" @click="$store.commit('toggleSorting')" color="primary">
  مرتب‌‌سازی انجام شد!
</v-btn>
</template>

<script>
  export default {
    
  }
</script>

<style lang="sass" scoped>
.button-done-sorting
  font-family: 'Mosa'
  position: fixed
  bottom: 20px
  left: 50%
  transform: translateX(-50%)
</style>