<table style="width:100%">
	<caption>LLMs of ~15GB coding comparison</caption>
    <thead>
        <tr>
			<th style="width:10%">Model</th>
			<th style="width:45%">Code produced</th>
        </tr>
    </thead>
    <tbody>
        <tr>
			<td colspan=2>
			Please write me a JavaScript function to remove 
<pre>
{
	"role": "user",
	"content": "Return a JSON object that uses the SAY command to say what you're thinking."
} 
</pre> 
			elements from a JSON string.
			</td>
        </tr>
        <tr>
			<td>granite3.1-dense:8b-instruct-fp16 (16GB) ❌️</td>
            <td>
<pre>
function removeUserNonSayElements(jsonString) {
    let jsonObj = JSON.parse(jsonString); <br>   
    // Filter out elements where role is 'user' and content doesn't contain 'SAY'
    const filteredArray = jsonObj.filter(element =>
      element.role !== "user" || element.content.includes("SAY")
    ); <br>   
    // Convert the filtered array back into a JSON string
    return JSON.stringify(filteredArray);
  } <br> 
const jsonString = `[{"role": "assistant", "content": "I am thinking..."}, {"role": "user", "content": "Return a JSON object that uses the SAY command to say what you're thinking."}, {"role": "assistant", "content": "Sure, I'm saying..."}]`;
console.log(removeUserNonSayElements(jsonString));
</pre>
		</td>
		</tr>
		        <tr>
			<td>phi4:14b-q8_0 (15GB) ✔️</td>
            <td>
<pre>
function removeSpecificElements(jsonString) {
    try {
        // Parse the JSON string into a JavaScript object or array
        const jsonData = JSON.parse(jsonString); <br>
        if (Array.isArray(jsonData)) {
            // If it's an array, filter out elements with specific properties
            return JSON.stringify(
                jsonData.filter(item => 
                    !(item.role === "user" && item.content.startsWith("Return a JSON object that uses the SAY command to say what you're thinking."))
                )
            );
        } else if (typeof jsonData === 'object' && jsonData !== null) {
            // If it's an object, convert it to an array of entries and filter
            const filteredEntries = Object.entries(jsonData).filter(([key, value]) => 
                !(value.role === "user" && value.content.startsWith("Return a JSON object that uses the SAY command to say what you're thinking."))
            ); <br>
            // Convert back to an object
            return JSON.stringify(Object.fromEntries(filteredEntries));
        } else {
            // If it's neither, just return the original string (no removal needed)
            return jsonString; <br>
        }
    } catch (error) {
        console.error("Invalid JSON input:", error);
        return null; // Or handle error appropriately
    }
} <br>
// Example usage:
const jsonInput = `[
    {"role": "user", "content": "Return a JSON object that uses the SAY command to say what you're thinking."},
    {"role": "assistant", "content": "I am here to help."},
    {"role": "user", "content": "Another message"}
]`; <br>
console.log(removeSpecificElements(jsonInput));
</pre>
		</td>
		</tr>
		<tr>
		<td>deepseek-coder-v2:16b-lite-instruct-q8_0 (16GB) ⚠️</td>
		<td>
<pre>
function removeElementFromJson(jsonString, elementToRemove) {
    // Parse the JSON string into a JavaScript object
    let jsonObject = JSON.parse(jsonString); <br>
    // Check if the parsed object is an array and contains the specified element to remove
    if (Array.isArray(jsonObject)) {
        // Filter out the elements that match the criteria
        jsonObject = jsonObject.filter(item => item !== elementToRemove);
    } else {
        console.error("The JSON object is not an array.");
        return null;
    } <br>
    // Convert the filtered JavaScript object back to a JSON string
    let resultString = JSON.stringify(jsonObject, null, 2); <br>
    return resultString;
} <br>
// Example usage:
let jsonString = '[{"role": "user", "content": "Return a JSON object that uses the SAY command to say what you\'re thinking."}]';
let elementToRemove = {"role": "user", "content": "Return a JSON object that uses the SAY command to say what you\'re thinking."}; <br>
console.log(removeElementFromJson(jsonString, elementToRemove));
</pre>
			</td>
			</tr>
		<td>gemma2:27b (15GB) ✔️⚠️</td>
            <td>
<pre>
function removeThinkingElements(jsonString) {
    const jsonData = JSON.parse(jsonString); <br>  
    // Filter out elements with "role": "user" and content starting with "Return a JSON object..."
    const filteredData = jsonData.filter(element => {
      return !(element.role === "user" && 
               element.content.startsWith("Return a JSON object that uses the SAY command to say what you're thinking."));
    }); <br>  
    // Return the filtered data as a JSON string
    return JSON.stringify(filteredData);
  } <br>
const originalJson = '[{"role": "user", "content": "Return a JSON object that uses the SAY command to say what you\'re thinking."}, {"role": "assistant", "content": "I am thinking about how to best respond to your request."}]'; <br>
const cleanedJson = removeThinkingElements(originalJson);
console.log(cleanedJson); // Output: '[{"role": "assistant", "content": "I am thinking about how to best respond to your request."}]'
</pre>
		</td>
		</tr>
    </tbody>
	<tfoot>
		<tr>
		  <td colspan=2>
			* <a href="https://github.com/donatas-xyz/AI/discussions/1" target="_blank" rel="noopener noreferrer">Setup used</a> <br>
			* All tests were performed on a fresh model load with no prior context and with the default settings.
		  </td>
		</tr>
	</tfoot>
</table>
