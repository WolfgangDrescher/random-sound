<template>
    <div id="app"></div>
</template>

<script>
import {Howl, Howler} from 'howler';

export default {
    data() {
        return {
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
            let soundFile = this.path + this.getRandomSound();
            var sound = new Howl({
                src: [soundFile],
                autoplay: true,
                loop: true,
                volume: 1,
                onend: function() {
                    console.log('Finished!');
                },
            });
            return sound;
        },
    },
    mounted() {
        this.playRandomSound();
    },
};
</script>
