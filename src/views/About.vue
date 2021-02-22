<template>
  <div>
    <v-container>
     <v-row
     v-for="n in 4"
     :key = 'n'
     >
       <v-col>
        <v-skeleton-loader
          class="mx-auto"
          max-width="1000"
          type="card"
        ></v-skeleton-loader>
      </v-col>
     </v-row>
    </v-container>
  </div> 
</template>

<script>
  export default {
    // Vuetify components provide
    // a theme variable that is
    // used to determine dark
    inject: {
      theme: {
        default: { isDark: false },
      },
    },
  }
</script>
