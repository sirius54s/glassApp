<template>
  <!-- default -->
  <div>
    <!-- banner de seguridad -->
    <v-banner two-line v-model="bannerSeguridad">
      <v-avatar slot="icon" color="orange accent-º  º º º º º º " size="40">
        <v-icon icon="mdi-lock" color="white"> mdi-lock </v-icon>
      </v-avatar>

      Nuestra plataforma esta protejida contra rastreo web.

      <template v-slot:actions>
        <v-btn
          text
          color="orange accent-1"
          @click="bannerSeguridad = false"
        >
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
        <v-breadcrumbs :items="items" divider="/"></v-breadcrumbs>
      </div>
    </template>
    <!-- card index -->
    <template>
      <v-card class="mx-auto" max-width="344" outlined>
        <v-list-item three-line>
          <v-list-item-content>
            <div class="text-overline mb-4">Samsung</div>
            <v-list-item-title class="text-h5 mb-1">
              A12 compatiblidad
            </v-list-item-title>
            <v-list-item-subtitle>
             <v-list three-line>
      <template v-for="(item, index) in itemList">
        <v-subheader
          v-if="item.header"
          :key="item.header"
          v-text="item.header"
        ></v-subheader>

        <v-divider
          v-else-if="item.divider"
          :key="index"
          :inset="item.inset"
        ></v-divider>

        <v-list-item
          v-else
          :key="item.title"
        >
          <v-list-item-avatar>
            <v-img :src="item.avatar"></v-img>
          </v-list-item-avatar>

          <v-list-item-content>
            <v-list-item-title v-html="item.title"></v-list-item-title>
            <v-list-item-subtitle v-html="item.subtitle"></v-list-item-subtitle>
          </v-list-item-content>
        </v-list-item>
      </template>
    </v-list>
            </v-list-item-subtitle
            >
          </v-list-item-content>

          <v-list-item-avatar tile size="80">
            <v-img
              src="https://www.productsvsprice.com/images/electronics/smartphone/samsung/samsung-galaxy-a12-smartphone-details-and-price-310492406.svg"
            >
            </v-img
          ></v-list-item-avatar>
        </v-list-item>

        <v-card-actions>
          <v-btn outlined rounded text> Button </v-btn>
        </v-card-actions>
      </v-card>
    </template>
  </div>
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
      itemList: [
        { header: 'usuarios' },
        {
          avatar: 'https://cdn.vuetifyjs.com/images/lists/1.jpg',
          title: 'samsung a02',
          subtitle: `usuario: Pedro421`,
        },
        { divider: true, inset: true },
        {
          avatar: 'https://cdn.vuetifyjs.com/images/lists/2.jpg',
          title: 'samsung a03',
          subtitle: `usuario: raul011`,
        }
      ]

    };
  },
};
</script>

<style></style>
