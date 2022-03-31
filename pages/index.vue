<template>
  <!-- default -->
  <v-div>
    <!-- banner de seguridad -->
    <v-banner two-line v-model="bannerSeguridad">
      <v-avatar slot="icon" color="deep-purple accent-4" size="40">
        <v-icon icon="mdi-lock" color="white"> mdi-lock </v-icon>
      </v-avatar>

      Nuestra plataforma esta protejida contra rastreo web.

      <template v-slot:actions>
        <v-btn
          text
          color="deep-purple accent-2"
          @click="bannerSeguridad = false"
        >
          Cerrar
        </v-btn>
        <v-btn text color="deep-purple accent-2"> Mas detalles </v-btn>
      </template>
    </v-banner>
    <!-- breadcrumbs -->
    <template color="deep-purple accent-2">
      <div mt-5>
        <v-breadcrumbs :items="items" divider="/"></v-breadcrumbs>
      </div>
    </template>
  </v-div>
</template>

<script>
export default {
  data() {
    return {
      bannerSeguridad: true,
      items: [
        {
          text: "inicio",
          disabled: false,
          href: "#",
        },
      ],
    };
  },
};
</script>

<style></style>
