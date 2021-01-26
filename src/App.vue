<template>
  <div class="container column">
    <resume-form @addResume="addResume"></resume-form>

    <resume-vuews :blocks="blocks"></resume-vuews>
  </div>
  <div class="container">
    <p>
      <button @click.prevent="" class="btn primary">Загрузить комментарии</button>
    </p>

    <resume-coments></resume-coments>

    <app-loader></app-loader>
  </div>
</template>

<script>
import AppLoader from '@/components/AppLoader'
import ResumeForm from '@/components/ResumeForm'
import ResumeComents from '@/components/ResumeComents'
import ResumeVuews from '@/components/ResumeVuews'

export default {
  data() {
    return {
      blocks: [],
    }
  },
  methods: {
    addResume(data) {
      this.blocks.push(data)
      console.log('this.blocks', this.blocks)
    },
  },

  // eslint-disable-next-line vue/no-unused-components
  components: { AppLoader, ResumeForm, ResumeComents, ResumeVuews },
}
</script>

<style>
.avatar {
  display: flex;
  justify-content: center;
}

.avatar img {
  width: 150px;
  height: auto;
  border-radius: 50%;
}
</style>
