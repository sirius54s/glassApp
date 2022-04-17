<template>
  <!-- default -->
  <div>
    <!-- banner de seguridad -->
    <v-banner two-line v-model="bannerSeguridad">
      <v-avatar slot="icon" color="orange accent-º  º º º º º º " size="40">
        <v-icon icon="mdi-lock" color="white"> mdi-lock </v-icon>
      </v-avatar>

      Nuestra plataforma esta protegida contra rastreo web.

      <template v-slot:actions>
        <v-btn text color="orange accent-1" @click="bannerSeguridad = false">
          Cerrar
        </v-btn>
        <v-btn text color="orange accent-1"> Mas detalles </v-btn>
      </template>
    </v-banner>

    <!-- carousel -->
    <template>
      <v-carousel :show-arrows="false">
        <v-carousel-item
          v-for="(item, i) in imagenCarousel"
          :key="i"
          :src="item.src"
        ></v-carousel-item>
      </v-carousel>
    </template>
    <!-- breadcrumbs -->
    <template color="orange accent-1">
      <div mt-5>
        <v-breadcrumbs :items="itemsCategoria" divider="/"></v-breadcrumbs>
      </div>
    </template>
    <!-- card index -->
    <template  mt-5>
      <div v-for="(itemDefault, index) in defaultData" :key="index" mt-5>
        <v-card class="mx-auto" max-width="344" outlined>
          <v-list-item three-line>
            <v-list-item-content>
              <div class="text-overline mb-4">{{ itemDefault.marca }}</div>
              <v-list-item-title class="text-h5 mb-1">
                {{ itemDefault.modelo }} compatiblidad
              </v-list-item-title>
              <v-list-item-subtitle>
                <v-list three-line>
                  <div
                    v-for="(
                      itemCompatibilidad, index
                    ) in itemDefault.compatibilidad"
                    :key="index"
                  >
                    <v-subheader
                      v-if="header"
                      :key="index"
                      v-text="header"
                    ></v-subheader>

                    <v-list-item>
                      <v-list-item-avatar>
                        <v-img :src="itemCompatibilidad.avatar"></v-img>
                      </v-list-item-avatar>

                      <v-list-item-content>
                        <v-list-item-title
                          v-html="itemCompatibilidad.titulo"
                        ></v-list-item-title>
                        <v-list-item-subtitle
                          v-html="itemCompatibilidad.subtitulo"
                        ></v-list-item-subtitle>
                      </v-list-item-content>
                    </v-list-item>
                  </div>
                </v-list>
              </v-list-item-subtitle>
            </v-list-item-content>

            <v-list-item-avatar tile size="80">
              <v-img
                src="https://www.productsvsprice.com/images/electronics/smartphone/samsung/samsung-galaxy-a12-smartphone-details-and-price-310492406.svg"
              >
              </v-img
            ></v-list-item-avatar>
          </v-list-item>

          <v-card-actions>
            <v-btn outlined rounded text> Agregar compatiblidad </v-btn>
          </v-card-actions>
        </v-card>
                        
      </div>
    </template>
  </div>
</template>

<script>
import cardIndex from "@/components/cardIndex";
export default {
  components: {
    cardIndex,
  },
  data: () => ({
    bannerSeguridad: true,
    header: "usuario:",

    itemsCategoria: [
      {
        text: "inicio",
        disabled: false,
        href: "#",
      },
    ],

    imagenCarousel: [
      {
        src: "http://cdn.shopify.com/s/files/1/0090/5913/9662/products/KlMFp7dLT-MICA-11D-OFICIAL_e1752f3d-1b03-4b23-b483-adf10db50c83.jpg?v=1619702919",
      },
      {
        src: "https://m.media-amazon.com/images/I/71mUWg7Ph6L._AC_SX679_.jpg",
      },
      {
        src: "https://http2.mlstatic.com/D_644170-MLA46451256552_062021-O.jpg",
      },
      {
        src: "https://i.linio.com/p/c15ebf71725a73a7751f5cd0c3eedd01-product.jpg",
      },
    ],

    defaultData: [
      {
        marca: "samsung",
        modelo: "a12",
        compatibilidad: [
          {
            avatar: "https://cdn.vuetifyjs.com/images/lists/2.jpg",
            titulo: "samsung a03",
            subtitulo: `usuario: raul011`,
          },
          {
            avatar: "https://cdn.vuetifyjs.com/images/lists/2.jpg",
            titulo: "samsung a03",
            subtitulo: `usuario: raul011`,
          },
        ],
      },
      {
        marca: "samsung",
        modelo: "a12",
        compatibilidad: [
          {
            avatar: "https://cdn.vuetifyjs.com/images/lists/2.jpg",
            titulo: "samsung a03",
            subtitulo: `usuario: raul011`,
          },
          {
            avatar: "https://cdn.vuetifyjs.com/images/lists/2.jpg",
            titulo: "samsung a03",
            subtitulo: `usuario: raul011`,
          },
        ],
      },
    ],
  }),
};
//{ divider: true, inset: true },
</script>

<style></style>
