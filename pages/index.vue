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
                  <v-tabs
                    v-model="selectedLanguage"
                  >
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
                label="put your text here"
                counter
                maxlength="500"
                full-width
                single-line
            ></v-textarea>
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
      <v-col cols="12" md="6">
        <v-card>
          <v-card-title primary-title>
            <div>
              <v-tabs
              v-model="tobeTranslateLanguage"
              >
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
            <v-textarea
            v-model="result"
            readonly
            >
              {{ result }}
            </v-textarea>
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
      languages : ['Indonesia', 'English', 'Arabic', 'Chinese'],
      index_langueages : ['id', 'en', 'ar', 'zh'],
      selectedLanguage : 1,
      tobeTranslateLanguage : 0,
      text : '',
      result: '',
    }
    },
    methods: {
      switchLanguage: function() {
        var temp = this.selectedLanguage;
        this.selectedLanguage = this.tobeTranslateLanguage;
        this.tobeTranslateLanguage = temp;
      },
      copyText: function() {
        navigator.clipboard.writeText(this.text);
      },
      translate: async function() {
        this.result = '';
        if(this.text == '') {
          alert('Please enter text to translate');
        } else {
          if(this.selectedLanguage == this.tobeTranslateLanguage){
            this.result = this.text;
          } else {
            var url = 'https://translate.googleapis.com/translate_a/single?client=gtx&sl=' + this.index_langueages[this.selectedLanguage] + '&tl=' + this.index_langueages[this.tobeTranslateLanguage] + '&dt=t&q=' + this.text;
            var response = await fetch(url);
            var data = await response.json();
            this.result = data[0][0][0];
          }
        }
      }
    }
  }
</script>

<style>
.center {
  display: flex;
  align-items: center;
  justify-content: center;
}
.v-container {
  height: 100%;
  display: flex;
  max-width: 500px;
}
</style>
