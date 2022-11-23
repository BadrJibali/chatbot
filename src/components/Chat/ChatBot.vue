<template>
    <section class="chat-box">
        <div class="chat-header d-flex align-items-center justify-content-start gap-2">
            <img class="img-fluid image-avatar" src="../../assets/background/avatar.png" alt="avatar">
            <h6 class="m-0 fw-semibold">Jarvis</h6>
        </div>
        <div class="chat-box-list-container" ref="chatbox">
            <ul class="chat-box-list">
                <li class="message" v-for="(message, idx) in messages" :key="idx" :class="message.author">
                    <p>
                        <span style="white-space: pre-wrap;">{{ message.text }}</span>
                    </p>
                </li>
            </ul>
        </div>
        <div class="chat-inputs">
            <input type="text" placeholder="Enter Your Massage..." v-model="message" @keyup.enter="sendMessage" />
            <button @click="sendMessage"><font-awesome-icon class="fs-5" :icon="['far', 'paper-plane']"/></button>
        </div>
    </section>
</template>
  
<script>
export default {
    name: 'ChatBox',
    data: () => ({
        message: '',
        messages: []
    }),
    methods: {
        sendMessage() {
            const message = this.message

            this.messages.push({
                text: message,
                author: 'client'
            })

            this.message = ''

            this.$axios.get(`https://www.cleverbot.com/getreply?key=CC8uqcCcSO3VsRFvp5-uW5Nxvow&input=${message}`)
                .then(res => {
                    this.messages.push({
                        text: res.data.output,
                        author: 'server'
                    })

                    this.$nextTick(() => {
                        this.$refs.chatbox.scrollTop = this.$refs.chatbox.scrollHeight
                    })
                })
        }
    },
}
</script>

<style lang="scss"  scoped>
@import '../../sass/global/variables';
@import '../../sass/global/scrollbar';
.chat-box {
    background: $background-color;
}

.chat-box,
.chat-box-list {
    display: flex;
    flex-direction: column;
}

.chat-box-list-container {
    overflow-x: hidden;
    overflow-y: scroll;
    margin: 1rem 0 0 0;
}

.chat-box-list {
    padding: 3rem 1rem 1rem 1rem;
    gap: 1.5rem;

    span {
        color: $light-text-color;
    }

    .server {
        span {
            background: $second-main-color;
            padding: 0.5rem 0.8rem 0.5rem 0.8rem;
            border-radius: 2rem 2rem 0rem 2rem;
        }

        p {
            float: right;
            margin: 0;
        }
    }

    .client {
        span {
            background: $first-main-color;
            padding: 0.5rem 0.8rem 0.5rem 0.5rem;
            border-radius: 2rem 2rem 2rem 0rem;
        }

        p {
            float: left;
            margin: 0;
        }
    }
}

.chat-box {
    box-shadow: rgba(145, 33, 140, 0.05) 0 0 0 0.1rem inset, rgb(145, 33, 140) 0 0 0 0.08rem;
    width: 90%;
    max-height: 80vh;
    min-height: 27rem;
    height: 100%;
    border-radius: 1rem;
    justify-content: space-between;
    margin: 2rem auto;
    align-content: center;
    padding: 0;
    overflow: hidden;
    @media (min-width: 768px) {
        width: 100%;
    }

    .chat-header {
        background: $first-main-color;
        padding: 0.5rem 1rem;

        .image-avatar {
            height: 2.5rem;
            width: 2.5rem;
            border-radius: 50%;
            border: 0.15rem solid $second-main-color;
        }

        h6 {
            color: $light-text-color;
        }
    }
}

.chat-inputs {
    display: flex;
    padding: 1rem 1rem 1rem 1rem;

    input {
        line-height: 3;
        width: 100%;
        border: 1px solid $first-main-color;
        border-right: none;
        border-radius: 0.7rem 0rem 0rem 0.6rem;
        padding: 0.1rem 1rem;

        &:focus-visible {
            outline: none;
        }
    }

    button {
        width: 7rem;
        color: $light-text-color;
        background: $first-main-color;
        border-left: none;
        border-radius: 0 0.6rem 0.6rem 0;
        border: 0.1rem solid $first-main-color;
    }
}
</style>
  