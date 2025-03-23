<table style="width:100%">
	<caption><a href="https://ollama.com/library/granite3.2-vision" target="_blank" rel="noopener noreferrer">Granite3.2</a> vs <a href="https://ollama.com/library/llava" target="_blank" rel="noopener noreferrer">LLaVA</a> vs <a href="https://ollama.com/library/gemma3" target="_blank" rel="noopener noreferrer">Gemma3</a> vs <a href="https://ollama.com/library/llama3.2-vision" target="_blank" rel="noopener noreferrer">Llama3.2</a> tests (2B vs 27B vs 34B vs 90B)</caption>
    <thead>
        <tr>
			<th style="width:12%"></th>
			<th style="width:22%">granite3.2-vision:2b-fp16</th>
			<th style="width:22%">llava:34b-v1.6-q8_0</th>
			<th style="width:22%">gemma3:27b-it-fp16</th>
			<th style="width:22%">llama3.2-vision:90b-instruct-q8_0</th>
        </tr>
    </thead>
    <tbody>
        <tr>
			<td>Size</td>
			<td>8.8 GB</td>
			<td>38 GB</td>
			<td>54 GB</td>
			<td>101 GB</td>
        </tr>
		<tr>
			<td>Processing</td>
			<td>100% GPU</td>
			<td>72%/28% CPU/GPU</td>
			<td>82%/18% CPU/GPU</td>
			<td>89%/11% CPU/GPU</td>
        </tr>
        <tr>
		<td>Response</td>
			<td>
				<img src="https://github.com/user-attachments/assets/3629a19d-7464-431f-8340-7ac5ce1af30f" alt="Granite3.2 - What does the sign say and in what language?"/>
			        <img src="https://github.com/user-attachments/assets/49a49dd7-c042-4a77-9a03-bb9be32c70c4" alt="Granite3.2 - What timeline is this cannon from?"/>
				<img src="https://github.com/user-attachments/assets/43c283ad-b8f1-424d-85b7-c74ee698d2a8" alt="Granite3.2 - Which tree does this belong to and is it native to UK?"/>
			</td>
            <td>
				<img src="https://github.com/user-attachments/assets/185ef8ab-f1e1-4b27-adca-2cfbd3c5ae2a" alt="LLaVA - What does the sign say and in what language?"/>
			    <img src="https://github.com/user-attachments/assets/b956a48c-9e78-4816-b90b-e094d5f592a6" alt="LLaVA - What timeline is this cannon from?"/>
				<img src="https://github.com/user-attachments/assets/30bb154b-4b5d-4edf-bb78-ad77d89440d1" alt="LLaVA - Which tree does this belong to and is it native to UK?"/>
			</td>
			<td>
				<img src="https://github.com/user-attachments/assets/8f19fcc5-c134-4a14-be03-405b0231a2ae" alt="Gemma3 - What does the sign say and in what language?"/>
				<img src="https://github.com/user-attachments/assets/4e066c22-6578-4ccd-aeed-4923f0e6afdd" alt="Gemma3 - What timeline is this cannon from?"/>
				<img src="https://github.com/user-attachments/assets/b5299350-cb3c-424b-8f28-29c750413b38" alt="Gemma3 - Which tree does this belong to and is it native to UK?"/>
			</td>
			<td>
				<img src="https://github.com/user-attachments/assets/3edddd11-b9f3-47b4-be05-77c81ee08829" alt="Llama - What does the sign say and in what language?"/>
				<img src="https://github.com/user-attachments/assets/9b961042-48ad-4f7d-af46-2833c56ac11f" alt="Llama - What timeline is this cannon from?"/>
				<img src="https://github.com/user-attachments/assets/874b1b77-720e-45ec-b96c-9e6c82b805e9" alt="Llama - Which tree does this belong to and is it native to UK?"/>
			</td>
        </tr>
		<tr>
			<td>Results</td>
			<td>
				<samp>
					total duration:       3.1295685s <br>
					load duration:        74.5903ms <br>
					prompt eval count:    7349 token(s) <br>
					prompt eval duration: 2.852s <br>
					prompt eval rate:     2576.79 tokens/s <br>
					eval count:           10 token(s) <br>
					eval duration:        171ms <br>
					eval rate:            58.48 tokens/s
				</samp>
			</td>
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
					total duration:       1m25.5513265s <br>
					load duration:        92.971ms <br>
					prompt eval count:    281 token(s) <br>
					prompt eval duration: 6.5869986s <br>
					prompt eval rate:     42.66 tokens/s <br>
					eval count:           57 token(s) <br>
					eval duration:        1m18.8398634s <br>
					eval rate:            0.72 tokens/s
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
		  <td colspan=5>
			* <a href="https://github.com/donatas-xyz/AI/discussions/1" target="_blank" rel="noopener noreferrer">Setup used</a> <br>
			* All tests were performed on a fresh model load with no prior context and with the default settings.
		  </td>
		</tr>
	</tfoot>
</table>
