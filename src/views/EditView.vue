<script setup>
import { inject } from 'vue'

const Store = inject('profile')
</script>

<template>
  <main class="container">
    <h2>Edit your profile</h2>
    <form @submit.prevent="Store.update">
      <label>
        Firstname
        <input type="text" name="firstname" id="firstname" v-model="Store.profile.firstname" />
      </label>
      <label>
        Lastname
        <input type="text" name="lastname" id="lastname" v-model="Store.profile.lastname" />
      </label>
      <label>
        Job
        <input type="text" name="job" id="job" v-model="Store.profile.job" />
      </label>
      <label>
        Age
        <input type="text" name="age" id="age" v-model="Store.profile.age" />
      </label>
      <button>Valid changes</button>
    </form>
  </main>
</template>
