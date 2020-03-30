<template>
  <li class="list-group-item d-flex" @click="onVideoSelect">
    <img class="mr-3" :src="thumbnailUrl" />
    {{ video.snippet.title }}
  </li>
</template>

<script>
export default {
  name: "VideoListItem",
  props: ["video"],
  methods: {
    onVideoSelect() {
      this.$emit("videoSelect", this.video);
    }
  },
  computed: {
    thumbnailUrl: function() {
      return this.video.snippet.thumbnails.default.url;
    }
  }
};
</script>

<style scoped>
li {
  cursor: pointer;
}
li:hover {
  background-color: #eee;
}
</style>
