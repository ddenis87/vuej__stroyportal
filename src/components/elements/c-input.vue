<template>
  <div class="c-input">
    <input class="c-input__field" 
           type="text" 
           placeholder="Хочу найти..."
           v-model="inputValue"/>
    <div class="c-input__list" v-show="(listSearchLive.length != 0)">
      <ul class="list-search">
        <li class="list-search__item"
            v-for="(item, index) in listSearchLive"
            :key="index"
            @click="selectItem(item)">{{ item.title }}</li>
      </ul>
    </div>
  </div>
</template>

<script>
export default {
  name: 'cInput',
  props: {
    inListSearch: Array
  },
  updated() {
    console.log('Update');
  },
  beforeUpdate() {
    console.log('Before');
  },
  computed: {
    listSearchLive() {
      if (this.inputValue == '') return [];
      let filterList = [];
      let vm = this;
      filterList = this.inListSearch.filter(function (item) {
        return item.title.toLowerCase().indexOf(vm.inputValue.toLowerCase()) !== -1
      });
      return (filterList.length != 0) ? filterList : filterList = [{title: 'Ничего не найдено'}];
    },
    listItem() { return this.inListSearch; }
  },
  data() {
    return {
      inputValue: '',
    }
  },
  methods: {
    selectItem(item) {
      this.listSearchLive.length = 0;
      this.inputValue = item.title;
    }
  }
}
</script>

<style lang="scss" scoped>
.c-input {
  position: relative;
  height: 40px;
  &__field {
    width: 100%;
    height: 40px;
    padding-left: 14px;
    border: 1px solid #ECEFF1;
    box-sizing: border-box;
    border-radius: 4px;
    font-family: 'Open Sans';
    font-style: normal;
    font-weight: normal;
    font-size: 14px;
    line-height: 24px;
    color: #708598;
  }
  &__list {
    position: absolute;
    display: block;
    width: 100%;
    min-height: 40px;
    border: 1px solid #ECEFF1;
    border-radius: 4px;
    color: black;
    background-color: white;
    box-sizing: border-box;
    z-index: 999;

    .list-search {
      padding: 0px;
      margin: 0px;
      &__item {
        list-style: none;
        font-size: 12px;
        text-transform: uppercase;
        padding: 3px;
        padding-left: 10px;
        border-bottom: 1px solid grey;
        cursor: pointer;
        &:hover {
          // color: lightblue;
          background-color: rgba(173, 216, 230, .3);
        }
      }
    }
  }
}
</style>