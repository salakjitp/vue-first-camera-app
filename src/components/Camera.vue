<template>
  <div class="camera">
      <video autoplay class="camera-display"></video>
      <div class="py-3">
        <button class="btn btn-info" v-on:click="$emit('take-picture')">SNAP</button>
      </div>
  </div>
</template>

<script>
export default {
    name: 'camera',
    methods:{
        init:() => {
            if ('mediaDevices' in navigator && 'getUserMedia' in navigator.mediaDevices) {
                let constraints = {
					video: {
                        width: {
                            min: 640,
                            ideal : 1280,
                            max: 1920
                        },
                        height: {
                            min: 720,
                            ideal: 720,
                            max:1080
                        }
					},
				};
				// const stream = await navigator.mediaDevices.getUserMedia(constraints);
                // const video = document.querySelector('video');

                navigator.mediaDevices.getUserMedia(constraints).then(stream=>{
                    const videoPlayer = document.querySelector("video");
                    videoPlayer.srcObject = stream;
                    videoPlayer.play();
                });

            }
            else{
                alert("Cannot get Media Devices.");
            }
        }
    },
    beforeMount: function () {
		this.init();
	}
}
</script>

<style lang="scss" scoped>
.camera {
    width: 100%;
    height: 100vh;
    margin-bottom:  25px;
    box-sizing: border-box;

    .camera-display{
        // display: block;
        width: 100%;
        max-width: 1280px;
        margin: 0 auto;
        background-color: #171717;
        box-shadow: 6px 6px 12px 0px rgba(0,0,0,0.35);
    }
}
</style>