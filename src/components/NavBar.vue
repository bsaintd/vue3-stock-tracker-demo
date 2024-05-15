<script setup lang="ts">
import { computed  } from 'vue'
import { RouterLink, useRouter, useRoute } from 'vue-router'

const appTitle = 'Vue 3 Stock Tracker Demo'
const currentRoute = useRoute()
const routes = computed(() => {
  return useRouter().getRoutes()
})
</script>

<template>
  <header>
    <nav class="navbar navbar-light bg-light">
      <div class="container-fluid">
        <router-link class="navbar-brand" to="/">
          <img
            src="@/assets/vue3-stock-tracker-logo-v1.svg"
            alt="Vue 3 Stock Tracker Demo Logo"
            width="60"
            height="60"
            class="d-inline-block align-text-center">
          {{ appTitle }}
        </router-link>
        <button class="navbar-toggler"
          type="button"
          data-bs-toggle="collapse"
          data-bs-target="#navbarNav"
          aria-controls="navbarNav"
          aria-expanded="false"
          aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav">
              <li v-for="route in routes" :key="route.path" class="nav-item">
                <router-link
                  :class="currentRoute.name === route.name ? 'active' : ''"
                  class="nav-link"
                  :aria-label="route.name"
                  :to="route.path">
                  {{route.name}}
                </router-link>
              </li>
          </ul>
        </div>
      </div>
    </nav>
  </header>
</template>