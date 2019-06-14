<template>
  <div id="app">
    <img src="./assets/logo.png" width="70px" alt>
    <div class="wrapper">
      <h1>Translator</h1>
      <TranslateForm @formSubmit="translateText"/>
      <TranslateOutput v-if="translatedText" v-text="translatedText"/>
    </div>
    <footer>
      <h3>
        &copy; made by
        <a
          href="https://www.linkedin.com/in/simadurlan92/"
          target="_blank"
        >Stefan Simic</a>
      </h3>
    </footer>
  </div>
</template>

<script>
import TranslateForm from "./components/TranslateForm";
import TranslateOutput from "./components/TranslateOutput";

export default {
  name: "app",
  components: {
    TranslateForm,
    TranslateOutput
  },
  data() {
    return {
      translatedText: ""
    };
  },
  methods: {
    translateText(text, language) {
      this.$http
        .get(
          "https://translate.yandex.net/api/v1.5/tr.json/translate?key=trnsl.1.1.20190613T214744Z.88416eb5dc9c683f.709a71a569d29592da19d65b86b8e609e04e3151&lang=" +
            language +
            "&text=" +
            text
        )
        .then(response => {
          this.translatedText = response.body.text[0];
        });
    }
  }
};
</script>

<style>
* {
  margin: 0;
  padding: 0;
  box-sizing: border-box;
}
body {
  background: #ff6b81;
  box-sizing: border-box;
}
#app {
  font-family: "Avenir", Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #fff;
  padding-top: 100px;
  height: 100%;
  box-sizing: border-box;
}

img {
  position: absolute;
  top: 20px;
  left: 30px;
}

footer {
  width: 80%;
  position: absolute;
  bottom: 0;
  left: 50%;
  transform: translateX(-50%);
}

footer h3 {
  padding: 10px;
  border-top: 1px solid #fff;
  text-align: center;
}

footer a {
  color: #2c3e50;
  text-decoration: none;
  transition: all 0.3s ease;
}

footer a:hover {
  color: #fff;
  border-bottom: 1px solid #fff;
}

@media (max-width: 600px) {
  img {
    width: 50px;
  }

  footer {
    position: absolute;
    left: 50%;
    top: 93%;
    margin: 0 auto;
    transform: translateX(-50%);
  }
}
</style>
