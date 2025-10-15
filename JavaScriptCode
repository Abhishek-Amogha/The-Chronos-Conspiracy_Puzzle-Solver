/**
 * Asynchronously tries all numerical keys from 100 to 999 on the JotForm.
 * It identifies the correct key by checking when the form reveals the hidden 'Next' button.
 */
async function findTheKey() {
    // A helper function to create a short pause
    const sleep = (ms) => new Promise(resolve => setTimeout(resolve, ms));

    // Select the necessary form elements by their ID
    const inputField = document.getElementById('input_42');
    const nextButtonContainer = document.getElementById('cid_52');

    // Check if the elements exist on the current page
    if (!inputField || !nextButtonContainer) {
        console.error("Could not find the necessary form elements. Please make sure you are on the correct page of the form (the one with the riddle).");
        return;
    }

    console.log("🚀 Starting brute-force attempt to find the key...");

    // Loop through every number from 100 to 999
    for (let i = 100; i <= 999; i++) {
        const key = i.toString();

        // Set the value of the input field to the current key
        inputField.value = key;

        // Dispatch common events to trigger JotForm's conditional logic checks
        inputField.dispatchEvent(new Event('input', { bubbles: true }));
        inputField.dispatchEvent(new Event('keyup', { bubbles: true }));
        inputField.dispatchEvent(new Event('change', { bubbles: true }));

        // Pause briefly to allow the page's scripts to run
        await sleep(55);

        // Check if the container for the 'Next' button is now visible.
        // JotForm shows the button by changing its display style from 'none'.
        if (nextButtonContainer.style.display !== 'none') {
            console.log(`%c✅ SUCCESS! The key is: ${key}`, 'color: #22c55e; font-size: 1.2em; font-weight: bold;');
            
            // Optional: Automatically click the 'Next' button to proceed
            // document.getElementById('form-pagebreak-next_52').click();
            
            return; // Exit the function once the key is found
        }
        
        // Log progress every 100 attempts to avoid flooding the console
        if (i % 100 === 0) {
           console.log(`...checked up to key ${i}`);
        }
    }

    console.log("...Brute-force attempt finished. No valid key was found in the range 100-999.");
}

// Run the function
findTheKey();
