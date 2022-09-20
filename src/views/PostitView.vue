<template>
    <Postit />
</template>

<script>
import Postit from '../components/Postit.vue';

export default {
    components: {
        Postit
    },
};
</script>

<style >
body{
    margin: opx;
    padding: opx;
    background-image: url(src/assets/chalkboard_texture_bg.jpg);
    background-repeat: no-repeat;
    background-size: auto;
}
</style>
