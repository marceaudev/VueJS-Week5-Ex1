<script setup>
import { RouterView } from 'vue-router'
import Header from './components/Header.vue'
import { provide, ref } from 'vue'

const profile = ref({
  gender: 'female',
  firstname: 'Sophia',
  lastname: 'Rodriguez',
  age: 31,
  job: 'environmental scientist',
})

const updateProfile = (infos) => {
  if (infos.firstname) {
    profile.value.firstname = infos.firstname
  }
  if (infos.lastname) {
    profile.value.lastname = infos.lastname
  }
  if (infos.age) {
    profile.value.age = infos.age
  }
  if (infos.job) {
    profile.value.job = infos.job
  }
}

provide('profile', { profile: profile.value, update: updateProfile })
</script>

<template>
  <Header />
  <RouterView />
</template>

<style scoped></style>
