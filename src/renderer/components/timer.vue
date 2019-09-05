<template>
    <div class="timer">
        <div class="setup">
            <button v-on:click="isTomato = !isTomato">
                <svg v-if="!isTomato" enable-background="new 0 0 552.471 552.471" height="512" viewBox="0 0 552.471 552.471" width="512" xmlns="http://www.w3.org/2000/svg"><path d="m458.221 159.899c9.109-3.224 15.05-6.051 15.851-6.457 8.396-4.333 11.751-14.618 7.52-23.065-10.689-21.379-38.542-54.728-79.866-62.45 13.016-24.633 12.662-49.552 12.628-51.086-.118-5.007-2.411-9.711-6.255-12.898s-8.919-4.468-13.842-3.726c-17.062 2.849-85.548 16-118.02 48.338-32.474-32.338-100.96-45.488-118.022-48.338-4.94-.776-9.998.54-13.842 3.726-3.844 3.187-6.137 7.891-6.255 12.898-.034 1.534-.388 26.453 12.628 51.086-41.324 7.722-69.177 41.071-79.866 62.45-4.232 8.447-.877 18.732 7.52 23.065.797.409 6.744 3.229 15.859 6.449-38.58 39.859-59.729 92.142-59.729 150.535 0 147.045 94.872 242.045 241.706 242.045s241.706-95 241.706-242.045c-.001-58.389-21.146-110.67-59.721-150.527zm-272.49-56.852c8.211 2.124 16.658-2.124 20.013-9.863 3.372-7.756.624-16.793-6.457-21.379-13.05-8.43-19.709-21.429-23.115-32.591 40.06 9.981 82.8 28.493 82.8 47.09 0 9.543 7.722 17.265 17.265 17.265s17.265-7.722 17.265-17.265c0-18.546 42.723-37.041 82.783-47.056-3.406 11.145-10.065 24.127-23.098 32.557-7.081 4.586-9.829 13.623-6.457 21.379 3.338 7.739 11.802 11.954 20.013 9.863 35.71-8.852 60.005 11.111 72.987 26.673-22.508 6.643-62.618 12.965-104.161-7.149-5.496-2.681-11.954-2.209-17.012 1.096-5.092 3.338-8.042 9.104-7.772 15.174.961 22.188-18.917 56.245-34.563 66.563-15.764-10.335-35.642-44.342-34.529-66.429.303-6.103-2.63-11.903-7.722-15.275-2.866-1.905-6.188-2.866-9.526-2.866-2.563 0-5.142.573-7.536 1.737-41.189 19.962-81.451 13.674-104.077 7.064 13.012-15.579 37.273-35.457 72.899-26.588zm90.504 414.95c-100.149 0-207.176-54.536-207.176-207.572 0-56.688 23.454-106.492 65.841-141.169 21.591 2.62 47.503 2.167 75.143-6.795 8.683 34.243 35.187 70.391 61.05 78.45 1.686.523 3.406.776 5.142.776 1.737 0 3.456-.253 5.142-.776 25.678-8.009 52.182-44.19 60.949-78.484 27.703 9.016 53.653 9.473 75.265 6.847 42.371 34.679 65.82 84.473 65.82 141.15.001 153.037-107.026 207.573-207.176 207.573z"/></svg>
                <svg v-if="isTomato" enable-background="new 0 0 556.235 556.235" height="512" viewBox="0 0 556.235 556.235" width="512" xmlns="http://www.w3.org/2000/svg"><path d="m461.071 161.081c-23.788 11.751-54.203 22.468-86.994 22.468-7.231 0-14.31-.509-21.219-1.562-14.004 42.828-30.147 83.89-64.403 94.551l-10.338 3.225-10.338-3.225c-34.255-10.66-50.399-51.723-64.403-94.551-6.909 1.052-13.987 1.562-21.202 1.562-6.975.002-13.756-.77-20.489-1.642-46.518 40.623-74.775 98.875-74.775 165.739 0 29.288 4.133 56.527 11.645 81.539-18.324-31.005-29.027-69.644-29.027-116.304 0-57.112 22.999-104.551 60.183-137.911-12.585-3.917-24.181-8.761-34.552-13.885-37.801 39.556-60.395 92.199-60.395 151.796 0 145.56 97.793 243.353 243.353 243.353s243.353-97.792 243.353-243.352c0-59.599-22.593-112.245-60.399-151.801z"/><path d="m69.53 104.294s84.739 69.529 156.441 34.765c11.95 34.765 27.523 96.619 52.147 104.294 24.624-7.675 40.197-69.529 52.147-104.294 71.702 34.765 156.441-34.765 156.441-34.765s-52.146-52.147-121.676-34.765c35.851-23.177 34.765-69.529 34.765-69.529s-121.676 20.279-121.676 69.529c0-49.25-121.677-69.529-121.677-69.529s-1.086 46.352 34.765 69.529c-69.53-17.382-121.677 34.765-121.677 34.765z"/></svg>
            </button>
        </div>
        <button v-on:click="toggleTimer" v-bind:class="{stop: isStarted}">

            <svg v-if="!isStarted" version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
                 viewBox="0 0 16 16" style="enable-background:new 0 0 16 16;" xml:space="preserve">
                    <path d="M3,16l10-8L3,0V16z"/>
                </svg>
            <svg v-if="isStarted" version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
                 viewBox="0 0 36 36" style="enable-background:new 0 0 36 36;" xml:space="preserve">
                    <path d="M35,0H1C0.448,0,0,0.447,0,1v34c0,0.553,0.448,1,1,1h34c0.552,0,1-0.447,1-1V1C36,0.447,35.552,0,35,0z"/>
                </svg>
        </button>
        <div class="time">
            {{ pad(time.h) }} : {{ pad(time.m) }} : {{ pad(time.s) }} : {{ pad(time.ms, 3) }}
        </div>
        <button class="reset" v-on:click="resetTimer">
            <svg version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
                 viewBox="0 0 489.533 489.533" style="enable-background:new 0 0 489.533 489.533;" xml:space="preserve">
                    <path d="M268.175,488.161c98.2-11,176.9-89.5,188.1-187.7c14.7-128.4-85.1-237.7-210.2-239.1v-57.6c0-3.2-4-4.9-6.7-2.9
                        l-118.6,87.1c-2,1.5-2,4.4,0,5.9l118.6,87.1c2.7,2,6.7,0.2,6.7-2.9v-57.5c87.9,1.4,158.3,76.2,152.3,165.6
                        c-5.1,76.9-67.8,139.3-144.7,144.2c-81.5,5.2-150.8-53-163.2-130c-2.3-14.3-14.8-24.7-29.2-24.7c-17.9,0-31.9,15.9-29.1,33.6
                        C49.575,418.961,150.875,501.261,268.175,488.161z"/>
                </svg>
        </button>
    </div>
