<template>
<v-conatiner>
  <v-footer
    dark
    padless
  >
    <v-card
      flat
      tile
      class="indigo lighten-1 white--text text-center"
    >
      <v-card-text>
        <v-btn
          v-for="icon in icons"
          :key="icon"
          class="mx-4 white--text"
          icon
          centered
        >
          <v-icon size="24px">{{ icon }}</v-icon>
        </v-btn>
      </v-card-text>

      <v-card-text class="white--text pt-0">
        Lorem ipsum dolor sit amet consectetur adipisicing elit. Ad provident deserunt exercitationem animi veniam assumenda nobis autem sunt dolorem porro fuga cupiditate est dolor, accusamus officiis deleniti! Reprehenderit, quos aut?
      </v-card-text>

      <v-divider></v-divider>

      <v-card-text class="white--text">
        {{ new Date().getFullYear() }} — <strong>Zapatos</strong>
      </v-card-text>
    </v-card>
  </v-footer>
  </v-conatiner>
</template>

<script>
  export default {
    data: () => ({
      icons: [
        'mdi-facebook',
        'mdi-twitter',
        'mdi-linkedin',
        'mdi-instagram',
      ],
    }),
  }
</script>

<style lang="css">
/* .pie{
  background: #aaaaaa;
  } */
</style>