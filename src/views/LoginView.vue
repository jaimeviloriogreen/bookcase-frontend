<script lang="ts" setup>
  import { ref } from "vue";

  const email = ref<string>("");
  const password = ref<string>("");

  const handleSubmit = async () => {
    const request = await fetch("http://localhost:3000/auth/login", {
      headers: {
        "Content-Type": "application/json;charset=utf-8",
      },
      body: JSON.stringify({
        email: email.value,
        password: password.value,
      }),
      method: "POST",
    });
    const response = await request.json();
    console.log(response);
  };
</script>
<template>
  <h1>Login</h1>

  <section class="section">
    <form class="form" @submit.prevent="handleSubmit">
      <input type="text" placeholder="Email" v-model="email" />
      <input type="password" placeholder="Contraseña" v-model="password" />

      <button type="submit">Ingresar</button>
    </form>
  </section>
</template>
