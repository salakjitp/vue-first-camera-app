<template>
  <div class="camera">
      <video autoplay class="camera-display"></video>
      <button class="btn btn-info snap mt-3" v-on:click="$emit('take-picture')">SNAP</button>
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
    width: 100vw;
    height: 100vh;
    padding:  25px;
    box-sizing: border-box;

    .camera-display{
        display: block;
        width: 100%;
        max-width: 1280px;
        margin: 0 auto;
        background-color: #171717;
        box-shadow: 6px 6px 12px 0px rgba(0,0,0,0.35);
    }

    // .snap{
    //     display: block;
    //     margin: 0 auto;

    //     cursor: pointer;

    // }
}
</style>