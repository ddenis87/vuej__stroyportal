<template>
  <div class="content">
    <h3 class="content__title">Список для проверки поиска</h3>
    <ul class="content__list">
      <li class="content__list-item"
          v-for="(item, index) in listSearch"
          :key="index">{{ item.title }}</li>
    </ul>
  </div>
</template>

<script>
export default {
  name: 'mainPageContent',
  data() {
    return {
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
  }
}
</script>