<script setup>
import { ref, onMounted } from "vue";

const usersQty = ref(1);
const users = ref(null);
onMounted(async () => {
  await fetchRandomUser();
});

const fetchRandomUser = async () => {
  const res = await fetch(
    `https://randomuser.me/api/?results=${usersQty.value}`
  );
  const json = await res.json();
  users.value = json.results;
};
</script>

<template>
  <main>
    <h1>WELCOME!</h1>
    <div v-for="user in users" :key="user.id.value">
      {{ user.name.first }}
    </div>
  </main>
</template>
