<script setup>
import { inject } from 'vue'
import { RouterLink } from 'vue-router'

const Store = inject('profile')
</script>

<template>
  <main class="container">
    <section>
      <h2>Your profile</h2>
      <p><span>Firstname : </span>{{ Store.profile.firstname }}</p>
      <p><span>Lastname : </span>{{ Store.profile.lastname }}</p>
      <p><span>Age : </span>{{ Store.profile.age }}</p>
      <p><span>Job : </span>{{ Store.profile.job }}</p>
      <RouterLink :to="{ name: 'edit' }">
        <button>Edit</button>
      </RouterLink>
    </section>
  </main>
</template>
