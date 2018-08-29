<template>
<div v-if='video' class="col-md-8">
    <div class="embed-responsive embed-responsive-16by9">
        <iframe class="embed-responsive-item" :src="videoUrl" ></iframe>
    </div>
    <div class= "details">
    <h4>{{video.snippet.title}}</h4>
    <p>{{video.snippet.description}}</p>
    </div>
    </div>
</template>

<script>
export default {
  name: "VideoDetail",
  props: ["video"],
  computed: {
    videoUrl() {
      //   const videoId = this.video.id.videoId;
      const { videoId } = this.video.id;
      //   return "https://www.youtube.com/embeb/" + videoId;
      return `https://www.youtube.com/embed/${videoId}`;
    }
  }
};
</script>

<style scoped>
.details {
  padding: 10px;
  border: 1.2px solid rgb(221, 221, 221);
  border-radius: 4px;
  margin-top: 10px;
}
</style>
