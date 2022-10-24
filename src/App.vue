<template>
    <Header    
        :options = "options"
        v-model = "selectOption"
    />
    <main class="main" id="main">
    <CardForm  @create = "addCard"/>
    <CardList 
        :cards = "cards"
        @remove = "delCard"
    />
    </main>
</template>


<script>
import Header from "./components/Header.vue"
import CardForm from "./components/CardForm.vue"
import CardList from "./components/CardList.vue"
export default {
    components : {
        CardForm, CardList, Header
    },
    data() {
        return {
            cards:[
                { id: 1,image: require('/assets/Card.png'), Name:'Фотоаппарат', Description:' Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк'
                    ,Price:' 12 000 руб.'},
                    {id: 2,image:require('/assets/Card.png'),Name:'Игровая приставка',Description: 'Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк'
                        ,Price:' 15 000 руб.'},
                    {id: 3, image:require('/assets/Card.png'),Name: 'Арбалет',Description:' Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк'
                        ,Price:' 10 000 руб.'},
                    { id: 4,image:require('/assets/Card.png'),Name: 'Кукуруза',Description:' Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк'
                        ,Price:' 11 000 руб.'},
                    { id: 5,image:require('/assets/Card.png'),Name: 'Солнце',Description:' Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк'
                        ,Price:' 10 000 руб.'},
                    { id: 6,image:require('/assets/Card.png'), Name: 'Наимеование товара ', Description:' Довольно-таки интересное описание товара в несколько строк. Довольно-таки интересное описание товара в несколько строк'
                        ,Price:' 14 000 руб.'}
                ],       
            options:[
                { text:'По умолчанию', value: 'default'},
                { text:'По цене max', value: 'PriceMax'},
                { text:'По цене min', value: 'PriceMin'}
            ],
            selectOption: 'default',
        }                
    },
    methods : {
        addCard(card) {
            this.cards.push(card);
        },
        delCard(card) {
            this.cards = this.cards.filter(c => c.id !== card.id)
        },
    },
    watch: {
        selectOption(newValue)
        {   
            
            if(newValue === 'PriceMax')
            {
                newValue = 'Price'
                this.cards.sort((card1,card2) => {
                return card1[newValue]?.localeCompare(card2[newValue])
                })
            }
            if(newValue === 'PriceMin')
                {
                    newValue = 'Price'
                    this.cards.sort((card1,card2) => {
                    return card2[newValue]?.localeCompare(card1[newValue])
                })
            }
            if(newValue === 'default')
                {
                    return 0;
                }
        },
    }
}        
</script>

<style>
.main{
    display: flex;
}
</style>