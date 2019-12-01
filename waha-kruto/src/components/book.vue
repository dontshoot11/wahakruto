<template lang="pug">
  .book-card
    
    
    
    .book-card__picture-box(v-if="!showDescripiton" @click="switchDescription")
      img.book-card__pic(:src=`book.cover`)
    h2.book-card__name {{book.name}}
    .book-card__info(v-if ="showDescripiton" @click="switchDescription")  
      
      .book-card__author Автор: {{book.author}}
      .book-card__date Год публикации: {{book.date}}
      .book-card__setting Сеттинг: {{book.setting}}
      .book-card__description {{book.description}}
</template>

<script>
export default {
  props: {
    book: {},
   
  
  },
  data(){return {
    showDescripiton: false,
    
    



  }},

  methods:{
    switchDescription(){this.showDescripiton = !this.showDescripiton},
    
    resetFilter(){this.$emit('resetFilter')}
  }
}
</script>

<style lang="scss" scoped>
.book-card{height: 100%;
width: 100%;
display: flex; 
flex-direction: column;
align-items: center;
overflow: auto;}
.book-card__name{font-weight: bold; font-size: 20rem}
.book-card__picture-box{max-height: 100%; cursor:pointer; overflow: hidden;}
.desctiption{height: 100%;width:100%; cursor: pointer;}
.book-card__description{margin-top: 15rem;}
.book-card__pic{max-height: 100%;
width: auto

}



</style>