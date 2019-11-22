<template lang="pug">
  .book-card
    h2.book-card__name {{book.name}}
    p.book-card__setting {{book.setting}}
    .book-card__picture-box(v-if="!showDescripiton" @click="switchDescription")
      img.book-card__pic(:src=`book.cover`)
    .desctiption(v-if ="showDescripiton" @click="switchDescription") Блаблаблаблабла
</template>

<script>
export default {
  props: {
    book: {}
  },
  data(){return {
    showDescripiton: false



  }},
  methods:{
    switchDescription(){this.showDescripiton = !this.showDescripiton}
  }
}
</script>

<style lang="scss" scoped>
.book-card{height: 100%;
width: 100%;
display: flex; 
flex-direction: column;
align-items: center}
.book-card__picture-box{height: 100%; cursor:pointer}
.desctiption{height: 100%;width:100%; cursor: pointer;}



</style>