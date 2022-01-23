<template>
  <select v-model="selected" class="select-input" @change="onChange">
    <option disabled value="0">Please select one</option>
    <option v-for="country in countries" :value="country.ID" :key="country.ID">
      {{ country.Country }}
    </option>
  </select>
</template>
<style >
.select-input{
    font-size: 1rem;
   margin-top: 1.5rem;
    font-weight: bold;
    cursor: pointer;
    width: 100%;
    background-color: rgb(95, 95, 240);
}
</style>
<script>
export default {
  name: "InputComponent",
  props: ["countries"],
  data() {
    return {
      selected: 0,
    };
  },
  methods: {
    onChange() {
      const country = this.countries.find((item) => 
        item.ID === this.selected
      );
      console.log(country);

      this.$emit('get-country',country)
    },
  },
};
</script>
