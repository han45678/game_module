<template>
  <div class="home">
    <div id="frame">
      <div id="frame-content">
        <U1LettersD3 v-if="game === U1LettersD3" />
        <U1LettersD4 v-if="game === U1LettersD4" />
        <div v-else>
          <p>哈囉,請點開選單並選擇題目</p>
        </div>
      </div>
    </div>
    <div id="menu" :class="{ active: open_menu }">
      <div id="menu_button" @click="open_menu = !open_menu">MENU</div>
      <h2>遊戲選單</h2>
      <ul>
        <li>
          Unit1
          <ol>
            <li @click="game = U1LettersD3">U1LettersD3</li>
            <li @click="game = U1LettersD4">U1LettersD4</li>
            <li @click="game = U1SPD5">U1SPD5</li>
            <li @click="game = U1StoryD1">U1StoryD1</li>
            <li @click="game = U1VocabularyD5">U1VocabularyD5</li>
          </ol>
        </li>
      </ul>
    </div>
  </div>
</template>

<script>
import U1LettersD3 from "@/components/U1_Letters_D3.vue";
import U1LettersD4 from "@/components/U1_Letters_D4.vue";

export default {
  name: "Home",
  components: {
    U1LettersD3,
    U1LettersD4,
  },
  data() {
    return {
      game: "",
      open_menu: false,
    };
  },
  mounted() {
    // let fw = document.querySelector("#frame").offsetWidth;
    // let fh = document.querySelector("#frame").offsetHeight;
    // let ww = window.innerWidth;
    // let wh = window.innerHeight;
    // let wfh = wh - fh;
    // let wfw = ww - fw;
    // document.querySelector("#frame").style.height = fh + wfh + "px";
    // document.querySelector("#frame").style.width = fw + wfh + "px";
    // if(!fw + wfh < ww){
    //   document.querySelector("#frame").style.height = fh + wfh + "px";
    //   document.querySelector("#frame").style.width = fw + wfh + "px";
    // }else{
    //   console.log(1)
    //   document.querySelector("#frame").style.height = fh + wfw + "px";
    //   document.querySelector("#frame").style.width = fw + wfw + "px";
    // }
    // window.onresize = function () {
    //   let fw = document.querySelector("#frame").offsetWidth;
    //   let fh = document.querySelector("#frame").offsetHeight;
    //   // let ww = window.innerWidth;
    //   let wh = window.innerHeight;
    //   let wfh = wh - fh;
    //   document.querySelector("#frame").style.height = fh + wfh + "px";
    //   document.querySelector("#frame").style.width = fw + wfh + "px";
    // };
  },
  methods: {},
};
</script>

<style lang="scss" scoped>
* {
  margin: 0;
  padding: 0;
  user-select: none;
}
body {
  // background-image: url(@images/background.jpg);
}
#frame {
  position: absolute;
  left: 0;
  right: 0;
  top: 0;
  bottom: 0;
  margin: auto;
  width: 1248px;
  height: 710px;
  border: 5px solid #000;
  background-color: #fff;
  box-sizing: border-box;
  border-radius: 20px;
  background-color: #7a7a7a;
  transform-origin: center;
  #frame-content {
    position: absolute;
    top: 5px;
    left: 5px;
    width: calc(100% - 10px);
    height: calc(100% - 10px);
    border: 5px solid #000;
    background-color: #fff;
    box-sizing: border-box;
    border-radius: 15px;
    overflow: hidden;
  }
  // @media screen and (max-width: 1920px){
  //   transform: scale(1.365);
  // }
  // @media screen and (max-width: 1680px){
  //   transform: scale(1.335);
  // }
  // @media screen and (max-width: 1366px){
  //   transform: scale(1.085);
  // }
  // // @media screen and (max-height: 768px){
  // //   transform:scale(1.08);
  // // }
  // @media screen and (max-width: 1280px){
  //   transform: scale(1);
  // }
  // @media screen and (max-width: 1024px){
  //   transform: scale(0.9);
  // }
}

#menu {
  position: fixed;
  background-color: aquamarine;
  right: 0;
  top: 0;
  width: 300px;
  height: 100vh;
  transform: translateX(100%);
  transition: 0.3s;
  &.active {
    transform: translateX(0);
    #menu_button {
      transform: rotate(0deg);
    }
  }
  #menu_button {
    transition: 0.6s;
    cursor: pointer;
    position: absolute;
    left: -60px;
    top: 15px;
    transform: rotate(-90deg);
    width: 60px;
    text-align: center;
    height: 60px;
    line-height: 60px;
    background-color: aquamarine;
    color: #fff;
    text-shadow: 1px 1px 5px black;
  }
  h2 {
    margin-top: 30px;
    margin-bottom: 30px;
    font-size: 48px;
    color: #fff;
    text-shadow: 1px 1px 5px black;
  }
  ul {
    li {
      list-style: none;
      font-size: 18px;
      line-height: 3;
      font-weight: bolder;
      color: #fff;
      text-shadow: 1px 1px 5px black;
      cursor: pointer;
      transition: 0.3s;
      position: relative;
      &::before {
        content: "";
        width: 0;
        height: 0;
        border-style: solid;
        border-width: 10px 5px 0 5px;
        border-color: #ffffff transparent transparent transparent;
        position: absolute;
        right: 15px;
        top: 22.5px;
        translate: 0.6s;
      }
      &:hover {
        background-color: #70a694;
        &::before {
          transform: rotate(-180deg);
        }
        ol {
          height: auto;
          transform: scaleY(1);
        }
      }
      ol {
        overflow: hidden;
        transform-origin: top;
        height: 0;
        transform: scaleY(0);
        transition: 0.6s;
        li {
          list-style: none;
          font-size: 18px;
          line-height: 3;
          font-weight: bolder;
          color: #fff;
          text-shadow: 1px 1px 5px black;
          cursor: pointer;
          transition: 0.3s;
          &::before{
            display: none;
          }
          &:hover {
            background-color: aquamarine;
          }
        }
      }
    }
  }
}
</style>
