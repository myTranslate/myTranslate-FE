<template>
  <v-app>
    <!-- create 2 card in one row -->
    <v-row class="center">
      <v-col cols="12" md="6">
        <v-card>
          <v-card-title primary-title>
            <div>
              <v-row>
                <v-col cols="15" md="10">
                <template>
                  <v-tabs>
                    <v-tab
                      v-for="item in languages"
                      :key="item"
                    >
                      {{ item }}
                    </v-tab>
                  </v-tabs>
                </template>
                </v-col>
                <v-col cols="15" md="1"><v-spacer></v-spacer></v-col>
                <v-col cols="15" md="1">
                <!-- button mdi switch -->
                <v-btn
                  v-if="languages.length > 1"
                  @click="switchLanguage"
                  icon
                >
                  <v-icon>mdi-swap-horizontal</v-icon>
                </v-btn>
                </v-col>
              </v-row>
            </div>
          </v-card-title>
          <v-card-text>
            <!-- create text area -->
            <v-textarea
               v-model="text"
                label="Message"
                counter
                maxlength="200"
                full-width
                single-line
            ></v-textarea>
          </v-card-text>
        </v-card>
      </v-col>
      <v-col cols="12" md="6">
        <v-card>
          <v-card-title primary-title>
            <div>
              <v-tabs>
                  <v-tab
                    v-for="item in languages"
                    :key="item"
                  >
                    {{ item }}
                  </v-tab>
                </v-tabs>
            </div>
          </v-card-title>
          <v-card-text>
            <v-container>
              {{ text }}
            </v-container>
          </v-card-text>
          <!-- add copy button on right corner -->
          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
              @click="copyText"
              icon
            >
              <v-icon>mdi-content-copy</v-icon>
            </v-btn>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
    <!-- Create primary button on right corner with name Translate -->
    <v-row>
      <v-spacer></v-spacer>
      <v-btn
        @click="translate"
        color="#27D3EB"
        dark
        large
        class="ma-2"
        right
      >
        Translate
      </v-btn>
    </v-row>
  </v-app>
</template>

<script>
  export default {
    data () { 
      return{
      languages : ['Indonesia', 'English', 'Arabic'],
      selectedLanguage : 'Indonesia',
      tobeTranslateLanguage : 'English',
      text : '',
    }
    },
    methods: {
      switchLanguage: function() {
        this.tobeTranslateLanguage = this.selectedLanguage;
        this.selectedLanguage = this.languages[0];
      },
      copyText: function() {
        navigator.clipboard.writeText(this.text);
      }
    }
  }
</script>

<style>
.center {
  display: flex;
  align-items: center;
  justify-content: center;
  transform: translate(0%, -10%);
}
.v-container {
  height: 100%;
  display: flex;
  max-width: 500px;
}
</style>
