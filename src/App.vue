<template>
  <div class="container column">
    <resume-form></resume-form>

    <resume-vuews></resume-vuews>
  </div>
  <div class="container">
    <p>
      <button class="btn primary">Загрузить комментарии</button>
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
