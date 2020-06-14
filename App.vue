<template>
  <div id="app">
     <carousel
      @next="next"
      @prev="prev">
         <carouselslide v-for="(slide, index) in slides" 
        :key="slide"
        :index="index"
        :visibleSlide="visibleSlide">

          <carouselslideimage 
            :slides="slides"
            :index="index">
          </carouselslideimage>
        
         </carouselslide>
     </carousel>
  </div>
</template>

<script>

import carousel from './components/carousel';
import carouselslide from './components/carousel-slide';
import carouselslideimage from './components/carousel-slide-image';

export default {
  data(){
   return {
        slides: [
          {
              category1: {img:'https://picsum.photos/id/1003/250/250', description:'Animals'},
              category2: {img:'https://picsum.photos/id/1075/250/250', description:'Buildings'},
              category3: {img:'https://picsum.photos/id/1080/250/250', description:'Fruits'},
              category4: {img:'https://picsum.photos/id/1018/250/250', description:'Nature'},
          },
          {
              category5: {img:'https://picsum.photos/id/1066/250/250', description:'Family'},
              category6: {img:'https://picsum.photos/id/1070/250/250', description:'Cars'},
              category7: {img:'https://picsum.photos/id/4/250/250', description:'Office'},
              category8: {img:'https://picsum.photos/id/407/250/250', description:'Celebration'},
          },
    ],
      visibleSlide: 0, 
      

    }
  },
      components: {
        carousel,
        carouselslide,
        carouselslideimage
  }, 
  methods:{
      next(){
          if(this.visibleSlide >=  this.slides.length - 1){
              this.visibleSlide = 0;
          }
          else{
            this.visibleSlide++;
          }
      }, 

      prev(){
           if(this.visibleSlide <=  0){
              this.visibleSlide = this.slides.length - 1;
          }
          else{
            this.visibleSlide--;
          }
      }
  }
}
</script>

<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
