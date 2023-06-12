<script>
import WelcomeItem from '../components/WelcomeItem.vue';

export default{
  components: {
    WelcomeItem
  },
  data() {
    return {
      list: [
        {icon: "@/assets/img/apps.svg"},
        {icon: "@/assets/img/apps.svg"},
        {icon: "@/assets/img/apps.svg"}
      ]
    }
  }
}
</script>

<template>
  <div>
    <!-- divに入れて1つにしておかないとバラけた -->
    <WelcomeItem v-for="item in list" :key="item">
      <template #icon>
        <img src="@/assets/img/apps.svg" />
      </template>
      <template #heading>Documentation</template>

      Vue’s
      <a href="https://vuejs.org/" target="_blank" rel="noopener">official documentation</a>
      provides you with all information you need to get started.
    </WelcomeItem>
  </div>
</template>

