<script setup>
  import { ref } from 'vue';
  const animationDuration = 10
  const total = ref(3)
  const active = ref(0)
  const preactive = ref(0)
  const pictures = ref([
    {id: 1, url: '/src/assets/kv_img1.jpg'}, 
    {id: 2, url: '/src/assets/kv_img2.jpg'}, 
    {id: 3, url: '/src/assets/kv_img3.jpg'}])
  const triangleImg = ref([
    {id:1, url: '/src/assets/thumbs1.jpg'},
    {id:2, url: '/src/assets/thumbs2.jpg'},
    {id:3, url: '/src/assets/thumbs3.jpg'},
    {id:4, url: '/src/assets/thumbs4.jpg'},
    {id:5, url: '/src/assets/thumbs5.jpg'},
  ])
  const img = function(url){
    return{
      backgroundImage: `url(${url})`,
      animationDuration: `${animationDuration}s`,
      // animationDelay: `${(n-1)*animationDuration/2}s`
    }
  }
  setInterval(function(){
    preactive.value = active.value
    active.value = (active.value + 1 + total.value) % total.value
  }, animationDuration/2*1000)
</script>

<template>
  <div class="container">
    <div class="top-info">
      <h6>NINTENDO SWITCH</h6>
      <h6>THE LEGEND OF ZELDA BREATH OF THE WILD</h6>
      <h6>APRIL 28TH, 2023</h6>
    </div>

    <div class="title-group">
      <div class="zelda-logo">
        <img src="/src/assets/zelda-logo.png">
      </div>
      <div class="title">
        <div class="eng-title">
          <h4>HYRULE DISCOVERY JOURNEY</h4>
        </div>
        <div class="ch-title">
          <img src="/src/assets/ch-title.png">
        </div>
      </div>
      <div class="switch-logo">
        <img src="/src/assets/switch-logo.png">
      </div>
    </div>
    <div class="welcome-block">
      <div class="kv">
        <ul class="kvList">
          <li v-for="picture in pictures" :key="picture.id" :style="img(picture.url)"  :class="{animate: active === picture.id-1|| preactive === picture.id-1}"></li>
        </ul>
        <div class="text">
          <img src="/src/assets/kv_copy.png">
        </div>
      </div>

      <div class="about">
        <div class="about-text">
          <div class="about-title">
            <h1><span>-A</span>BOUT</h1>
            <h4>HYRULE DISCOVERY JOURNEY</h4>
          </div>
          <div class="about-p">
            <p>廣大的海拉魯擁有美麗的自然環境與不為人知的秘境，</p>
            <p>這裡也住著許多個性十足的人與怪物……</p>
            <p>除此之外，它也具備許多的樣貌。</p>
            <p>以下我們將為您介紹幾個海拉魯不可不去的景點。</p>
            <p>即使您已經走遍整個海拉魯，或許也會有新的發現。</p>
          </div>
        </div>
        <div class="about-img"></div>
      </div>
    </div>

    <div class="region-group">
      <div id="region6">
        <a href="#">
          <div class="region-inner">
            <div class="region-innerLeft">
              <div class="text">
              </div>
            </div>
            <div class="region-innerRight">
              <div class="vol">
                <img id="arrow" src="/src/assets/midashi_arrow.png">
                <img src="/src/assets/vol.png">
                <div class="text">HYRULE DISCOVERY</div>
              </div>
              <div class="title">
                <img src="/src/assets/title.png">
              </div>
              <div class="triangles">
                <img src="/src/assets/thumb1.jpg">
                <img src="/src/assets/thumb2.jpg">
                <img src="/src/assets/thumb3.jpg">
                <img src="/src/assets/thumb4.jpg">
                <img src="/src/assets/thumb5.jpg">
                <div class="more">
                  <div class="text">
                    <h2>MORE</h2>
                    <h2>></h2>
                  </div>
                </div>
              </div>
            </div>
          </div>
        </a>
      </div>
    </div>
  </div>
</template>

