<template>
  <div>
    <SearchBar @termChange="onTermChange"></SearchBar>
  </div>
</template>

<script>
import SearchBar from "./components/SearchBar";
const API_KEY = "AIzaSyCTA9FQVy0wxDecGSo2raVEKf1iPLOuI7A";

export default {
  name: "App",
  components: {
    SearchBar
  },
  methods: {
    onTermChange: function(searchTerm) {
      console.log(searchTerm);
    }
  }
};
</script>