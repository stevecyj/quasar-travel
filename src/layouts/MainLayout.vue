<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar class="bg-grey-1 text-orange-13">
        <q-toolbar-title>
          好想旅遊
        </q-toolbar-title>
        <div class="gt-xs">
          <q-btn-toggle v-model="model" flat stretch toggle-color="grey-10" :options="options" />
        </div>
        <q-btn flat dense round icon="menu" aria-label="Menu" @click="toggleRightDrawer" />
      </q-toolbar>
    </q-header>

    <q-drawer v-model="rightDrawerOpen" side="right" show-if-above bordered>
      <q-list>
        <q-item-label header>
          Essential Links
        </q-item-label>

        <EssentialLink v-for="link in essentialLinks" :key="link.title" v-bind="link" />
      </q-list>
    </q-drawer>


    <q-page-container>
      <router-view />
      <q-page-sticky position="top-right" :offset="[36, 36]">
        <q-btn round color="accent" @click="alert" icon="alarm" />
      </q-page-sticky>
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: 'Docs',
    caption: 'quasar.dev',
    icon: 'school',
    link: 'https://quasar.dev'
  },
  {
    title: 'Github',
    caption: 'github.com/quasarframework',
    icon: 'code',
    link: 'https://github.com/quasarframework'
  },
  {
    title: 'Discord Chat Channel',
    caption: 'chat.quasar.dev',
    icon: 'chat',
    link: 'https://chat.quasar.dev'
  },
  {
    title: 'Forum',
    caption: 'forum.quasar.dev',
    icon: 'record_voice_over',
    link: 'https://forum.quasar.dev'
  },
  {
    title: 'Twitter',
    caption: '@quasarframework',
    icon: 'rss_feed',
    link: 'https://twitter.quasar.dev'
  },
  {
    title: 'Facebook',
    caption: '@QuasarFramework',
    icon: 'public',
    link: 'https://facebook.quasar.dev'
  },
  {
    title: 'Quasar Awesome',
    caption: 'Community Quasar projects',
    icon: 'favorite',
    link: 'https://awesome.quasar.dev'
  }
]

const btnOptions = [
  { label: 'One', value: 'one' },
  { label: 'Two', value: 'two' },
  { label: 'Three', value: 'three' }
]

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup () {
    const rightDrawerOpen = ref(false)
    const model = ref('one')

    const toggleRightDrawer = () => {

      rightDrawerOpen.value = !rightDrawerOpen.value
      console.log('toggleDrawer');
    }

    const alert = function () {
      console.log('alert');
    }

    return {
      essentialLinks: linksList,
      rightDrawerOpen,
      model,
      options: btnOptions,
      toggleRightDrawer,
      alert
    }
  }
})
</script>

<style lang="scss" scoped>
.bg_klook_primary {
  background-color: $klook_primary;
}
</style>