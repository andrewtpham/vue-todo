<template>
    <header class="header">
        <h1>Task List</h1>
        <div id="nav">
            <router-link to="/">Home</router-link> |
            <router-link to="/about">About</router-link>
        </div>
    </header>
</template>

<script>
export default {
    name: "Header"
}
</script>

<style scoped>
    .header {
        background: #EFFBFB;
        color: #25CED1;
        text-align: center ;
        padding: 10px;
        font-family: Arial, Helvetica, sans-serif;
        font-weight: 300;
    }

    .header a{ 
        color: #fff;
        padding-right: 5px;
        text-decoration: none;
    }

    #nav a.router-link-exact-active {
    color: #25CED1;
    }

</style>