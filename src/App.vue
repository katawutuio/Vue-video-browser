<template>
  <div class="container">
    <SearchBar @termChange="onTermChange"></SearchBar>
    <VideoList :videos="videos" @videoSelect="onVideoSelect"></VideoList>
  </div>
</template>

<script>
import axios from "axios";
import SearchBar from "./components/SearchBar";
import VideoList from "./components/VideoList";

const API_KEY = "AIzaSyCTA9FQVy0wxDecGSo2raVEKf1iPLOuI7A";

export default {
  name: "App",
  components: {
    SearchBar,
    VideoList
  },
  data: function() {
    return {
      videos: []
    };
  },
  methods: {
    onVideoSelect(video) {
      console.log(video);
    },
    onTermChange: function(searchTerm) {
      axios
        .get("https://www.googleapis.com/youtube/v3/search", {
          params: {
            key: API_KEY,
            type: "video",
            part: "snippet",
            q: searchTerm
          }
        })
        .then(response => {
          this.videos = response.data.items;
        });
    }
  }
};
</script>
