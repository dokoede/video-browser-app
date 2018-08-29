<template>
    <ul class="list-group col-md-4">
<videolist-item v-for="singlevideo in videos" 
:video="singlevideo" v-bind:key="singlevideo.etag" 
@videoSelect="onVideoSelect"
>
</videolist-item>
    </ul>
</template>

<script>
import VideolistItem from "./VideoListItem.vue";
export default {
  name: "VideoList",
  components: {
    VideolistItem
  },

  props: ["videos"],
  methods: {
    onVideoSelect(video) {
      this.$emit("videoSelect", video);
    }
  }
};
</script>

<style></style>