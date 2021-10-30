<template>
  <div class="card" :class="getClassname">
    
    <div class="card-body">
      <div class="card-title">
        <h3>{{ cardData.title }}</h3>
        <a href="#">
          <img src="@/assets/img/icon-ellipsis.svg" alt="dots">
        </a>
      </div>
      <div class="card-time">
        <h1>{{ getCurrent }}hrs</h1>
        <p>{{ getTimeframe }} - {{ getPrevious }}hrs</p>
      </div>
    </div>
  </div>
</template>

<script>
export default {
    name: 'Card',
    props: ['cardData', 'currentTimeframe'],
    
    computed: {
      getCurrent() {
        return this.cardData.timeframes[this.currentTimeframe].current
      },
      getPrevious() {
        return this.cardData.timeframes[this.currentTimeframe].previous
      },
      getTimeframe() {
        if (this.currentTimeframe === 'monthly') {
          return 'Last month'
        } else if (this.currentTimeframe === 'weekly') {
          return 'Last week'
        } else {
          return 'Yesterday'
        }
      },
      getClassname() {
        return this.cardData.title.toLowerCase().replace(/\s/g, '-')
      }
    }
}
</script>

<style lang="scss">
    @import '@/assets/variables.scss';
    .card {
        display: flex;
        align-items: center;
        justify-content: center;
        border-radius: 1rem;
    }
    .card-body {
        margin-top: 2.5rem;
        width: 101%;
        padding: 2rem;
        background: $card-bg;
        border-radius: 1rem;
    }
    .card-title {
        display: flex;
        align-items: center;
        justify-content: space-between;
        margin-bottom: 0.5rem;
        h3 {
            font-weight: 400;
        }
    }
    .card-time {
        display: flex;
        align-items: center;
        justify-content: space-between;
        h1 {
            font-size: 2.1rem;
            font-weight: 300;

        }
    }
    .work {
    background: url('~@/assets/img/icon-work.svg') no-repeat top -5% right 10%, $work;
    }
    .play {
        background:url('~@/assets/img/icon-play.svg') no-repeat top -5% right 10%, $play;
    }
    .study {
        background:url('~@/assets/img/icon-study.svg') no-repeat top -5% right 10%, $study;
    }
    .exercise {
        background:url('~@/assets/img/icon-exercise.svg') no-repeat top -5% right 10%, $exercise;
    }
    .social {
        background:url('~@/assets/img/icon-social.svg') no-repeat top -5% right 10%, $social;
    }
    .self-care {
        background:url('~@/assets/img/icon-self-care.svg') no-repeat top -5% right 10%, $self-care;
    }
    @media (min-width: 50em) {
        .card-title {
            margin-bottom: 1rem;
        }
        .card-time {
            flex-direction: column;
            align-items: flex-start;
            gap: 1rem;
        }
    }
    @media (min-width: 70em) {
        .card {
            align-items: flex-end;
            cursor: pointer;

            &:hover .card-body {
                background: $card-bg-hover;
            }
        }
        .card-body {
            margin-top: 0;
            transition: background 0.4s ease;
        }
        .card-title {
            a {
                img {
                    display: block;
                    transition: all 0.4s ease;
                }
                &:hover img {
                    filter: brightness(1.5);
                }
            }
        }
        .card-time h1 {
            font-size: 3.5rem;

        }
    }
</style>