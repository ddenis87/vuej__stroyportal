<template>
  <div class="c-input">
    <div class="c-input-box">
      <input class="c-input-box__field" 
             type="text" 
             placeholder="Хочу найти..."
             v-model="inputValue"
             @input="setInputValue"
             @keyup="ligthText"
             @blur="searchLiveHidden"/>
      <div class="c-input-box__button">
        <svg width="20" height="20" viewBox="0 0 20 20" fill="none" xmlns="http://www.w3.org/2000/svg">
          <path d="M9.16667 15.8333C12.8486 15.8333 15.8333 12.8486 15.8333 9.16667C15.8333 5.48477 12.8486 2.5 9.16667 2.5C5.48477 2.5 2.5 5.48477 2.5 9.16667C2.5 12.8486 5.48477 15.8333 9.16667 15.8333Z" stroke="#708598" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
          <path d="M17.5 17.5L13.875 13.875" stroke="#708598" stroke-width="2" stroke-linecap="round" stroke-linejoin="round"/>
        </svg>
      </div>
    </div>
    
    <div class="c-input__list" v-show="(isSearchLive)">
      <ul class="list-search">
        <li class="list-search__item"
            v-for="(item, index) in listSearchLive"
            :key="index"
            @click="selectItem(item)"
            >{{ item.title }}</li>
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
  data() {
    return {
      inputValue: '',
      isSearchLive: false,
      defaultDomList: '',
    }
  },
  beforeUpdate() {
    // console.log('Before');
    // console.log(this.listSearchLive);
  },
  updated() {
    // console.log('Update');
    // console.log(document.querySelector('.c-input__list').innerHTML);
    this.defaultDomList = document.querySelector('.c-input__list');
  },
  mounted() {
    // console.log('Mount');
  },
  computed: {
    listSearchLive:{ 
      get() {
        if (this.inputValue == '') return [];
        let filterList = [];
        let vm = this;
        filterList = this.inListSearch.filter(function (item) {
          return item.title.toLowerCase().indexOf(vm.inputValue.toLowerCase()) !== -1
        });
        return (filterList.length != 0) ? filterList : filterList = [{title: 'Ничего не найдено'}];
      },
      set(empty) {
        return [];
      }
    },
    listItem() { return this.inListSearch; }
  },
  methods: {
    setInputValue() {
      if (this.inputValue == '') {
        this.isSearchLive = false;
        return;
      }
      this.isSearchLive = true;
      setTimeout(() => { this.ligthText }, 500);
    },
    ligthText() {
      let regString = new RegExp("(?![^&;]+;)(?!<[^<>]*)("+this.inputValue+")(?![^<>]*>)(?![^&;]+;)",'gi');
      let searchListDom = this.defaultDomList;
      // setTimeout(() => {
        // console.log(searchListDom.innerHTML.replace(regString, `<span style="background-color: red">${this.inputValue}</span>`));
        searchListDom.innerHTML = searchListDom.innerHTML.replace(regString, `<span style="background-color: red">${this.inputValue}</span>`);
      // }, 500);
    },
    selectItem(item) {
      this.inputValue = item.title;
      this.isSearchLive = false
    },
    searchLiveHidden() {
      setTimeout(() => {
        this.isSearchLive = false;
      }, 100);
    }
  }
}
</script>

<style lang="scss" scoped>
.c-input {
  position: relative;
  height: 40px;
  &-box {
    position: relative;
    display: flex;
    justify-content: flex-end;
    align-items: center;
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
      outline: none;
      &:hover, &:focus {
        box-shadow: 1px 1px 1px lightblue, -1px -1px 1px lightblue;
      }
    }
    &__button {
      position: absolute;
      display: inline-flex;
      align-items: center;
      height: 40px;
      padding: 0px 10px;
      border-radius: 0px 4px 4px 0px;
      box-sizing: border-box;
      cursor: pointer;
    }
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
        text-transform: lowercase;
        padding: 3px;
        padding-left: 10px;
        // border-bottom: 1px solid grey;
        cursor: pointer;
        &:hover {
          background-color: rgba(173, 216, 230, .3);
        }
      }
    }
  }
}
</style>