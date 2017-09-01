**데이터 바인딩 js버전**
```html
<body>
    <input type="text" id="input">

    <script>
        let data = {
          message : 'hello'
        }
      
        document.querySelector('#input').value = data.message;
    </script>
</body>
```
<br>

**데이터 바인딩 vue버전**
```html
<body>
    <div id="root">
        <input type="text" v-model="message">
        <p>{{ message }}</p>
    </div>

    <script src="https://unpkg.com/vue@2.4.2"></script>

    <script>
        var app = new Vue({
            el: '#root',
            data: {
                message: 'hello'
            }
        });
    </script>
</body>
```
<br>

**리스트 데이터 바인딩 js버전**
```html
<body>
    <div id="root">
        <ul>
            <li v-for="name in names" v-text="name">
        </ul>
        <input id="input" type="text"><button id="button">add name</button>
    </div>

    <script src="https://unpkg.com/vue@2.4.2"></script>

    <script>
        var app = new Vue({
            el: '#root',
            data: {
                names: ['a', 'b', 'c']
            },
            mounted: function() {
                document.querySelector('#button').addEventListener('click', () => { 
                    let name = document.querySelector('#input');

                    app.names.push(name.value);

                    name.value = '';
                });
            }
        });
    </script>
</body>
```
<br>

**리스트 데이터 바인딩 vue버전**
```html
<body>
    <div id="root">
        <ul>
            <li v-for="name in names" v-text="name">
        </ul>
        <input type="text" v-model="newName"><button @click="addName">add name</button>
    </div>

    <script src="https://unpkg.com/vue@2.4.2"></script>

    <script>
        var app = new Vue({
            el: '#root',
            data: {
                names: ['a', 'b', 'c'],
                newName: ''
            },
            methods: {
                addName: function() {
                    this.names.push(this.input);
                    this.input = '';
                }
            }
        });
    </script>
</body>
```
<br>

**스타일 바인딩 vue버전**
```html
<html>
<head>
    <style>
        .is-loading {
            background: red;
        }
    </style>
</head>
<body>
    <div id="root">
        <button :class="{'is-loading': isLoading}" @click="toggleClass">toggle</button>
    </div>

    <script src="https://unpkg.com/vue@2.4.2"></script>

    <script>
        var app = new Vue({
            el: '#root',
            data: {
                isLoading: false
            },
            methods: {
                toggleClass: function() {
                    this.isLoading = !this.isLoading;
                }
            }
        });
    </script>
</body>
</html>
```
<br>

**계산되지 않은 프로퍼티 vue버전**
```html
<body>
    <div id="root">
        <h2>All tasks</h2>
        <ul>
            <li v-for="task in tasks" v-text="task.desc"></li>
        </ul>

        <h2>Incompleted tasks</h2>
        <ul>
            <li v-for="task in tasks" v-if="! task.completed" v-text="task.desc"></li>
        </ul>
    </div>

    <script src="https://unpkg.com/vue@2.4.2"></script>

    <script>
        var app = new Vue({
            el: '#root',
            data: {
                tasks: [
                    { desc: 'task 1', completed: true },
                    { desc: 'task 2', completed: false },
                    { desc: 'task 3', completed: false },
                    { desc: 'task 4', completed: true }
                ]
            }
        });
    </script>
</body>
```
콘솔에서 ```app.tasks[0].completed = false```
<br>

**계산된 프로퍼티 vue버전**
```html
<body>
    <div id="root">
        <h2>All tasks</h2>
        <ul>
            <li v-for="task in tasks" v-text="task.desc"></li>
        </ul>

        <h2>Incompleted tasks</h2>
        <ul>
            <li v-for="task in incompletedTasks" v-text="task.desc"></li>
        </ul>
    </div>

    <script src="https://unpkg.com/vue@2.4.2"></script>

    <script>
        var app = new Vue({
            el: '#root',
            data: {
                tasks: [
                    { desc: 'task 1', completed: true },
                    { desc: 'task 2', completed: false },
                    { desc: 'task 3', completed: false },
                    { desc: 'task 4', completed: true }
                ]
            },
            computed: {
                incompletedTasks: function() {
                    return this.tasks.filter(task => ! task.completed);
                }
            }
        });
    </script>
</body>
```
콘솔에서 ```app.tasks[0].completed = false```
<br>

**컴포넌트 js버전**
```html
<body>
    <div id="root">
        <ul>
            <li>Go to work.</li>
            <li>Go to store.</li>
            <li>Go to school.</li>
        </ul>
    </div>
</body>
```
<br>

