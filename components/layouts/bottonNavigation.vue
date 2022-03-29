<template>
  <v-bottom-navigation
    :value="value"
    color="teal accent-3"
    horizontal
  > 
    <v-btn>
      <span>recientes</span>

      <v-icon>mdi-history</v-icon>
    </v-btn>

    <v-btn>
      <span>mas buscados</span>

      <v-icon>mdi-heart</v-icon>
    </v-btn>

    <v-btn>
      <span>configuracion</span>

      <v-icon>mdi-wrench</v-icon>
    </v-btn>
  </v-bottom-navigation>
</template>

