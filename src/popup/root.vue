<template>
  <div id="app">
    <div class="loading" v-show="loading">
      <svg xmlns="http://www.w3.org/2000/svg" viewBox="0 0 512 512" class="icon">
        <path
          d="M304 48c0 26.51-21.49 48-48 48s-48-21.49-48-48 21.49-48 48-48 48 21.49 48 48zm-48 368c-26.51 0-48 21.49-48 48s21.49 48 48 48 48-21.49 48-48-21.49-48-48-48zm208-208c-26.51 0-48 21.49-48 48s21.49 48 48 48 48-21.49 48-48-21.49-48-48-48zM96 256c0-26.51-21.49-48-48-48S0 229.49 0 256s21.49 48 48 48 48-21.49 48-48zm12.922 99.078c-26.51 0-48 21.49-48 48s21.49 48 48 48 48-21.49 48-48c0-26.509-21.491-48-48-48zm294.156 0c-26.51 0-48 21.49-48 48s21.49 48 48 48 48-21.49 48-48c0-26.509-21.49-48-48-48zM108.922 60.922c-26.51 0-48 21.49-48 48s21.49 48 48 48 48-21.49 48-48-21.491-48-48-48z"
        ></path>
      </svg>
    </div>
    <transition>
      <router-view :key="key"/>
    </transition>
  </div>
</template>
<script>
// import BCX from "bcxjs-api";
import { mapState } from "vuex";
export default {
  name: "root",
  computed: {
    ...mapState(["loading"]),
    key: function() {
      return this.$route.name !== undefined
        ? this.$route.name + "" + new Date()
        : this.$route + "" + new Date();
    }
  }
  // mounted() {
  //   let bcxNodes = [];
  //   bcxNodes.push({
  //     url: "ws://47.93.62.96:8050",
  //     name: "COCOS节点1",
  //     ip: "47.93.62.96"
  //   });
  //   bcxNodes.push({
  //     url: "ws://39.96.33.61:8080",
  //     name: "COCOS节点2",
  //     ip: "39.96.33.61"
  //   });
  //   bcxNodes.push({
  //     url: "ws://39.96.29.40:8050",
  //     name: "COCOS节点3",
  //     ip: "39.96.29.40"
  //   });
  //   bcxNodes.push({
  //     url: "ws://39.106.126.54:8050",
  //     name: "COCOS节点4",
  //     ip: "39.106.126.54"
  //   });

  //   let nodeIndex = 0;
  //   let node = bcxNodes[nodeIndex];

  //   let bcx = new BCX({
  //     default_ws_node: node.url,
  //     ws_node_list: [
  //       {
  //         url: node.url,
  //         name: node.name
  //       }
  //     ],
  //     networks: [
  //       {
  //         core_asset: "COCOS",
  //         chain_id:
  //           "53b98adf376459cc29e5672075ed0c0b1672ea7dce42b0b1fe5e021c02bda640"
  //       }
  //     ],
  //     faucet_url: "http://" + node.ip + ":3000",
  //     auto_reconnect: true,
  //     worker: false
  //   });
  // }
};
</script>
<style lang="scss" scoped>
@-webkit-keyframes spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}

@keyframes spin {
  0% {
    -webkit-transform: rotate(0deg);
    transform: rotate(0deg);
  }
  100% {
    -webkit-transform: rotate(360deg);
    transform: rotate(360deg);
  }
}
.icon {
  display: inline-block;
  stroke-width: 0;
  stroke: currentColor;
  fill: currentColor;
  width: 1em;
  height: 1em;
}

.loading {
  display: flex;
  justify-content: center;
  align-items: center;
  background: rgba(255, 255, 255, 0.8);
  position: absolute;
  top: 60px;
  right: 0;
  bottom: 0;
  left: 0;
  font-size: 40px;
  color: #616161;
  z-index: 10;
}
.loading .icon {
  -webkit-animation: spin 2s infinite linear;
  animation: spin 2s infinite linear;
}
</style>
