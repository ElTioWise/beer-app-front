<template>
  <q-layout view="hHh LpR fFf">
    <q-header elevated class="bg-primary text-white">
      <q-toolbar>
        <q-btn dense flat round icon="menu" @click="toggleLeftDrawer" />
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          Title
        </q-toolbar-title>
      </q-toolbar>
    </q-header>
    <q-drawer v-model="leftDrawerOpen" side="left" overlay behavior="mobile" elevated>
      <q-list bordered>

        <q-item v-for="(value,index) in links" :key="index" clickable @click="redirect(value.link)" v-ripple>
          <q-item-section avatar>
            <q-icon color="primary" :name="value.icon" />
          </q-item-section>

          <q-item-section>{{ value.name }}</q-item-section>
        </q-item>
        <q-separator />

    </q-list>
    </q-drawer>
    <q-page-container>
      <router-view />
    </q-page-container>

    <q-footer reveal elevated class="bg-grey-8 text-white">
      <q-toolbar>
        <q-toolbar-title>
          <q-avatar>
            <img src="https://cdn.quasar.dev/logo-v2/svg/logo-mono-white.svg">
          </q-avatar>
          <div>Title</div>
        </q-toolbar-title>
      </q-toolbar>
    </q-footer>

  </q-layout>
</template>

<script setup lang="ts">
import { ref } from 'vue';
import { Notify } from 'quasar';
function redirect(link:string){
  Notify.create(link);
}
const links: { name: string; link: string; icon: string; }[] = [
  {
    'name': 'Google',
    'link': 'https://www.google.com',
    'icon': 'search'
  },
  {
    'name': 'Facebook',
    'link': 'https://www.facebook.com',
    'icon': 'facebook'
  },
  {
    'name': 'Twitter',
    'link': 'https://www.twitter.com',
    'icon': 'close'
  },
  {
    'name': 'Instagram',
    'link': 'https://www.instagram.com',
    'icon': 'camera_alt'
  },
  {
    'name': 'LinkedIn',
    'link': 'https://www.linkedin.com',
    'icon': 'business'
  },
  {
    'name': 'YouTube',
    'link': 'https://www.youtube.com',
    'icon': 'play_circle_outline'
  },
  {
    'name': 'Pinterest',
    'link': 'https://www.pinterest.com',
    'icon': 'photo'
  },
  {
    'name': 'Amazon',
    'link': 'https://www.amazon.com',
    'icon': 'shopping_cart'
  },
  {
    'name': 'Netflix',
    'link': 'https://www.netflix.com',
    'icon': 'movie'
  },
  {
    'name': 'GitHub',
    'link': 'https://www.github.com',
    'icon': 'code'
  }
];
const leftDrawerOpen = ref(false)
function toggleLeftDrawer() {
  leftDrawerOpen.value = !leftDrawerOpen.value
}
</script>
