<template>
    <div id="nav">
        <p>DigiList</p>
    </div>
</template>

<script>
export default {
    name: 'NavBar',
}
</script>

<style scoped>
    #nav {
        background-color: black;
        border-bottom: 2px solid orange;
        padding: 15px 50px;

    }
    p {
        color: yellow;
        text-align: center;
    }
    p:hover{
        color: #fff;
    }
</style>