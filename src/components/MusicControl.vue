<template>
  <div class="MusicControl"
    :class="musicControlVisable ? 'full' : 'apart'"
  >
    <div class="visableControl">
      <div
        :class="musicControlVisable ? 'close_icon' : 'open_icon'"
        @click="musicControlVisable ? controlBtn(false) : controlBtn(true)"
      />
    </div>
    <div class="content">
      <div class="full"
        v-if="musicControlVisable"
      >
        <div class="info">
          <div class="title">{{playListNow.title}}</div>
          <div class="singer">{{playListNow.singer}}</div>
        </div>
        <div class="img">
          <img :src="playListNow.img" alt="">
        </div>
        <div class="playBar">
          <div class="previous"></div>
          <div class="playorpause"></div>
          <div class="next"></div>
        </div>
      </div>
      <div class="apart"
        v-else
      >
        <div class="info">
          <div class="title">{{playListNow.title}}</div>
          <div class="singer">{{playListNow.singer}}</div>
        </div>
        <div class="playBar">
          <div class="previous"></div>
          <div class="playorpause"></div>
          <div class="next"></div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>
import { computed } from 'vue';

export default {
  name: 'MusicControl.vue',
  emit: ['changeVisable'],
  props: {
    musicControlVisable: Boolean,
    playerList: Array,
  },
  setup(props, { emit }) {
    const controlBtn = (value) => {
      emit('changeVisable', value);
    };
    // const playListNow = props.playerList.find((item) => item.status === 'play');
    const playListNow = computed(() => props.playerList.find((item) => item.status === 'play'));
    console.log(playListNow);
    return {
      controlBtn,
      playListNow,
    };
  },
};
</script>
<style lang="scss">
  .MusicControl {
    background-color: var(--bk-color);
    width: 100vw;
    border-top-left-radius: 40px;
    border-top-right-radius: 40px;
    .visableControl {
      height: 40px;
      display: flex;
      align-items: center;
      justify-content: center;
      .close_icon, .open_icon {
        cursor: pointer;
        width: 40px;
        height: 40px;
        background-repeat: no-repeat;
        background-size: contain;
      }
      .close_icon {
        background: url('../assets/close.svg');
      }
      .open_icon {
        background: url('../assets/open.svg');
      }
    }
    .content {
      .apart {
        height: 110px;
        display: flex;
        width: 100%;
        justify-content: space-between;
        align-items: center;
        .info {
          max-width: 180px;
          height: 100px;
          padding-left: 20px;
          overflow: hidden;
          white-space: nowrap;
          text-overflow: ellipsis;
          display: flex;
          flex-direction: column;
          justify-content: center;
          .title {
            font-size: 20px;
            color: var(--font-color3);
          }
          .singer {
            padding-top: 10px;
            font-size: 14px;
            color: var(--font-color4);
          }
        }
        .playBar {
          box-sizing: border-box;
          width: 220px;
          height: 100px;
          padding-right: 20px;
          display: flex;
          justify-content: space-around;;
          align-items: center;
          .previous, .next {
            width: 40px;
            height: 40px;
          }
          .previous {
            background: url('../assets/previous.svg');
            background-repeat: no-repeat;
            background-size: cover;
          }
          .playorpause {
            width: 80px;
            height: 80px;
            background: url('../assets/play.svg');
            background-repeat: no-repeat;
            background-size: cover;
          }
          .next {
            background: url('../assets/next.svg');
            background-repeat: no-repeat;
            background-size: cover;
          }
        }
      }
      .full {
        height: calc(100vh - 140px);
        display: flex;
        flex-direction: column;
        justify-content: space-evenly;
        align-items: center;
        .info {
          width: 100%;
          display: flex;
          flex-direction: column;
          justify-content: center;
          align-items: center;
          .title {
            text-align: center;
            width: calc(100% - 20px);
            font-size: 32px;
            color: var(--font-color3);
            overflow: hidden;
            white-space: nowrap;
            text-overflow: ellipsis;
          }
          .singer {
            padding-top: 10px;
            font-size: 24px;
            color: var(--font-color4);
          }
        }
        .img {
          display: flex;
          justify-content: center;
          align-items: center;
          width: 100%;
          img {
            width: 225px;
            height: 225px;
          }
        }
        .playBar {
          width: 100%;
          display: flex;
          flex-direction: row;
          justify-content: space-evenly;
          align-items: center;
          .previous, .next {
            width: 80px;
            height: 80px;
          }
          .previous {
            background: url('../assets/previous.svg');
            background-repeat: no-repeat;
            background-size: cover;
          }
          .playorpause {
            width: 120px;
            height: 120px;
            background: url('../assets/play.svg');
            background-repeat: no-repeat;
            background-size: cover;
          }
          .next {
            background: url('../assets/next.svg');
            background-repeat: no-repeat;
            background-size: cover;
          }
        }
      }
    }
  }
</style>
