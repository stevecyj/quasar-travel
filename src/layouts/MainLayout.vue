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

    <q-drawer v-model="rightDrawerOpen" class="bg-grey-10 text-white" side="right" show-if-above>
      <div>

        <q-list class="text-white">
          <q-item-label header>
            好想旅遊
          </q-item-label>

          <EssentialLink v-for="link in essentialLinks" :key="link.title" v-bind="link" />
        </q-list>
      </div>
    </q-drawer>


    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { defineComponent, ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

const linksList = [
  {
    title: '登入',
    caption: '登的入',
    icon: 'fas fa-sign-in-alt',
    link: 'https://forum.quasar.dev'
  },
  {
    title: '註冊',
    caption: '註冊',
    icon: 'fas fa-edit',
    link: 'https://twitter.quasar.dev'
  },
  {
    title: '精選景點',
    caption: '精選的景點',
    icon: 'fas fa-search-location',
    link: 'https://quasar.dev'
  },
  {
    title: '美食地圖',
    caption: '美食的地圖',
    icon: 'fas fa-map-marked-alt',
    link: 'https://github.com/quasarframework'
  },
  {
    title: '夜宿曉行',
    caption: '夜宿的曉行',
    icon: 'fas fa-utensils',
    link: 'https://chat.quasar.dev'
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