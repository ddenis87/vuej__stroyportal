<template>
  <div class="navigation">
    <div class="navigation__logo">
      <img src="@/assets/images/logo.png">
    </div>
    <div class="navigation__control-catalog">
      <c-button inButtonType="catalog">Каталог</c-button>
    </div>
    <div class="navigation__search">
      <c-input v-model="inputValue" @input="searchLive" :inListSearch="listSearch"></c-input>
    </div>
    <div class="navigation__control-list">
      <c-button inButtonType="list">Список</c-button>
    </div>
    <div class="navigation__control-profile">
      <c-button inButtonType="profile">A</c-button>
    </div>
  </div>
</template>

<script>
import cButton from '@/components/elements/c-button';
import cInput from '@/components/elements/c-input';
export default {
  name: 'mainPageNavigation',
  components: {
    cButton,
    cInput,
  },
  data() {
    return {
      inputValue: '',
      listSearch: [
        {title: 'Труба 3'},
        {title: 'Труба 4'},
        {title: 'Профиль 6'},
        {title: 'Профиль 7'},
        {title: 'Гвоздь 3'},
        {title: 'Гвоздь 43'},
        {title: 'Гвоздь 37'},
        {title: 'Труба 7'},
        {title: 'Гвоздодер 3'},
        {title: 'Гвоздодер 6'},
        {title: 'Трубопровод 3'},
        {title: 'Трубопровод 8'},
        {title: 'Трубопровод 6'},
        {title: 'Труба прямая 4'},
        {title: 'Труба косая 4'},
        {title: 'Труба кривая 4'},
        {title: 'Труба гнутая 4'},
        {title: 'Труба загнутая 4'},
        {title: 'Загнутый гвоздь 4'},
      ],
    }
  },
  methods: {
    searchLive(inputValue) {
      console.log(inputValue);
    }
  }
}
</script>

<style lang="scss" scoped>
.navigation {
  display: grid;
  grid-template-areas: "navigation__logo navigation__control-catalog navigation__search navigation__control-list navigation__control-profile";
  grid-template-rows: 100%;
  grid-template-columns: auto auto 1fr auto auto;
  justify-content: space-between;
  max-width: 1103.5px;
  width: 100%;
  margin-left: auto;
  margin-right: auto;
  align-items: center;
  box-sizing: border-box;

  &__logo { grid-area: navigation__logo; max-width: 221px; height: 48px; margin-right: 12px;}
  &__control-catalog { grid-area: navigation__control-catalog; max-width: 116px; margin: 0px 12px;}
  &__search { grid-area: navigation__search; box-sizing: border-box; margin: 0px 12px;}
  &__control-list { grid-area: navigation__control-list; max-width: 116px; margin: 0px 12px;}
  &__control-profile { grid-area: navigation__control-profile; margin-left: 12px}
}

@media screen and (max-width: 1024px) {
  .navigation {
    display: grid;
    grid-template-areas: "navigation__control-catalog navigation__logo navigation__control-profile"
                         "navigation__search navigation__search navigation__control-list";
    grid-template-rows: auto auto;
    grid-template-columns: 1fr 1fr auto;
    width: 100%;
    &__control-catalog { margin-left: 0px; margin-top: 10px; }
    &__search { margin-left: 0px; margin-top: 10px; }
    &__control-list { margin-right: 0px; margin-top: 10px; }
    &__control-profile { margin-top: 10px; margin-right: 0px; }
  }
}
</style>