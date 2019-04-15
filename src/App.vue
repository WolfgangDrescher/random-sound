<template>
    <div id="app" @click="playRandomSound">{{ randomSoundFile }}</div>
</template>

<script>
import { Howl } from 'howler';

export default {
    data() {
        return {
            howl: null,
            randomSoundFile: null,
            path: '/sounds/',
            sounds: [
                '1152_1024.mp3',
                '1280_1024.mp3',
                '1280_1152.mp3',
            ],
        };
    },
    methods: {
        getRandomSound() {
            return this.sounds[Math.floor(Math.random() * this.sounds.length)];
        },
        playRandomSound() {
            this.randomSoundFile = this.getRandomSound();
            if(this.howl !== null) {
                this.howl.stop();
            }
            this.howl = new Howl({
                src: [this.path + this.randomSoundFile],
                autoplay: true,
                loop: true,
                volume: 1,
            });
        },
    },
    mounted() {
        this.playRandomSound();
    },
};
</script>

<style>
body {
    height: 100vh;
    margin: 0;
}
</style>

<style scoped>
#app {
    display: flex;
    align-items: center;
    height: 100%;
    justify-content: center;
    align-items: center;
    font-size: 5rem;
    font-family: Monaco, 'Courier New', Courier, monospace;
    color: #f3f3f3;
    opacity: 0;
    cursor: pointer;
}

#app:hover {
    opacity: 1;
}
</style>