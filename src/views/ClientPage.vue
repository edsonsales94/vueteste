<template>
    <div class="container-form">
        <div class="container-input">
            <label for="name">Nome Cliente: </label>
            <input type="text">
        </div>
        <div class="container-input">
            <label for="document">Documento: </label>
            <input type="text">
        </div>
        <div class="container-input">
            <label for="phone">Telefone: </label>
            <input type="text">
        </div>
        <div class="container-input">
            <label for="email">E-mail: </label>
            <input type="email">
        </div>
        <div class="container-input">
            <div class="radio">
                <label for="flag" style="margin-right: 15px;">Ativo</label>
                <input class="radio-btn" type="radio" id="flag" name="ativo" value="1">
            </div>
            <div class="radio">
                <label for="flag">Inativo</label>
                <input class="radio-btn" type="radio" id="flag" name="ativo" value="1">
            </div>
        </div>
        <div class="container-input">
            <input class="submit-btn" type="submit" value="Cadastrar CLiente">
        </div>
    </div>
</template>

<script>
export default {

}
</script>

<style lang="sass" scoped>
.container-form 
    max-width: 100%
    margin: 0 auto
    padding: 25px 0
    
.container-input
    width:80%
    display: flex
    flex-direction: column
    margin-bottom: 20px
.container-input label, .submit-btn
    text-align: left
    margin-left: 19%
    
label
    font-weight: bold
    margin-bottom: 15px
    color: #222
    padding: 5px 10px
    border-left: 4px solid #fcba03
    font-size: 22px

input,select
    padding: 5px 10px
    width: 60%
.radio
    display: flex
    width: 60%
    margin-bottom: 10px
    justify-content: flex-start
    flex-direction: row

#flag
    width: 10%
    margin: 0
    padding: 0
    
.radio label
    border-left: none
    margin: 0
    padding: 0
.submit-btn
    background-color: #222
    color:#fcba03
    font-weight: bold
    border: 2px solid #222
    padding: 10px
    font-size: 16px
    margin: 0 auto
    cursor: pointer
    transition: .5s    
.submit-btn:hover 
    background-color: transparent
    color: #222


</style>