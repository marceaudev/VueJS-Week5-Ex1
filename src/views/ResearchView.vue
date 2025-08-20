<script setup>
import { personsList } from '@/assets/data'
import { ref } from 'vue'

const who = ref('')
const personFind = ref(null)
const isSubmit = ref(false)

const handleSearch = () => {
  personFind.value = personsList.find((p) => p.firstname === who.value) || null
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
        <p>{{ personFind.firstname }} {{ personFind.lastname }}</p>
        <p>{{ personFind.age }} ans</p>
        <p>{{ personFind.job[0].toUpperCase() + personFind.job.slice(1) }}</p>
      </div>
      <p v-else>Enter a firstname</p>
    </section>
  </main>
</template>
