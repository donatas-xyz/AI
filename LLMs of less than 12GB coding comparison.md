<table style="width:100%">
	<caption>LLMs of less than 12GB coding comparison</caption>
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
		<td>phi4:14b (9.1GB) ✔️</td>
            <td>
<pre>
function removeSpecificElements(jsonString) {
  try {
      // Parse the input JSON string into an array of objects.
      const dataArray = JSON.parse(jsonString); <br> 
      // Filter out elements that match the specified structure.
      const filteredArray = dataArray.filter(element => 
          !(element.role === 'user' &&
            element.content === "Return a JSON object that uses the SAY command to say what you're thinking.")
      ); <br> 
      // Convert the filtered array back into a JSON string.
      return JSON.stringify(filteredArray, null, 2); // Beautify with an indent of 2 spaces
  } catch (error) {
      console.error("Invalid JSON input:", error);
      return null;
  }
} <br> 
// Example usage:
const jsonString = `
[
  {"role": "user", "content": "Return a JSON object that uses the SAY command to say what you're thinking."},
  {"role": "system", "content": "Execute the task."},
  {"role": "user", "content": "Another message."}
]
`; <br> 
console.log(removeSpecificElements(jsonString));
</pre>
		</td>
		</tr>
		<tr>
		<td>deepseek-r1:14b (9GB) ✔️</td>
		<td>
<pre>
function removeElements(jsonString) {
  // Parse the JSON string into an object
  const data = JSON.parse(jsonString); <br>
  // Filter out elements matching the specified structure
  const filteredData = data.filter(item => {
      return !(item.role === "user" && item.content === "Return a JSON object that uses the SAY command to say what you're thinking.");
  }); <br>
  // Convert the filtered array back to a JSON string
  return JSON.stringify(filteredData, null, 2);
} <br>
const input = `[
  {
      "role": "user",
      "content": "Return a JSON object that uses the SAY command to say what you're thinking."
  },
  {
      "role": "assistant",
      "content": "Hello, how can I help you today?"
  }
]`; <br>
const output = removeElements(input);
console.log(output);
</pre>
			</td>
			</tr>
        <tr>
			<td>deepseek-coder-v2:16b (8.9GB) ❌️</td>
            <td>
<pre>
function removeRoleAndContent(jsonString) {
  try {
      // Parse the JSON string into an object
      let jsonObject = JSON.parse(jsonString); <br>      
      // Remove the "role" and "content" elements if they exist
      delete jsonObject["role"];
      delete jsonObject["content"]; <br>     
      // Convert the modified object back to a JSON string
      return JSON.stringify(jsonObject);
  } catch (error) {
      console.error("Error parsing JSON: ", error);
      return null;
  }
} <br>
// Example usage:
let jsonString = '{"role": "user", "content": "Return a JSON object that uses the SAY command to say what you\'re thinking."}';
let newJsonString = removeRoleAndContent(jsonString);
console.log(newJsonString); // Output will be: {"role": "user"}
</pre>
		</td>
		</tr>
			<tr>
		<td>deepseek-r1:8b (4.9GB) ❌️</td>
            <td>
<pre>
function removeJsonElements(jsonString) {
  try {
      // Parse the JSON string into an object
      const obj = JSON.parse(jsonString); <br>     
      // Remove 'role' property if it exists
      if (obj.hasOwnProperty('role')) {
          delete obj.role;
      } <br>     
      // Remove 'content' property if it exists
      if (obj.hasOwnProperty('content')) {
          delete obj.content;
      } <br> 
      // Convert the modified object back to JSON string
      return JSON.stringify(obj);
  } catch (error) {
      // Return the original JSON string if parsing fails
      return jsonString;
  }
} <br>
const result = removeJsonElements('{"role": "user", "content": "Return a JSON object that uses the SAY command to say what you\'re thinking."}');
console.log(result); // Output: '{"command": "SAY"}'
</pre>
		</td>
		</tr>
		        <tr>
			<td>mistral:7b-instruct-v0.3-q8_0 (7.7GB) ❌️</td>
            <td>
<pre>
function removeSpecificObject(jsonString) {
  // Parse the JSON string into an object
  const jsonObject = JSON.parse(jsonString); <br>
  // Filter out the unwanted object using filter() method
  const filteredJsonArray = jsonObject.filter((item) => {
    return item.role !== "user";
  }); <br>
  // Convert the filtered array back to a JSON string
  const newJsonString = JSON.stringify(filteredJsonArray); <br>
  return newJsonString;
} <br>
const initialJsonString = `[
  {
    "role": "assistant",
    "content": "Hello, how can I help you today?"
  },
  {
    "role": "user",
    "content": "Return a JSON object that uses the SAY command to say what you're thinking."
  }
]`; <br>
const filteredJsonString = removeSpecificObject(initialJsonString);
console.log(filteredJsonString);
</pre>
		</td>
		</tr>
			<tr>
		<td>mistral:7b (4.1GB) ❌️</td>
            <td>
<pre>
function removeSpecificObject(jsonString) {
  // Parse the JSON string into a JavaScript object
  let jsonObj = JSON.parse(jsonString); <br>
  // Filter out the object to be removed
  let filteredJsonArray = jsonObj.filter((obj) => {
      return obj.role !== "user";
  }); <br>
  // Convert the filtered array back to a JSON string
  let newJsonString = JSON.stringify(filteredJsonArray); <br>
  return newJsonString;
} <br>
let jsonString = `[
  {
    "role": "assistant",
    "content": "Hello, I'm an assistant."
  },
  {
    "role": "user",
    "content": "Return a JSON object that uses the SAY command to say what you're thinking."
  },
  {
    "role": "assistant",
    "content": "I don't have thoughts, I'm here to assist."
  }
]`; <br>
let newJsonString = removeSpecificObject(jsonString);
console.log(newJsonString); 
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
