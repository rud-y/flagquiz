<template>
    <div>
        <ul>
        <li class="name-list"><button class="name-btn">{{country}}</button></li>
        </ul>
    </div>
</template>

<script>
export default {
    name: 'CountryName',
    props: ['country']
}

</script>

<style scoped>

.name-list {
    list-style: none;
}
.name-btn {
    color: white;
    background-color: black;
    font-weight: bold;
    padding: 5px;
}
</style>