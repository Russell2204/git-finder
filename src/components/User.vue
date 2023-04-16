<template lang="pug">
.user(v-if="user")
    .user-left
        img(:src="user.avatar_url", :alt="user.login")
        a(:href="user.html_url") ПОСЕТИТЬ
    .user-right
        p {{user.login}} 
        p Репозиториев: 
            span {{ user.public_repos }}
        p Создан: 
            span {{ new Date(user.created_at).toLocaleDateString() }}
        p Подписчиков: 
            span {{user.followers}}
        p Подписок: 
            span {{user.following}} 
//- .user(v-else)
//-     .user-left
//-         img(src="", alt="")
//-         a(href="") ПОСЕТИТЬ
//-     .user-right
//-         p USER
//-         p Репозиториев: 
//-             span 1
//-         p Создан: 
//-             span 10.10.10
//-         p Подписчиков: 
//-             span 100
//-         p Подписок: 
//-             span 0
</template>
<script>
import { mapState } from "vuex";
export default {
    computed: {
        ...mapState(['user'])
    },
}
</script>
<style lang="scss">
    
</style>