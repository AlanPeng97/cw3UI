<template>
  <v-app>
    <v-app-bar
      app
      color="primary"
      dark
    >

      <v-spacer></v-spacer>

    </v-app-bar>

      <v-main :class="[setPosition]">
        <v-form>
            <v-container>
              <v-row class="justify-center">
                <v-col cols="8">
                  <v-text-field
                    v-model="message"
                    prepend-inner-icon="mdi-search-web"
                    :prepend-icon="icon"
                    filled
                    clear-icon="mdi-close-circle"
                    clearable
                    label="Search"
                    type="text"
                    @click:prepend="changeIcon"
                    @click:clear="clearMessage"
                  >
                      
                    <template v-slot:append-outer>
              
                      <v-btn
                        style="top: -14px"
                        fab
                        dark
                        @click="jumpSearch"
                      >
                        <v-icon>
                          mdi-text-box-search
                        </v-icon>
                      </v-btn>
                      </template>
                  </v-text-field>
                </v-col>
              </v-row>
            </v-container>
        </v-form>
            <router-view/>
      </v-main>
  </v-app>
</template>

<script>

export default {
  name: 'App',
  data: () => ({
      password: 'Password',
      show: false,
      message: 'Type to search',
      iconIndex: 0,
      setPosition: 'align-center',
      icons: [
        'mdi-emoticon',
        'mdi-emoticon-cool',
        'mdi-emoticon-dead',
        'mdi-emoticon-excited',
        'mdi-emoticon-happy',
        'mdi-emoticon-neutral',
        'mdi-emoticon-sad',
        'mdi-emoticon-tongue',
      ],
    }),

    computed: {
      icon () {
        return this.icons[this.iconIndex]
      },
    },

    methods: {
      jumpSearch () {
        this.setPosition = 'align-auto'
        this.$router.push('/about')
      },
      sendMessage () {
        this.resetIcon()
        this.clearMessage()
      },
      clearMessage () {
        this.message = ''
      },
      resetIcon () {
        this.iconIndex = 0
      },
      changeIcon () {
        this.iconIndex === this.icons.length - 1
          ? this.iconIndex = 0
          : this.iconIndex++
      },
    },
  components: {
  },

};
</script>

<style scoped>

</style>