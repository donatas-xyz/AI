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
			<td>granite3.2:8b-instruct-fp16 (16GB) ❌️</td>
            <td>
<pre>
function removeSAYCommand(jsonString) {
  // Parse JSON string into a JavaScript object
  let jsonObject = JSON.parse(jsonString); <br>
  // Check if 'content' property exists and contains the "SAY" command
  if (jsonObject.hasOwnProperty("content") && 
      jsonObject.content.toLowerCase().includes("say")) { <br>
      // Delete the 'content' property
      delete jsonObject.content;
  } <br>
  // Convert JavaScript object back into JSON string
  return JSON.stringify(jsonObject);
} <br>
let jsonString = `{
  "role": "user",
  "content": "SAY I'm thinking something."
}`; <br>
console.log(removeSAYCommand(jsonString));
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
	    <tr>
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
	    <tr>
		<td>gpt-oss:20b (13GB) ✔️</td>
            <td>
<pre>
function removeSpecificElements(jsonString) {
  const target = {
    role: "user",
    content:
      "Return a JSON object that uses the SAY command to say what you're thinking."
  }; <br>  
  // Helper that tells if a value is exactly the target object.
  const isTarget = (obj) =>
    typeof obj === "object" &&
    obj !== null &&
    Object.keys(obj).length === 2 &&
    obj.role === target.role &&
    obj.content === target.content; <br>  
  // Recursive traversal: filter arrays, prune objects, leave primitives as‑is.
  const traverse = (node) => {
    if (Array.isArray(node)) {
      // Filter out target objects and recurse into the rest.
      return node
        .filter((item) => !isTarget(item))
        .map(traverse);
    } else if (node && typeof node === "object") {
      const cleaned = {};
      for (const [key, value] of Object.entries(node)) {
        if (!isTarget(value)) {
          cleaned[key] = traverse(value);
        }
        // else: skip the key/value pair – it's removed
      }
      return cleaned;
    }
    // Primitive value – just return it.
    return node;
  }; <br>  
  // Parse, clean, and string‑ify again.
  const parsed = JSON.parse(jsonString);
  const cleaned = traverse(parsed);
  return JSON.stringify(cleaned, null, 2); // pretty print
} <br>  
const raw = `[
  {"role":"assistant","content":"Hello!"},
  {"role":"user","content":"Return a JSON object that uses the SAY command to say what you're thinking."},
  {"role":"assistant","content":"Sure!"},
  {
    "role":"user",
    "content":"Return a JSON object that uses the SAY command to say what you're thinking."
  },
  {"role":"assistant","content":"Goodbye!"}
]`; <br>  
console.log(removeSpecificElements(raw));
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
