<template>
    <header class="header">
        <h1 class="row">Добавление товара</h1>
        <div class="sorting__list">
            <select 
                v-model="modelValue" 
                class="sorting__name"
                @change = "changeOptions"
            >
                <option 
                    v-for="option in options" 
                    :value="option.value"
                    :key = "option.value"
                >
                    {{option.text}}
                </option>
            </select>
        </div>
    </header>
</template>

<script>
export default {
    props : {
        options: {
            type : Array,
            required : true,
        },
        modelValue: {
            type: String,
        }
    },
    methods: {
        changeOptions(event){
            this.$emit('update:modelValue',event.target.value)
        },
    },
}
</script>

<style>
.header{
    width: 100%;
    display: flex;
    justify-content: space-between;    
}

.row
{
    margin: 32px 0px 16px 31px;
}

.sorting__list{
    width: 121.49px;
    height: 36px;
    display: flex;
    align-items: center;
    margin: 31px 31px 16px 0px;
    background: #FFFEFB;
    box-shadow: 0px 2px 5px rgba(0, 0, 0, 0.1);
    border-radius: 4px;
}

.sorting__name{
    width: 105px;
    height: 15px;
    margin: 0 auto;
    color: #B4B4B4;
    font-size: 12px;
    font-weight: 400px;
    border: none;
    outline: none;
}
</style>