<style >
  *{
    padding: 0;
    margin: 0;
    list-style: none;
    box-sizing: border-box;
    font-family:'Trebuchet MS', 'Lucida Sans Unicode', 'Lucida Grande', 'Lucida Sans', Arial, sans-serif
  }
  :root{
    --main-color: #b7a78a;
  }
  body{
    background-color: var(--main-color);
  }
  .container{
    width: calc(100vw - 130px);
    /* height: calc(100vw - 70px); */
    height: auto;
    margin: 35px 65px;
    display: flex;
    flex-direction: column;
  }
  .top-info{
    display: flex;
    width: 100%;
    height: 30px;
  }
  .top-info  h6{
    font-size: 14px;
    line-height: 30px;
  }
  .top-info  h6:nth-child(2){
    margin: auto;
  }
  .title-group{
    width: 100%;
    height: 25vh;
    border: 8px solid black;
    display: flex;
    margin-bottom: 10px;
  }
  .title-group .zelda-logo{
    width: 23%;
    display: flex;
    justify-content: center;
    text-align: center;
    padding: 30px 20px 20px 25px;
    border-right: 4px solid black;
  }
  .title-group .zelda-logo img{
    height: 80%;
    width: auto;
  }
  .title-group .title{
    width: 65%;
    display: flex;
    flex-direction: column;
    border-left: 4px solid black;
    border-right: 4px solid black;
    align-items: center;
    padding: 15px;
  }
  .title-group .title .eng-title{
    width: 100%;
    height: 40%;
    display: flex;
    justify-content: start;
    align-items: center;
  }
  .title-group .title .eng-title h4{
    font-size: 22px;
    font-weight: 550;
    letter-spacing: -0.5px;
    display: flex;
  }
  .title-group .title .eng-title h4::before,
  .title-group .title .eng-title h4::after{
    content: '';
    display: block;
    height: 4px;
    background-color: black;
    margin: auto;
    flex-grow: 1;
  }
  .title-group .title .eng-title h4::before{
    width: .4em;
    margin-right: 5px;
  }
  .title-group .title .eng-title h4::after{
    width: 25em;
    margin-left: 5px;
  }
  .title-group .title .ch-title{
    height: 55%;
    display: flex;
    justify-content: center;
    align-items: center;
    margin: 10px;
  }
  .title-group .title .ch-title img{
    height: 65px;
    width: 100%;
  }
  .title-group .switch-logo{
    width: 12%;
    display: flex;
    justify-content: center;
    align-items: center;
    padding: 15px;
    border-left: 4px solid black;
  }
  .title-group .switch-logo img{
    width: 100%;
    height: 100%;
  }
  .welcome-block{
    width: 100%;
    height: 150vh;
    border: 8px solid black;
    position: relative;
    margin-bottom: 15px;
  }
  .welcome-block .kv{
    width: 100%;
    height: 70%;
    padding: 15px;
    border-bottom: 4px solid black;
    position: relative;
  }
  .welcome-block .kv .text{
    width: 50%;
    position: absolute;
    bottom: 30px;
    left: 30px;
  }
  .welcome-block .kv .text img{
    width: 100%;
    height: 100%;
  }
  .welcome-block .kv .kvList{
    list-style: none;
    width: 100%;
    height: 100%;
    background-color: #9b9b9b;
    position: relative;
  }
  .welcome-block .kv .kvList > li{
    opacity: 0;
    position: absolute;
    width: 100%;
    height: 100%;
    background-position: center;
    background-repeat: no-repeat;
    background-size: 100% 100%;
  }
  .welcome-block .kv .kvList > li.animate{
    animation-name: kvAnimate;
    animation-timing-function:  linear;
    /* animation-iteration-count: infinite; */
  }
  @keyframes kvAnimate{
    0%{
      opacity: 0;
    }
    25%{
      opacity: 1;
    }
    50%{
      opacity: 1;
    }
    75%{
      opacity: 0;
    }
    100%{
      opacity: 0;
    }
  }
  .welcome-block .about{
    width: 100%;
    height: 30%;
    border-top: 4px solid black;
    display: flex;
  }
  .about .about-text{
    width: 50%;
    height: 100%;
    display: flex;
    flex-direction: column;
    padding: 15px;
  }
  .about .about-text .about-title{
    width: 125%;
    height: 30%;
    background: url("/src/assets/about_title_bg.png") no-repeat center / 100% 100%;
    display: flex;
    align-items: center;
    color: var(--main-color);
    position: relative;
    display: flex;
  }
  .about .about-text .about-title h1{
    font-size: 40px;
    position: absolute;
    left: 30px;
  }
  .about .about-text .about-title h1 span{
    font-size: 70px;
  }
  .about .about-text .about-title h4{
    font-size: 20px;
    position: absolute;
    right: 50px;
  }
  .about .about-text .about-p{
    width: 100%;
    height: 70%;
    font-size: 25px;
    font-weight: 900;
    display: flex;
    flex-direction: column;
    justify-content: center;
    padding-left: 30px;
  }
  .about .about-img{
    width: 50%;
    height: 100%;
    background: linear-gradient(120deg, var(--main-color) 25%, black 26%, transparent 26.5%) center center / 100% 100%,
                url("/src/assets/about_img2.jpg") no-repeat left bottom / 400% 450%;
    animation-name: aboutAnimate;  
    animation-duration: 60s;   
    animation-iteration-count: infinite;
    animation-timing-function: linear;
  }
  @keyframes aboutAnimate{
    0%{
      background-position: 0% 100%;
    }
    100%{
      background-position: 22.15% 35.6%;     
    }
  }
  .region-group{
    width: 100%;
    height: 350vh;
    border: 8px solid black;
  }
  #region6{
    width: 100%;
    height: 20%;
    padding: 50px 20px 60px 20px;
    border-bottom: 3px dashed black;
    position: relative;
  }
  #region6::before{
    content: 'NEW';
    color:  white;
    font-size: 32px;
    width: 10%;
    height: 20%;
    position: absolute;
    top: 32px;
    right: -39px;
    z-index: 2;
    transform: rotate(42deg);
  }
  #region6::after{
    content: '';
    width: 9.5%;
    height: 24%;
    position: absolute;
    top: -8px;
    right: -8px;
    color: white;
    background: linear-gradient(42deg, transparent 50% , rgb(163, 68, 68) 50%);
  }
  #region6 a{
    text-decoration: none;
    color: black;
  }
  #region6 .region-inner{
    width: 100%;
    height: 100%;
    display: flex;
  }
  #region6 .region-inner .region-innerLeft{
    width: 50%;
    height: 100%;
    background: url("/src/assets/region6_bg.jpg") no-repeat center / 100% 100%;
    position: relative;
    display: flex;
  }
  #region6 .region-inner .region-innerLeft .text{
    width: 20%;
    height: 120%;
    background: url("/src/assets/copy.png") no-repeat center / 100% 100%;;
    position: absolute;
    top: -10%;
    left: 2%;
  }
  #region6 .region-inner .region-innerRight{
    width: 50%;
    height: 100%;
    display: flex;
    flex-direction: column;
  }
  #region6 .region-inner .region-innerRight .vol{
    width: 100%;
    height: 10%;
    display: flex;
    align-items: flex-end;
    position: relative;
    padding: 0 50px;
  }
  #region6 .region-inner .region-innerRight .vol img{
    height: 100%;
  }
  #region6 .region-inner .region-innerRight .vol #arrow{
    height: 30%;
    position: relative;
    bottom: 7px;
    margin-right: 5px;
  }
  #region6 .region-inner .region-innerRight .vol .text{
    font-size: 18px;
    position: absolute;
    right: 50px;
    font-weight: 900;
  }
  #region6 .region-inner .region-innerRight .title{
    width: 100%;
    height: 45%;
    padding: 15px 50px 25px;
    border-top: 2px solid black;
    margin-top: 10px;
  }
  #region6 .region-inner .region-innerRight .title img{
    width: 100%;
    height: 100%;
  }
  #region6 .region-inner .region-innerRight .triangles{
    width: 100%;
    height: 45%;
    display: flex;
    padding: 10px 50px;
  }
  #region6 .region-inner .region-innerRight .triangles img{
    width: 29%;
    height: 100%;
    position: relative;
  }
  #region6 .region-inner .region-innerRight .triangles img:nth-child(even){
    clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
  }
  #region6 .region-inner .region-innerRight .triangles img:nth-child(odd){
    clip-path: polygon(0% 0%, 100% 0%, 50% 100%);
  }
  #region6 .region-inner .region-innerRight .triangles img:nth-child(2){
    left: -13%;
  }
  #region6 .region-inner .region-innerRight .triangles img:nth-child(3){
    left: -26%;
  }
  #region6 .region-inner .region-innerRight .triangles img:nth-child(4){
    left: -39%;
  }
  #region6 .region-inner .region-innerRight .triangles img:nth-child(5){
    left: -52%;
  }
  #region6 .region-inner .region-innerRight .triangles .more{
    clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
    width: 30%;
    height: 100%;
    background-color: black;
    position: relative;
    left: -65%;
    display: flex;
    justify-content: center;
    align-items: center;
    flex-shrink: 0;
  }
  #region6 .region-inner .region-innerRight .triangles .more .text{
    clip-path: polygon(50% 0%, 0% 100%, 100% 100%);
    width: 95%;
    height: 95%;
    color: black;
    background-color: var(--main-color);
    display: flex;
    flex-direction: column;
    justify-content: center;
    align-items: center;
    font-size: 18px;
    padding-top: 50px;
  }
  #region6 a:hover .region-inner .region-innerRight .triangles .more .text{
    color: white;
    background-color: black;
  }

</style>
