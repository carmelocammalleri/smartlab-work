<script>
export default {
    name: 'Footer',
    data(){
        return{
            whatsappNumber: "393701315770"
        }
    }

}
</script>

<template>
    <footer class="footer">
        <div class="footer-links">
            <a href="https://www.instagram.com/smartlab.canicatti/" target="_blank">
                <img src="/Instagram.png" alt="Instagram" class="icon-social">
            </a>
            <a href="https://www.facebook.com/info.smartlab/?locale=it_IT" target="_blank">
                <img src="/Facebook.png" alt="Facebook" class="icon-social">
            </a>
            <a :href="'https://wa.me/' + whatsappNumber" target="_blank">
                <button class="whatsapp-button">Contattaci su WhatsApp</button>
            </a>
        </div>
    </footer>
</template>

<style>
    footer{
        background-color: black;
        color: white;
        height: 100px;
        border-top: 1px solid white;
    }

    .footer-links{
        display: flex;
        justify-content: center;
        align-items: center;
        height: 100%;
    }

    .whatsapp-button{
        display: inline-block;
        cursor: pointer;
        height: 100%;
        background-color: #0BD53E;
        border: 2px solid white;
        border-radius: 50%;
        font-size: .5rem;
        color: white;
    }

    a{
        height: 50px;
        width: 50px;
        display: block;
    }

    .icon-social{
        height: 80%;
        margin: 5px;
    }
</style>