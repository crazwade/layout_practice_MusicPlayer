<template>
  <div class="MusicPlayList"
    v-for="(item, index) in playerList" :key="index"
    :class="item.status === 'play' ? 'play' : ''"
  >
    <div class="head_btn">
      <div
        :class="item.status === 'play' ? 'pause_icon' : 'play_icon'"
        @click="playThis(index)"
      />
    </div>
    <div class="content">
      <div class="title">
        {{item.title}}
      </div>
      <div class="detail">
        {{item.singer}}
      </div>
    </div>
    <div class="info">
      <div class="info_icon"></div>
    </div>
  </div>
</template>
<script>
export default {
  name: 'MusicPlayList',
  props: {
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
.MusicPlayList {
  border-bottom: 1px rgb(173, 172, 172) solid;
  height: 55px;
  width: 100%;
  display: flex;
  justify-content: space-between;
  align-items: center;
  padding: 5px 0;
  &.play {
    background-color: var(--bk-color2);
  }
  .head_btn {
    padding-left: 30px;
  }
  .info {
    padding-right: 30px;
  }
  .head_btn, .info {
    width: 40px;
    height: 40px;
    display: flex;
    align-items: center;
    justify-content: center;
    .play_icon, .info_icon, .pause_icon {
      cursor: pointer;
      width: 40px;
      height: 40px;
    }
    .pause_icon {
      background: url('../../assets/pause.svg');
      background-repeat: no-repeat;
      background-size: cover;
    }
    .play_icon {
      background: url('../../assets/play.svg');
      background-repeat: no-repeat;
      background-size: cover;
    }
    .info_icon {
      background: url('../../assets/info.svg');
      background-repeat: no-repeat;
      background-size: cover;
    }
  }
  .content {
    padding: 0 20px;
    width: calc(100% - 80px);
    max-width: 200px;
    .title {
      font-size: 16px;
      color: var(--font-color);
      padding-bottom: 5px;
      overflow: hidden;
      white-space: nowrap;
      text-overflow: ellipsis;
    }
    .detail {
      font-size: 12px;
      color: var(--font-color1);
    }
  }
}
</style>
