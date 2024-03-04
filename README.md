# Auto Capitalize Selected Text Script

This JavaScript script allows you to automatically capitalize the selected text in any editable area of a web page by pressing Ctrl + left mouse button click. You can use this script by pasting it into the browser's developer console.

## Instructions

1. **Copy the script:**
   - Copy the JavaScript code provided below.

2. **Open the developer console:**
   - Open your browser's developer tools console. You can usually do this by pressing F12 or right-clicking on the page and selecting "Inspect", then navigating to the "Console" tab.

3. **Paste and run the script:**
   - Paste the copied JavaScript code into the console.
   - Press Enter to run the script.

4. **Usage:**
   - After running the script, click and drag to select text in any editable area (e.g., input fields, text areas).
   - Press Ctrl and click the left mouse button while selecting text.
   - The selected text will be automatically capitalized.

## JavaScript Code

```javascript
// Function to capitalize the first letter of each word, handling non-ASCII characters
function capitalizeFirstLetter(str) {
    return str.replace(/(^|\s)\S/g, function (char) {
        return char.toUpperCase();
    });
}

// Function to capitalize selected text
function capitalizeSelectedText() {
    const selection = window.getSelection();
    if (selection.toString()) {
        const modifiedText = capitalizeFirstLetter(selection.toString());
        document.execCommand('insertText', false, modifiedText);
    }
}

// Function to handle mouse down events
function handleMouseDown(event) {
    // Check if Ctrl key is pressed and left mouse button is clicked
    if (event.ctrlKey && event.button === 0) {
        // Prevent default action to avoid selecting text
        event.preventDefault();
        
        // Capitalize the selected text
        capitalizeSelectedText();
    }
}

// Add mouse down event listener to the document
document.addEventListener('mousedown', handleMouseDown);