</template>

<script>
  import { ipcRenderer } from 'electron'

  export default {
    name: 'timer',
    props: [
      'selectedTask',
      'tomatoLength'
    ],
    data: function () {
      return {
        time: {
          ms: 0,
          s: 0,
          m: 0,
          h: 0
        },
        tomatoTimer: 0,
        isStarted: false,
        timer: null,
        isTomato: false,
        notification: () => {
          return new Notification('TimeTracker', {
            body: "it's time to relax"
          })
        }

      }
    },
    mounted: function () {
      ipcRenderer.on('contexmenuchange', (e, data) => {
        if (data.type === 'start') {
          this.startTimer()
        }
        if (data.type === 'stop') {
          this.stopTimer()
        }
      })
    },
    computed: {},
    watch: {
      selectedTask: function () {
        this.time = this.selectedTask
      }
    },
    methods: {
      pad (value, n) {
        n = n || 2
        return (new Array(n).join('0') + value).slice(-n)
      },
      startTimer () {
        if (this.selectedTask) {
          this.time = this.selectedTask
        }
        this.timer = setInterval(() => {
          this.time.ms += 10
          if (this.time.ms >= 999) {
            this.time.ms = 0
            this.time.s += 1
          }
          if (this.time.s >= 60) {
            this.time.s = 0
            this.time.m += 1
            if (this.isTomato) {
              this.tomatoTimer++
              if (this.tomatoTimer >= parseInt(this.tomatoLength)) {
                this.tomatoTimer = 0
                this.stopTimer()
                this.notification()
              }
            }
          }
          if (this.time.m >= 60) {
            this.time.m = 0
            this.time.h += 1
          }
        }, 10)
        this.isStarted = true
        ipcRenderer.send('timerchange', this.isStarted)
      },
      stopTimer () {
        clearInterval(this.timer)
        this.isStarted = false
        ipcRenderer.send('timerchange', this.isStarted)
      },
      toggleTimer () {
        if (this.isStarted) {
          this.stopTimer()
        } else {
          this.startTimer()
        }
      },
      resetTimer () {
        this.tomatoTimer = 0
        this.stopTimer()
        this.time.m = 0
        this.time.s = 0
        this.time.h = 0
        this.time.ms = 0
      }
    }
  }
</script>

<style scoped>





    .timer {
        padding: 25px;
        background: #2c3e50;
        color: #fff;
        text-align: center;
        font-family: "Conv_7fonts.ru_Digit";
        display: flex;
        flex-wrap: wrap;
        justify-content: space-between;
        align-items: center;
        min-height: 105px;
    }

    .timer .setup {
        width: 100%;
        text-align: left;
        margin-top: -10px;
    }
    .timer .setup button{
        position: relative;
        color: #ffffff;
        margin-right: 15px;
    }

    .buttons {
        margin: 10px 0;

    }

    button {
        background: transparent;
        border: none;
        border-radius: 3px;
        padding: 0;
        outline: none!important;
        color: #00ff49;
    }
    button svg {
        width: 25px;
        height: 25px;
    }

    button.stop {
        color: #b80000;
    }

    button.reset {
        color: #f7ff00;
    }

    .time {
        font-size: 40px;
    }
</style>
