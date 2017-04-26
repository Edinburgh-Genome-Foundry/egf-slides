<template lang='pug'>
.frontpage
  .content
    h1
      span.logo
      span EGF
      span.grey SLIDES
    h2 The slides of the Edinburgh Genome Foundry



    .thumbnails
      .box-card(v-for='slideshow in slideshows')
        router-link(:to='slideshow.infos.path' @click.native="click")
          .embedded-slideshow-container
            component(:is="slideshow", :embedded='true',
                      :keyboardNavigation='false',
                      :mouseNavigation='false')
        .caption
          h3 {{slideshow.infos.title}}
          p.thumbnail-description {{slideshow.infos.description}}
</template>

<script>
import slideshows from 'slideshows/slideshows'

export default {
  data: function () {
    return {
      slideshows: slideshows.list
    }
  },
  mounted: function () {
    console.log(this.slideshows)
    document.currentSlide = {}
  },
  methods: {
    click: function (evt) {
      evt.stopPropagation()
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style lang='scss' scoped>
@import "node_modules/eagle.js/src/themes/frontpage/frontpage";
.frontpage {
  .content {
    min-height: 1500px;
    p, h1, h2, h3 {
      font-family: 'Geometria', Helvetica, Arial, sans-serif !important;
    }
    h1 {
      font-size: 80px;
      font-weight: bold;
    }
    h2 {
      font-size: 25px;
      font-weight: bold;
    }
  }
}
.logo {
  display: block;
  margin: 0 auto;
  width: 160px;
  margin-bottom: 30px;
  height:160px;
  background-image: url(./logo.svg);
  background-size: contain;
  background-position: center bottom;
  background-repeat: no-repeat;
}
</style>
