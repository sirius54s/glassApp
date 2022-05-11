<template>
  <!-- default -->
  <div>
    <!-- banner de seguridad -->
    <v-banner two-line v-model="bannerSeguridad">
      <v-avatar slot="icon" color="orange accent-º  º º º º º º " size="40">
        <v-icon icon="mdi-lock" color="white"> mdi-lock </v-icon>
      </v-avatar>

      Plataforma protegida contra rastreo web.

      <template v-slot:actions>
        <v-btn text color="orange accent-3" @click="bannerSeguridad = false">
          Cerrar
        </v-btn>
        <v-btn text color="orange accent-3"> Mas detalles </v-btn>
      </template>
    </v-banner>

    <!-- carousel -->
    <template>
      <v-carousel :show-arrows="false">
        <v-carousel-item v-for="(item, i) in imagenCarousel" :key="i" :src="item.src"></v-carousel-item>
      </v-carousel>
    </template>
    <!-- breadcrumbs -->
    <template>
      <div class="ml-5 mt-1">
        <h3>inicio <v-icon color="orange accent-3" class="pb-1">mdi-arrow-down-circle</v-icon>
        </h3>

      </div>
    </template>
    <!-- card index -->
    <template>
      <div v-for="(itemDefault, index) in defaultData" :key="index">
        <h1 class="mt-2"></h1>
        <v-card class="mx-auto" max-width="344" outlined>
          <v-list-item three-line>
            <v-list-item-content>
              <div class="text-overline mb-4">{{ itemDefault.marca }}</div>
              <v-list-item-title class="text-h5 mb-1">
                {{ itemDefault.modelo }} compatiblidad
              </v-list-item-title>
              <v-list-item-subtitle>
                <v-list three-line>
                  <div v-for="(
                      itemCompatibilidad, index
                    ) in itemDefault.compatibilidad" :key="index">


                    <v-list-item>
                      <v-list-item-avatar>
                        <v-img :src="itemCompatibilidad.avatar"></v-img>
                      </v-list-item-avatar>

                      <v-list-item-content>
                        <v-list-item-title v-html="itemCompatibilidad.titulo"></v-list-item-title>

                        <v-list-item-subtitle v-html="itemCompatibilidad.usuario"></v-list-item-subtitle>
                      </v-list-item-content>
                    </v-list-item>
                  </div>
                </v-list>
              </v-list-item-subtitle>
            </v-list-item-content>

            <v-list-item-avatar tile size="80">
              <v-img
                src="https://www.productsvsprice.com/images/electronics/smartphone/samsung/samsung-galaxy-a12-smartphone-details-and-price-310492406.svg">
              </v-img>
            </v-list-item-avatar>
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

    imagenCarousel: [
      {
        src: "http://cdn.shopify.com/s/files/1/0090/5913/9662/products/KlMFp7dLT-MICA-11D-OFICIAL_e1752f3d-1b03-4b23-b483-adf10db50c83.jpg?v=1619702919",
      },
      {
        src: "https://feria.bandurria.pe/wp-content/uploads/2020/11/ELE-FS-0007-3.png",
      },
      {
        src: "https://promart.vteximg.com.br/arquivos/ids/896154-1000-1000/image-1f7a57adb1bf4cbb946b0b4158372831.jpg?v=637546462270500000",
      },
      {
        src: "https://s.alicdn.com/@sc04/kf/H29ac9f2bf32c41a9982a80d264a46180p.jpg",
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
            usuario: `raul011`,
          },
          {
            avatar: "https://cdn.vuetifyjs.com/images/lists/2.jpg",
            titulo: "samsung a03",
            usuario: `raul011`,
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
            usuario: `raul011`,
          },
          {
            avatar: "https://cdn.vuetifyjs.com/images/lists/2.jpg",
            titulo: "samsung a03",
            usuario: `raul011`,
          },
        ],
      },
    ],
  }),
};
//{ divider: true, inset: true },
</script>

<style>
</style>
