<table style="width:100%">
	<caption>LLMs of ~70GB and over coding comparison</caption>
    <thead>
        <tr>
			<th style="width:10%">Model</th>
			<th style="width:90%">Code produced</th>
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
			<td>command-a:111b-03-2025-q4_K_M (67GB) ✔️</td>
            <td>
<pre>
/**
 * Removes specific JSON objects from an array within a JSON string.
 * 
 * @param {string} jsonString - The input JSON string containing an array of objects.
 * @returns {string} The modified JSON string with the specified elements removed.
 */
function removeSpecificElementsFromJson(jsonString) {
  // Parse the JSON string into a JavaScript object
  const data = JSON.parse(jsonString); <br>
  // Filter out the unwanted elements from the array
  const filteredData = data.filter(item => 
      !(item.role === "user" && item.content === "Return a JSON object that uses the SAY command to say what you're thinking.")
  ); <br>
  // Convert the filtered array back into a JSON string
  return JSON.stringify(filteredData);
} <br>
// Example usage:
const inputJson = `[
  {
      "role": "user",
      "content": "Return a JSON object that uses the SAY command to say what you're thinking."
  },
  {
      "role": "assistant",
      "content": "Here is the response."
  },
  {
      "role": "user",
      "content": "Another user message."
  }
]`; <br>
const outputJson = removeSpecificElementsFromJson(inputJson);
console.log(outputJson);
</pre>
		</td>
		</tr>
        <tr>
			<td>exaone-deep:32b-fp16 (64GB) ✔️</td>
            <td>
<pre>
function removeElements(jsonStr) {
  const TARGET = {
      role: 'user',
      content: "Return a JSON object that uses the SAY command to say what you're thinking."
  };
  const array = JSON.parse(jsonStr);
  const filtered = array.filter(obj => {
      return !(
          obj.role === TARGET.role &&
          obj.content === TARGET.content &&
          Object.keys(obj).length === Object.keys(TARGET).length
      );
  });
  return JSON.stringify(filtered);
}
</pre>
		</td>
		</tr>
        <tr>
			<td>mistral-large:123b (73GB) ✔️</td>
            <td>
<pre>
function removeSpecificElements(jsonString) {
    // Parse the input JSON string into an array of objects
    let jsonArray = JSON.parse(jsonString); <br>
    // Define the specific content to be removed
    const targetContent = "Return a JSON object that uses the SAY command to say what you're thinking."; <br>
    // Filter out elements with the specified role and content
    let filteredArray = jsonArray.filter(item => !(item.role === 'user' && item.content === targetContent)); <br>
    // Convert the filtered array back into a JSON string
    return JSON.stringify(filteredArray);
} <br>
// Example usage:
const inputJsonString = `[
  {"role": "user", "content": "Return a JSON object that uses the SAY command to say what you're thinking."},
  {"role": "system", "content": "Hello World"},
  {"role": "assistant", "content": "I am thinking about coding"}
]`; <br>
const outputJsonString = removeSpecificElements(inputJsonString);
console.log(outputJsonString);
</pre>
		</td>
		</tr>
		        <tr>
			<td>llama3.3:70b-instruct-q8_0 (74GB) ✔️</td>
            <td>
<pre>
/**
 * Removes elements with the specified role and content from a given JSON string.
 *
 * @param {string} jsonString The input JSON string.
 * @param {string} targetRole The target role to remove.
 * @param {string} targetContent The target content to remove.
 * @returns {string} The filtered JSON string.
 */
function removeElements(jsonString, targetRole = 'user', targetContent) {
    // Parse the JSON string into a JavaScript object
    let jsonObject = JSON.parse(jsonString); <br>
    // Filter out elements with the specified role and content
    if (Array.isArray(jsonObject)) {
        jsonObject = jsonObject.filter(element => !(element.role === targetRole && element.content.includes(targetContent)));
    } else if (typeof jsonObject === 'object') {
        for (let key in jsonObject) {
            if (Array.isArray(jsonObject[key])) {
                jsonObject[key] = jsonObject[key].filter(element => !(element.role === targetRole && element.content.includes(targetContent)));
            }
        }
    } <br>
    // Stringify the filtered object back into a JSON string
    return JSON.stringify(jsonObject, null, 4);
} <br>
// Example usage:
const jsonString = '[{"role": "admin", "content": "Hello"}, {"role": "user", "content": "Return a JSON object that uses the SAY command to say what you\'re thinking."}, {"role": "moderator", "content": "World"}]';
const targetRole = 'user';
const targetContent = 'Return a JSON object that uses the SAY command to say what you'; <br>
console.log(removeElements(jsonString, targetRole, targetContent));
</pre>
		</td>
		</tr>
		<tr>
		<td>qwen3:32b-fp16 (66GB) ✔️</td>
		<td>
