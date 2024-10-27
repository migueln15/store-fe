<template>
  <q-layout>
    <q-page-container>
      <q-page class="flex flex-center q-pa-md" style="height: 100vh">
        <q-card-section>
          <h5>Inicio de sesión</h5>
        </q-card-section>
        <q-card-section>
          <q-input v-model="emailValue" label="Email" outlined dense />
          <q-input v-model="pwdValue" label="Password" outlined dense />
        </q-card-section>
        <q-card-section>
          <q-btn label="Login" color="primary" @click="inicioSesion" />
        </q-card-section>
      </q-page>
    </q-page-container>
  </q-layout>
</template>

<style></style>

<script>
export default {
  name: "LoginForm",
  data() {
    return {
      emailValue: "",
      pwdValue: "",
    };
  },
  methods: {
    inicioSesion() {
      console.log("Click en el boton de inicio de sesión");
      console.log(`Valor de email: ${this.emailValue}`);

      let endpointLoing = "/api/User/SignIn";
      let user = { email: this.emailValue, password: this.pwdValue };

      this.$api
        .post(endpointLoing, user)
        .then((response) => {
          console.log("respuesta exitosa: " + JSON.stringify(response));
        })
        .catch((error) => {
          console.log("Error en: " + error);
        });
    },
  },
};
</script>
