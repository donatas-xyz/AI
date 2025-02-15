<table>
    <thead>
        <tr>
			<th></th>
            <th>Windows 11</th>
            <th>WSL (Ubuntu 24.04)</th>
        </tr>
    </thead>
    <tbody>
        <tr>
			<td>Model</td>
            <td colspan=2><kbd>ollama run deepseek-r1:32b --verbose</kbd></td>
        </tr>
        <tr>
			<td>Prompt</td>
            <td colspan=2><kbd>Who are you?</kbd></td>
        </tr>
        <tr>
			<td>Response</td>
            <td colspan=2>
				<samp>
					Greetings! I'm DeepSeek-R1, an artificial intelligence assistant created by DeepSeek. I'm at your service and would be delighted to assist you with any inquiries or tasks you may have.
				</samp>
			</td>
        </tr>
        <tr>
			<td>Results</td>
            <td>
				<samp>
					total duration:       14.7184093s <br>
					load duration:        16.6963ms <br>
					prompt eval count:    7 token(s) <br>
					prompt eval duration: 1.025s <br>
					prompt eval rate:     6.83 tokens/s <br>
					eval count:           44 token(s) <br>
					eval duration:        13.675s <br>
					eval rate:            3.22 tokens/s
				</samp>
			</td>
            <td>
				<samp>
					total duration:       15.551926379s <br>
					load duration:        12.573405ms <br>
					prompt eval count:    7 token(s) <br>
					prompt eval duration: 1.63s <br>
					prompt eval rate:     4.29 tokens/s <br>
					eval count:           44 token(s) <br>
					eval duration:        13.908s <br>
					eval rate:            3.16 tokens/s
				</samp>
			</td>
        </tr>
    </tbody>
</table>
