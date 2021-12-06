<template>
  <div class="wrapper">
    <button @click="order++" v-if="order < maxOrder" />
    <div class="cover" v-if="order === 1">
      <img src="../../public/images/筆順配對.png" alt="cover" />
    </div>
    <div class="cover" v-else-if="order === 2">
      <img src="../../public/images/說明頁.png" alt="cover" />
    </div>
    <iframe
      v-else-if="order === 3"
      src="iframe/SB_Active/Unit1/Letters/U1_Letters_D4-1/U1_Letters_D4-1.html"
      frameborder="0"
    />
    <iframe
      v-else-if="order === 4"
      src="iframe/SB_Active/Unit1/Letters/U1_Letters_D4-2/U1_Letters_D4-2.html"
      frameborder="0"
    />
    <iframe
      v-else-if="order === 5"
      src="iframe/SB_Active/Unit1/Letters/U1_Letters_D4-3/U1_Letters_D4-3.html"
      frameborder="0"
    />
    <iframe
      v-else-if="order === 6"
      src="iframe/SB_Active/Unit1/Letters/U1_Letters_D4-4/U1_Letters_D4-4.html"
      frameborder="0"
    />
    <div class="cover" v-else-if="order === 7">
      <img src="../../public/images/筆順配對_過關.png" alt="cover" />
    </div>
    <div class="cover" v-else-if="order === 8">
      <h1>過關</h1>
    </div>
  </div>
</template>
<script>
export default {
  name: "U1LettersD4",
  data() {
    return {
      order: 1,
      maxOrder: 8,
    };
  },
  created() {
    window.addEventListener("storage", (event) => {
      if (event.key === "end_game") {
        if (event.newValue === "next") {
          console.log("done");

        //   localStorage.removeItem("end_game");
        }
      }
    });
  },
  mounted() {},
  methods: {
    on_order() {
      //   if (this.order === this.maxOrder) {
      //     this.order = this.maxOrder;
      //   } else {
      //     this.order++;
      //   }
    },
  },
};
</script>

<style lang="scss" scoped>
.wrapper {
  width: 100%;
  height: 100%;
  position: relative;
  h1 {
    position: absolute;
    top: 50%;
    left: 50%;
    color: #fff000;
    transform: translate(-50%, -50%) rotate(-20deg) skew(20deg);
    text-shadow: -1px 1px 0 rgb(161, 162, 167), -2px 2px 0 rgb(161, 162, 167),
      -3px 3px 0 rgb(161, 162, 167), -4px 4px 0 rgb(161, 162, 167),
      -5px 5px 0 rgb(161, 162, 167), -6px 6px 0 rgb(161, 162, 167);
    font-size: 180px;
    margin: 0;
  }
  button {
    cursor: pointer;
    position: absolute;
    width: 120px;
    height: 60px;
    right: 15px;
    bottom: 15px;
    border-radius: 15px;
    border: orangered 5px solid;
    background-color: #fff;
    color: orangered;
    font-size: 32px;
    font-weight: 900;
    &::before {
      content: "下一步";
    }
  }
  iframe {
    width: 100%;
    height: 100%;
  }
  .cover {
    width: 100%;
    height: 100%;
    img {
      width: 100%;
      height: 100%;
      object-fit: cover;
    }
  }
}
</style>