**컴포넌트 vue버전**
```html
<body>
    <div id="root">
        <task-list></task-list>
    </div>

    <script src="https://unpkg.com/vue@2.4.2"></script>
    
    <script>
        Vue.component('task-list', {
            template: `
                <div>
                    <task v-for="task in tasks" v-text="task.desc"></task>
                </div>
            `,
            data: function() {
                return {
                    tasks: [
                        { desc: 'Go to work.', completed: false },
                        { desc: 'Go to store.', completed: true },
                        { desc: 'Go to school.', completed: false }
                    ]
                };
            }
        });

        Vue.component('task', {
            template: '<li><slot></slot></li>'
        });

        new Vue({
            el: '#root'
        });
    </script>
</body>
```
<br>

**컴포넌트 연습1 vue버전**
```html
<head>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bulma/0.5.1/css/bulma.css">
    <style type="text/css">
        body {
            padding-top: 40px;
        }
    </style>
</head>
<body>
    <div id="root" class="container">
        <message title="Hello World" body="Lorem ipsum dolor sit amet, consectetur adipiscing elit."></message>
        <message title="Apple" body="Tasty good."></message>
    </div>

    <script src="https://unpkg.com/vue@2.4.2"></script>
    
    <script>
        Vue.component('message', {
            template: `
                <article class="message" v-show="isVisible">
                    <div class="message-header">
                        {{ title }}
                        <button @click="isVisible = false">X</button>
                    </div>
                    <div class="message-body">
                            {{ body }}
                    </div>
                </article>
            `,
            props: ['title', 'body'],
            data: function() {
                return {
                    isVisible: true
                }
            }
        });

        new Vue({
            el: '#root'
        });
    </script>
</body>
```
<br>

**컴포넌트 연습2 vue버전**
```html
<head>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bulma/0.5.1/css/bulma.css">
</head>
<body>
    <div id="root">
        <tabs>
    </tab>
    </div>

    <script src="https://unpkg.com/vue@2.4.2"></script>
    
    <script>
        Vue.component('modal', {
            template: `
                <div class="modal is-active">
                    <div class="modal-background"></div>
                        <div class="modal-content">
                            <div class="box">
                                <p>Any other Bulma elements you want</p>
                            </div>
                        </div>
                    <button class="modal-close" @click="$emit('close')"></button>
                </div>
            `
        });

        new Vue({
            el: '#root',
            data: {
                showModal: false
            }
        });
    </script>
</body>
```
<br>

**컴포넌트 연습3 vue버전**
```html
<head>
    <link rel="stylesheet" href="https://cdnjs.cloudflare.com/ajax/libs/bulma/0.5.1/css/bulma.css">
</head>
<body>
    <div id="root">
        <tabs>
            <tab name="Tab A" :selected="true">
                <h1>blah blah A</h1>
            </tab>
            <tab name="Tab B">
                <h1>blah blah B</h1>
            </tab>
            <tab name="Tab C">
                <h1>blah blah C</h1>
            </tab>
        </tabs>
    </div>

    <script src="https://unpkg.com/vue@2.4.2"></script>
    
    <script>
        Vue.component('tabs', {
            template: `
                <div>
                    <div class="tabs">
                        <ul>
                            <li v-for="tab in tabs" :class="{ 'is-active': tab.isActive }">
                            <a :href="tab.href" @click="selectTab(tab)">{{ tab.name }}</a>
                            </li>
                        </ul>
                    </div>
                    <div class="tabs-details">
                        <slot></slot>
                    </div>
                </div>
            `,
            data: function() {
                return {
                    tabs: []
                }
            },
            created: function() {
                this.tabs = this.$children;
            },
            methods: {
                selectTab: function(selectedTab) {
                    this.tabs.forEach(tab => {
                        tab.isActive = (tab.name == selectedTab.name);
                    });
                }
            }
        });

        Vue.component('tab', {
            template: `
                <div v-show="isActive">
                    <slot></slot>
                </div>
            `,
            props: {
                name: { required: true },
                selected: { default: false }
            },
            data: function() {
                return {
                    isActive: false
                }
            },
            mounted: function() {
                this.isActive = this.selected;
            },
            computed: {
                href: function() {
                    return '#' + this.name.toLowerCase().replace(/ /g, '-');
                }
            }
        });

        new Vue({
            el: '#root'
        });
    </script>
</body>
```
