<template lang="pug">
  .book-card
    h2.book-card__name {{book.name}}
    p.book-card__setting(@click="filterBySetting" v-if="isFilterApplied === false") {{book.setting}}
    
    .book-card__picture-box(v-if="!showDescripiton" @click="switchDescription")
      img.book-card__pic(:src=`book.cover`)
    .desctiption(v-if ="showDescripiton" @click="switchDescription") Блаблаблаблабла
</template>

<script>
export default {
  props: {
    book: {},
    isFiltered: Boolean
  
  },
  data(){return {
    showDescripiton: false,
    
    



  }},
  computed:{
    isFilterApplied: function(){
      return this.isFiltered
      }
      },
  methods:{
    switchDescription(){this.showDescripiton = !this.showDescripiton},
    filterBySetting(){this.$emit('filterBySetting', this.book.setting)},
    resetFilter(){this.$emit('resetFilter')}
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
.book-card__setting{cursor:pointer}



</style>