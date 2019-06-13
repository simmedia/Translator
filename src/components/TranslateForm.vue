<template>
  <div id="translateForm">
    <form @submit="formSubmit">
      <input type="text" v-model="textToTranslate" placeholder="Enter a word">
      <select v-model="language">
        <option value="sr">Serbian</option>
        <option value="en">English</option>
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
      language: ""
    };
  },
  created() {
    this.language = "sr";
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
  height: 30px;
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
