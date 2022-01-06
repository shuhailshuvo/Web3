# Web3
Presentation on web3

Check Master presentation [here](https://shuhailshuvo.github.io/Web3/Web3.html)
Check Multicast presentation [here](https://shuhailshuvo.github.io/Web3)

## Thanks to [RevealJs](https://github.com/hakimel/reveal.js) for their wonderful work

### Simple
* Each `<section>` under `<div class="slides">` is a horizontal presentation slide
* Each nested `<section>` under any `<section>` is a vertical slide under parent slide.

### Transaction
`data-transition` attribute of section defines the slide transition. 
    - `<section data-transition="zoom">`
    - `<section data-transition="zoom-in fade-out">` defines different transition style for in & out
    - Available transition styles: `[none, zoom, fade, slide, convex, concave]`

### Events
They have few cool events like
* `Reveal.on( 'slidechanged', event => { } );` 
* `Reveal.on( 'ready', event => { } );` 
* `Reveal.on( 'customEvent', event => { } );` 
Custome event can be triggered by defining state.
 `<section data-state="customEvent">`

`event` have previous slide, current slide & index of current slide in horizontal & vertical way. For example if you want to quickly move to the 3rd child of 5th slide,
`Reveal.slide( 5, 3 );`

Check more of their cool APIs [here](https://revealjs.com/)

### Multicast
To multicast your presentation, you'll need a copy of your presentation file. there will be 1 master & 1 client, both are same except the initialization params.
* Master (full controll)
```
    Reveal.initialize({
		multiplex: {
			secret: '16413735489792691470',
			id: 'c0ac864259d5120f', // Obtained from https://reveal-multiplex.glitch.me/
			url: 'https://reveal-multiplex.glitch.me/'
		},

		// Don't forget to add the dependencies
		dependencies: [
			{ src: 'https://reveal-multiplex.glitch.me/socket.io/socket.io.js', async: true },
			{ src: 'https://reveal-multiplex.glitch.me/master.js', async: true },

			// and if you want speaker notes
			{ src: 'https://unpkg.com/reveal-notes-server/client.js', async: true }
		]
	});
```

* Client (No controll)
```
    Reveal.initialize({
		multiplex: {
            controls:false,
            keyboard: false,
            touch: false,
			secret: '16413735489792691470',
			id: 'c0ac864259d5120f', // Obtained from https://reveal-multiplex.glitch.me/
			url: 'https://reveal-multiplex.glitch.me/'
		},

		// Don't forget to add the dependencies
		dependencies: [
			{ src: 'https://reveal-multiplex.glitch.me/socket.io/socket.io.js', async: true },
			{ src: 'https://reveal-multiplex.glitch.me/master.js', async: true },

			// and if you want speaker notes
			{ src: 'https://unpkg.com/reveal-notes-server/client.js', async: true }
		]
	});
```
