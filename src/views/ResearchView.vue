<script setup>
import { personsList } from '@/assets/data'
import { ref } from 'vue'

const who = ref('')
const personFind = ref(null)
const isSubmit = ref(false)

const handleSearch = () => {
  const searchWho = who.value.toLowerCase()
  personFind.value =
    personsList.find((p) => p.firstname.toLowerCase() === searchWho) ||
    personsList.find((p) => p.lastname.toLowerCase() === searchWho) ||
    null
  isSubmit.value = true
}
</script>

<template>
  <main class="container">
    <section>
      <h2>Research by name</h2>
      <form @submit.prevent="handleSearch">
        <input type="text" placeholder="Marceau" v-model="who" />
        <button>Search</button>
      </form>
    </section>
    <section>
      <p v-if="!personFind && who.length > 0 && isSubmit">
        This name doesn't exist in the list, sorry
      </p>
      <div v-else-if="personFind">
        <h3>Found it !!!</h3>
        <div class="person">
          <p>{{ personFind.firstname }} {{ personFind.lastname }}</p>
          <p>{{ personFind.age }} ans</p>
          <p>{{ personFind.job[0].toUpperCase() + personFind.job.slice(1) }}</p>
        </div>
      </div>
      <p v-else>Enter a firstname</p>
    </section>
  </main>
</template>

<style scoped>
.container {
  height: calc(100dvh - var(--header-height));
  display: flex;
  align-items: center;
  justify-content: center;
}

section {
  width: 50%;
  display: flex;
  flex-direction: column;
  justify-content: center;
  align-items: center;
}

form {
  display: flex;
  gap: 10px;
}

input[type='text'] {
  width: 250px;
}

section:first-of-type {
  gap: 25px;
}

section:last-of-type div:first-child {
  display: flex;
  flex-direction: column;
  gap: 25px;
}

section:last-of-type div:first-child {
  display: flex;
  flex-direction: column;
  gap: 25px;
}

.person {
  display: flex;
  align-items: center;
  flex-direction: column;
  border: 1px solid black;
  padding: 10px;
  border-radius: 10px;
}
</style>
