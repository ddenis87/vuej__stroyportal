<template>
  <div class="c-button">
    <button :class="'c-button__item_' + buttonType">
      <img v-if="buttonType == 'catalog'" class="c-button__item-images" src="@/assets/images/menu.png">
      <img v-if="buttonType == 'list'" class="c-button__item-images" src="@/assets/images/list.png">
      <slot></slot>
    </button>
  </div>
</template>

<script>
export default {
  name: 'cButton',
  props: [
    'inButtonType'
  ],
  computed: {
    buttonType() { return this.inButtonType; }
  }
}
</script>

<style lang="scss" scoped>
.c-button {
  // width: 116px;
  height: 40px;
  &__item {
    &-images {
      margin-right: 10.5px;
    }
    &_catalog {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 116px;
      // width: 100%;
      height: 100%;
      border-radius: 4px;
      border: 0px;
      background-color: #FED83D;
      font-family: 'Open sans';
      font-weight: bold;
      line-height: 24px;
    }
    &_list {
      display: flex;
      justify-content: center;
      align-items: center;
      width: 116px;
      // width: 100%;
      height: 100%;
      border-radius: 4px;
      border: 1px solid #ECEFF1;
      box-sizing: border-box;
      background-color: #FAFBFC;
      font-family: 'Open sans';
      font-weight: bold;
      line-height: 24px;
    }
    &_profile {
      width: 40px;
      height: 40px;
      font-family: 'Open sans';
      font-weight: bold;
      line-height: 24px;
      color: #FFF;
      border: 0px;
      border-radius: 20px;
      background-color: #9B51E0;
    }
  }
}
</style>