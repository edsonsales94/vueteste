<template>
    <!-- Site footer -->
    <footer class="site-footer">
        <div class="container">
            <div class="container-footer">
                <div>
                    <h6>Brasil</h6>
                    <ul class="footer-links">
                        <li><a href="#">Manaus-AM</a></li>
                        <li><a href="#">São Paulo-SP</a></li>
                    </ul>
                </div> 

                <div>
                    <h6>Auxiliar</h6>
                    <ul class="footer-links">
                        <li><a href="#">Ferramenta</a></li>
                        <li><a href="#">Contatos</a></li>
                        <li><a href="#">Suporte</a></li>
                    </ul>
                </div>

                <div>
                    <h6>Segue</h6>
                    <ul class="footer-links">
                        <li><a href="#">Sobre</a></li>
                        <li><a href="#">Contato</a></li>
                        <li><a href="#">Politica de Privacidade</a></li>
                        <li><a href="#">Site</a></li>
                    </ul>
                </div>
            </div>
            <hr>
        </div>
        <div class="container">
            <div>
                <div>
                    <p class="copyright-text">Copyright &copy; 2023 All Rights Reserved by
                        <a href="#">SalesSystem</a>.
                    </p>
                </div>

                <div>
                    <ul class="social-icons">
                        <li><a class="facebook" href="#"><i class="fa fa-facebook"></i></a></li>
                        <li><a class="twitter" href="#"><i  class="fa fa-twitter"></i></a></li>
                        <li><a class="dribbble" href="#"><i class="fa fa-dribbble"></i></a></li>
                        <li><a class="linkedin" href="#"><i class="fa fa-linkedin"></i></a></li>
                    </ul>
                </div>
            </div>
        </div>
    </footer>
</template>

<script>
export default {
    name: "Footer"
}
</script>

<style lang="sass" scoped>
.site-footer 
    background-color: #26272b
    padding: 45px 0 20px
    font-size: 15px
    line-height: 24px
    color: #737373
.site-footer hr 
    border-top-color: #bbb
    opacity: 0.5
.site-footer hr.small 
    margin: 20px 
.site-footer h6 
    color: #fff
    font-size: 16px
    text-transform: uppercase
    margin-top: 5px
    letter-spacing: 2p
.site-footer a 
    color: #737373
.site-footer a:hover
    color: #3366cc
    text-decoration: none
.footer-links
    padding-left: 0
    list-style: none
.footer-links li 
    display: block
.footer-links a 
    color: #737373
.footer-links a:active
.footer-links a:focus
.footer-links a:hover 
    color: #3366cc
    text-decoration: none
.footer-links.inline li 
    display: inline-block
.site-footer .social-icons 
    text-align: righ
.site-footer .social-icons a 
    width: 40px
    height: 40px
    line-height: 40px
    margin-left: 6px
    margin-right: 0
    border-radius: 100%
    background-color: #33353d
.copyright-text 
    margin: 0

@media (max-width:991px) 
    .site-footer [class^=col-] 
        margin-bottom: 30px

@media (max-width:767px) 
.site-footer 
    padding-bottom:0
.site-footer .copyright-text
.site-footer .social-icons 
    text-align: center
.social-icons 
    padding-left: 0
    margin-bottom: 0
    list-style: none
.social-icons li
    display: inline-block
    margin-bottom: 4px
.social-icons li.title 
    margin-right: 15px
    text-transform: uppercase
    color: #96a2b2
    font-weight: 700
    font-size: 13px
.social-icons a 
    background-color: #eceeef
    color: #818a91
    font-size: 16px
    display: inline-block
    line-height: 44px
    width: 44px
    height: 44px
    text-align: center
    margin-right: 8px
    border-radius: 100%
    -webkit-transition: all .2s linear
    -o-transition: all .2s linear
    transition: all .2s linea
.social-icons a:active
.social-icons a:focus
.social-icons a:hover 
    color: #fff
    background-color: #29aafe
.social-icons.size-sm a 
    line-height: 34px
    height: 34px
    width: 34px
    font-size: 14px
.social-icons a.facebook:hover 
    background-color: #3b5998
.social-icons a.twitter:hover 
    background-color: #00aced
.social-icons a.linkedin:hover 
    background-color: #007bb6
.social-icons a.dribbble:hover 
    background-color: #ea4c89
.container-footer 
    display: flex
@media (max-width:767px) 
    .social-icons li.title 
        display: block
        margin-right: 0
        font-weight: 600
</style>