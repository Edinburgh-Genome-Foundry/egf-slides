<template lang='pug'>
.in-the-foundry
  .eg-slideshow

    slide.title-slide(leave='slideOutLeft')
      fullscreen-button

    slide(enter='slideInRight' leave='slideOutLeft', :steps='6')
      h3 The SynBio development cycle
      .whole-slide-svg
        include ./assets/design_build.svg

    slide(enter='slideInRight' leave='slideOutLeft', :steps='7')
      h3 The EGF Robotic Setup
      .whole-slide-svg
        include ./assets/robotic_plans.svg

    slide(enter='slideInRight' leave='slideOutLeft', :steps='14')
      h3 DNA Assembly
      eg-transition(enter='fadeIn' leave='fadeOut')
        eg-modal(v-if="step === 5")
          video.modal-video(autoplay loop)
            source(src="./assets/echo.webm" type="video/webm")
            source(src="./assets/echo.mp4" type="video/mp4")

      .whole-slide-svg
        include ./assets/how_we_assemble.svg

    slide(enter='slideInRight' leave='slideOutLeft', :steps='10')
      h3 Assembly Verification
      .whole-slide-svg
        include ./assets/how_we_verify.svg

    slide(enter='slideInRight' leave='slideOutLeft', :steps='4')
      h3 Assembly Testing
      .whole-slide-svg
        include ./assets/how_we_test.svg

    slide(enter='slideInRight' leave='slideOutLeft', :steps='8')
      h3 Software Integration
      .whole-slide-svg
        include assets/software_integration.svg
</template>

<script>
import eagle from 'eagle.js'
import FullScreenButton from './FullScreenButton'

require('./assets/title_photo.jpg')
export default {
  mixins: [ eagle.slideshow ],
  infos: {
    // These infos appear on the home page, below the slideshow's thumbnail
    title: 'In the Foundry',
    description: 'Slides for the Foundry\'s screens',
    path: 'in-the-foundry'
  },
  components: {
    'fullscreen-button': FullScreenButton
  }
}
</script>

<style lang='scss'>
@import url(https://fonts.googleapis.com/css?family=Raleway);
@import url(https://cdnjs.cloudflare.com/ajax/libs/animate.css/3.5.2/animate.min.css);

.in-the-foundry {

  @import 'node_modules/eagle.js/src/themes/base';
  .eg-slideshow{
    h3 {
      color: #544b96;
      font-size: 1.5em;
      margin-top: 0.4em;
    }

    font-family: 'Open Sans';
    background-color: white;
    .eg-slide{
      .eg-slide-content{
        width: 30em;
        max-width: 90%;
        margin: 0 auto;
      }
    }
  }
  .eg-slide-content{
    width: 25em;
    max-width: 80%;
    margin: 0 auto;
  }
}

.title-slide {
  background-image: url("./assets/title_photo.jpg");
  background-position: center center;
  background-size: cover;
}

.eg-fullscreen-button {
  position: absolute;
  left: 10px;
  bottom: 10px;
  color: white;
  font-size: 0.5em;
  font-weight: bold;
}

.whole-slide-svg {
  svg {
    width: 100% !important;
    height: auto !important;
  }
}

.eg-modal {
  background-color: rgba(0,0,0,0.9);
}
.modal-video {
  width: 60%;
  height: auto;
  margin-left: 20%;
  margin-top: 2em;
}

</style>
