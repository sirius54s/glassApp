<template>
  <div>
    <v-card class="overflow-hidden">
      <v-app-bar absolute color="white" elevate-on-scroll scroll-target="#scrolling-techniques-7">
        <v-app-bar-nav-icon></v-app-bar-nav-icon>

        <v-toolbar-title>glassApp</v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn icon @click="dialogBuscador = true">
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-heart</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-dots-vertical</v-icon>
        </v-btn>
      </v-app-bar>
      <v-sheet id="scrolling-techniques-7" class="overflow-y-auto" max-height="50">
        <v-container style="height: 50px;">
        </v-container>
      </v-sheet>
    </v-card>

    <!--card persistente buscador-->
    <v-container>
      <v-layout row justify-center>
        <v-dialog v-model="dialogBuscador" max-width="380">
          <v-card class="px-5 pt-5">
            <v-autocomplete v-model="model" :items="items" :loading="isLoading" :search-input.sync="search" chips
              clearable hide-details hide-selected item-text="name" item-value="symbol" label="Search for a coin..."
              solo>
              <template v-slot:no-data>
                <v-list-item>
                  <v-list-item-title>
                    Search for your favorite
                    <strong>Cryptocurrency</strong>
                  </v-list-item-title>
                </v-list-item>
              </template>
              <template v-slot:selection="{ attr, on, item, selected }">
                <v-chip v-bind="attr" :input-value="selected" color="blue-grey" class="white--text" v-on="on">
                  <v-icon left>
                    mdi-bitcoin
                  </v-icon>
                  <span v-text="item.name"></span>
                </v-chip>
              </template>
              <template v-slot:item="{ item }">
                <v-list-item-avatar color="indigo" class="text-h5 font-weight-light white--text">
                  {{ item.name.charAt(0) }}
                </v-list-item-avatar>
                <v-list-item-content>
                  <v-list-item-title v-text="item.name"></v-list-item-title>
                  <v-list-item-subtitle v-text="item.symbol"></v-list-item-subtitle>
                </v-list-item-content>
                <v-list-item-action>
                  <v-icon>mdi-bitcoin</v-icon>
                </v-list-item-action>
              </template>
            </v-autocomplete>
            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="dark" text @click="dialogBuscador = false">Cancelar</v-btn>
            </v-card-actions>

          </v-card>
        </v-dialog>
      </v-layout>
    </v-container>
  </div>





</template>

<script>
export default {
  data() {
    return {
      dialogBuscador: false,

      isLoading: false,
      items: [],
      model: null,
      search: null,
      tab: null,
    }
    
  },
  watch: {
      model (val) {
        if (val != null) this.tab = 0
        else this.tab = null
      },
      search (val) {
        // Items have already been loaded
        if (this.items.length > 0) return

        this.isLoading = true

        // Lazily load input items
        fetch('https://api.coingecko.com/api/v3/coins/list')
          .then(res => res.clone().json())
          .then(res => {
            this.items = res
          })
          .catch(err => {
            console.log(err)
          })
          .finally(() => (this.isLoading = false))
      },
    },
}
</script>