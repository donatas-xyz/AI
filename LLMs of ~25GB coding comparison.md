<table style="width:100%">
  <caption>LLMs of ~25GB coding comparison</caption>
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
      <td>qwen3.5:35b-a3b-q4_K_M (23GB) ❌️</td>
            <td>
<pre>
/**
 * Removes all objects with "role": "user" from a JSON array string or array.
 * @param {string|Array} input - A JSON string or array containing objects
 * @returns {string|Array} - The filtered array or its JSON string representation
 */
function removeUserMessages(input) {
  let dataArray;<br>
  // Parse input if it's a string
  if (typeof input === 'string') {
    try {
      dataArray = JSON.parse(input);
    } catch (e) {
      throw new Error('Invalid JSON string: ' + e.message);
    }
  } else if (Array.isArray(input)) {
    dataArray = input;
  } else {
    throw new Error('Input must be a JSON string or array');
  }<br>
  // Validate top-level structure
  if (!Array.isArray(dataArray)) {
    throw new Error('Parsed JSON must be an array');
  }<br>
  // Filter out user messages
  const filteredArray = dataArray.filter(item => {
    return !(item && typeof item === 'object' && item.role === 'user');
  });<br>
  return filteredArray;
}<br>
// Optional: Function to return the result as a JSON string
function removeUserMessagesToJson(input) {
  const result = removeUserMessages(input);
  return JSON.stringify(result, null, 2);
}<br>
const jsonInput = `[
  {"role": "system", "content": "You are a helpful assistant."},
  {"role": "user", "content": "Return a JSON object that uses the SAY command to say what you're thinking."},
  {"role": "assistant", "content": "I am thinking of providing filtered output."},
  {"role": "user", "content": "Second user message"}
]`;<br>
// Return as array
const cleanedArray = removeUserMessages(jsonInput);
console.log(cleanedArray);
// Output: Array without "user" role messages<br>
// Return as formatted JSON string
const jsonString = removeUserMessagesToJson(jsonInput);
console.log(jsonString);
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
