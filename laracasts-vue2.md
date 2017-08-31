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
        <task>Go to work.</task>
        <task>Go to store.</task>
        <task>Go to school.</task>
    </div>

    <script src="https://unpkg.com/vue@2.4.2"></script>
    
    <script>
        Vue.component('task', {
            template: '<li><slot></slot></li>'
        });

        new Vue({
            el: '#root'
        });
    </script>
</body>
```
