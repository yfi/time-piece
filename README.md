# time-piece
time-piece is a vanilla javascript component which will work in any frontend framework. You can install from npm like this:

```text
npm install --save time-piece
```

#### Usage: Javascript (assumes es module) 
```javascript
import TimePiece from 'time-piece'

let timePiece = new TimePiece({target:document.body);
 
```

The "target" is where the component is created. Here it is added to the html body with "document.body", but it could also be document.getElementById('id-of-html-element'). 

You initialize properties with "props" and you can change the prop values by just assigning the props to new values - this will be updated in the UI. 

#### Usage: Legacy Javascript
Below you can see how to use the component with vanilla js.
```html
...
<head>
  ...
  <script src="https://unpkg.com/time-piece@0.0.1/index.js"></script>
</head>
<body>
  <script>
    let timePiece = new TimePiece({target:document.body})
  </script>
</body>
```

#### Usage: Web Component (aka. Custom Element)
You can use it as a web component.
```html
<head>
  <script src="https://unpkg.com/time-piece@0.0.1/index.js"></script>
</head>
<body>
  <time-piece  />    
</body>
```

#### Svelte Component
```html
<script>
  import TimePiece from 'time-piece';
</script>
<TimePiece/>
```

#### Pelte
This component was created by [pelte](https://www.npmjs.com/package/publish-svelte) (aka publish-svelte)