<script setup lang="ts">
import { computed  } from 'vue'
import { RouterLink, useRouter, useRoute } from 'vue-router'

const routes = computed(() => {
  return useRouter().getRoutes()
})
</script>

<template>
  <header>
    <nav class="navbar navbar-light bg-light">
      <div class="container-fluid">
        <a class="navbar-brand" href="#">
          <img src="@/assets/vue3-stock-tracker-logo-v1.svg" alt="Vue 3 Stock Tracker Demo Logo" width="60" height="60" class="d-inline-block align-text-center">
          Vue 3 Stock Tracker Demo
        </a>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNav" aria-controls="navbarNav" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNav">
          <ul class="navbar-nav">
              <li v-for="route in routes" :key="route.path" class="nav-item">
                <router-link
                  :class="useRoute().name === route.name ? 'active' : ''"
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