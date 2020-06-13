<template>
  <div class="box">
    <div class="code" @click="refreshCode">
      <identify :identifyCode="identifyCode"></identify>
    </div>
  </div>
</template>

<script>
import identify from "./identify";
export default {
  components: {
    identify
  },
  data() {
    return {
      identifyCodes: "1234567890",
      identifyCode: "",
      size: 5
    };
  },
  methods: {
    // 点击刷新
    refreshCode() {
      this.identifyCode = "";
      this.makeCode(this.identifyCodes, this.size);
    },
    makeCode(code, size) {
      for (let i = 0; i < size; i++) {
        this.identifyCode += code[this.randomNum(0, size)];
      }
      console.log("as==>", this.identifyCode);
    },
    // 随机数字
    randomNum(min, max) {
      return Math.floor(Math.random() * (max - min) + min);
    }
  },
  created() {
    this.makeCode(this.identifyCodes, this.size);
  }
};
</script>
<style scoped>
.box {
  width: 100%;
  height: 100%;
  background: darkgray;

}


</style>