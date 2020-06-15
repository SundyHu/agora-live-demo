<template>
    <div class="home">
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