<template>
    <div class="home">
        <img alt="Vue logo" src="../assets/logo.png" style="display: none;">
        <AgoraLiveDemo/>
    </div>
</template>

<script>
    // @ is an alias to /src
    import AgoraLiveDemo from '@/components/AgoraLiveDemo.vue'

    export default {
        name: 'Home',
        components: {
            AgoraLiveDemo
        }
    }
</script>
