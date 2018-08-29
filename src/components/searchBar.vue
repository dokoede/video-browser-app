<template >
    <div>
       Search <input @input="onInput"/>
    </div>
</template>

<script>
export default {
  name: "searchBar",
  methods: {
    onInput: function(event) {
      this.$emit("termchange", event.target.value);
    }
  }
};
</script>

<style scoped>
input {
  width: 75%;
}

div {
  text-align: center;
  margin: 20px;
}
</style>

