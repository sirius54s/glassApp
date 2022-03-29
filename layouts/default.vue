<template>
  <v-app>
    <navbar />
    <v-main>
      <div>
        <nuxt />
      </div>
    </v-main>
    <bottonNavigation />
  </v-app>
</template>

<script>
import navbar from '@/components/layouts/navbar.vue'
import bottonNavigation from '@/components/layouts/bottonNavigation.vue'
export default {
  components: {
    navbar,
    bottonNavigation
  },
  data () {
    return {}
  }
}
</script>