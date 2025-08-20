<script setup>
import { ref } from 'vue'

const firstName = ref('')
const lastName = ref('')
const email = ref('')
const selectType = ref('Adult')

const personList = ref([])

const handleSubmit = () => {
  personList.value.push({
    firstName: firstName.value,
    lastName: lastName.value,
    email: email.value,
    type: selectType.value,
  })
}
</script>

<template>
  <main class="container">
    <section>
      <form @submit.prevent="handleSubmit">
        <label for="firstname">Firstname :</label>
        <input
          type="text"
          name="firstname"
          id="firstname"
          placeholder="First name"
          v-model="firstName"
        />
        <label for="lastname">Lastname :</label>
        <input
          type="text"
          name="lastname"
          id="lastname"
          placeholder="Last name"
          v-model="lastName"
        />
        <label for="email">Email :</label>
        <input type="text" name="email" id="email" placeholder="Email" v-model="email" />
        <div>
          <label for="adult">Adult</label>
          <input type="radio" value="Adult" id="adult" v-model="selectType" />
          <label for="minor">Minor</label>
          <input type="radio" value="Minor" id="minor" v-model="selectType" />
        </div>
        <button>Add to waiting list</button>
      </form>
    </section>
    <section>
      <div v-for="(person, i) in personList" :key="i">
        <p>Name : {{ person.firstName }} {{ person.lastName }}</p>
        <p>Email : {{ person.email }}</p>
        <p>Is {{ person.type }}</p>
      </div>
    </section>
  </main>
</template>
