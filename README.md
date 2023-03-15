### Emdeding code snippets in Webflow


Webflow hat eine Limite von 1000 Zeichen in einem Embed. 

Um dies zu umgehen, zB. komplexes Styling eines Formular, kann man den gesamten Code hier lagern. Zum einbinden

1. code kopieren und in embed-widget einfügen
2. die klasse __target-container__ und __der dazugehörige Selector__ passend ändern (Achtung: muss unique für jede seite)
3. das gewünschte File in dieser Repo kopieren, und in der Variable __url__ anpassen
4. Seite publizieren und kaffe holen :coffee:


:sparkles:


``` HTML
<div class="target-container"></div>
<script>
let url = "https://raw.githubusercontent.com/Dantolos/LD-Snippets/main/ld-basecamo-form.html"

window.onload = function() {
	// a new request object
	let request = new XMLHttpRequest()
	
	// when the state of the request changes (like it is opened, closed, headers recieved etc.), do something
	request.onreadystatechange = function() {
	
		// when the request.readyState is 4, it means that the operation of recieving the response is over (see https://developer.mozilla.org/en-US/docs/Web/API/XMLHttpRequest/readyState)
		// if the status of the response is 200, it means that the response was successfully recieved
		if (request.readyState == 4 && request.status == 200) {
			// the text content of the response
			let text = request.responseText
			
			//alert("The content of the code is\n" + text)
			// render the text between the body tags to the screen
			document.querySelector(".github-content-basecamp-form").innerHTML = text;
		}
	}
	
	// open a request
	request.open("GET", url)
	// send the request
	request.send()
}
```
</script>