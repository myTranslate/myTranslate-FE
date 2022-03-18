<template>
  <v-app>
    <!-- create 2 card in one row -->
    <v-row class="center">
      <v-col cols="12" md="6">
        <v-card>
          <v-card-title primary-title>
            <div>
              <h3 class="headline mb-0">Card Title</h3>
              <div>
                <v-icon>star</v-icon>
                <v-icon>star</v-icon>
                <v-icon>star</v-icon>
                <v-icon>star</v-icon>
                <v-icon>star</v-icon>
              </div>
            </div>
          </v-card-title>
          <v-card-text>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit.
            Mauris sagittis pellentesque lacus eleifend lacinia...
          </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="12" md="6">
        <v-card>
          <v-card-title primary-title>
            <div>
              <h3 class="headline mb-0">Card Title</h3>
              <div>
                <v-icon>star</v-icon>
                <v-icon>star</v-icon>
                <v-icon>star</v-icon>
                <v-icon>star</v-icon>
                <v-icon>star</v-icon>
              </div>
            </div>
          </v-card-title>
          <v-card-text>
            Lorem ipsum dolor sit amet, consectetur adipiscing elit.
            Mauris sagittis pellentesque lacus eleifend lacinia...
          </v-card-text>
        </v-card>
      </v-col>
    </v-row>
  </v-app>
</template>

<script>
  export default {
    data: () => ({
      reveal: false,
    }),
  }
</script>

<style>
.center {
  display: flex;
  align-items: center;
  justify-content: center;
  transform: translate(0%, -10%);
}
</style>
