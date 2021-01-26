<template>
  <form class="card card-w30">
    <div class="form-control">
      <label for="type">Тип блока</label>
      <select id="type" v-model="type">
        <option value="title">Заголовок</option>
        <option value="subtitle">Подзаголовок</option>
        <option value="avatar">Аватар</option>
        <option value="text">Текст</option>
      </select>
    </div>

    <div class="form-control">
      <label for="value">Значение</label>
      <textarea v-model="value" id="value" rows="3"></textarea>
    </div>

    <button @click.prevent="addResume" class="btn primary">Добавить</button>
  </form>
</template>

<script>
export default {
  emits: ['addResume'],
  data() {
    return {
      type: 'title',
      value: '',
    }
  },
  methods: {
    addResume() {
      if (this.value.length < 5) {
        return false
      }
      console.log('this.type', this.type)
      console.log('this.value', this.value)
      this.$emit('addResume', { type: this.type, value: this.value, id: Date.now() })
    },
  },
}
</script>

<style></style>
