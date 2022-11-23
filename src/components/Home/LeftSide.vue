<template>
    <section class="">
        <div class="left-side">
            <div class="center-y">
                <ul class="fs-3 chat-sh">
                    <li><p class="animate fw-bold m-0">Our Intelligence ChatBot</p></li>
                    <li><p class="animate fw-bold m-0">Our chatterbots helps you to add convenience for your customers</p></li>
                    <li><p class="animate fw-bold m-0">they are automated programs that interact with customers</p></li>
                    <li><p class="animate fw-bold m-0">like a human would and cost little to nothing to engage with</p></li>
                </ul>
            </div>
        </div>
    </section>
</template>

<script>
    export default {
        
    }
</script>

<style lang="scss" scoped>
.left-side {
    background: #29abe226;
    border-radius: 16px;
    box-shadow: 0 4px 30px #0000001a;
    backdrop-filter: blur(3.4px);
    -webkit-backdrop-filter: blur(3.4px);
    border: 1px solid #29abe208;
    padding: 1rem 1.5rem;
    width: 100%;
    @media (min-width: 992px) {
        width: 90%;
    }

.center-y {

    ul {
        display: flex;
        flex-direction: column;

        li {
            margin: 0.3rem 0;
            backdrop-filter: blur(0.8px);
            -webkit-backdrop-filter: blur(0.8px);
            width: fit-content;

            p {
                width: fit-content;
            }
        }

        li:nth-child(2n+1) {
            background: #94278e91;
            box-shadow: 0 4px 30px #0000001a;
            padding: 0.8rem 1.1rem 0.8rem 0.8rem;
            border-radius: 2rem 2rem 2rem 0rem;
            

            border: 1px solid #94278e08;
        }
        li:nth-child(2n) {
            text-align: end;
            background: #29abe2d1;
            padding: 0.8rem 1.1rem 0.8rem 1.1rem;
            border-radius: 2rem 2rem 0rem 2rem;
        }
    }
}
}
</style>