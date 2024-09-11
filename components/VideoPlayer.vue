<!-- <template>
    <div class="video-container">
      <video
      ref="videoElement"
      :src="videoSrc"
      class="video-player"
      controls
      autoplay
      muted
      @play="onPlay"
      @pause="onPause"
      >
        Your browser does not support the video tag.
      </video>
    </div>
  </template>
  
  <script lang="ts" setup>
  // Props
  const props = defineProps<{
    videoUrl: string;
  }>();
  
  // Refs
  const videoElement = ref<HTMLVideoElement | null>(null);
  const videoSrc = ref<string>("@/assets/img/election-videos.mp4");
  

// Methods
const onPlay = () => {
  console.log('Video is playing...');
};

const onPause = () => {
  console.log('Video is paused.');
};

// Lifecycle hooks
onMounted(() => {
  if (videoElement.value) {
    // Autoplay the video when mounted
    videoElement.value.play().catch(error => {
      console.error('Autoplay was prevented:', error);
    });
  }
});

onBeforeUnmount(() => {
  if (videoElement.value) {
    console.log('Cleaning up video element...');
    videoElement.value.pause();
  }
});
  </script>
  
  <style scoped>
  .video-container {
    max-width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .video-player {
    width: 100%;
    height: auto;
  }
  </style>
   -->

   <template>
    <div class="video-container">
      <video
        ref="videoElement"
        :src="videoSrc"
        class="video-player"
        controls
        autoplay
        muted
        @play="onPlay"
        @pause="onPause"
      >
        Your browser does not support the video tag.
      </video>
    </div>
  </template>
  
  <script lang="ts" setup>
  import { ref, onMounted, onBeforeUnmount } from 'vue';
  
  // Refs
  const videoElement = ref<HTMLVideoElement | null>(null);
  const videoSrc = ref<string>('/election.mp4');  // Change to public folder path
  
  // Methods
  const onPlay = () => {
    console.log('Video is playing...');
  };
  
  const onPause = () => {
    console.log('Video is paused.');
  };
  
  // Lifecycle hooks
  onMounted(() => {
    if (videoElement.value) {
      videoElement.value.play().catch((error) => {
        console.error('Autoplay was prevented:', error);
      });
    }
  });
  
  onBeforeUnmount(() => {
    if (videoElement.value) {
      videoElement.value.pause();
    }
  });
  </script>
  
  <style scoped>
  .video-container {
    max-width: 100%;
    display: flex;
    justify-content: center;
    align-items: center;
  }
  
  .video-player {
    width: 100%;
    height: auto;
  }
  </style>
  