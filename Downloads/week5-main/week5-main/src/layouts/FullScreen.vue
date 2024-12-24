<template>
  <q-layout view="hHh Lpr fFf"> <!-- Be sure to play with the Layout demo on docs -->

    <q-page-container>
      <q-header elevated>
        <q-toolbar>
          <q-btn flat dense round icon="menu" aria-label="Menu" />

          <q-toolbar-title> Quasar App </q-toolbar-title>

          <div><q-btn icon="logout" @click="authStore.logout()"></q-btn></div>
        </q-toolbar>
      </q-header>

      <router-view />
    </q-page-container>

  </q-layout>
</template>

<script setup lang="ts">
import { useAuthStore } from 'src/stores/authStore'

const authStore = useAuthStore()
</script>
