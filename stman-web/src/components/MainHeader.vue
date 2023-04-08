<template>
    <header class="main-header">
        <div class="logo">
            <a href="#">南通大学学生管理系统</a>
        </div>
    </header>
</template>

<script>
export default {
    name: 'MainHeader',
    data() {
        return {}
    }
}
</script>

<style scoped>
.main-header {
    background-color: #007bff;
    color: #fff;
    display: flex;
    align-items: center;
    justify-content: space-between;
    padding: 10px;
}

.logo a {
    color: #fff;
    font-size: 24px;
    font-weight: bold;
    text-decoration: none;
}
</style>
