<script setup>
import router from '@/router'
import { inject, ref } from 'vue'

const Store = inject('profile')

const firstname = ref(Store.profile.firstname)
const lastname = ref(Store.profile.lastname)
const job = ref(Store.profile.job)
const age = ref(Store.profile.age)

const handleSubmit = () => {
  const newInfos = {
    firstname: firstname.value,
    lastname: lastname.value,
    age: age.value,
    job: job.value,
  }
  Store.update(newInfos)
  router.push({ name: 'profile' })
}
</script>

<template>
  <main class="container">
    <section>
      <h2>Edit your profile</h2>
      <form @submit.prevent="handleSubmit">
        <label>
          Firstname
          <input type="text" name="firstname" id="firstname" v-model="firstname" />
        </label>
        <label>
          Lastname
          <input type="text" name="lastname" id="lastname" v-model="lastname" />
        </label>
        <label>
          Job
          <input type="text" name="job" id="job" v-model="job" />
        </label>
        <label>
          Age
          <input type="text" name="age" id="age" v-model="age" />
        </label>
        <button>Valid changes</button>
      </form>
    </section>
  </main>
</template>

<style scoped>
section {
  margin-top: 40px;
  display: flex;
  flex-direction: column;
  align-items: center;
}

h2 {
  margin-bottom: 40px;
}

form {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 15px;
}

label {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5px;
}

input[type='text'] {
  width: 250px;
}
</style>
