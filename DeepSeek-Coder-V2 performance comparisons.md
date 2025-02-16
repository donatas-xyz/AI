<table style="width:100%">
	<caption>DeepSeek-Coder-V2 performance comparison</caption>
    <thead>
        <tr>
			<th style="width:10%"></th>
			<th style="width:30%">deepseek-coder-v2:16b</th>
            <th style="width:30%">deepseek-coder-v2:16b-lite-instruct-q8_0</th>
            <th style="width:30%">deepseek-coder-v2:16b-lite-instruct-fp16</th>
        </tr>
    </thead>
    <tbody>
        <tr>
			<td>Size</td>
            <td>8.9 GB</td>
			<td>16 GB</td>
			<td>31 GB</td>
        </tr>
		<tr>
			<td>Processing</td>
            <td>100% GPU</td>
			<td>40%/60% CPU/GPU</td>
			<td>67%/33% CPU/GPU</td>
        </tr>
        <tr>
			<td>Prompt</td>
            <td colspan=3><kbd>Who are you?</kbd></td>
        </tr>
        <tr>
			<td>Response</td>
            <td>
				<samp>
					I am DeepSeek Coder, an intelligent assistant developed by China's DeepSeek company. My design aims to provide services such as information retrieval, conversational interaction, and answering questions through natural language processing and machine learning technologies.
				</samp>
			</td>
			<td colspan=2>
				<samp>
					I am DeepSeek Coder, an intelligent assistant developed by the Chinese company DeepSeek. My design aims to provide services such as information retrieval, conversational interaction, and answering questions through natural language processing and machine learning technologies.
				</samp>
			</td>
        </tr>
        <tr>
			<td>Results</td>
            <td>
				<samp>
					total duration:       1.3380367s <br>
					load duration:        12.5062ms <br>
					prompt eval count:    12 token(s) <br>
					prompt eval duration: 396ms <br>
					prompt eval rate:     30.30 tokens/s <br>
					eval count:           46 token(s) <br>
					eval duration:        928ms <br>
					eval rate:            49.57 tokens/s 
				</samp>
			</td>
            <td>
				<samp>
					total duration:       2.6039002s <br>
					load duration:        13.1781ms <br>
					prompt eval count:    12 token(s) <br>
					prompt eval duration: 558ms <br>
					prompt eval rate:     21.51 tokens/s <br>
					eval count:           45 token(s) <br>
					eval duration:        2.032s <br>
					eval rate:            22.15 tokens/s
				</samp>
			</td>
			<td>
				<samp>
					total duration:       5.1907445s <br>
					load duration:        12.4864ms <br>
					prompt eval count:    12 token(s) <br>
					prompt eval duration: 733ms <br>
					prompt eval rate:     16.37 tokens/s <br>
					eval count:           45 token(s) <br>
					eval duration:        4.442s <br>
					eval rate:            10.13 tokens/s
				</samp>
			</td>
        </tr>
    </tbody>
	<tfoot>
		<tr>
		  <td colspan=4>* <a href="https://github.com/donatas-xyz/AI/discussions/1">Setup used</a></td>
		</tr>
	</tfoot>
</table>
