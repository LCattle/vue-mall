<template>
  <div class="hello">
    <h1>{{ msg }}</h1>
    <div>  
        <swiper :options="swiperOption"  ref="mySwiper">  
            <!-- 这部分放你要渲染的那些内容 -->  
            <swiper-slide v-for="item in items"> 
              <img :src=item />
            </swiper-slide>  
            <!-- 这是轮播的小圆点 -->  
            <div class="swiper-pagination" slot="pagination"></div>  
        </swiper>  
    </div>  
  </div>
</template>

<script>
 import { swiper, swiperSlide } from 'vue-awesome-swiper';
    export default {  
        components: {  
            swiper,  
            swiperSlide  
        },  
        
        data() {  
            return {  
                msg: 'Hello Cattle! Wecomle to you web App!',
                items: ['./../../static/images/cccc.jpg', './../../static/images/cccc.jpg'],
                swiperOption: {  
                //是一个组件自有属性，如果notNextTick设置为true，组件则不会通过NextTick来实例化swiper，也就意味着你可以在第一时间获取到swiper对象，假如你需要刚加载遍使用获取swiper对象来做什么事，那么这个属性一定要是true  
                notNextTick: true,  
                pagination: '.swiper-pagination',  
                slidesPerView: 'auto',
                autoplayDisableOnInteraction: false,
                autoplay: 5000,  
                centeredSlides: true,  
                paginationClickable: true,  
                spaceBetween: 30,  
                onSlideChangeEnd: swiper => {  
                    //这个位置放swiper的回调方法  
                    this.page = swiper.realIndex+1;  
                    this.index = swiper.realIndex;  
                }  
            }
          }
        },  
        //定义这个sweiper对象  
        computed: {  
  
            swiper() {  
              return this.$refs.mySwiper.swiper;  
            }  
        },  
        mounted () {  
            //这边就可以使用swiper这个对象去使用swiper官网中的那些方法  
            this.swiper.slideTo(0, 0, false);  
        }  
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
body{
  width: 100vw;
}
h1, h2 {
  font-weight: normal;
}

ul {
  list-style-type: none;
  padding: 0;
}

li {
  display: inline-block;
  margin: 0 10px;
}

a {
  color: #42b983;
}
.banner-item{
  width: 100%;
  height: 150px;

}
</style>

