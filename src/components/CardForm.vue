<template>
            <form class="form" @submit.prevent>
                <div class="row-1">
                    <div class="required__field">
                        <div class = "row-name" >Наимеование товара</div>
                        <img :src="require('/assets/RedPoint.png')" alt="red__point" class="red__point">
                    </div>
                    <input 
                    v-model = "card.Name"
                    @input = "NameValue"
                    :class="{'red__input':reminder1 , 'default__input':!reminder1}"
                    type="text" 
                    placeholder="Введите наименование товара">
                    <div v-show="reminder1" class="reminder ">Поле является обязательным</div>
                    <div v-if="!reminder1" class="off__reminder"></div>
                </div>
                <div class="row-1">
                    <div class = "row-name">Описание товара</div>
                    <input 
                    v-model = "card.Description"
                    type="text" 
                    class="text__control"
                    placeholder="Введите описание товара">
                </div>
                <div class="row-1">
                    <div class="required__field">
                        <div 
                        class = "row-name" 
                        >Ссылка на изорбражение товара</div>
                        <img :src="require('/assets/RedPoint.png')" alt="" class="red__point">
                    </div>
                    <input v-model = "card.image" @input = "imageValue" type="text"  :class="{'red__input': reminder2 , 'default__input': !reminder2}" placeholder="Введите ссылку">
                    <div v-show="reminder2"  class="reminder">Поле является обязательным</div>
                    <div v-if="!reminder2" class="off__reminder"></div>
                </div>
                <div class="row-1">
                    <div class="required__field">
                        <div class = "row-name" >Цена товара</div>
                        <img :src="require('/assets/RedPoint.png')" alt="" class="red__point">
                    </div>
                    <input v-model = "card.Price" @input = "PriceValue" type="text"  :class="{'red__input': reminder3 , 'default__input': !reminder3}" placeholder="Введите цену">
                    <div v-show="reminder3" class="reminder">Поле является обязательным</div>
                    <div v-if="!reminder3" class="off__reminder"></div>
                </div>
                <button @click="addCard" :class="{'product__search': !ActiveBox , 'product__search1': ActiveBox}" >Добавить товар</button>
            </form>
</template>

<script>
export default {
    data () {
        return {
            card: {
                Name:'',
                Description:'',
                image: '',
                Price: '',
            },
            reminder1 : false,
            reminder2 : false, 
            reminder3 : false,
        }
    },
    methods : {
            NameValue()
            {
                if(this.card.Name != ''){
                    this.reminder1 = false;
                }
            },
            imageValue()
            {
                if(this.card.image != ''){
                    this.reminder2 = false; 
                }
            },
            PriceValue()
            {
                if(this.card.Price != ''){
                    this.reminder3 = false; 
                }
            },
            addCard(){
                if(this.card.Name === '')
                    {
                        this.reminder1 = true;
                    }
                if(this.card.image === '')
                    {
                        this.reminder2 = true; 
                    }
                if(this.card.Price === '')
                    {
                        this.reminder3 = true; 
                    }
                if((this.card.Name && this.card.image && this.card.Price) != '')
                {
                    this.card.id = Data.now()
                    this.$emit('create' , this.card)
                    this.card = {
                        Name:'',
                        Description:'',
                        image: '',
                        Price: '',
                    }
                }
            },
    },
    computed : {
            ActiveBox(){
                return (this.card.Name && this.card.image && this.card.Price && this.card.Description);
            },
        },
}
</script>

<style>
.form{
    width: 332px;
    height: 440px;
    background-color: #FFFEFB;
    border-radius: 4px;
    padding-top: 24px;    
    margin-left: 32px;
}

.reminder{
    display: block;
    width: 100px;
    height: 10px;
    font-style: normal;
    font-weight: 400;
    font-size: 8px;
    line-height: 10px;
    letter-spacing: -0.02em;
    color: #FF8484;
    margin-bottom: 4px;
}

.off__reminder{
    display: block;
    width: 100px;
    height: 10px;
    margin-bottom: 2px;
} 

.red__input.active{
    border-color: 
    #FF8484;
}

.required__field{
    display: flex;
}

.red__point{
    width: 4px;
    height: 4px;
}

.row-1{
    margin: 0px 24px 4px;
}

.text__control{
    border: none;
    width: 284px;
    height: 108px;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
    border-radius: 4px;
    font-style: normal;
    font-weight: 400;
    font-size: 12px;
    line-height: 15px;
    outline: none;
    margin-bottom: 16px;
}

.row-name{
    font-size: 10px;
    font-weight: 400;
    margin-bottom: 4px;
}

.default__input{
    border: none;
    width: 284px;
    height: 36px;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
    border-radius: 4px;
    outline: none;
    font-style: normal;
    font-weight: 400;
    font-size: 12px;
    line-height: 15px;
    padding: 5px 0px 0px 16px;
}

.red__input{
    width: 284px;
    height: 36px;
    border-radius: 4px;
    outline: none;
    font-style: normal;
    font-weight: 400;
    font-size: 12px;
    line-height: 15px;
    border-color:#FF8484;
    padding: 10px 0px 0px 16px;
}

.product__search{
    width: 284px;
    height: 36px;
    background: #EEEEEE;
    border-radius: 10px;
    margin: 8px 24px 24px;
    border: #B4B4B4;
    font-family: 'Inter';
    font-style: normal;
    font-weight: 600;
    font-size: 12px;
    line-height: 15px;
    text-align: center;
    letter-spacing: -0.02em;
    color: #B4B4B4;
    cursor: url("/assets/hover.png"),pointer;
}

.product__search1{
    width: 284px;
    height: 36px;
    background: #7BAE73;
    border-radius: 10px;
    margin: 8px 24px 24px;
    border: #B4B4B4;
    font-family: 'Inter';
    font-style: normal;
    font-weight: 600;
    font-size: 12px;
    line-height: 15px;
    text-align: center;
    letter-spacing: -0.02em;
    color: #FFFFFF;
    cursor: url("/assets/hover.png"),pointer;
}
</style>