<!--suppress ALL -->
<template>
    <div class="sidebar" data-state="false">
        <div class="site-title">
            <saber-link to="/">
                <h1>{{ title }}</h1>
                <h2>{{ subTitle }}</h2>
            </saber-link>
        </div>
        <div class="site-nav">
            <div class="nav-item" v-if="screenWidth <= 760">
                <saber-link :to="spHome.link">{{ spHome.title }}</saber-link>
            </div>
            <div class="nav-item" v-for="(item, index) in nav" :key="index">
                <saber-link :to="item.link">{{ item.title }}</saber-link>
            </div>
        </div>
        <div class="site-copyright">
            <p>
                Powered by <a href="https://github.com/egoist/saber" target="_blank" rel="noopener noreferrer">Saber</a><br />
                Theme <a href="https://github.com/iCyris/Ume" target="_blank" rel="noopener noreferrer">Ume</a><br />
                © 2019 <a href="https://cyris.pen.moe" target="_blank" rel="noopener noreferrer">Cyris's pen</a>
            </p>
        </div>
    </div>
</template>

<script>
    import { themeConfig } from 'saber/config'

    export default {
        data() {
            return {
                title: themeConfig.title,
                subTitle: themeConfig.subTitle,
                nav: themeConfig.sideBar,
                spHome: themeConfig.spHome,
                screenWidth: typeof document === 'object' ? document.documentElement.clientWidth : ''
            }
        },

        mounted: function () {
            window.addEventListener('resize', this.handleResize)
        },
        beforeDestroy: function () {
            window.removeEventListener('resize', this.handleResize)
        },

        methods: {
            handleResize (event) {
                this.screenWidth = document.documentElement.clientWidth
            }

        }
    }
</script>