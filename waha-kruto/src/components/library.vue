<template lang="pug">
    ul.books-list
        li.books-list__item(v-for = "book in books")
            book(:book="book")
    
</template>

<script>
import book from "../components/book"

export default {
    components: {book},
    data(){return{
    books:[]
    }
 
    },
    created(){
        let data = require('../jsons/library.json'); this.books = data
    }

}
</script>

<style lang="scss" scoped>
.books-list{
    display: grid;
    grid-template-columns: 1fr 1fr 1fr;
    justify-items: center
    
}

.books-list__item {height: 500rem; width: 100%}
</style>