<template>
    <div class="container-home">
        <div class="container">
            <div class="card card-1">
                <router-link class="link" to="/listProduct">
                    <div class="card-header">
                        <img src="https://images.pexels.com/photos/7203788/pexels-photo-7203788.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
                            class="card-img" />
                    </div>
                    <div class="card-body">
                        <h3 class="card-local">Vizualizar</h3>
                        <h2 class="card-titulo">Produtos</h2>
                    </div>
                </router-link>
            </div>
            <div class="card card-2">
                <router-link class="link" to="/listclient">
                    <div class="card-header">
                        <img src="https://images.pexels.com/photos/5869616/pexels-photo-5869616.jpeg?auto=compress&cs=tinysrgb&w=600"
                            class="card-img" />
                    </div>
                    <div class="card-body">
                        <h3 class="card-local">Vizualizar</h3>
                        <h2 class="card-titulo">Cliente</h2>
                    </div>
                </router-link>
            </div>
            <div class="card card-3">
                <router-link class="link" to="/listpageassociation">
                    <div class="card-header">
                        <img src="https://images.pexels.com/photos/4464486/pexels-photo-4464486.jpeg?auto=compress&cs=tinysrgb&w=1260&h=750&dpr=1"
                            class="card-img" />
                    </div>
                    <div class="card-body">
                        <h3 class="card-local">Vizualizar</h3>
                        <h2 class="card-titulo">Associação Cliente x Produto</h2>
                    </div>
                </router-link>
            </div>
        </div>
    </div>
</template>
<script>
export default {
    name: 'home'
}
</script>

<style lang="sass" scoped>

.container 
    width: 100%
    display: flex
    justify-content: space-evenly
    flex-wrap: wrap
.link
    text-decoration: none
.card 
    width: 250px
    height: 300px
    margin: 25px
    background-color: #fff
    border-radius: 20px
    overflow: hidden
    box-shadow: 0px 0px 10px rgba(0, 0, 0, 0.7)
    transition: 0.3s
.card-header 
    width: 100%
    height: 200px
    overflow: hidden
.card-img 
    min-width: 100%
    width: auto
    height: 100%

.card-body 
    height: 170px
    padding: 15px
    text-align: center
    font-family: sans-serif
.card-local 
    font-size: 16px
    margin: 10px 0
.card-titulo 
    font-size: 32px
    margin: 15px 0
    color: #009879
.card-texto 
    font-size: 12px
    width: 250px
    margin: 0 auto
.card-footer 
    margin-top: 10px
    text-align: center
    background-color: #000
.card-footer a 
    color: #fff
    display: block
    padding: 16px
    text-decoration: none
    font-family: sans-serif
    font-weight: 600
.card-1 .card-footer 
    background-color: #2740d1
.card-1 .card-local 
    color: #000ccc
.card-2 .card-footer 
   background-color: #d12761
.card-2 .card-local 
    color: #000ccc
.card-3 .card-footer 
    background-color: #00c702
.card-3 .card-local 
    color: #000ccc
.card:hover 
    transform: scale3d(1.1, 1.1, 1)

</style>