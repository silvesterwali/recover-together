<template>
  <v-sheet class="pa-4" color="transparent">
    <v-row justify="center">
      <v-col cols="12" sm="6" lg="4" md="4" order-lg="last">
        <v-form>
          <v-card elevation="1" min-height="400">
            <v-card-title>
              <span class="headline mx-auto">Login</span>
            </v-card-title>
            <v-card-text class="pa-8">
              <v-text-field
                label="Email"
                class="my-3"
                outlined
                rounded
              ></v-text-field>
              <v-text-field
                label="Password"
                class="my-3"
                type="password"
                rounded
                outlined
              ></v-text-field>
              <v-checkbox label="Remember me" class="mt-1"></v-checkbox>
            </v-card-text>
            <v-card-actions class="pl-8 pr-8 pb-10">
              <v-btn color="primary" class="mb-10" x-large block rounded
                >Login</v-btn
              >
            </v-card-actions>
          </v-card>
        </v-form>
      </v-col>
      <v-col v-if="$vuetify.breakpoint.mdAndUp" cols="12" sm="8" lg="8" md="8">
        <v-sheet
          color="transparent"
          class="white--text d-flex align-center justify-center"
          min-height="420"
        >
          <span class="mx-auto">
            <h2 class="display-2 mb-10">Recover Together</h2>
            Lorem ipsum dolor sit, amet consectetur adipisicing elit. Ut quae
            nemo odio, quas veritatis voluptatem facere error laboriosam,
            doloremque perferendis ratione dignissimos temporibus odit autem
            saepe laborum culpa. Facilis, molestiae?
          </span>
        </v-sheet>
      </v-col>
    </v-row>
  </v-sheet>
</template>

<script>
export default {
  layout: 'login',
}
</script>

<style lang="scss" scoped>
</style>