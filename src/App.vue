<template>
  <HeadBar
    :musicControlVisable="musicControl"
    :soungTitle="'Rockstar'"
    :subTitle="'Post Malone'"
  />
  <MusicPlayArea
    :musicControlVisable="musicControl"
    :playerList="playerList"
    @playThis="playThis"
  />
  <MusicControl
    :musicControlVisable="musicControl"
    :playerList="playerList"
    @changeVisable="changeVisable"
  />
</template>

<script>
import { reactive, ref } from 'vue';
import HeadBar from './components/HeadBar.vue';
import MusicControl from './components/MusicControl.vue';
import MusicPlayArea from './components/MusicPlayArea/MusicPlayArea.vue';
import playlist from './store/playlist';

export default {
  name: 'App',
  emits: ['changeVisable'],
  components: {
    HeadBar,
    MusicControl,
    MusicPlayArea,
  },
  setup() {
    const musicControl = ref(false);
    const changeVisable = (value) => {
      musicControl.value = value;
    };
    const playerList = reactive(playlist);
    const playThis = (index) => {
      const arr = playerList.findIndex((item) => item.status === 'play');
      playerList[index].status = 'play';
      playerList[arr].status = 'wait';
    };
    return {
      musicControl,
      playerList,
      changeVisable,
      playThis,
    };
  },
};
</script>

<style lang="scss">
:root {
  --bk-color: #f8f5ff;
  --bk-color1: #9a7adf;
  --bk-color2: #8566c3;
  --font-color: #eee1f9;
  --font-color1: #c2b7e3;
  --font-color2: #c3c2c8;
  --font-color3: #9a7adf;
  --font-color4: black;
}
body {
  padding: 0;
  margin: 0;
}

#app {
  width: 100vw;
  height: 100vh;
  background-color: var(--bk-color1);
}
</style>
