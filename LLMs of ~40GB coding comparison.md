<table style="width:100%">
	<caption>LLMs of ~40GB coding comparison</caption>
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
			<td>deepseek-r1:70b (42GB) ✔️⚠️</td>
            <td>
<pre>
function removeUserRoles(jsonString) {
    // Parse the JSON string into an object
    const jsonObj = JSON.parse(jsonString); <br>    
    // Filter out elements where role is user and content starts with specific text
    const filteredObj = jsonObj.filter(element => 
        !(element.role === "user" && element.content.startsWith("Return a JSON object"))) <br>    
    // Convert back to JSON string with proper formatting
    return JSON.stringify(filteredObj, null, 2);
} <br>
const inputJson = `
[
    {
        "role": "user",
        "content": "Return a JSON object that uses the SAY command to say what you're thinking."
    },
    {
        "role": "assistant",
        "content": "Here's an example response..."
    }
]
`; <br>
const outputJson = removeUserRoles(inputJson);
console.log(outputJson);
</pre>
		</td>
		</tr>
		        <tr>
			<td>llama3.3:70b (42GB) ❌</td>
            <td>
<pre>
/**
 * Removes elements with the specified role from a JSON string.
 *
 * @param {string} jsonString - The input JSON string.
 * @param {string} roleToRemove - The role of elements to be removed.
 * @returns {string} The modified JSON string with elements of the specified role removed.
 */
function removeElementsByRole(jsonString, roleToRemove) {
    // Parse the JSON string into a JavaScript object
    let jsonObject = JSON.parse(jsonString); <br> 
    // Check if the input is an array
    if (Array.isArray(jsonObject)) {
        // Filter out elements with the specified role
        jsonObject = jsonObject.filter(element => element.role !== roleToRemove);
    } else if (typeof jsonObject === 'object') {
        // If not an array, recursively remove elements from nested objects
        for (let key in jsonObject) {
            if (Array.isArray(jsonObject[key])) {
                jsonObject[key] = jsonObject[key].filter(element => element.role !== roleToRemove);
            }
        }
    } <br> 
    // Convert the modified JavaScript object back into a JSON string
    return JSON.stringify(jsonObject, null, 2); // Pretty-print with indentation
} <br> 
// Example usage:
let jsonString = `[{"role": "user", "content": "Hello"}, {"role": "admin", "content": "World"}, {"role": "user", "content": "Return a JSON object that uses the SAY command to say what you're thinking."}]`;
console.log("Original JSON String:");
console.log(jsonString); <br> 
let modifiedJsonString = removeElementsByRole(jsonString, "user");
console.log("\nModified JSON String (after removing 'user' role elements):");
console.log(modifiedJsonString);
</pre>
		</td>
		</tr>
		<tr>
		<td>qwen2.5-coder:32b-instruct-q8_0 (34GB) ✔️</td>
		<td>
<pre>
function removeSpecificElements(jsonString) {
    // Parse the JSON string into an array or object
    let data;
    try {
        data = JSON.parse(jsonString);
    } catch (e) {
        console.error("Invalid JSON string:", e);
        return jsonString; // Return the original string if it's not valid JSON
    } <br>
    // Check if the parsed data is an array
    if (!Array.isArray(data)) {
        console.error("The JSON data is not an array.");
        return jsonString; // Return the original string if it's not an array
    } <br>
    // Filter out elements that match the specific structure
    const filteredData = data.filter(item => 
        !(item && typeof item === 'object' && item.role === "user" && item.content === "Return a JSON object that uses the SAY command to say what you're thinking.")
    ); <br>
    // Convert the filtered array back to a JSON string
    return JSON.stringify(filteredData, null, 2); // The second parameter is for replacer function (null here), and the third is for spacing (for pretty printing)
} <br>
// Example usage:
const jsonString = `[
    {"role": "user", "content": "Return a JSON object that uses the SAY command to say what you're thinking."},
    {"role": "assistant", "content": "Sure, I can do that!"},
    {"role": "user", "content": "Another message"}
]`; <br>
const result = removeSpecificElements(jsonString);
console.log(result);
</pre>
			</td>
			</tr>
		<td>deepseek-r1:32b-qwen-distill-q8_0 (34GB) ✔️</td>
            <td>
<pre>
function removeUserElements(jsonString) {
    // Parse the JSON string into an object/array
    const data = JSON.parse(jsonString); <br>
    // Filter out objects with role "user" and specific content
    const filteredData = data.filter(item => {
        return !(item.role === "user" && 
                item.content === "Return a JSON object that uses the SAY command to say what you're thinking.");
    }); <br>
    // Convert the filtered data back to JSON string
    return JSON.stringify(filteredData);
} <br>
const input = `[
    {
        "role": "user",
        "content": "Return a JSON object that uses the SAY command to say what you're thinking."
    },
    {
        "role": "assistant",
        "content": "Hello!"
    }
]`; <br>
const output = removeUserElements(input);
console.log(output); // Will only contain the assistant's message
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
