<template>
  <div
    id="ref"
    class="
      cursor-pointer
      w-1/2
      xl:w-1/3
      bg-blue-200
      grid grid-cols-3
      gap-2
      md:mx-auto
      rounded
      shadow-lg
    "
  >
    <div
      v-for="tab in tabs"
      :key="tab"
      class="
        h-48
        xl:h-64
        bg-gray-200
        shadow-lg
        rounded
        flex
        justify-center
        items-center
      "
      @click="putPion(tab)"
    >
      <img v-if="pion.length" :src="checkSrc(pion[tab])" alt="" class="w-24" />
    </div>
  </div>
</template>

<script>
import croix from "@/assets/croix.png";
import rond from "@/assets/rond.png";

export default {
  data() {
    return {
      size: 9,
      tabs: [],
      pion: [],
      rond,
      croix,
      pathImage: "",
    };
  },
  created() {
    this.inittabs(this.size);
    this.pathImage = this.croix;
    console.log(this.pathImage);
  },
  mounted() {},
  methods: {
    checkLine(p) {
      if (
        this.pion[p] &&
        this.pion[parseInt(p + 1)] &&
        this.pion[parseInt(p + 2)]
      ) {
        if (
          this.pion[p].sym === this.pion[parseInt(p + 1)].sym &&
          this.pion[p].sym === this.pion[parseInt(p + 2)].sym
        ){
          return true;
        }
        else return false;
      } else return false;
    },
    checkWinner() {
      let res = false;
      for (const p in this.pion) {
        res = this.checkLine(p);   
        if (res === true) break;
      }
      return res;
    },
    inittabs(size) {
      for (let i = 0; i < size; i++) {
        this.tabs.push(i);
      }
    },
    putPion(i) {
      if (!this.pion[i]) {
        this.pion[i] = {
          clicked: true,
          src: this.pathImage,
          sym: this.pathImage === this.croix ? "croix" : "rond",
        };
       
        this.pathImage = this.pathImage == this.croix ? this.rond : this.croix;
        if (this.checkWinner())
          console.log('you win');
        // play Bot
      }
    },
    checkSrc(pion) {
      if (pion && pion.src) {
        return pion.src;
      } else return "";
    },
  },
};
</script>

<style>
</style>