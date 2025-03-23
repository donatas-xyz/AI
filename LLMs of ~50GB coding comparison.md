<table style="width:100%">
	<caption>LLMs of ~50GB coding comparison</caption>
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
			<td>gemma3:27b-it-fp16 (54GB) ✔️</td>
            <td>
<pre>
/**
 * Removes elements with the structure {"role": "user", "content": "Return a JSON object that uses the SAY command to say what you're thinking."} from a JSON string.
 *
 * @param {string} jsonString The JSON string to process.
 * @returns {string} The JSON string with the specified elements removed.  Returns the original string if input is invalid.
 */
function removeSayElements(jsonString) {
  try {
    const data = JSON.parse(jsonString); <br>
    if (Array.isArray(data)) {
      const filteredData = data.filter(item => {
        return !(item.role === "user" && item.content === "Return a JSON object that uses the SAY command to say what you're thinking.");
      });
      return JSON.stringify(filteredData, null, 2); // Use null, 2 for pretty printing
    } else if (typeof data === 'object' && data !== null) {
      // Handle the case where the input is a single object, not an array
      const filteredObject = {};
      for (const key in data) {
        if (data.hasOwnProperty(key)) {
          if (typeof data[key] === 'object' && data[key] !== null) {
            if (Array.isArray(data[key])) {
              filteredObject[key] = data[key].filter(item => {
                return !(item.role === "user" && item.content === "Return a JSON object that uses the SAY command to say what you're thinking.");
              });
            } else {
              filteredObject[key] = data[key];
            }
          } else {
            filteredObject[key] = data[key];
          }
        }
      }
      return JSON.stringify(filteredObject, null, 2);
    } else {
      // Handle cases where the input is not a valid JSON object or array
      return jsonString; // Return the original string if it's not a valid JSON object/array
    }
  } catch (error) {
    // Handle JSON parsing errors
    console.error("Error parsing JSON:", error);
    return jsonString; // Return the original string if parsing fails
  }
} <br>
// Example Usage:
const jsonString1 = `
[
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
]
`; <br>
const cleanedJson1 = removeSayElements(jsonString1);
console.log("Cleaned JSON 1:\n", cleanedJson1); <br>
const jsonString2 = `
{
  "messages": [
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
  ]
}
`; <br>
const cleanedJson2 = removeSayElements(jsonString2);
console.log("Cleaned JSON 2:\n", cleanedJson2); <br>
const invalidJson = "This is not JSON";
const cleanedInvalidJson = removeSayElements(invalidJson);
console.log("Cleaned Invalid JSON:\n", cleanedInvalidJson);
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
