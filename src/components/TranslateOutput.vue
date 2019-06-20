<template>
  <div id="translateOutput">
    <h2>{{translatedText}}</h2>
  </div>
</template>

<script>
export default {
  name: "TranslateOutput",
  props: ["translatedText"]
};
</script>

<style>
#translateOutput {
  margin: 60px auto 0px auto;
  padding: 10px;
  font-size: 1rem;
  width: 30%;
  text-align: left;
  color: #2c3e50;
  background: #ffffff;
}

@media (max-width: 600px) {
  #translateOutput {
    width: 80%;
  }
}
</style>
