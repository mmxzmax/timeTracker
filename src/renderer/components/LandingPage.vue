<template>
    <div class="main">
        <timer v-bind:selected-task="selected.time" v-bind:tomato-length="tomatoLength" task></timer>
        <div class="home">
            <div class="list">
                <ul>
                    <li v-for="(task, index) in tasks" :key="task.id">
                        <div class="radio">
                            <input v-bind:id="'radio' + index" name="task" type="radio"
                                   v-on:change="selectTask(task)" v-bind:checked="task.selected">
                            <label v-bind:for="'radio' + index"></label>
                        </div>
                        <input v-model="task.name" v-bind:readonly="task.edit" class="name"> : <input ref="input" class="time" readonly
                                                                          v-bind:value="time(task)">
                        <button v-on:click="copyToClipboard(index)">copy</button>
                        <button v-on:click="removeTask(index)">
                            <svg version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
                                 viewBox="0 0 512 512" style="enable-background:new 0 0 512 512;" xml:space="preserve">

                                        <polygon points="353.574,176.526 313.496,175.056 304.807,412.34 344.885,413.804 			"/>
                                                            <rect x="235.948" y="175.791" width="40.104" height="237.285"/>
                                                            <polygon points="207.186,412.334 198.497,175.049 158.419,176.52 167.109,413.804 			"/>
                                                            <path d="M17.379,76.867v40.104h41.789L92.32,493.706C93.229,504.059,101.899,512,112.292,512h286.74
                                            c10.394,0,19.07-7.947,19.972-18.301l33.153-376.728h42.464V76.867H17.379z M380.665,471.896H130.654L99.426,116.971h312.474
                                            L380.665,471.896z"/>

                                                            <path d="M321.504,0H190.496c-18.428,0-33.42,14.992-33.42,33.42v63.499h40.104V40.104h117.64v56.815h40.104V33.42
                                        C354.924,14.992,339.932,0,321.504,0z"/>
                            </svg>
                        </button>
                        <button v-on:click="editTask(index)">
                            <svg v-if="task.edit" version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
                                 viewBox="0 0 469.331 469.331" style="enable-background:new 0 0 469.331 469.331;" xml:space="preserve">
                                <path d="M438.931,30.403c-40.4-40.5-106.1-40.5-146.5,0l-268.6,268.5c-2.1,2.1-3.4,4.8-3.8,7.7l-19.9,147.4
                                    c-0.6,4.2,0.9,8.4,3.8,11.3c2.5,2.5,6,4,9.5,4c0.6,0,1.2,0,1.8-0.1l88.8-12c7.4-1,12.6-7.8,11.6-15.2c-1-7.4-7.8-12.6-15.2-11.6
                                    l-71.2,9.6l13.9-102.8l108.2,108.2c2.5,2.5,6,4,9.5,4s7-1.4,9.5-4l268.6-268.5c19.6-19.6,30.4-45.6,30.4-73.3
                                    S458.531,49.903,438.931,30.403z M297.631,63.403l45.1,45.1l-245.1,245.1l-45.1-45.1L297.631,63.403z M160.931,416.803l-44.1-44.1
                                    l245.1-245.1l44.1,44.1L160.931,416.803z M424.831,152.403l-107.9-107.9c13.7-11.3,30.8-17.5,48.8-17.5c20.5,0,39.7,8,54.2,22.4
                                    s22.4,33.7,22.4,54.2C442.331,121.703,436.131,138.703,424.831,152.403z"/>
                            </svg>

                            <svg v-if="!task.edit" version="1.1" id="Capa_1" xmlns="http://www.w3.org/2000/svg" xmlns:xlink="http://www.w3.org/1999/xlink" x="0px" y="0px"
                                 viewBox="0 0 49 49" style="enable-background:new 0 0 49 49;" xml:space="preserve">

                                    <path d="M39.914,0H37.5h-28h-9v49h7h33h8V8.586L39.914,0z M35.5,2v14h-24V2H35.5z M9.5,47V28h29v19H9.5z M46.5,47h-6V26h-33v21h-5
                                        V2h7v16h28V2h1.586L46.5,9.414V47z"/>
                                                            <path d="M13.5,33h7c0.553,0,1-0.447,1-1s-0.447-1-1-1h-7c-0.553,0-1,0.447-1,1S12.947,33,13.5,33z"/>
                                                            <path d="M23.5,35h-10c-0.553,0-1,0.447-1,1s0.447,1,1,1h10c0.553,0,1-0.447,1-1S24.053,35,23.5,35z"/>
                                                            <path d="M25.79,35.29c-0.181,0.189-0.29,0.45-0.29,0.71s0.109,0.52,0.29,0.71C25.979,36.89,26.229,37,26.5,37
                                        c0.26,0,0.52-0.11,0.71-0.29c0.18-0.19,0.29-0.45,0.29-0.71s-0.11-0.521-0.29-0.71C26.84,34.92,26.16,34.92,25.79,35.29z"/>
                                                            <path d="M33.5,4h-6v10h6V4z M31.5,12h-2V6h2V12z"/>
                            </svg>

                        </button>
                    </li>
                    <li>
                        <button v-on:click="addTask">+</button> add new task
                    </li>
                </ul>
            </div>
        </div>
        <div class="all">
            <div class="router">
                <router-link to="/info">setup</router-link>
            </div>
            all: {{ allTime }}
        </div>
    </div>
</template>

