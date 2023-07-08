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
          michaellamb.dev
        </q-toolbar-title>

        <div>Built with Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer
      v-model="leftDrawerOpen"
      bordered
    >
      <q-list>
        <q-item-label
          header
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

<script lang="ts">
import { defineComponent, ref } from 'vue';
import EssentialLink from 'components/EssentialLink.vue';

const linksList = [
  {
    title: 'Docs',
    caption: 'quasar.dev',
    icon: 'school',
    link: 'https://quasar.dev'
  },
  {
    title: 'Github',
    caption: 'github.com/michaellambgelo',
    icon: 'code',
    link: 'https://github.com/michaellambgelo'
  },
  {
    title: 'Dev Discord',
    caption: 'michaellamb.dev',
    icon: 'chat',
    link: 'https://discord.gg/T2esqjDEVU'
  },
  {
    title: 'LinkStack',
    caption: 'connect with Michael Lamb',
    icon: 'rss_feed',
    link: 'https://link.michaellamb.dev'
  },
  {
    title: 'michaellamb.dev blog',
    caption: 'tech & life',
    icon: 'favorite',
    link: 'https://michaellamb.dev'
  }
];

export default defineComponent({
  name: 'MainLayout',

  components: {
    EssentialLink
  },

  setup () {
    const leftDrawerOpen = ref(false)

    return {
      essentialLinks: linksList,
      leftDrawerOpen,
      toggleLeftDrawer () {
        leftDrawerOpen.value = !leftDrawerOpen.value
      }
    }
  }
});
</script>
