<template>
  <div>
    <v-bottom-navigation
      :value="value"
      color="orange accent-4"
      horizontal
      fixed
      class="d-lg-none d-xl-flex"
    >
      <v-btn>
        <span>recientes</span>

        <v-icon>mdi-history</v-icon>
      </v-btn>

      <v-btn>
        <span>mas buscados</span>

        <v-icon>mdi-heart</v-icon>
      </v-btn>

      <v-btn @click="dialog = true">
        <v-icon>mdi-wrench</v-icon>
      </v-btn>
    </v-bottom-navigation>
    <!-- inicio config..-->
    <v-row justify="center">
      <v-dialog
        v-model="dialog"
        fullscreen
        hide-overlay
        transition="dialog-bottom-transition"
      >
        <v-card>
          <v-toolbar dark color="orange accent-2">
            <v-btn icon dark @click="dialog = false">
              <v-icon>mdi-close</v-icon>
            </v-btn>
            <v-toolbar-title>Configuracion</v-toolbar-title>
            <v-spacer></v-spacer>
            <v-toolbar-items>
              <v-btn dark text @click="dialog = false">Guardar</v-btn>
            </v-toolbar-items>
          </v-toolbar>
          <v-list three-line subheader>
            <v-subheader>Control de Usuario</v-subheader>
            <v-list-item>
              <v-list-item-content>
                <v-list-item-title>Terminos y condiciones</v-list-item-title>
                <v-list-item-subtitle
                  >Nuestra web esta para facilitar la vida util de sus servicios tecnicos</v-list-item-subtitle
                >
              </v-list-item-content>
            </v-list-item>
          </v-list>
          <v-divider></v-divider>
          <v-list three-line subheader>
            <v-subheader>General</v-subheader>
            <v-list-item>
              <v-list-item-action>
                <v-checkbox v-model="notifications"></v-checkbox>
              </v-list-item-action>
              <v-list-item-content>
                <v-list-item-title>Notificaciones</v-list-item-title>
                <v-list-item-subtitle
                  >notificacion de nuevos enventos</v-list-item-subtitle
                >
              </v-list-item-content>
            </v-list-item>
          </v-list>
        </v-card>
      </v-dialog>
    </v-row>
  </div>
</template>

<script>
export default {
  data() {
    
    return {
      value: 1,
      dialog: false,
      notifications: false,
      sound: true,
      widgets: false,
    };
  },
};
</script>