<script>
  // @ is an alias to /src
  import timer from './timer'

  const task = `{
  "name" : "",
  "edit" : false,
  "time" : {
    "ms" : 0,
    "s" : 0,
    "m" : 0,
    "h" : 0
  },
  "selected" : false
}`

  export default {
    name: 'home',
    data: function () {
      return {
        tasks: [],
        selected: {},
        timout: null,
        tomatoLength: null
      }
    },
    computed: {
      allTime: function () {
        let all = 0
        this.tasks.forEach(task => {
          all += (parseInt(task.time.h) + parseFloat((task.time.m / 60).toFixed(2)))
        })
        return `${all}h`
      }
    },
    components: {
      timer
    },
    mounted () {
      const tasks = JSON.parse(localStorage.getItem('timeTrackerData'))
      const tomato = localStorage.getItem('timeTrackerTomatoLength')
      this.tomatoLength = tomato !== undefined ? tomato : 20
      if (!tomato) {
        localStorage.setItem('timeTrackerTomatoLength', 20)
      }
      if (tasks) {
        this.tasks = tasks
      }
      const self = this
      window.onbeforeunload = function () {
        localStorage.setItem('timeTrackerData', JSON.stringify(self.tasks))
      }
    },
    methods: {
      selectTask (task) {
        this.tasks.map(t => {
          t.selected = false
        })
        this.selected = task
        this.selected.selected = true
        this.saveHistory()
      },
      time: function (task) {
        const isFullHr = parseInt(task.time.h) >= 1
        const partMin = `${parseInt(task.time.m / 60 * 100)}h`
        const partSec = `${parseInt(task.time.s / 60 * 100)}m`
        return `${isFullHr ? task.time.h : task.time.m},${isFullHr ? partMin : partSec}`
      },
      copyToClipboard (index) {
        const input = this.$refs.input[index]
        input.focus()
        input.select()
        try {
          let successful = document.execCommand('copy')
          let msg = successful ? 'Copied successful' : 'error'
          alert(msg)
        } catch (err) {
          alert('error')
        }
      },
      addTask () {
        this.tasks.unshift(JSON.parse(task))
        this.saveState()
        this.saveHistory()
      },
      removeTask (num) {
        this.tasks.splice(num, 1)
        this.saveState()
        this.saveHistory()
      },
      saveState () {
        clearTimeout(this.timeout)
        this.timeout = setTimeout(() => {
          localStorage.setItem('timeTrackerData', JSON.stringify(this.tasks))
        }, 500)
      },
      editTask (num) {
        const currentTask = this.tasks[num]
        if (!currentTask.edit) {
          this.saveState()
        }
        currentTask.edit = !currentTask.edit
        this.saveHistory()
      },
      saveHistory () {
        // const NOW = new Date()
        // let history = JSON.parse(localStorage.getItem('timeTrackerHistoryData'))
        // if (!history) {
        //   history = []
        // }
        // history.push({
        //   date: NOW.getTime(),
        //   state: this.tasks
        // })
        // localStorage.setItem('timeTrackerHistoryData', JSON.stringify(history))
      }
    }
  }
</script>

<style scoped>

    .main{
        position: fixed;
        width: 100%;
        top: 0;
        left: 0;
        display: flex;
        flex-direction: column;
        height: 100vh;
        justify-content: flex-start;
    }

    .main >*{
        height: 100%;
    }

    .home {
        display: inline-block;
        border: 1px solid #2c3e50;
        padding: 15px;
        width: 500px;
        height: calc(100vh - 145px);
    }

    .list {
        overflow: auto;
        max-width: 100%;
        height: 100%;
    }

    .home ul {
        list-style: none;
        padding: 0;
        margin: 15px 0;
        text-align: left;
        display: flex;
        flex-wrap: wrap;
        justify-content: flex-start;
        align-items: center;
    }

    .home ul li {
        display: inline-flex;
        margin: 5px 0;
    }

    .home ul li:last-child {
      position: sticky;
      bottom: 0;
      width: 100%;
      background-color: #fff;
        padding: 5px 0;
        border-top: 1px solid #86b4d6;
        display: flex;
        justify-content: flex-start;
        align-items: center;
        color: #00671e;
    }
    .home ul li:last-child button {
        margin-right: 15px;
    }

    .home ul li > * {
        margin: 0 2.5px;
    }

    .home ul li > *:first-child {
        margin-left: 0;
    }

    .all {
        text-align: right;
        font-weight: bold;
        padding: 10px;
        background: #2c3e50;
        color: #fff;
        font-family: "Conv_7fonts.ru_Digit";
        width: 100%;
    }

    button {
        background: #00671e;
        border: 1px solid transparent;
        border-radius: 3px;
        color: #fff;
        padding: 5px;
        min-width: 25px;
        outline: none !important;
    }

    input {
        border-radius: 3px;
        padding: 5px;
        border: 1px solid #688eaf;
    }


    button:hover {
        background: #00511d;
    }

    button:active {
        box-shadow: inset 1px 2px 1px 1px rgba(0, 0, 0, 0.5);
    }

    .radio input {
        display: none;
    }

    .radio {
        position: relative;
        display: inline-block;
    }

    .radio input + label:before {
        content: '';
        display: block;
        width: 21px;
        height: 21px;
        position: absolute;
        left: 0;
        top: 0;
        border: 1px solid #688eaf;
        border-radius: 50%;
        background: #ffffff;
        transition: transform 0.3s ease;
    }

    .radio label {
        display: block;
        width: 45px;
        height: 25px;
        border: 1px solid #688eaf;
        border-radius: 15px;
        position: relative;
        background: #ececec;
        transition: background-color 0.3s ease;
    }

    .radio input:checked + label:before {
        transform: translateX(20px);
    }

    .radio input:checked + label {
        background: #00671e;
    }

    input.time {
        max-width: 50px;
    }

    input.name {
        width: 230px;
    }
    .router{
        display: inline-block;
        float: left;
        font-family: "Helvetica Neue", Helvetica, Arial, sans-serif;
        color: #ffffff;
    }
    .router a{
        color: #ffffff;
    }

</style>

