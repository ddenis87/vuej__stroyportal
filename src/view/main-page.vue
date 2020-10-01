<template>
  <div class="main-page">
    <div class="main-page__head">
      <main-page-head></main-page-head>
    </div>
    <div class="main-page__navigation">
      <main-page-navigation></main-page-navigation>
    </div>
    <div class="main-page__content"></div>
  </div>
</template>

<script>
import mainPageHead from '@/components/main-page/__head';
import mainPageNavigation from '@/components/main-page/__navigation';

export default {
  name: 'mainPage',
  components: {
    mainPageHead,
    mainPageNavigation,
  }
}
</script>

<style lang="scss">
$maxWidth: 1280px;

$heightHead: 32px;
$heightNavigation: 76px;

.main-page {
  display: grid;
  grid-template-areas: "main-page__head" 
                       "main-page__navigation" 
                       "main-page__content";
  grid-template-rows: $heightHead $heightNavigation auto;
  grid-template-columns: 1fr;
  max-width: $maxWidth;
  width: 100%;
  margin-left: auto;
  margin-right: auto;

  &__head { 
    grid-area: main-page__head; 
    display: flex;
    align-items: center;
    background-color: #FAFBFC; 
    box-sizing: border-box;
  }
  &__navigation {
    grid-area: main-page__navigation; 
    display: flex;
    align-items: center;
    box-sizing: border-box;
  }
  &__content { grid-area: main-page__content; border: 1px solid red; min-height: 600px;}
}

</style>