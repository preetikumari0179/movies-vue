<template>
    <div>
    <div class="movie-content">
    <div class="title">
    <span >
        {{title}}
    </span>
    </div>
        <Carousel :perPage="perPage">
            <Slide v-for="(item, index) in items" :key="index">
                <movie-card :movie="item">
                </movie-card>
            </Slide>
        </Carousel>
    </div>
    </div>
</template>
<script>
import { Carousel, Slide } from 'vue-carousel';

export default {
  components: {
    Carousel,
    Slide,
    'movie-card': () => import('./movieCard')
  },
  props: {
      items: {
          type: Array,
          required: true,
      },
      title: {
          type: String,
          required: true
      },
      perPage: {
          type: Number,
          default: 4,
      }
  }
}
</script>
<style lang="css">
    .title {
  font-family: Helvetica;
  font-size: 16px;
  font-weight: bold;
  font-style: normal;
  font-stretch: normal;
  line-height: normal;
  letter-spacing: normal;
  color: #69c297;
  float: left;
  padding: 16px
    }
    .movie-content {
         background-color: #24242c;
         padding: 5px;
    margin: 20px 0px 100px 10px;
    display: block
    }
    .VueCarousel {
        display: block !important
    }
</style>