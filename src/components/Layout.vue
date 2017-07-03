<template>
<q-layout>
  <div slot="header" class="toolbar">
    <button class="hide-on-drawer-visible" @click="$refs.leftDrawer.open()">
      <i>menu</i>
    </button>
    <q-toolbar-title :padding="1">
      Tizen PWA Store
    </q-toolbar-title>
  </div>
  <q-drawer ref="leftDrawer">
    <div class="toolbar">
      <q-toolbar-title>
        Menu
      </q-toolbar-title>
    </div>
    <div class="list no-border platform-delimiter">
      <q-drawer-link icon="mail" :to="{path: '/all-apps', exact: true}">
        All Apps
      </q-drawer-link>
      <q-drawer-link icon="mail" :to="{path: '/my-apps', exact: true}">
        My Apps
      </q-drawer-link>
      <q-drawer-link icon="mail" :to="{path: '/import-project', exact: true}">
        Import Project
      </q-drawer-link>
    </div>
  </q-drawer>
  <router-view class="layout-view">Default Content</router-view>
  <div slot="footer" class="toolbar">
    Copyrights by Kamil Nować 2017
  </div>
</q-layout>
</template>

<script>
export default {
}
</script>

<style lang="stylus">
</style>
