<template>
            <div class="products" >
                <div class="cards" v-for="card in cards ">
                    <img class = "del__card" @click="$emit('remove',card)" :src = "require('/assets/DeletIcon.png')" alt=""/>
                    <img
                        class="product__foto"
                        :src="card.image"
                        alt="" 
                        width=332px;
                        height=200px
                        :key = "card.id"
                    >
                    <div class="card__description">
                        <h2 class="product__name">{{card.Name}}</h2>
                        <div class="product__description">{{card.Description}}</div>
                        <div class="prouct__price">{{card.Price}}</div>
                    </div>
                </div>
            </div>
</template>

<script>
export default {
    props : {
        cards : {
            type: Array,
            required: true,
        },
    }
} 
</script>

<style>
.cards{
    width: 332px;
    height: 423px;
    background: #FFFEFB;
    box-shadow: 0px 20px 30px rgba(0, 0, 0, 0.04), 0px 6px 10px rgba(0, 0, 0, 0.02);
    border-radius: 4px;
    cursor: url("/assets/hover.png"),pointer;
    position: relative;
    margin-bottom: 16px;
    margin-left: 16px;
}

.del__card{
    position: absolute;
    left: 93%;
    top: -4%;
    display: none;
}

.cards:hover .del__card{
    position: absolute;
    left: 93%;
    top: -4%;
    display: block;
    cursor: url("/assets/hover.png"),pointer;
}

.products{
    width: 1044px;
    display: flex;
    flex-wrap: wrap;    
    align-items: stretch;  
    align-content: stretch;  
}

.product__foto{
    width: 332px;
    height: 200px;
    border-radius: 4px 4px 0px 0px;
}

.product__name{
    width: 201px;
    height: 25px;
    font-style: normal;
    font-weight: 600;
    font-size: 20px;
    line-height: 25px;
    color: #3F3F3F;
    margin: 0px;
    margin: 16px 0px 16px 16px;
}

.product__description{
    width: 300px;
    height: 80px;
    font-style: normal;
    font-weight: 400;
    font-size: 16px;
    line-height: 20px;
    color: #3F3F3F;
    margin: 16px 16px 32px;
}

.prouct__price{
    width: 117px;
    height: 30px;
    font-style: normal;
    font-weight: 600;
    font-size: 24px;
    line-height: 30px;
    color: #3F3F3F;
    margin: 0px 0px 24px 16px;
}
</style>