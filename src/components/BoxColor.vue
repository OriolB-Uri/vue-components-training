<script setup>

defineProps(['r', 'g', 'b'])

function rgbToHex(r, g, b) {
    const componentToHex = (c) => {
        const hex = c.toString(16);
        return hex.length === 1 ? '0' + hex : hex;
    };

    const red = componentToHex(r);
    const green = componentToHex(g);
    const blue = componentToHex(b);

    return '#' + red + green + blue;
}

function whiteOrBlack(r, g, b) {
    if (r < 128 || g < 128 || b < 128) {
        return "white"
    }

    return "black"
}

</script>

<template>
    <div :style="{ backgroundColor: `rgb(${r}, ${g}, ${b})`, color: whiteOrBlack(r, g, b) }" class="container">
        <div>
            rgb( {{ r }}, {{ g }}, {{ b }} )
        </div>
        <div>
            {{ rgbToHex(r, g, b) }}
        </div>
    </div>
</template>

<style scoped>
div.container {

    border: 1px solid black;
    width: 50%;
    padding: 2rem;
}
</style>