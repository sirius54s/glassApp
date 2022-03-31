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
    

<!-- carousel -->
    <template>
  <v-carousel :show-arrows="false">
    <v-carousel-item
      v-for="(item,i) in imagenCarousel"
      :key="i"
      :src="item.src"
    ></v-carousel-item>
  </v-carousel>
</template>
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
       imagenCarousel: [
          {
            src: 'https://m.media-amazon.com/images/I/712pM1KqGhL._AC_SX466_.jpg',
          },
          {
            src: 'https://www.kindpng.com/picc/m/220-2208379_celular-desarmado-siendo-reparado-con-tarjeta-de-cmara.png',
          },
          {
            src: 'https://kyscomunicaciones.com/wp-content/uploads/2021/08/K41S-WEB-1.jpg',
          },
          {
            src: 'https://i.linio.com/p/c15ebf71725a73a7751f5cd0c3eedd01-product.jpg',
          },
        ]
    };
  },
};
</script>

<style></style>
