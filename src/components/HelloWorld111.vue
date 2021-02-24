<template>
    <main id="main">
        <div class="slider">
            <div class="window">
                <div id="btn-left"></div>
                <ul class="container" :style="containerStyle">
                    <li>
                        <img :src="sliders[sliders.length-1].img">
                    </li>
                    <li v-for="(p,i) of sliders" :key="i">
                        <img :src="p.img">
                    </li>
                    <li>
                        <img :src="sliders[0].img"> <!--和第一张图一样,用于切换-->
                    </li>
                </ul>
                <ul class="dots"> <!--ul-idxs-->
                    <li v-for="(dot,i) of sliders" :key="i" :class="{dotted:i===(currentIndex-1)}" class="active"></li>
                </ul>
                <div id="btn-right"></div>
            </div>
        </div>
        <img src="" alt="">
    </main>
</template>

<script>
import MyHeader from "./MyHeader"
export default {
    name: 'slider',
    data(){
        return {
            sliders:[
                {img:'../img/carousel/banner1.jpg'},
                {img:'../img/carousel/banner2.jpg'},
                {img:'../img/carousel/banner3.jpg'},
                {img:'../img/carousel/banner4.jpg'},
            ],
            currentIndex:1,
            distance:-600
        }
    },
    computed:{
        containerStyle(){
            return {
                transform:`translate3d(${this.distance}px,0,0)`
            }
        }
    }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
    *{margin:0;padding:0;}
    #main{width:100%;}
    .slider{
        width:100%;height:408px;
        overflow: hidden;
        position:relative;
        float: left;
    }
    #bannerbox #bannerwidth #switch{
        margin-top:20px;
    }
    #btn-left{
        left:10px;
        background-image: url(../img/carousel/left.png);
    }
    #btn-right{
        right:10px;
        background-image: url(../img/carousel/right.png);
    }
    .container{list-style:none;}
    .container.transition{
        transition:all .5s linear;
    }
    .container>li{
        width:1520px;height:500px;
        float:left;
    }
    .container img{
        width:100%;height:100%;
    }
    #ul-idxs{ /*整排圆点宽度*/
        width:250px;
        margin:0 auto;
        list-style: none;
        position:absolute;
        bottom:25px;
        left:50%;
        margin-left:-100px;
    }
    #ul-idxs>li{ /*小方块*/
        float: left;
        width:30px;height:2px;
        background-color:rgb(255, 255, 255,.5);
        margin:0 5px;
        cursor:pointer;
    }
    #ul-idxs>li.active{
        background-color:#8391A5;
    }
    #btn-left,#btn-right{
        width:30px;height:30px;
        position:absolute;
        top:50%;
        background-repeat: no-repeat;
        background-position: center;
        background-color:rgb(255, 255, 255,.2);
        opacity: 0.5;
        border-radius:50%;
        cursor: pointer;
    }
    #btn-left{
        left:10px;
        background-image: url(../img/carousel/left.png);
    }
    #btn-right{
        right:10px;
        background-image: url(../img/carousel/right.png);
    }
    #btn-left:hover,#btn-right:hover{
        opacity: 1;
        transition:all .2s linear;
    }
</style>
