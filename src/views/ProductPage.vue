<template>
    <form class="container-form">
        <div class="container-input">
            <label for="name">Nome Cliente: </label>
            <input type="text" v-model="name">
        </div>
        <div class="container-input">
            <div class="radio">
                <label for="flag" style="margin-right: 15px;">Ativo</label>
                <input class="radio-btn" type="radio" id="flag" v-model="ativo" :value="true">
            </div>
            <div class="radio">
                <label for="flag">Inativo</label>
                <input class="radio-btn" type="radio" id="flag" v-model="ativo" :value="false">
            </div>
        </div>
        <div class="container-input">
            <input  class="submit-btn" type="submit" @click="cadProduto" value="Cadastrar Produto">
        </div>
        <div class="container-input">
            <span class="messege">{{ msg }}</span>
            <span class="error">{{ error }}</span>
        </div>
    </form>
</template>

<script>
export default {
    name: "Product",
    data() {
        return {
            name: '',
            ativo: false,
            msg: null,
            error: ''
        }
    },
    methods: {
        async cadProduto(e) {

            if (this.name!=="") {

                e.preventDefault()
                const data = {
                    nome: this.name,
                    ativo: this.ativo,
                }
                //requisicao post
                const dataJson = JSON.stringify(data)
                const req = await fetch("http://localhost:3000/product", {
                    method: "POST",
                    headers: { "Content-Type": "application/json" },
                    body: dataJson
                });
                const res = await req.json()
                console.log(res)
                this.msg = "Cadastro realizado com sucesso!"
                // // limpar campos
                this.name = ""
                this.ativo = null
                setInterval(()=>this.msg="" ,3000)

            } else { 
                //validar campo vazio
                e.preventDefault()
                this.error = 'O campos nome não pode ficar em Vazio!!!'
                setInterval(()=>this.error="" ,5000)
                
            }
        }
    }

}
</script>

<style lang="sass" scoped>
.container-form 
    max-width: 100%
    margin: 0 auto
    padding: 25px 0
    background: #F5F5DC
    
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
    text-align: center
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
.messege
    background: green
    width:  60%
    text-align: center
    color: #fff
    font-weight: bold
    font-size: 18px
.error
    background: red
    width:  60%
    text-align: center
    color: #fff
    font-weight: bold
    font-size: 18px
</style>
