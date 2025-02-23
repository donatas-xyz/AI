<table style="width:100%">
	<caption>LLMs of ~70GB and over coding comparison</caption>
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
		<td>qwq:32b-preview-fp16 (65GB) ✔️</td>
		<td>
<pre>
function removeUserElements(jsonString) {
  const obj = JSON.parse(jsonString);
  const specificContent = "Return a JSON object that uses the SAY command to say what you're thinking."; <br>
  function clean(item) {
    if (Array.isArray(item)) {
      let cleanedArray = item.filter(el => !isMatchingUserObject(el)).map(clean);
      return cleanedArray.length > 0 ? cleanedArray : [];
    } else if (typeof item === 'object' && item !== null) {
      if (isMatchingUserObject(item)) {
        return {};
      } else {
        const cleanedObj = {};
        for (const [key, value] of Object.entries(item)) {
          const cleanedValue = clean(value);
          if (Object.keys(cleanedValue).length > 0 || typeof cleanedValue !== 'object') {
            cleanedObj[key] = cleanedValue;
          }
        }
        return Object.keys(cleanedObj).length > 0 ? cleanedObj : {};
      }
    } else {
      return item;
    }
  } <br>
  function isMatchingUserObject(obj) {
    return obj.role === 'user' && obj.content === specificContent;
  } <br>
  const cleaned = clean(obj);
  return JSON.stringify(cleaned);
}
// Example usage:
const inputJson = `{
  "messages": [
    {
      "role": "user",
      "content": "Return a JSON object that uses the SAY command to say what you're thinking."
    },
    {
      "role": "assistant",
      "content": "Okay, here it is.",
      "data": [
        {
          "role": "user",
          "content": "Return a JSON object that uses the SAY command to say what you're thinking."
        }
      ]
    }
  ]
}`; <br>
console.log(removeUserElements(inputJson));
</pre>
			</td>
			</tr>
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
