<template>
    <el-row type="flex">
        <el-col v-for="category in categories" :key="category.id" :xs="12" :sm="6">
            <el-card class="category" shadow="never">
                <div class="media">
                    <img :src="category.icon" class="category-icon"/>
                    <div class="media-body">
                        <router-link :to="{name: 'category-id', params: {id: category.id}}">
                            <div class="category-name">{{ category.name }}</div>
                        </router-link>
                    </div>
                </div>
            </el-card>
        </el-col>
    </el-row>
</template>

<script>
export default {
    name: 'catalog',
    layout: 'blog',
    head() {
        return {
            title: '分类列表'
        }
    },
    data() {
        return {
            categories: []
        }
    },
    async asyncData({app}) {
        let response = await app.$axios.get('categories')
        return {categories: response.data};
    }
}
</script>