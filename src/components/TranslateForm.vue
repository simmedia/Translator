<template>
  <div id="translateForm">
    <form @submit="formSubmit">
      <input type="text" v-model="textToTranslate" placeholder="Enter a word">
      <select v-model="language">
        <option v-for="(language,index) in allLanguages" :key="index" class="option" :value="language.value">
          {{language.name}}
        </option>









  

<!-- 
        <option class="option" value="en">English</option>
        <option class="option" value="de">German</option>
        <option class="option" value="fr">French</option>
        <option class="option" value="cs">Chech</option>
        <option class="option" value="es">Spanish</option>
        <option class="option" value="it">Italian</option>
        <option class="option" value="ru">Russian</option> -->
      </select>
      <input type="submit" value="Translate">
    </form>
  </div>
</template>

<script>
export default {
  name: "TranslateForm",
  data() {
    return {
      textToTranslate: "",
      language: "",

      allLanguages: [
        {name: 'Chech', value: 'cs'},
        {name: 'English', value: 'en'},
        {name: 'French', value: 'fr'},
        {name: 'German', value: 'de'},
        {name: 'Spanish', value: 'es'},
        {name: 'Italian', value: 'it'},
        {name: 'Russian', value: 'ru'},
      ]
    };
  },
  created() {
    this.language = "en";
  },
  methods: {
    formSubmit(each) {
      this.$emit("formSubmit", this.textToTranslate, this.language);
      each.preventDefault();
    }
  }
};
</script>

<style>
select {
  padding: 5px;
  font-size: 1rem;
  height: 40px;
  color: #2c3e50;
  border: none;
  background: #fff;
}

form {
    flex: 8;
}

select:focus {
    border: none;
    outline: none;
}

input[type="text"] {
  border: none;
  border-right: 1px solid #2c3e50;
  outline: none;
  width: 40%;
  padding: 5px;
  height: 40px;
  color: #2c3e50;
  font-size: 1rem;
  margin-top: 60px;
}

input[type="submit"] {
  display: none;
}

@media(max-width: 600px) {
    input[type="text"] {
        display: block;
        border: none;
        width: 80%;
        margin: 60px auto 20px auto;
    }

}
</style>
