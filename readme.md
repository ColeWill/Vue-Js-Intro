
# Vue.js

## What is it?

is a progressive framework for building user interfaces. Unlike other monolithic frameworks, Vue is designed from the ground up to be incrementally adoptable. The core library is focused on the view layer only, and is very easy to pick up and integrate with other libraries or existing projects. On the other hand, Vue is also perfectly capable of powering sophisticated Single-Page Applications when used in combination with modern tooling and supporting libraries.

### Let's code along in Vue.js!



	1) mkdir simple-jack

	2) touch index.html

	3) go here and download the 'Development Version' 

### [Vue.js](https://vuejs.org/v2/guide/installation.html)

	4) unzip and move it into simple-jack!
	5) touch index.html
	6) <script src="Wherever your vue.js is.../vue.js"></script>  add this to your html

see its very easy!

![simple-jack](http://i.imgur.com/0FV2mgs.jpg)


## Now let's start vue-ing!

At the core of Vue.js is a system that allows anyone,  to declaratively render data to the DOM using straightforward template syntax!
And what exactly does that mean?  Well thats a great question!

let's do this

		<div id="app">
		  {{ message }}
		</div>

Now do this

	<script>
		var app = new Vue({
	  		el: '#app',
	 		 data: {
	    	message: 'Hello simple-Jack!'
	  		}
		})
	</script>

We just created our first Vue app!  Now you may be thinking that this is pretty basic... and it is.  But you should know that the data and the DOM are now magically linked -- just like Bobby Schank and his water bottle.  And it's Reactive!

#### Try opening up dev tools and typing your own message into the console!

	app.message = ' your message here ';

## Its also simple to toggle the presence of an element! 
-Copy and paste this into your html...

	<!-- <div id="app-3">
  		<p v-if="seen"><img src="https://media.giphy.com/media/hdniZqvSq2e52/giphy.gif" height=300px width=300px></p>
  		<h2>Cole vs. Technology</h2>
	</div> -->



#### Now let's code this in our script tags!

	var app3 = new Vue({
  		el: '#app-3',
 		 data: {
    		seen: false
  		}
	})

#### lets toggle this command in dev tools...

	app3.seen = true; 

##### we are not only binding data to text and attributes, but also the DOM!


Lets display a list of Bob's todos using a for Loop...

	<div id="app-4">
  		<ol>
    		<li v-for="todo in todos">
      			{{ todo.text }}
    		</li>
  		</ol>
	</div>

#### and in app.js

	var app4 = new Vue({
	  el: '#app-4',
	  data: {
	    todos: [
	      { text: 'Hydrate' },
	      { text: 'Put large box of spinach in fridge' },
	      { text: 'code' }
	      { text:'take healthy tupperware out of fridge'}
	      { text: 'make a sassy remark'}
	    ]
	  }
	})

### Now lets add a new item to the array using dev tools! 

	app4.todos.push({text: 'ninja turtles'});


#### Now let's use the v-on directive to attach event listeners that will call methods on our vues!

	<div id="app-5">
  		<p>{{ message }}</p>
  		<button v-on:click="reverseMessage">Reverse Message</button>
	</div> 

![](https://statcdn.fandango.com/MPX/image/NBCU_Fandango/200/159/TropicThunder_SimpleJack.jpg)

And let's make a Vue thing that allows us to decipher the hidden message.

	var app5 = new Vue({
  		el: '#app-5',
 		 data: {
    		message: '?si elttob retaw ym erehw wonk enoyna seoD'
	  },

	  methods: {
	    reverseMessage: function () {
	      this.message = this.message.split('').reverse().join('')
	    }
	  }
	})

#### Note in the method we update the state of our app without touching the DOM -- so hands off.

Also, who asked if Vue.js provides 2-way data binding between form input and app state? was it Nate? Great question, the answer is of course yes.

	<div id="app-6">
  		<p>{{ message }}</p>
  		<input v-model="message">
	</div>

#### js...

	var app6 = new Vue({
  		el: '#app-6',
  		data: {
			message: 'Im not king kong but my body is strong!'
		}
	})
### Did you know that simple-jack loves breakfast burritos?  Well, he does.

![](https://www.chowstatic.com/assets/2015/03/31332_RecipeImage_chorizo_burrito.jpg)


### Now let's do some stuff with components 

Vue's component system allows us to build large apps out of lots of smaller compenent things

![](https://vuejs.org/images/components.png)

Let's make one... 

	// Define a new component called todo-item
	
	Vue.component('todo-item', {
  		props: ['todo'],
  		template: '<li>{{ todo.text }}</li>'
	})

#### Now you might connect it to a template like this
	
	<ol>
		<todo-item></todo-item>
	</ol>



But this would render the same item over and over again, which is fine if you are simple jack! but not if you are a web developer.

So let's make make the template thing that will render our shopping list...

	<div id="app-7">
			<ol>
				<todo-item
				v-for="item in groceryList"
				v-bind:todo="item"
				v-bind:key="item.id">
				
				</todo-item>
			</ol>
		</div>

And make an app for it...

	Vue.component('todo-item', {
	  props: ['todo'],
	  template: '<li>{{ todo.text }}</li>'
	})

	var app7 = new Vue ({
		el: '#app-7',
		data: {
			groceryList:[
			{ id: 0, text: 'Ping Pong Balls'},
			{ id:1, text :'Latex Gloves' },
			{ id:2, text :'Butter'},
			{ id:3, text:'potato chips'}
			]
		}
	});