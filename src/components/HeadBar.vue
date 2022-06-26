<template>
  <div class="HeadBar"
    :class="musicControlVisable ? 'control' : ''"
  >
    <div class="menu">
      <div class="menu_icon"></div>
    </div>
    <div class="title"
      :class="musicControlVisable ? '' : 'control'"
    >
      <div class="title_header">{{soungTitle}}</div>
      <div class="title_sub">{{subTitle}}</div>
    </div>
    <div class="search">
      <div class="search_icon"></div>
    </div>
  </div>
</template>
<script>

export default {
  name: 'HeadBar',
  props: {
    musicControlVisable: Boolean,
    soungTitle: String,
    subTitle: String,
  },
};

</script>
<style lang="scss">
.HeadBar {
  width: 100vw;
  display: flex;
  &.control {
    align-items: center;
  }
  .menu, .search {
    padding:0 20px;
    width: 40px;
    height: 80px;
    display: flex;
    justify-content: center;
    align-items: center;
    cursor: pointer;
    .menu_icon, .search_icon {
      height: 40px;
      width: 100%;
      background-repeat: no-repeat;
      background-size: contain;
    }
    .menu_icon {
      background: url('../assets/menu.svg');
    }
    .search_icon {
      background: url('../assets/search.svg');
    }
  }
  .title {
    height: 80px;
    width: calc(100% - 160px);
    display: flex;
    flex-direction: column;
    justify-content: flex-end;;
    align-items: center;
    box-sizing: border-box;
    &.control {
      height: 160px;
    }
    .title_header {
      padding-bottom: 10px;
      font-size: 36px;
      color: var(--font-color);
    }
    .title_sub {
      font-size: 16px;
      color: var(--font-color);
    }
  }
}
</style>
