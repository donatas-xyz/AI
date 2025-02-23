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
			<td>wizardlm2:8x22b-q4_0 ✔️</td>
            <td>
<pre>
function removeSpecifiedElement(jsonString) {
	// Parse the JSON string into an array of objects
	let jsonArray = JSON.parse(jsonString); <br>
	// Filter out the specified element
	let filteredArray = jsonArray.filter(obj => {
		return !(obj.role === "user" && 
		obj.content === "Return a JSON object that uses the SAY command to say what you're thinking.");
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
		<tr>
		<td>qwq:32b-preview-fp16 ✔️</td>
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
