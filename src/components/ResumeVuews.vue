<template>
  <div class="card card-w70">
    <div v-if="blocks.length">
      <component
        v-for="block in blocks"
        :key="block.id"
        v-bind="{ data: block.value }"
        :is="'resume-' + block.type"
      >
      </component>
    </div>
    <h3 v-else>Добавьте первый блок, чтобы увидеть результат</h3>
    <!-- <h1>Резюме Nickname</h1>
    <div class="avatar">
      <img
        src="https://cdn.dribbble.com/users/5592443/screenshots/14279501/drbl_pop_r_m_rick_4x.png"
      />
    </div>
    <h2>Опыт работы</h2>
    <p>
      главный герой американского мультсериала «Рик и Морти», гениальный учёный, изобретатель,
      атеист (хотя в некоторых сериях он даже молится Богу, однако, каждый раз после чудесного
      спасения ссылается на удачу и вновь отвергает его существование), алкоголик, социопат, дедушка
      Морти. На момент начала третьего сезона ему 70 лет[1]. Рик боится пиратов, а его главной
      слабостью является некий - "Санчезиум". Исходя из того, что существует неограниченное
      количество вселенных, существует неограниченное количество Риков, герой сериала
      предположительно принадлежит к измерению С-137. В серии комикcов Рик относится к измерению
      C-132, а в игре «Pocket Mortys» — к измерению C-123[2]. Прототипом Рика Санчеза является
      Эмметт Браун, герой кинотрилогии «Назад в будущее»[3].
    </p>
    <h3>Добавьте первый блок, чтобы увидеть результат</h3> -->
  </div>
</template>

<script>
import ResumeTitle from '@/components/partResume/ResumeTitle'
import ResumeSubtitle from '@/components/partResume/ResumeSubtitle'
import ResumeAvatar from '@/components/partResume/ResumeAvatar'

import ResumeText from '@/components/partResume/ResumeText'

export default {
  props: ['blocks'],
  mounted() {},
  computed: {
    // componentName() {
    //   if (this.block.type === 'title') {
    //     return 'ResumeTitle'
    //   } else if (this.block.type === 'text') {
    //     return 'ResumeText'
    //   } else if (this.block.type === 'subtitle') {
    //     return 'ResumeSubtitle'
    //   } else if (this.block.type === 'avatar') {
    //     return 'ResumeAvatar'
    //   }
    //   return 'ResumeTitle'
    // },
  },
  // eslint-disable-next-line vue/no-unused-components
  components: { ResumeTitle, ResumeAvatar, ResumeText, ResumeSubtitle },
}
</script>

<style></style>