<pre>
function removeUserSAYCommands(jsonString) {
  try {
      // Step 1: Parse the JSON string into an array of objects
      const data = JSON.parse(jsonString); <br>
      // Step 2: Filter out the matching elements
      const filteredData = data.filter(item => 
          item.role !== 'user' ||
          item.content !== 'Return a JSON object that uses the SAY command to say what you\'re thinking.'
      ); <br>
      // Step 3: Convert the modified array back to a JSON string
      return JSON.stringify(filteredData, null, 2); // Optional: pretty-printed with 2 spaces <br>
  } catch (error) {
      // Handle invalid JSON input
      throw new Error('Invalid JSON input: ' + error.message);
  }
} <br>
const input = `
[
  {
    "role": "user",
    "content": "Return a JSON object that uses the SAY command to say what you're thinking."
  },
  {
    "role": "assistant",
    "content": "I understand the request."
  }
]
`; <br>
const result = removeUserSAYCommands(input);
console.log(result);
</pre>
			</td>
			</tr>
		<tr>
		<td>qwen3-coder:30b-a3b-fp16 (61GB) ✔️</td>
		<td>
<pre>
function removeUserThinkingElement(jsonString) {
    try {
        // Parse the JSON string into an array/object
        const parsed = JSON.parse(jsonString); <br>        
        // If it's an array, filter out the specific object
        if (Array.isArray(parsed)) {
            const filtered = parsed.filter(item => 
                !(item.role === "user" && 
                  item.content === "Return a JSON object that uses the SAY command to say what you're thinking.")
            );
            return JSON.stringify(filtered, null, 2);
        } <br>        
        // If it's an object, check if it matches the target and return empty object or handle accordingly
        if (typeof parsed === 'object' && parsed !== null) {
            // For objects, we can't simply remove elements without knowing the structure
            // This would require more specific logic based on your use case
            console.warn("Input is an object, not an array. Consider restructuring for proper filtering.");
            return jsonString;
        } <br>        
        return jsonString;
    } catch (error) {
        console.error("Invalid JSON string:", error);
        return jsonString;
    }
} <br>
// Example usage:
const inputJson = `[
    {
        "role": "user",
        "content": "Hello"
    },
    {
        "role": "user",
        "content": "Return a JSON object that uses the SAY command to say what you're thinking."
    },
    {
        "role": "assistant",
        "content": "Hi there!"
    }
]`; <br>
const result = removeUserThinkingElement(inputJson);
console.log(result);
</pre>
			</td>
			</tr>
	    <tr>
		<td>wizardlm2:8x22b-q4_0 (79GB) ✔️</td>
            <td>
<pre>
function removeSpecifiedElement(jsonString) {
	// Parse the JSON string into an array of objects
	let jsonArray = JSON.parse(jsonString); <br>
	// Filter out the specified element
	let filteredArray = jsonArray.filter(obj => {
		return !(obj.role === "user" && obj.content === "Return a JSON object that uses the SAY command to say what you're thinking.");
	}); <br>
	// Convert the filtered array back into a JSON string
	let updatedJsonString = JSON.stringify(filteredArray); <br>
	return updatedJsonString;
} <br>
// Example usage:
const originalJsonString = `[
	{"role": "system", "content": "Hello, how can I assist you?"},
	{"role": "user", "content": "Return a JSON object that uses the SAY command to say what you're thinking."},
	{"role": "assistant", "content": "I'm thinking about how to best help you today."}
]`; <br>
const updatedJsonString = removeSpecifiedElement(originalJsonString);
console.log(updatedJsonString);
</pre>
		</td>
		</tr>
        <tr>
			<td>r1-1776:70b-distill-llama-q8_0 (74GB) ❌️</td>
            <td>
<pre>
function removeUserElements(jsonStr) {
  const data = JSON.parse(jsonStr);
  if (!Array.isArray(data)) {
      throw new Error('Input must be a JSON array.');
  } <br>
  const filteredData = data.filter(element => 
      !(element.role === 'user' && element.content?.startsWith('{'))
  ); <br>
  return JSON.stringify(filteredData, null, 2);
} <br>
const input = `[{"role": "user", "content": "{\\n\"role\": \"assistant\", ..."},{"role": "assistant", "content": "Hello"}]`;
const output = removeUserElements(input);
console.log(output); // Output: [{"role":"assistant","content":"Hello"}]
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
