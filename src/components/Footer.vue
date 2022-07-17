<template>
    <footer id="footer">
        <p>DigiList &copy; 2022</p>
    </footer>
</template>

<script>

export default {
    name: 'Footer',
}
</script>

<style scoped>
    #footer{
        height: 100px;
        background-color: black;
        border-top: 4px solid orange;
        display: flex;
        align-items: center;
        justify-content: center;
        width: 100%;
    }
    p {
        color: yellow;
        text-align: center;
    }
</style>