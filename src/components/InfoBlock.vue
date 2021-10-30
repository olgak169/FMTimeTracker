<template>
<div class="info-card">
    <div class="info-profile">
        <div class="avatar">
            <img src="@/assets/img/image-jeremy.png" alt="avatar">
        </div>
        <div class="info-details">
            <p>Report for</p>
            <h1>Jeremy Robson</h1>
        </div>
    </div>
    <div class="info-btns">
        <a 
        @click="updateTimeframe('daily')" 
        :class="{ active: currentTimeframe === 'daily'}">Daily</a>
        <a 
        @click="updateTimeframe('weekly')" 
        :class="{ active: currentTimeframe === 'weekly'}">Weekly</a>
        <a 
        @click="updateTimeframe('monthly')" 
        :class="{ active: currentTimeframe === 'monthly'}">Monthly</a>
    </div>
</div>
</template>

<script>
export default {
    name: 'InfoCard',
    props: ['currentTimeframe'],
    methods: {
        updateTimeframe(opt) {
            this.$emit('timeframeChange',opt)
        }
    }

}
</script>
<style lang="scss">
    @import '@/assets/variables.scss';

    .info-card {
        background: $card-bg;
        display: flex;
        flex-direction: column;
        align-items: center;
        border-radius: 1rem;
    }
    .info-profile {
        background: $profile-bg;
        border-radius: 1rem;
        width: 100%;
        padding: 2rem;
        display: flex;
        align-items: center;
        justify-content: center;
        gap: 1.5rem;
        .avatar {
            border-radius: 50%;
            border: 2px solid #fff;
            width: 4.2rem;
            height: 4.2rem;
            img {
                max-width: 100%;
                object-fit: cover;
            }
        }
        h1 {
            font-size: 1.5rem;
            font-weight: 300;
        }
    }
    .info-btns {
        display: flex;
        justify-content: space-evenly;
        align-items: center;
        padding: 1.5rem 0;
        a {
            cursor: pointer;
            color: $text-muted;
            margin: 0 2rem;
            transition: color 0.4s ease;
            &.active {
                color: #fff;
                font-weight: 400;
            }
        }
    }
    @media (min-width: 70em) {
        .info-card {
            align-items: flex-start;
        }
        .info-profile {
            flex-direction: column;
            align-items: flex-start;
            padding: 2rem 0 5rem 2rem;
            gap: 1rem;
            .avatar {
                width: 5.4rem;
                height: 5.4rem;
                margin-bottom: 1rem;
            }
            h1 {
                font-size: 2.6rem;
            }
        }
        .info-btns {
            flex-direction: column;
            align-items: flex-start;
            gap: 1.2rem;
            padding: 2rem 0 2rem 2rem;
            a {
                margin: 0;
                &:hover {
                    color: #fff;
                    font-weight: 400;
                }
            }
        }
    }
</style>