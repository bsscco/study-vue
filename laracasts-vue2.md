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
