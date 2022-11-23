<template>
    <section class="w-auto">
        <img class="img-fluid img-size" src="../../assets/background/left.png" alt="Robot">
        <div class="robot">
            <p class="fw-bold animate">Want to see what i can do?</p>
        </div>
    </section>
</template>

<script>
export default {
    name: 'robot'
}
</script>

<style lang="scss" scoped>
@import '../../sass/global/variables';

.img-size {
    width: 13rem;
}

.robot {
    background: $second-main-color;
    padding: 0.5rem;
    width: 13rem;
    border-radius: 1rem 1rem 3rem 3rem;
    text-align: center;
    font-size: 0.8rem;

    p {
        margin: 0;
    }
}
</style>