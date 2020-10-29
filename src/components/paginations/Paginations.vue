<template>
    <div class="pagination">

      
 <div class="pagination_left arrow" v-if="hasPrev()" @click.prevent="changePage(prevPage)">
            <a href="">Prev</a>
        </div>  

        <div class="pagination_mid">
            <ul>
                <li v-for='page in pages' v-bind:key='page'>
                    <a href=""
                     @click.prevent='changePage(page)' :class='{active: current == page}'>
                     {{page}}
                     </a>
                </li>
            </ul>
        </div>

        
        <div class="pagination_right arrow"  @click.prevent="changePage(nextPage)">
            <a href="">Next</a>
        </div>

     

    </div>
</template>

<script>

export default {
    props:{
        current: {
            type: Number,
            default: 1
        },
        total:{
            type: Number,
            default: 1
        },
        perPage: {
            type:Number,
            default: 32
        },
        pageRange:{
            type: Number,
            default: 1
        }
    },
   computed:{

        pages(){
            let pages = []
            for(let i  = this.rangeStart; i <= this.rangeEnd; i++) {
                pages.push(i)
            }
            return pages
        },

        rangeStart(){
         let start = this.current - this.pageRange
         return start > 0 ? start : 1
        },

        rangeEnd(){
         let end = this.current + this.pageRange
         return (end < this.totalPages) ? end : this.totalPages
        },

        totalPages(){
            return Math.ceil(this.total/this.perPage)
        },

        nextPage(){
            return this.current + 1
        },
            prevPage(){
            return this.current - 1
        },

   },
   methods:{
      
       hasPrev(){
           return this.current >= 1
       },

    //    hasNext(){
    //        return this.current <= this.totalPages
    //    },
       changePage(page){
           this.$emit('page-changed',page)
           console.log(page)
       }
   }

}
</script>


<style scoped>
.pagination{

    padding: 1rem 0;
    display: flex;
    justify-content: space-around;
}


a{
    text-decoration: none;
    border: 2px solid rgb(110, 110, 110);
    border-radius: .3rem;
    padding: 0 1rem;
    cursor: pointer;
    font-size: 2rem;
    color: rgb(110, 110, 110);
}

a:hover, a.active{
    text-decoration: none;
    color: #c74cf8;
    border: 2px solid  #c74cf8;
}

span{
    font-size: 2rem
}

.pagination_mid ul {
display: flex;
justify-content: center;
list-style: none;
padding: 0;
margin: 0;
}
.pagination_mid li {
display: flex;
    margin: 0 .3rem;
}


</style>