<template>
  <div>
    <Description v-if="status === 0"/>
    <SearchInput
      v-if="!showDetails"
      v-model="searchValue"
      @input="searchData"
      :value="searchValue"
      :status="status"
    />

    <div v-if="results && status === 1 && !showDetails" class="objects">
      <Object
        v-for="result in results"
        :key="result.data[0].nasa_id"
        :result="result"
        @click.native="openDetails(result)"
      />
    </div>
    <Details v-if="showDetails" :result="resultToDetails" @closeDetails="closeDetails"/>
  </div>
</template>

<script>
import Description from "./components/Description.vue";
import SearchInput from "./components/SearchInput.vue";
import Object from "./components/Object.vue";
import Details from "./components/Details.vue";
import axios from "axios";
import debounce from "lodash.debounce";

const API = "https://images-api.nasa.gov/search";

export default {
  name: "app",
  components: {
    Description,
    SearchInput,
    Object,
    Details
  },
  data() {
    return {
      searchValue: "",
      results: [],
      status: 0,
      showDetails: false,
      resultToDetails: null
    };
  },
  methods: {
    searchData: debounce(function() {
      axios
        .get(`${API}?q=${this.searchValue}&media_type=image`)
        .then(response => {
          this.results = response.data.collection.items;
          this.status = 1;
        })
        .catch(error => {
          console.log(error);
        });
    }, 500),
    openDetails(result) {
      this.showDetails = true;
      this.resultToDetails = result;
    },
    closeDetails() {
      this.showDetails = false;
    }
  }
};
</script>

<style lang="scss" scoped>
.objects {
  padding-left: 0.4rem;
  padding-right: 0.4rem;
  margin-left: auto;
  margin-right: auto;
  margin-top: 2.5rem;
  display: grid;
  grid-template-columns: auto auto auto;
  grid-gap: 1rem;
}
</style>
