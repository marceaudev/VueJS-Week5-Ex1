<script setup>
import { RouterView } from 'vue-router'
import Header from './components/Header.vue'
import { provide, ref } from 'vue'
import router from './router'

const profile = ref({
  gender: 'female',
  firstname: 'Sophia',
  lastname: 'Rodriguez',
  age: 31,
  job: 'environmental scientist',
})

const updateProfile = () => {
  profile.value.firstname = firstname.value
  profile.value.lastname = lastname.value
  profile.value.age = age.value
  profile.value.job = job.value
  router.push('/profile')
}

provide('profile', { profile: profile.value, update: updateProfile })
</script>

<template>
  <Header />
  <RouterView />
</template>

<style scoped></style>
