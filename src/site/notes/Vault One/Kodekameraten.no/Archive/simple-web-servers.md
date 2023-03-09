---
{"dg-publish":true,"permalink":"/vault-one/kodekameraten-no/archive/simple-web-servers/"}
---



A look at some web server frameworks and languages for quick and simple api creation.

# Languages and frameworks
| Language	| Framework	|
| ------------- | ------------- |
| Python	| Flask		|
| Ruby		| Sinatra	|
| JavaScript	| Express	|

# Endpoints
I want my apis to implement two endpoints. 
1. Hello World
- Returns the famous greeting at the root endpoint '/'. 
2. Roll Dice
- Return a random value from 1 to and including 6. Just like a normal dice roll. 
- Endpoint: "/roll_dice"

## Python with Flask
https://flask.palletsprojects.com
```python
from flask import Flask
import random

app = Flask(__name__)

@app.route('/')
def hello_world():
	return "Hello, World!"

@app.route('/roll_dice')
def roll_dice():
	return str(random.randint(1,6))
```

## Ruby with Sinatra
http://sinatrarb.com/
```ruby
require 'sinatra'
	get '/' do
		"Hello world"
	end

	get '/roll_dice' do
		rand(1..6).to_s
	end
```

## Javascript with Express
https://expressjs.com/
```js
const express = require('express');
const app = express();
const port = 3000;

app.get('/', (req, res) => res.send('Hello World!'));

app.get('/roll_dice', (req, res) =>
	res.send(`${Math.floor(Math.random() * 6) + 1}`)
);

app.listen(port, () =>
	console.log(`Example app listening at http://localhost:${port}`)
);

```
