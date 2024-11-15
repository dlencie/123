<template>
    <div class="search-view">
      <h1>비디오 검색</h1>
      <ArrowBack />
      <SearchInput class="search-input" @get-videos="getVideos" />
      <div v-if="isLoading">
        <LoadingIcon />
      </div>
      <div v-else>
        <SearchVideoList :video-list="videoList" />
      </div>
    </div>
  </template>
  
  <script setup>
  import SearchInput from "@/components/Search/SearchInput.vue";
  import SearchVideoList from "@/components/Search/SearchVideoList.vue";
  import LoadingIcon from "@/components/Common/LoadingIcon.vue";
  import ArrowBack from "@/components/Common/ArrowBack.vue";
  
  import { ref } from "vue";
  import axios from 'axios'
  import dayjs from "dayjs";
  
  const URL = "https://www.googleapis.com/youtube/v3"
  const API_KEY = "AIzaSyA3CulN6NGDWsoG2AoS_yiuUElgwwLjViw"  
  const videoList = ref([])
  const word = ref('')
  const isLoading = ref(false);
  
  const getVideos = (userInput) => {
    word.value = userInput
    isLoading.value = true
    axios
        .get(`${URL}/search`, {
          params: {
            key: API_KEY,
            part: "snippet",
            type: "video",
            q: word.value,
            maxResults: 10,
          },
        })
        .then((response) => {
            const parsedVideoList = response.data.items.map((item) => {
              return {
                videoId: item.id.videoId,
                title: item.snippet.title,
                description: item.snippet.description,
                publishTime: dayjs(item.snippet.publishTime).format("YYYY-MM-DD"),
                thumbnails: item.snippet.thumbnails,
              };
            });
            videoList.value=parsedVideoList;
            isLoading.value=false
          })
          .catch((error) => {
            console.error(error);
            isLoading.value=false
          });
  }
  
  </script>
  
  <style scoped>
  .content{
    margin-top: 2rem; 
  }
  
  .search-input {
    margin-bottom: 20px;
  }
  </style>