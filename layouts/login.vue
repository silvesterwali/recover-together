<template>
  <v-app dark>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
      elevate-on-scroll
      :color="color"
      :dark="color === 'transparent' ? true : false"
    >
      <v-toolbar-title @click="$router.push('/')" v-text="title" />
      <v-spacer />
      <v-btn text to="/login" class="mr-1"> Login </v-btn>
      <v-btn text to="register"> Register </v-btn>
    </v-app-bar>
    <v-main class="backme">
      <v-container class="pt-10 pb-10">
        <Nuxt />
      </v-container>
    </v-main>
    <v-scale-transition>
      <v-btn
        v-show="fab"
        v-scroll="onScroll"
        fab
        dark
        fixed
        bottom
        right
        color="secondary"
        @click="toTop"
      >
        <v-icon>mdi-arrow-up</v-icon>
      </v-btn>
    </v-scale-transition>

    <v-footer :absolute="!fixed" app>
      <span>&copy; {{ new Date().getFullYear() }}</span>
    </v-footer>
  </v-app>
</template>

<script>
export default {
  name: 'DefaultLayout',
  data() {
    return {
      color: null,
      clipped: true,
      fab: false,
      flat: false,
      drawer: false,
      fixed: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/',
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire',
        },
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Portfolio',
    }
  },
  watch: {
    fab(value) {
      if (value) {
        this.color = 'white'
        this.flat = false
      } else {
        this.color = 'transparent'
        this.flat = true
      }
    },
  },
  created() {
    if (process.server) {
      return
    }
    // eslint-disable-next-line nuxt/no-globals-in-created
    const top = window.pageYOffset || 0
    if (top <= 40) {
      this.color = 'transparent'
      this.flat = true
    }
  },
  methods: {
    onScroll(e) {
      if (typeof window === 'undefined') return
      const top = window.pageYOffset || e.target.scrollTop || 0
      this.fab = top > 40
    },
    toTop() {
      this.$vuetify.goTo(0)
    },
  },
}
</script>
<style lang="scss" scoped>
.backme {
  background: rgb(2, 0, 36);
  background: linear-gradient(
    90deg,
    rgba(2, 0, 36, 1) 0%,
    rgba(9, 9, 121, 1) 35%,
    rgba(0, 212, 255, 1) 100%
  );
}
</style>
