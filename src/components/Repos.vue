<template lang="pug">
.sort
    h2 Сортировка
    .sort-box
        button(
            v-for="(btn, index) in btns"
            :key="btn.name"
            :class="{active: index == isActive}"
            @click="sortRepos(index, btn.sortType)"
        ) {{ btn.name }} 
.repos
   .repos-item(
        v-for="repos in repositories"
        :key="repos.id"
    ) 
        .repos-item-left
            h3 {{repos.name}}
            p Кол-во звёзд: {{repos.stargazers_count}}
            p Дата добавления: {{new Date(repos.created_at).toLocaleDateString()}}
        a(:href="repos.html_url") ПОСЕТИТЬ
</template>
<script>
import { mapState, mapMutations } from "vuex";
export default {
    data() {
        return {
            isActive: 0,
            btns: [
                { name: 'ИМЯ', sortType: 'name' },
                { name: 'ЗВЕЗДЫ', sortType: 'stargazers_count' },
                { name: 'ДАТА', sortType: 'created_at' },
            ]
        }
    },
    computed: {
        ...mapState(['repositories'])
    },
    methods: {
        ...mapMutations(['sort']),
        sortRepos(index, sortType){
            this.isActive = index
            this.sort(sortType)
        }
    },
}
</script>
<style lang="scss">
    
</style>