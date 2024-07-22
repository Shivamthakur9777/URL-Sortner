#by Shivam Singh

This HTML snippet creates a simple interface for a URL shortener. Users can input a long URL to get a shortened version, which will be displayed on the same page. Here's a breakdown of the components related to the URL shortener:

Key Components:

Input Field for Original URL:

<label for="originalUrl">Enter URL To Shorten :</label>: A label instructing the user to enter the URL they want to shorten.
<input type="text" id="originalUrl" placeholder="https://example.com">: An input field where users can type or paste the long URL they wish to shorten. The id attribute is used to identify and style the element and to reference it in JavaScript.
Action Buttons:

<div class="buttons">: A container for the action buttons.
<button id="reload-btn">Reload</button>: A button that, when clicked, will reload the page. This can be used to reset the input field and output area.
<button id="short-btn">Short It</button>: A button that initiates the URL shortening process. It is identified by the id attribute and is likely tied to a JavaScript function that handles the URL shortening logic.
Output Field for Shortened URL:

<label for="shortenedUrl">Shortened URL :</label>: A label indicating where the shortened URL will be displayed.
<textarea id="shortenedUrl" rows="3" readonly></textarea>: A read-only text area where the shortened URL will be displayed. The readonly attribute ensures that users cannot modify the shortened URL directly in this field. The id attribute is used to reference this element in JavaScript for displaying the result.

#js 
Element Selection:

const shortBtn = document.getElementById('short-btn');: Selects the button with the ID short-btn, which is used to trigger the URL shortening process.
const reloadBtn = document.getElementById('reload-btn');: Selects the button with the ID reload-btn, which is used to reload the page.
Event Listeners:

shortBtn.addEventListener('click', shortenUrl);: Adds a click event listener to the shortBtn. When the button is clicked, the shortenUrl function is called.
reloadBtn.addEventListener('click', () => { location.reload(); });: Adds a click event listener to the reloadBtn. When the button is clicked, the page is reloaded.
Shorten URL Function:

function shortenUrl() { ... }: Defines the function shortenUrl that handles the process of shortening the URL.
var originalUrl = document.getElementById("originalUrl").value;: Retrieves the value from the input field where the user enters the original URL.
var apiUrl = "https://tinyurl.com/api-create.php?url=" + encodeURIComponent(originalUrl);: Constructs the API URL by appending the encoded original URL to the TinyURL API endpoint.
shortenedUrlTextarea = document.getElementById("shortenedUrl");: Selects the text area where the shortened URL will be displayed.
fetch(apiUrl).then(response => response.text()).then(data => { ... }).catch(error => { ... });: Makes a request to the TinyURL API:
fetch(apiUrl): Sends a GET request to the TinyURL API with the original URL.
.then(response => response.text()): Processes the response and converts it to text.
.then(data => { shortenedUrlTextarea.value = data; }): Sets the value of the text area to the shortened URL returned by the API.
.catch(error => { shortenedUrlTextarea.value = "Error : Unable to shorten URL!"; }): Handles any errors by displaying an error message in the text area.
Reload Functionality:

reloadBtn.addEventListener('click', () => { location.reload(); });: Adds a click event listener to the reload button, which reloads the page to reset the input and output fields.
Usage:

Shortening a URL:

Enter a long URL into the input field labeled "Enter URL To Shorten".
Click the "Short It" button.
The JavaScript function shortenUrl sends the URL to the TinyURL API and displays the shortened URL in the text area below.
Reloading the Page:

Click the "Reload" button to refresh the page, clearing the input field and the output text area for a new URL shortening task.
This JavaScript code provides a simple and effective way to integrate URL shortening functionality into a webpage using the TinyURL API.