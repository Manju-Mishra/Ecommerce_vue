<template>
  <div>
     <router-view></router-view>
    <section id="slider">
      <!--slider-->
      <div class="container">
        <div class="row">
          <div class="col-sm-12">
            <div
              id="slider-carousel"
              class="carousel slide"
              data-ride="carousel"
            >
              <ol class="carousel-indicators">
                <li
                  data-target="#slider-carousel"
                  data-slide-to="0"
                  class="active"
                ></li>
                <li data-target="#slider-carousel" data-slide-to="1"></li>
                <li data-target="#slider-carousel" data-slide-to="2"></li>
              </ol>

              <div class="carousel-inner">
                <div v-for="(banner, index) in banners" v-bind:key="index" v-bind:class="index == 0 ? 'item active' : 'item'">
                  <div class="col-sm-6">
                    <h1><span>E</span>-SHOPPER</h1>
                    <h2>{{banner.caption}}</h2>
                    <p>
                      Lorem ipsum dolor sit amet, consectetur adipisicing elit,
                      sed do eiusmod tempor incididunt ut labore et dolore magna
                      aliqua.
                    </p>
                    <button type="button" class="btn btn-default get">
                      Get it now
                    </button>
                  </div>
                  <div class="col-sm-6">
                    <img
                       :src="'http://127.0.0.1:8000/uploads/'+banner.image"
                      class="girl img-responsive"
                      alt="" style="margin-top:100px"
                    />
                  </div>
                </div>
              
              </div>

              <a
                href="#slider-carousel"
                class="left control-carousel hidden-xs"
                data-slide="prev"
              >
                <i class="fa fa-angle-left"></i>
              </a>
              <a
                href="#slider-carousel"
                class="right control-carousel hidden-xs"
                data-slide="next"
              >
                <i class="fa fa-angle-right"></i>
              </a>
            </div>
          </div>
        </div>
      </div>
    </section>
    <!--/slider-->

   
  </div>
</template>

<script>
import axios from "axios";
export default {
  name: "Slider",
 
   data(){
      return{
         banners:null,
      };
   },

 mounted(){
    const url="http://127.0.0.1:8000/api/banner";
    axios.get(url).then((res)=>
    {
      this.banners=res.data;
      console.log(res.data.banners);
    })
 },
    
  
};
</script>

<style>
</style>