<template>
  <h1>{{ $attrs.data }}</h1>
</template>

<script>
export default {
  mounted() {
    console.log('this.$attrs', this.$attrs)
  },
}
</script>

<style></style>
