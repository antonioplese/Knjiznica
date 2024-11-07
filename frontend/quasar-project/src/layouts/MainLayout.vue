<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated>
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          icon="menu"
          aria-label="Menu"
          @click="toggleLeftDrawer"
        />

        <q-toolbar-title>
          Knjiznica
        </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      show-if-above
      bordered
    >
      <q-list>
        <q-item-label
          header
        >
          Essential Links
        </q-item-label>

        <EssentialLink
          v-for="link in linksList"
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

<script setup>
import { ref } from 'vue'
import EssentialLink from 'components/EssentialLink.vue'

defineOptions({
  name: 'MainLayout'
})

const linksList = [
  {
    title: 'Početna',
    caption: 'Početna stranica',
    icon: 'home',
    link: '#/'
  },
  {
    title: 'Popis knjiga',
    caption: 'Popis svih knjiga u knjižnici',
    icon: 'book',
    link: '#/popis_knjiga'
  },
  {
    title: 'Trazi knjigu',
    caption: 'Pretrazivanje',
    icon: 'chat',
    link: '#/pretrazivanje'
  },
  {
    title: 'O nama',
    caption: 'Informacije o nama',
    icon: 'record_voice_over',
    link: '#/o_nama'
  },
  {
    title: 'Lokacija',
    caption: 'Lokacija',
    icon: 'rss_feed',
    link: '#/lokacija'
  },
  {
    title: 'Login',
    caption: 'Prijavite se!',
    icon: 'public',
    link: '#/login'
  },
  {
    title: 'Register',
    caption: 'Registrirajte se',
    icon: 'favorite',
    link: '#/register'
  }
]

const leftDrawerOpen = ref(false)

function toggleLeftDrawer () {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
