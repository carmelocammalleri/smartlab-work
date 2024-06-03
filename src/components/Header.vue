<script>
export default {
    name: 'Header',
    data(){
        return{

        }
    }

}
</script>

<template>
    <header>
        <div class="container-header">
            <img id="logo"src="/smartlab.png" alt="logo">
            <div class="container-text-logo">
                <h1>Smartlab</h1>
                <span>La tua scelta energetica</span>
            </div>
        </div>
    </header>
</template>

<style>
    header{
        background-color: black;
        height: 70px;
        border-bottom: 1px solid rgb(4, 192, 4);
        color: white;
        padding: 10px;
    }

    .container-header{
        display: flex;
        height: 100%;
    }

    .container-text-logo{
        height: 100%;
        font-size: .7rem;
    }

    #logo{
        height: 100%;
        margin-right: 10px;
    }
</style>