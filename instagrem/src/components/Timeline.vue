<script setup>
import Container from "./Container.vue";
import { ref } from "vue";
import { useUsersStore } from "../stores/users";
import { storeToRefs } from "pinia";
import Cards from "./Cards.vue";
import LogInMessage from "./LogInMessage.vue";

const userStore = useUsersStore();
const { user, loadingUser } = storeToRefs(userStore);
</script>

<template>
  <Container>
    <div v-if="!loadingUser">
      <Cards v-if="user" />
      <LogInMessage v-else />
    </div>
    <div v-else class="spinner">
      <ASpin />
    </div>
  </Container>
</template>

<style>
.card-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  padding: 20px 0;
}

.spinner {
  display: flex;
  align-items: center;
  justify-content: center;
  height: 120px;
}
</style>
