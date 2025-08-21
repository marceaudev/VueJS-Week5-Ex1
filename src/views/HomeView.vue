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
        <label
          >Firstname :
          <input
            type="text"
            name="firstname"
            id="firstname"
            placeholder="First name"
            v-model="firstName"
          />
        </label>
        <label
          >Lastname :
          <input
            type="text"
            name="lastname"
            id="lastname"
            placeholder="Last name"
            v-model="lastName"
          />
        </label>
        <label
          >Email :
          <input type="text" name="email" id="email" placeholder="Email" v-model="email" />
        </label>
        <div class="radioBloc">
          <label>
            <input type="radio" value="Adult" id="adult" v-model="selectType" />
            Adult
          </label>
          <label>
            <input type="radio" value="Minor" id="minor" v-model="selectType" />
            Minor
          </label>
        </div>
        <button>Add to waiting list</button>
      </form>
    </section>
    <section>
      <h2>Waiting List</h2>
      <p v-if="personList.length === 0">Nobody on the list, yet !!!</p>
      <div v-else v-for="(person, i) in personList" :key="i" class="person">
        <p>Name : {{ person.firstName }} {{ person.lastName }}</p>
        <p>Email : {{ person.email }}</p>
        <p>Is {{ person.type }}</p>
      </div>
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

section:last-of-type {
  gap: 25px;
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

.radioBloc {
  display: flex;
  flex-direction: column;
  align-items: center;
  gap: 5px;
}

.radioBloc label {
  flex-direction: row;
}

input[type='text'] {
  width: 250px;
}

.person {
  border: 1px solid black;
  padding: 5px 10px;
}
</style>
