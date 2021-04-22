<template>
    <div>
        <!-- <img alt="Vue logo" src="./assets/logo.png" /> -->
        <HelloWorld msg="Hello Vue 3 + TypeScript + Vite" />
        <router-link to="/">Go to Home</router-link>
        <router-link to="/vuex">Go to vuex</router-link>
        <router-link to="/axios">Go to Axios</router-link>
        <router-view></router-view>
        <button @click="add">add</button>
        <p>{{ count }}</p>
        <el-row>
            <el-button>默认按钮</el-button>
            <el-button type="primary">主要按钮</el-button>
            <el-button type="success">成功按钮</el-button>
            <el-button type="info">信息按钮</el-button>
            <el-button type="warning">警告按钮</el-button>
            <el-button type="danger">危险按钮</el-button>
        </el-row>
    </div>
</template>

<script lang="ts">
import { defineComponent, computed } from 'vue'
import { useStore } from 'vuex'
import HelloWorld from './components/HelloWorld.vue'
import axios from './utils/axios'

export default defineComponent({
    name: 'App',
    components: {
        HelloWorld
    },
    setup() {
        const store = useStore()
        axios
            .get('/users/XPoet')
            .then((res: any) => {
                // eslint-disable-next-line no-console
                console.log('res: ', res)
            })
            .catch((err: any) => {
                // eslint-disable-next-line no-console
                console.log('err: ', err)
            })
        return {
            add: () => store.commit('increment'),
            count: computed(() => store.state.count)
        }
    }
})
</script>

<style>
#app {
    font-family: Avenir, Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    text-align: center;
    color: #2c3e50;
    margin-top: 60px;
}
</style>
