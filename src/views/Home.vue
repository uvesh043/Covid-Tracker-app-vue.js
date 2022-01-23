<template>
  <div class="home">
    <div v-if="!loading">
      <DataTittle :text="title" :dataDate="dataDate" />
      <DataBoxes :status="status" />
      <InputComponent @get-country="setCountryData" :countries="countries" />
      <button
        class="clear-country-btn"
        @click="clearCountry"
        v-if="status.Country"
      >
        Clear Country
      </button>
    </div>
    <div v-else class="loading">
      <img src="../assets/loading-gif.gif" />
    </div>
  </div>
</template>

<script>
// @ is an alias to /src
import DataTittle from "../components/DataTittle.vue";
import DataBoxes from "../components/DataBoxes.vue";
import InputComponent from "../components/InputComponent.vue";

export default {
  name: "Home",
  components: {
    DataTittle,
    DataBoxes,
    InputComponent,
  },
  data() {
    return {
      loading: true,
      title: "Global",
      dataDate: "",
      status: {},
      countries: [],
      loadingImage: require("../assets/loading-gif.gif"),
    };
  },
  methods: {
    async fetchCovidData() {
      const response = await fetch("https://api.covid19api.com/summary");
      const data = await response.json();
      console.log("Tgus is:", data);

      return data;
    },
    setCountryData(country) {
      (this.status = country), (this.title = country.Country);
    },
    async clearCountry() {
      this.loading = true;
      const data = await this.fetchCovidData();
      this.title = "Global";
      this.status = data.Global;
      this.loading = false;
    },
  },
  async created() {
    const data = await this.fetchCovidData();
    this.dataDate = data.Date;
    this.status = data.Global;
    this.countries = data.Countries;
    this.loading = false;
  },
};
</script>
<style >
.clear-country-btn {
  padding: 0.8rem;
  border-radius: 0.4rem;
  background-color: rgb(7, 182, 7);
  margin-top: 0.5rem;
}
.loading{

display: flex;
justify-content: center;
align-items: center;

}
</style>