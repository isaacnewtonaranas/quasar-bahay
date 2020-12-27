<template>
  <q-layout view="lHr Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-toolbar-title>
          Quasar App
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
        <q-btn
          flat
          dense
          round
          class="q-ml-md"
          icon="menu"
          aria-label="Menu"
          @click="leftDrawerOpen = !leftDrawerOpen"
        />

      </q-toolbar>
      <q-tabs align="left">
        <q-route-tab v-for="(each,i) in essentialLinks" :key="i" :to="each.link" :label="each.title" />
      </q-tabs>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      width="200"
      bordered
      side="right"
      content-class="bg-grey-1"
    >
      <q-list>
        <q-item-label
          header
          class="text-grey-8"
        >
          Essential Links
        </q-item-label>
        <EssentialLink
          v-for="link in essentialLinks"
          :key="link.title"
          v-bind="link"
        />
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import EssentialLink from 'components/EssentialLink.vue'

const linksData = [
  {
    title: 'Home',
    caption: '',
    icon: 'home',
    link: '/'
  },
  {
    title: 'Dashboard',
    caption: '',
    icon: 'dashboard',
    link: 'dashboard'
  },
  {
    title: 'Login',
    caption: '',
    icon: 'login',
    link: 'login'
  },
  {
    title: 'Register',
    caption: '',
    icon: 'how_to_reg',
    link: 'register'
  }
];

export default {
  name: 'MainLayout',
  components: { EssentialLink },
  data () {
    return {
      leftDrawerOpen: false,
      essentialLinks: linksData
    }
  }
}
</script>
