<template>
  <div class="container column">
    <resume-form @addResume="addResume"></resume-form>

    <resume-vuews :blocks="blocks"></resume-vuews>
  </div>
  <div class="container">
    <p>
      <button @click.prevent="fetchComments" class="btn primary">Загрузить комментарии</button>
    </p>
    <div v-if="comments.length">
      <resume-coments v-for="comment of comments" :key="comment.id"></resume-coments>
    </div>
    div
    <app-loader v-if="isLoading"></app-loader>
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
      isLoading: false,
      comments: [],
    }
  },
  async mounted() {
    const response = await fetch('https://resume-vue-3-default-rtdb.firebaseio.com/resume.json')
    const data = await response.json()
    console.log('data', data)
    const newData = Object.keys(data).map((key) => {
      return {
        ...data[key],
        id: key,
      }
    })
    console.log('newData', newData)
    this.blocks = newData
  },
  methods: {
    async addResume(data) {
      console.log('data', data)
      try {
        const response = await fetch(
          'https://resume-vue-3-default-rtdb.firebaseio.com/resume.json',
          {
            method: 'POST',
            headers: {
              'Content-type': 'application/json',
            },
            body: JSON.stringify(data),
          }
        )
        const firabase = await response.json()
        console.log(firabase.name)
        const newData = { ...data, id: firabase.name }
        this.blocks.push(newData)
      } catch (error) {
        console.log(error)
      }
    },
    async fetchComments() {
      try {
        this.isLoading = true
        const response = await fetch(`https://jsonplaceholder.typicode.com/comments?_limit=4`)
        const data = await response.json()

        this.comments = data
        this.isLoading = false
      } catch (error) {
        this.isLoading = false
        console.log(error)
      }
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

//https://resume-vue-3-default-rtdb.firebaseio.com/
