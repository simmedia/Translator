<template>
  <div id="app">
    <img src="./assets/logo.png" width="70px" alt="">
    <h1>Translator</h1>
    <TranslateForm @formSubmit="translateText" />
    <TranslateOutput v-if="translatedText" v-text="translatedText" />

  </div>
</template>

<script>
import TranslateForm from "./components/TranslateForm"
import TranslateOutput from "./components/TranslateOutput"

export default {
  name: "app",
  components: {
    TranslateForm,
    TranslateOutput
  },
  data() {
    return {
      translatedText: ''
    }
  },
  methods: {
    translateText(text,language) {
      this.$http.get('https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190613T214744Z.88416eb5dc9c683f.709a71a569d29592da19d65b86b8e609e04e3151&lang='+language+'&text='+text)
      .then((response)=> {
        this.translatedText = response.body.text[0]
      })
    }
  }
};


</script>

<style>
body {
  background: #ff6b81;
  height: 100vh;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  margin-top: 100px;
}

img {
  position: absolute;
  top: 20px;
  left: 30px;
}

@media(max-width: 600px) {
  img {
    width: 50px;
  }
}

</style>
