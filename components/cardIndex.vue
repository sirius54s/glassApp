<template>
  <v-container class="px-1 ml-0 mr-0">
    <v-card class="mx-auto" rounded="md">
      <v-toolbar
        height="40"
        src="https://assets.nflxext.com/ffe/siteui/allow-robots/contentSampling/seo-watch-free-link-preview.jpg"
        class="mb-4"
      >
        <template #extension>
          <v-sheet
            color="white"
            height="40"
            rounded="pill"
            width="100%"
            class="mt-10 mb-2 ml-2 mr-1"
          >
            <v-row
              class="text-center"
              :class="[
                $vuetify.breakpoint.xs
                  ? 'mt-0 mb-0 pt-0 pb-0 px-2'
                  : 'mt-0 mb-0 pt-0 pb-0 px-8',
              ]"
            >
              <v-col
                cols="2"
                :class="[$vuetify.breakpoint.xs ? 'ma-0 pa-0' : 'ma-0 pa-0']"
              >
                <v-avatar left size="38">
                  <v-img src="https://cdn.vuetifyjs.com/images/john.png" />
                </v-avatar>
              </v-col>
              <v-col
                cols="10"
                :class="[$vuetify.breakpoint.xs ? 'ma-0 pa-0' : 'ma-0 pa-0']"
              >
                <v-list-item-content class="ma-0 pa-0">
                  <v-list-item-title>
                    <span
                      :class="[
                        [$vuetify.breakpoint.xs ? 'caption' : 'caption'],
                      ]"
                      class="text--primary ma-0 pa-0"
                    >
                      {{ item.usuarioCreador }}
                    </span>
                  </v-list-item-title>
                  <v-list-item-subtitle>
                    <span
                      :class="[
                        [$vuetify.breakpoint.xs ? 'fiabilidad' : 'fiabilidad'],
                      ]"
                      class="text--primary ma-0 pa-0"
                    >
                      Fiabilidad 82%
                    </span>
                  </v-list-item-subtitle>
                </v-list-item-content>
              </v-col>
            </v-row>
          </v-sheet>
        </template>
      </v-toolbar>
      <v-row align="center" justify="center">
        <v-col
          cols="12"
          xs="12"
          :class="[
            [$vuetify.breakpoint.smAndDown ? 'mb-0' : ''],
            [$vuetify.breakpoint.smAndDown ? 'body-2' : ''],
            [$vuetify.breakpoint.smAndDown ? 'text-center' : 'text-center'],
          ]"
        >
          <span><b>{{ item.nombreServicio }}</b></span>
        </v-col>
      </v-row>
      <v-row
        class="text-center"
        :class="[[$vuetify.breakpoint.smAndDown ? 'body-2' : '']]"
      >
        <v-col
          cols="12"
          :class="[
            [
              $vuetify.breakpoint.smAndDown
                ? 'pb-0 pt-0 mt-0 mb-0'
                : 'pb-0 pt-0 mt-0 mb-0',
            ],
          ]"
        >
          <span class="text--primary">{{ item.precio }} S/ por mes </span>
        </v-col>

        <v-col
          cols="12"
          :class="[
            [
              $vuetify.breakpoint.smAndDown
                ? 'pb-0 pt-0 mt-0 mb-0'
                : 'pb-0 pt-0 mt-0 mb-0',
            ],
          ]"
        >
          <span class="text--primary">
            0/{{ item.integrantesMax }} puestos libres
          </span>
        </v-col>
      </v-row>
      <v-row
        class="pb-5 text-center"
        :class="[$vuetify.breakpoint.smAndDown ? 'body-2' : '']"
      >
        <v-col cols="12" class="pb-0 mt-0 mb-0">
          <span class="text--primary"> valoracion: 1.5 </span>
        </v-col>
        <v-col class="pt-0 mt-0 mb-0">
          <v-rating :value="1.5" color="amber" dense half-increments readonly />
        </v-col>
      </v-row>

      <!-- <v-card-actions class="grey lighten-3">
        <v-btn
          text
          block
          color="grey"
        >
          seguro<v-icon left large>
            mdi-key
          </v-icon>
        </v-btn>
      </v-card-actions>
      -->
    </v-card>
  </v-container>
</template>

<script>
export default {
  name: 'Grupos',
  props: ['item']
}
</script>

<style lang="scss">
.fiabilidad {
  font-size: 0.75em;
}
@media only screen and (min-device-width: 320px) and (max-device-width: 667px) {
  .v-toolbar__extension {
    padding-left: 0px;
    padding-right: 0px;
  }
}
@media only screen and (min-device-width: 1020px) and (max-device-width: 1970px) {
  .v-toolbar__extension {
    padding-left: 16px;
    padding-right: 16px;
  }
}
</style>