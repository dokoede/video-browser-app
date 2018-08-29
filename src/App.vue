<template>
<div class="container">
   <searchBar @termchange="onTermChange"></searchBar>
    <div class ="row">
      <VideoDetail :video="selectedVideo"></VideoDetail>
    <VideoList class="container" @videoSelect='onVideoSelect' v-bind:videos="videos"></VideoList>
    
    </div>
</div>
</template>


<script>
import axios from "axios";
import searchBar from "./components/searchBar";
import VideoList from "./components/VideoList";
import VideoDetail from "./components/VideoDetail";

const API_KEY = "";

export default {
  name: "App",
  components: {
    searchBar: searchBar,
    VideoList,
    VideoDetail
  },

  data() {
    return { videos: [], selectedVideo: null };
  },
  methods: {
    onVideoSelect(video) {
      this.selectedVideo = video;
    },
    onTermChange(searchTerm) {
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