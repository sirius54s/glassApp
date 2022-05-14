<template>
  <div>
    <v-card class="overflow-hidden">
      <v-app-bar absolute color="white" elevate-on-scroll scroll-target="#scrolling-techniques-7" dense>
        <v-app-bar-nav-icon @click="menuDesplegable = true "></v-app-bar-nav-icon>

        <v-toolbar-title>glassApp</v-toolbar-title>

        <v-spacer></v-spacer>

        <v-btn icon @click="dialogBuscador = true">
          <v-icon>mdi-magnify</v-icon>
        </v-btn>

        <v-btn icon>
          <v-icon>mdi-heart</v-icon>
        </v-btn>

        <v-btn icon @click="dialogCrear = true">
          <v-icon color="orange">mdi-plus-circle-outline</v-icon>
        </v-btn>
      </v-app-bar>
      <v-sheet id="scrolling-techniques-7" class="overflow-y-auto" max-height="50">
        <v-container style="height: 50px;">
        </v-container>
      </v-sheet>
    </v-card>

    <!--card dialogo buscador-->
    <v-container>
      <v-layout row justify-center>
        <v-dialog v-model="dialogBuscador" max-width="380">
          <v-card class="px-5 pt-5">
            <h3>Selecionar <v-icon class="pb-1 orange--text">mdi-select-search</v-icon>
            </h3>


            <v-autocomplete ref="marca" v-model="marca" :items="marcaLista" label="marca" placeholder="Selecinar..."
              required></v-autocomplete>

            <v-autocomplete ref="modelo" v-model="modelo" :items="modeloLista" label="modelo"
              placeholder="selecionar..." required></v-autocomplete>

            <br>

            <v-autocomplete v-model="model" :items="items" :loading="isLoading" :search-input.sync="search" chips
              clearable hide-details hide-selected item-text="name" item-value="symbol" label="Buscar por modelo..."
              solo v-if="mostrarOcultarBuscador">
              <template v-slot:no-data>
                <v-list-item>
                  <v-list-item-title>
                    Soporta solo por modelo simple
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
            <br>

            <v-card-actions>
              <v-spacer></v-spacer>
              <v-btn color="dark" text @click="dialogBuscador = false">Cancelar</v-btn>
              <v-btn color="orange" text @click="dialogBuscador = false">Buscar</v-btn>
            </v-card-actions>

          </v-card>
        </v-dialog>
      </v-layout>
    </v-container>
      <!--menu desplegable-->
    <v-container>
      <v-navigation-drawer
      v-model="menuDesplegable"
      absolute
      temporary
    >
      <v-list
        nav
        dense
      >
        
    <v-row justify="space-around">
      <v-card width="500">
        <v-img
          height="250px"
          src="https://promart.vteximg.com.br/arquivos/ids/896034-1000-1000/image-846dfd5921f14e3e85521cc2b4c4ec0e.jpg?v=637546461155770000"
        >
         

          <v-card-title class="white--text mt-8">
            <v-avatar size="56">
              <img
                alt="user"
                src="data:image/png;base64,iVBORw0KGgoAAAANSUhEUgAAAOEAAADhCAMAAAAJbSJIAAAAMFBMVEXBx9D///+9w83Y3OHDydLIzdXt7/HN0tn3+Pnq7O/S1t319vfh5Ojd4OX8/P3r7fDhTC8lAAAKfElEQVR4nN2d67LrJgyFOWB8wZf9/m9bO44TOzEgoYVNumY6/dHdhC/chJCE+pddU1t3w2hcY21VVWr+x9rGmXHo6nbK//Uq54dP9WBspWepMy3/obJmqLNy5iJsu7FZyM7ZDpwLaWO6NlNLchC2nas83RYA1ZXpcnQmmnCqjWXTvSmtqcENwhJOnVPJeBukch2yTUjCBU9E96Z0f7hmoQhrI+y8D0hlelDLMIQDf2WJQ1rMaAUQTiNodH4xqhGwuIoJe5cH7wnpxINVSJiXD8IoIuyb3HwARgFhm73/3owCky6ZcDJX8T0YzeWEw4V4q4ZLCXt7ZQeu0jZtOiYRXjpAd4xJQzWBsL4Fb1XCyYNPeNkKeqaEbuQS9tWNfIsq7mxkEo53duAqPWYknG5YQr+lLcse5xDeucQcxVlwGIQFjNBNnJFKJ7zEyqZKN3DCyd4N9SHyZCQS9ncDnYi4bdAI/0oaoZs0zSFHIhxKBJwRSccNCmGhgEREAmGxgLRdI05Y0Db4LQJilLBoQApijLDgIboqOhcjhMUDxhHDhF35gDNi+H4jSFj/AuCMGDxqhAj73wCcFXIYBwinu9vNUMAMDxCWdpoIyaYQNuhWPMJKVuEvHP3nRS8hdp+YoRozdHXdt31fd4NppCENn1/g3TN8hMhldAmv+D7MtbDIhvVLfAuqhxC4ymjnX8z/kO5lz2rjIUStMtrGjKoB5qH0rDbnhCBzW1eUcIquAn3buRF+SoiZhJp85TdgVp3zqXhKCLmb0I7ump4w87GiEjrEt0Xs4U9hbHxHI0Q41nTDjfWBOGTP3G8nhIhvSrmthdwsUwiN/Gu4F2BPIcyo75/2ixBwZKL5MfMg6i/j6YtQPh2YawwY8Wvf/ySUf0dyDy6SmxpfX/9JKP0CSfTSIsBOFSaULzP0i71zyWfJx098JGzl80Aa8yo/1eij1+ZIKB4jxBuvkOQGx9GyORDKd4ozs4krsY163DEOhHLXDAAQME4Pa8G+TeIuFOyEe4l3rEMn7gnFXRjw6bEkXk/3nbgjlHchKtNFfJTad+KOULyQoroQcATfrXhvwqmQWbhIPhPfe+KbcBR+KGYh3Zol1duwUTk+VC7xaVh/E2KXaKnE3r73EeNFKF6hTx1dyZK25r3sbYTyrQI5SBHDdBtSCvaJ2NxWsf39+sU3QvnZGpuHLd67XmvNk1DukMVt96vEm/42qJ6EcucB4ty0F6xFKyHgujDNReqX3AB5uhtWQvkgBS80wCathPIhEY7aSRDghs/tCMUf9un+kQvgFFNvQsDvBd4sENvFc1w9CAG3PkUSmhch4OpOh9ubIMAotRshYsiX2Ifr4rAQIm6YyyTsnoSIe/si19LHfrEQIkIvoOffRZDg1molhPxaBdo0ah1ZChXoIbkXPROkpMHyuytIaAL8iA9q1eIdU6goPfT5ENYqBdlaFf6MD2nUYogozEIDP1yAInjnpUbBsiexR2DAAXjR/Lsr1GeBJyKqdMMwE0IiERXYqgFNncWqUbi0CuSOCCvwY2dCWCkP5DCFNar6p3BR+cDVFJgLMSlg+pY0HOotXL6O7hXw54KdL4C/uq5VB/swXCciU646hSxLBpqJ0MTOQUFztTHLKTItUI8Kc0rZPg+xJ2Lz441CmTSrAIYNzJxZ5RQ4kVI+TsGpq41C58JKz/rQWTPLwgmFLil4iQOr4BXmRFsGvgJABkKJaZOhAkCVgTAdMUc1qkxVENMGaqZqVFkYk5abPHVUsoxSleQgzlT2NReh0pZn3bS5ik5W8P3wLY6Nmq/SD37Hf4te2rjOWDXUou3Sg2iVxvNWdm/AZ4sP6XjF+DpzXWKHPR+eSNvBf2cz4WpG+GSwZ/xTad0MZz3ZDxeURJ3P+NeUj9eqGV9PdC2PeI1Npmc/PjVcRLjoUVxoeZfM+4hXDnVIf2mJ0jXS512idA+8tyhTE/DuqUhVyPvDImWBd8BlygHv8cvUCIzFKFL6DxdPU6Ye8TSgmKgypYFxbWVqjWu76eWfS2SA8aVF6hlf+j9eap4xwv9ju+0Z542wanQOyZu1xerLJuJ8qm2cM3g511QyR8Ar3yJ9Imrthj7nq9pTP7j0znzlzKRORNRrrzF1qQ65R4mA9Nw13aCTSPxKcxrvctcSjG9t4Q9oB5Xi+F/r5STmkCbWfpSIP9DWjMHEPOBrO3AV+1G0fR4wc7+oci6ffk28FfGQy807QaHTY+hiHYOeaa0JNRXuA+T14qGmAmeYwnMpOWrpgB91MeirKby0AE+MS4iN7Plv8lqMzsLjinrf+VWfhnp9ga2VlCLiVPyqMURcpm4eo4uI4/SrThQx3gOXUpEuUmzFSa0v0pZYQBdSO/H157yaezduhTtRJtRZzT1KEQN0wnaaCBfzp3UTCXYNvDREmgh9cVr7krBhlDFICcPUU780ukjBc+5TFTVPPDVoo50IrwyRqpgV7a0jHOtEeHWPVMW6wlsLOvZ/FrLQRJeaQD3v2HJ6KUZI4WYGarJHfMP3W92bgtZ3sK5++GzyI4TBtxHC/f8jhB9/y3mj5CcIo2+UhOyFnyCMvjMT2jF+gZDwVlBgsfkFQsJ7T4HF5hcIv/+W8+5a+YTEd9e8lk35hMS387wfUDwh+f1Dn6+ndELGG5aesgaFE3LeIfXt+2U4onzF3FhvyXo+44a77TN57th47wF7pmIRnpr2fIwy33T2meAaXVyer/OUdv/w4r6tru++ufDEKyS8re49ZdwUpvCUx80W8OQGCL35Qjdez/iyJQO/esi75DtIQSoJJckT/BV0cwb9Z757rJvWm97zRHn4zi/sIfT6NKobnMO+xkSGVMQH6kW8fKROvvDEWEtiXl5vIjT/5W2R/nzRwtGfOurH9ud6X3hR439dPm5Ixj31AcTmovCozhvuTbCUCXcRARfqJaZ46w8QpqwGlNuWEGKVffsPlEQgLXek+6TQjWTmcO9QVAJtIaDdmAVDWGgVTJLUefb4VbThQ7wTDFbh0pkYw3yKOHaot55TOP4hw1gdwnyWuh3T73UjKQ+6Qb2Vu2gaw/lAjGMq4+Y6VudFV4FKNCzVsQQSzi7FuZuPh8zpRm7n9CaezsXZoljRB1M8cUUrIxmt/Tz7Yt+hyVPwIWZ8BaEi0dxC1yUN19qEF5fn5zPtKG4ESU0KQtbajn8syn4gFh1iG1H8GBlqbS6tKzfUBMy+Gy01xzDBu5AQBfRHa8yG2ZhhKxB11KNclLOKkUGZYgUnxTlx08geSb22ccaM47jkvzbWVvxU3zSPe1okV5+W1bkSJSaE0osUIgiBT2yQleoYSo/Gu7TYhOBKSBBv2GaueLjjk5xdRBGVeatWvvhk5xZhzGjURr6bT0w492PWsRqvDpqfcJ6PJlMZRK0NwHeAiWzuyGYXgw9UsQEVu0051XHwlEG5RYDR6V0D6sjl+IVrFjT+fuocx44+pcPi/QMTLqpN+pycTyIG7kPPkUPRDi7uizihc10Ot2uuLJG2Gxvq6Wj+u2bMQrcoax5MWw/OPuoG+8hUZd18QM7ZiAsyfZaz/DCux96qWmol2+U0PA7d+dkfrP8AELeBvwZOOcwAAAAASUVORK5CYII="
              >
            </v-avatar>
            <p class="ml-3 black--text">
              Invitado
            </p>
          </v-card-title>
        </v-img>

        <v-card-text class="mb-16 pb-16">
          <div class="font-weight-bold ml-8">
            notificaciones
          </div>

          <v-timeline
            align-top
            dense
          >
            <v-timeline-item
              v-for="message in messages"
              :key="message.time"
              :color="message.color"
              small
            >
              <div>
                <div class="font-weight-normal">
                  <strong>{{ message.from }}</strong> @{{ message.time }}
                </div>
                <div>{{ message.message }}</div>
              </div>
            </v-timeline-item>
          </v-timeline>
        </v-card-text>
      </v-card>
    </v-row>

      </v-list>
    </v-navigation-drawer>
    </v-container>

    <!--card dialogo crear-->
    <template>
      <v-layout row justify-center>
        <v-dialog v-model="dialogCrear">
          <v-card class="px-5 pt-5">
            <v-form>
              <v-container>
                <h3>Telefono </h3>
                <v-row>



                  <v-col cols="12" md="6">
                    <v-select v-model="marcaCrear" :items="marcaLista" :rules="[v => !!v || 'Item is required']"
                      label="marca crear" required></v-select>
                  </v-col>

                  <v-col cols="12" md="6">
                    <v-text-field v-model="modeloCrear" :counter="10" label="modelo crear" required></v-text-field>
                  </v-col>
                </v-row>

                <br>
                <h3>Telefono a comparar </h3>

                <v-row>



                  <v-col cols="12" md="6">
                    <v-select v-model="marcaCrearCompatible" :items="marcaLista"
                      :rules="[v => !!v || 'Item is required']" label="marca compatible" required></v-select>
                  </v-col>

                  <v-col cols="12" md="6">
                    <v-text-field v-model="modeloCrearCompatible" :counter="10" label="modelo compatible" required>
                    </v-text-field>
                  </v-col>
                </v-row>

                <v-btn class="ml-1 mr-1" @click="dialogCrear = false">
                  Cancelar
                </v-btn>
                <v-btn>
                  limpiar
                </v-btn>
                <v-btn class="mt-5 right">
                  Enviar
                </v-btn>

              </v-container>
            </v-form>
          </v-card>
        </v-dialog>
      </v-layout>
    </template>

  </div>





</template>

<script>
export default {
  data() {
    return {
      dialogBuscador: false,
      dialogCrear: false,
      menuDesplegable: false,

      isLoading: false,
      items: [],
      model: null,
      search: null,
      tab: null,

      mostrarOcultarBuscador: true,
      marca: null,
      modelo: null,
      marcaLista: ["samsung", "huawei"],
      modeloLista: ["j2 prime", "j5 prime"],


      marcaCrear: null,
      modeloCrear: null,
      marcaCrearCompatible: null,
      modeloCrearCompatible: null,


      messages: [
        {
          from: 'You',
          message: `Sure, I'll see you later.`,
          time: '10:42am',
          color: 'deep-purple lighten-1',
        },
        {
          from: 'John Doe',
          message: 'Yeah, sure. Does 1:00pm work?',
          time: '10:37am',
          color: 'green',
        },
        {
          from: 'You',
          message: 'Did you still want to grab lunch today?',
          time: '9:47am',
          color: 'deep-purple lighten-1',
        },
      ]
    }

  },
  mounted() {

  },
  watch: {
    model(val) {
      if (val != null) this.tab = 0
      else this.tab = null
    },
    search(val) {
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