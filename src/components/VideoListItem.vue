<template>
<li @click="onVideoSelect" class="list-group-item media">
  <img class="mr-3" :src="thumbnailsUrl"/>
  <div class="media-body">
     <h5 class="mt-0 mb-1"> {{ video.snippet.title }}</h5>
  </div>
</li>

</template>

<script>
export default {
  name: "VideoListItem",
  props: ["video"],
  computed: {
    thumbnailsUrl() {
      return this.video.snippet.thumbnails.default.url;
    }
  },
  methods: {
    onVideoSelect() {
      this.$emit("videoSelect", this.video);
    }
  }
};
</script>

<style scoped>
li {
  display: flex;
  cursor: pointer;
}

li:hover {
  background-color: #eee;
}

img:hover {
  transform: scale(1.1);
}
</style>
