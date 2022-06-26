<template>
  <div class="MusicPlayArea"
    :class="musicControlVisable ? 'apart' : 'full'"
  >
    <MusicPlayList
      :playerList="playerList"
      @playThis="playThis"
      v-if="!musicControlVisable"
    />
  </div>
</template>
<script>
import MusicPlayList from './MusicPlayList.vue';

export default {
  name: 'MusicPlayArea',
  components: {
    MusicPlayList,
  },
  props: {
    musicControlVisable: Boolean,
    playerList: Array,
  },
  emits: ['playThis'],
  setup(props, { emit }) {
    const playThis = (index) => {
      emit('playThis', index);
    };
    return {
      playThis,
    };
  },
};
</script>
<style lang="scss">
.MusicPlayArea {
  box-sizing: border-box;
  overflow-y: auto;
  overflow-x: hidden;
  &.full {
    height: calc(100vh - 150px - 220px);
    margin: 30px 0px;
  }
  &.apart {
    height: 20px;
  }
}
</style>
