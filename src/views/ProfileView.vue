<script setup>
import { inject } from 'vue'
import { RouterLink } from 'vue-router'

const Store = inject('profile')
</script>

<template>
  <main class="container">
    <section>
      <h2>Your profile</h2>
      <div class="info">
        <p><span>Firstname</span> : {{ Store.profile.firstname }}</p>
        <p><span>Lastname</span> : {{ Store.profile.lastname }}</p>
        <p><span>Age</span> : {{ Store.profile.age }}</p>
        <p><span>Job</span> : {{ Store.profile.job }}</p>
      </div>
      <RouterLink :to="{ name: 'edit' }">
        <button>Edit profile</button>
      </RouterLink>
    </section>
  </main>
</template>

<style scoped>
section {
  margin-top: 40px;
  display: flex;
  flex-direction: column;
  gap: 30px;
}

span {
  text-decoration: underline;
  font-weight: bold;
}

.info {
  display: flex;
  flex-direction: column;
  gap: 5px;
}

button {
  background-color: transparent;
  border: 1px solid #fc9603;
  color: #fc9603;
  padding: 8px;
  border-radius: 7px;
}
</style>
