<template>
    <div id="app">{{ randomSoundFile }}</div>
</template>

<script>
import { Howl } from 'howler';

export default {
    data() {
        return {
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
            var sound = new Howl({
                src: [this.randomSoundFile],
                autoplay: true,
                loop: true,
                volume: 1,
            });
            return sound;
        },
    },
    mounted() {
        this.playRandomSound();
    },
};
</script>
