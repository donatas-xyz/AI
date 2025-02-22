<table style="width:100%">
	<caption><a href="https://ollama.com/library/llava" target="_blank" rel="noopener noreferrer">LLaVA</a> vs <a href="https://ollama.com/library/llama3.2-vision" target="_blank" rel="noopener noreferrer">Llama3.2</a> tests (34B vs 90B)</caption>
    <thead>
        <tr>
			<th style="width:10%"></th>
			<th style="width:45%">llava:34b-v1.6-q8_0</th>
			<th style="width:45%">llama3.2-vision:90b-instruct-q8_0</th>
        </tr>
    </thead>
    <tbody>
        <tr>
			<td>Size</td>
			<td>38 GB</td>
			<td>101 GB</td>
        </tr>
		<tr>
			<td>Processing</td>
			<td>72%/28% CPU/GPU</td>
			<td>89%/11% CPU/GPU</td>
        </tr>
        <tr>
		<td>Response</td>
            <td>
              <img src="https://github.com/user-attachments/assets/185ef8ab-f1e1-4b27-adca-2cfbd3c5ae2a" alt="LLaVA - What does the sign say and in what language?">
<img src="https://github.com/user-attachments/assets/b956a48c-9e78-4816-b90b-e094d5f592a6" alt="LLaVA - What timeline is this cannon from?">
<img src="https://github.com/user-attachments/assets/30bb154b-4b5d-4edf-bb78-ad77d89440d1" alt="LLaVA - Which tree does this belong to and is it native to UK?">
			</td>
			<td>
				<img src="https://github.com/user-attachments/assets/3edddd11-b9f3-47b4-be05-77c81ee08829" alt="Llama - What does the sign say and in what language?">
				<img src="https://github.com/user-attachments/assets/9b961042-48ad-4f7d-af46-2833c56ac11f" alt="Llama - What timeline is this cannon from?">
				<img src="https://github.com/user-attachments/assets/874b1b77-720e-45ec-b96c-9e6c82b805e9" alt="Llama - Which tree does this belong to and is it native to UK?">
			</td>
        </tr>
		<tr>
			<td>Results</td>
            <td>
				<samp>
					total duration:       1m39.3982339s <br>
					load duration:        76.0085ms <br>
					prompt eval count:    619 token(s) <br>
					prompt eval duration: 11.165s <br>
					prompt eval rate:     55.44 tokens/s <br>
					eval count:           112 token(s) <br>
					eval duration:        1m28.115s <br>
					eval rate:            1.27 tokens/s
				</samp>
			</td>
			<td>
				<samp>
					total duration:       3m4.6938644s <br>
					load duration:        76.2814ms <br>
					prompt eval count:    24 token(s) <br>
					prompt eval duration: 15.466s <br>
					prompt eval rate:     1.55 tokens/s <br>
					eval count:           62 token(s) <br>
					eval duration:        2m48.6s <br>
					eval rate:            0.37 tokens/s
				</samp>
			</td>
        </tr>
    </tbody>
	<tfoot>
		<tr>
		  <td colspan=3>
			* <a href="https://github.com/donatas-xyz/AI/discussions/1" target="_blank" rel="noopener noreferrer">Setup used</a> <br>
			* All tests were performed on a fresh model load with no prior context and with the default settings.
		  </td>
		</tr>
	</tfoot>
</table>
