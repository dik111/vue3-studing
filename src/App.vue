<template>
  <img alt="Vue logo" src="./assets/logo.png">
  <h2>欢迎光临</h2>
  <div>请选择一位美女为你服务</div>
  <div>
    <button v-for="(item,index) in girls" :key="index" @click="selectGirlFun(index)">
      {{ index }}:{{ item }}
    </button>
    <div>你选择了哪个美女【{{ selectGirl }}】为你服务</div>
  </div>
</template>

<script lang="ts">
import { ref, reactive, toRefs} from 'vue';
interface DataProps{
  girls: string[];
  selectGirl: string;
  selectGirlFun: (index: number) => void;
}

export default {
  name: 'App',
  setup: function () {
    const data: DataProps = reactive({
      girls: ["大脚", "刘英", "晓红"],
      selectGirl: "",
      selectGirlFun: (index: number) => {
        data.selectGirl = data.girls[index]
      }
    })
    const refData = toRefs(data)


    // const girls = ref(["大脚", "刘英", "晓红"])
    // const selectGirl = ref("")
    // const selectGirlFun = (index: number) => {
    //     selectGirl.value = girls.value[index]
    // }
    return {
      ...refData
    }
  }
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
