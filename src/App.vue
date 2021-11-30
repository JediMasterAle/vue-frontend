<template>
  <q-layout view="lHh Lpr lFf">
    <q-header elevated class="">
      <q-toolbar>
        <q-btn
          flat
          dense
          round
          @click="leftDrawerOpen = !leftDrawerOpen"
          aria-label="Menu"
          icon="menu"
        />

        <q-toolbar-title> Quasar App </q-toolbar-title>

        <div>Quasar v{{ $q.version }}</div>
      </q-toolbar>
    </q-header>

    <q-drawer v-model="leftDrawerOpen" show-if-above bordered class="bg-grey-2">
      <q-list>
        <q-item-label header>Acessos</q-item-label>
        <q-item
          to="/"
          exact
          active-class="bg-blue-grey-12"
          class="text-blue-14"
        >
          <q-item-section avatar>
            <q-icon name="home" />
          </q-item-section>
          <q-item-section> Home </q-item-section>
        </q-item>
        <q-item
          to="/about"
          exact
          active-class="bg-blue-grey-12"
          class="text-blue-14"
        >
          <q-item-section avatar>
            <q-icon name="school" />
          </q-item-section>
          <q-item-section> About </q-item-section>
        </q-item>
      </q-list>
    </q-drawer>

    <q-page-container>
      <router-view />
    </q-page-container>
  </q-layout>
</template>

<script>
import { ref } from "vue";

export default {
  name: "LayoutDefault",

  components: {},
  computed: {},
  setup() {
    return {
      leftDrawerOpen: ref(false),
    };
  },
};
</script>
