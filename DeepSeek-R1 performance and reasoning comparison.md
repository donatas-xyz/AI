<table style="width:100%">
	<caption><a href="https://ollama.com/library/deepseek-r1" target="_blank" rel="noopener noreferrer">DeepSeek-R1</a> performance and accuracy comparison (14B, 32B, 70B)</caption>
    <thead>
        <tr>
			<th style="width:10%"></th>
			<th style="width:30%">deepseek-r1:14b</th>
            <th style="width:30%">deepseek-r1:32b</th>
            <th style="width:30%">deepseek-r1:70b</th>
        </tr>
    </thead>
    <tbody>
        <tr>
			<td>Size</td>
            <td>9 GB</td>
			<td>19 GB</td>
			<td>42 GB</td>
        </tr>
		<tr>
			<td>Processing</td>
            <td>100% GPU</td>
			<td>52%/48% CPU/GPU </td>
			<td>77%/23% CPU/GPU</td>
        </tr>
        <tr>
			<td>Prompt</td>
            <td colspan=3><kbd>List all the marriage dates and wives of Henry VIII</kbd></td>
        </tr>
        <tr>
			<td>Response</td>
            <td>
				<samp>
					Henry VIII had six wives in the following order: <br><br>
					1. **Catherine of Aragon** (married 1509) <br>
					2. **Anne Boleyn** (married 1533) <br>
					3. **Jane Seymour** (married 1536) <br>
					4. **Anna of Cleves** (married 1540) <br>
					5. **Kathryn Howard** (married 1543, executed 1544) <br>
					6. **Catherine Parr** (married 1547) <br><br>
					This order reflects the sequence of their marriages and notable events such as Kathryn Howard's execution.
				</samp>
			</td>
			<td>
				<samp>
					Henry VIII, King of England, married six times during his reign. Here is an organized list of his marriages, detailing the wives and their respective marriage dates: <br><br>
					1. **Catherine of Aragon** <br>
					   - Marriage Date: June 11, 1509 <br>
					   - Divorce/Annulment: Annulled in 1533 <br>
					2. **Anne Boleyn** <br>
					   - Marriage Date: May 28, 1533 <br>
					   - Execution: Executed on May 19, 1536 <br>
					3. **Jane Seymour** <br>
					   - Marriage Date: May 30, 1536 <br>
					   - Death: Died on October 24, 1537, after giving birth to Edward VI <br>
					4. **Anne of Cleves** <br>
					   - Marriage Date: January 6, 1540 <br>
					   - Divorce/Annulment: Annulled in July 1540 <br>
					5. **Catherine Howard** <br>
					   - Marriage Date: July 28, 1540 (Note: Some sources suggest the marriage may have been consummated later) <br>
					   - Execution: Executed on February 13, 1542 <br>
					6. **Catherine Parr** <br>
					   - Marriage Date: July 12, 1543 <br>
					   - Survival: Survived Henry VIII after his death in 1547 <br><br>
					This list provides a clear timeline of Henry VIII's marriages, highlighting the progression of his unions and their outcomes.
				</samp>
			</td>
			<td>
				<samp>
					Henry VIII, known for his six marriages, wed each of his wives on the following dates: <br><br>
					1. **Catherine of Aragon** <br>
					   - Married: June 11, 1509 <br>
					   - Ended: May 23, 1533 (annulled) <br>
					2. **Anne Boleyn** <br>
					   - Married: January 25, 1533 <br>
					   - Ended: May 19, 1536 (executed) <br>
					3. **Jane Seymour** <br>
					   - Married: May 30, 1536 <br>
					   - Ended: October 24, 1537 (died after childbirth) <br>
					4. **Anne of Cleves** <br>
					   - Married: January 6, 1540 <br>
					   - Ended: July 12, 1540 (annulled) <br>
					5. **Catherine Howard** <br>
					   - Married: July 28, 1540 <br>
					   - Ended: February 13, 1542 (executed) <br>
					6. **Catherine Parr** <br>
					   - Married: July 12, 1543 <br>
					   - Ended: January 28, 1547 (Henry's death) <br><br>
					Each marriage concluded due to annulment, execution, or natural causes, except for his final marriage to Catherine Parr, who survived him.
				</samp>
			</td>
        </tr>
        <tr>
			<td>Results</td>
            <td>
				<samp>
					total duration:       1m44.9149327s <br>
					load duration:        17.6081ms <br>
					prompt eval count:    13 token(s) <br>
					prompt eval duration: 521ms <br>
					prompt eval rate:     24.95 tokens/s <br>
					eval count:           4383 token(s) <br>
					eval duration:        1m44.375s <br>
					eval rate:            41.99 tokens/s
				</samp>
			</td>
            <td>
				<samp>
					total duration:       9m26.9783709s <br>
					load duration:        18.1699ms <br>
					prompt eval count:    13 token(s) <br>
					prompt eval duration: 1.345s <br>
					prompt eval rate:     9.67 tokens/s <br>
					eval count:           1588 token(s) <br>
					eval duration:        9m25.613s <br>
					eval rate:            2.81 tokens/s
				</samp>
			</td>
			<td>
				<samp>
					total duration:       15m58.9944251s <br>
					load duration:        20.7571ms <br>
					prompt eval count:    13 token(s) <br>
					prompt eval duration: 3.811s <br>
					prompt eval rate:     3.41 tokens/s <br>
					eval count:           1003 token(s) <br>
					eval duration:        15m55.161s <br>
					eval rate:            1.05 tokens/s
				</samp>
			</td>
        </tr>
    </tbody>
	<tfoot>
		<tr>
		  <td colspan=4>
			* <a href="https://github.com/donatas-xyz/AI/discussions/1" target="_blank" rel="noopener noreferrer">Setup used</a> <br>
			* <a href="https://www.youtube.com/watch?v=kgSMRmW2frA&t=834s" target="_blank" rel="noopener noreferrer">Test questions source</a> <br>
			* All tests were performed on a fresh model load with no prior context and with the default settings.
		  </td>
		</tr>
	</tfoot>
</table>

<table style="width:100%">
	<caption><a href="https://ollama.com/library/deepseek-r1" target="_blank" rel="noopener noreferrer">DeepSeek-R1</a> performance and accuracy comparison (1.5B, 8B)</caption>
    <thead>
        <tr>
			<th style="width:10%"></th>
			<th style="width:30%">deepseek-r1:1.5b</th>
			<th style="width:30%">deepseek-r1:8b</th>
        </tr>
    </thead>
    <tbody>
        <tr>
			<td>Size</td>
            <td>1.1 GB</td>
			<td>4.9 GB</td>
        </tr>
		<tr>
			<td>Processing</td>
            <td>100% GPU</td>
			<td>100% GPU</td>
        </tr>
        <tr>
			<td>Prompt</td>
            <td colspan=2><kbd>List all the marriage dates and wives of Henry VIII</kbd></td>
        </tr>
        <tr>
			<td>Response</td>
            <td>
				<samp>
					Henry VIII, born on August 15, 1567, is a key figure in English history. He was the sixth King of England and seventh/第八 King of France. His notable marriages are as follows: <br><br>
					1. **First Marriage**: 1574 - Castile de Meurs <br>
					   - **Married to:** Castile de Meurs <br>
					   - **Wife:** Castile de Meurs <br>
					2. **Second Marriage**: 1579 - Castile de Mazarin <br>
					   - **Married to:** Castile de Mazarin <br>
					   - **Wife:** Castile de Mazarin <br>
					3. **Third Marriage**: 1576 - Castile de Flandre <br>
					   - **Married to:** Castile de Flandre <br>
					   - **Wife:** Castile de Flandre <br><br>
					Henry VIII's third marriage completed in 1576, during which he had children. After this marriage, he became King of France and later the Holy See. <br><br>
					**Final Answer:** <br><br>
					- Henry VIII was first married to Castile de Meurs on September 28, 1574. <br>
					- He then married again to Castile de Mazarin on April 6, 1579. <br>
					- His third marriage was completed with Castile de Flandre on October 4, 1576. <br><br>
					Each marriage had a distinct wife: both were Castile de Mazarin.
				</samp>
			</td>
			<td>
				<samp>
					Henry VIII, famous for his multiple marriages and contributions to the English Reformation, had six official marriages, each followed by an annulment except for his final union with Catherine Parr. Here is a structured overview of his marriages: <br><br>
					1. **Catherine of Aragon** <br>
					   - **Marriage Date**: 1509 <br>
					   - **Annulled**: 1534 (on grounds of her supposed affair with Henry Mannix, a Roma manuscript suggests). <br>
					2. **Anne Boleyn** <br>
					   - **Marriage Date**: 1536 <br>
					   - **Annulled**: 1537 (due to accusations of adultery and incest; later posthumously cleared by Thomas Cromwell). <br>
					3. **Jane Seymour** <br>
					   - **Marriage Date**: 1537 <br>
					   - **Deceased**: 1537 (died shortly after giving birth to Edward VI, their only son). <br>
					4. **Anna of Cleves** <br>
					   - **Marriage Date**: 1540 <br>
					   - **Annulled**: 1541 (due to Henry's dissatisfaction with her appearance and accusations of infertility). <br>
					5. **Mary Jane** <br>
					   - Also known as the "Ninth Wife" or "Dowager Queen." <br>
					   - **Marriage Date**: 1543 (though some sources suggest she was a morganatic wife, not officially crowned). <br>
					   - **Annulled**: 1544. <br>
					6. **Catherine Parr** <br>
					   - **Marriage Date**: 1547 <br>
					   - **No Annulment**: Henry died in 1547, so this marriage remained valid until his death. <br><br>
					This list highlights the complexity of Henry's marital history, marked by political motivations and changes in religious stance, particularly with the rise of Protestantism. Each marriage, except the last, was annulled to allow remarriage, reflecting the theological and political landscape of the time.
				</samp>
			</td>
        </tr>
        <tr>
			<td>Results</td>
            <td>
				<samp>
					total duration:       6.148134s <br>
					load duration:        16.8301ms <br>
					prompt eval count:    13 token(s) <br>
					prompt eval duration: 237ms <br>
					prompt eval rate:     54.85 tokens/s <br>
					eval count:           1242 token(s) <br>
					eval duration:        5.892s <br>
					eval rate:            210.79 tokens/s
				</samp>
			</td>
            <td>
				<samp>
					total duration:       17.190704s <br>
					load duration:        17.8187ms <br>
					prompt eval count:    13 token(s) <br>
					prompt eval duration: 462ms <br>
					prompt eval rate:     28.14 tokens/s <br>
					eval count:           1286 token(s) <br>
					eval duration:        16.709s <br>
					eval rate:            76.96 tokens/s
				</samp>
			</td>
        </tr>
    </tbody>
	<tfoot>
		<tr>
		  <td colspan=3>
			* <a href="https://github.com/donatas-xyz/AI/discussions/1" target="_blank" rel="noopener noreferrer">Setup used</a> <br>
			* <a href="https://www.youtube.com/watch?v=kgSMRmW2frA&t=834s" target="_blank" rel="noopener noreferrer">Test questions source</a> <br>
			* All tests were performed on a fresh model load with no prior context and with the default settings.
		  </td>
		</tr>
	</tfoot>
</table>

<table style="width:100%">
	<caption><a href="https://ollama.com/library/deepseek-r1" target="_blank" rel="noopener noreferrer">DeepSeek-R1</a> reasoning comparison</caption>
    <thead>
        <tr>
			<th style="width:15%">Model</th>
			<th style="width:85%">Reasoning</th>
        </tr>
    </thead>
    <tbody>
		<tr>
			<td>Prompt</td>
            <td><kbd>List all the marriage dates and wives of Henry VIII</kbd></td>
        </tr>
        <tr>
			<td>deepseek-r1:1.5b</td>
            <td>
				<samp>
					<think>
					Okay, so I need to list out all the marriage dates and wives of Henry VIII. Hmm, first things first, I should make
					sure I know who Henry VIII is. From what I remember, he was the sixth King of England and later the seventh and
					eighth in France. His position as king gave him significant power over France, including his marriage. <br><br>
					I think he married a woman from France named Castile, right? Wait, no, that's Castile de Meurs on one of his
					campaigns. But I'm trying to recall if he got married to someone else. Maybe it was another French woman? Or
					perhaps she was from England? <br><br>
					Wait, now that I think about it, Henry VIII is the son of Henry VII and Mary Aeglas. So he was born in 1567 or so,
					I believe, but his marriage happened earlier. His first wife was Castile de Meurs on a campaign against Henry V's
					forces. That sounds familiar from his time in England. <br><br>
					Then, he got married again to Castile de Mazarin in 1574. Okay, that makes sense because they were both French
					people. So their marriage date is 1574. But what was the wife of his second marriage? Was it Castile again? Or
					someone else? <br><br>
					Wait, maybe I'm confusing him with another figure. Let me think. There's Henry VIII as a French king, but in
					reality, he was also a British monarch after getting married to Castile de Mazarin on 1574. So his wife for that
					second marriage is Castile again? That seems repetitive, though. <br><br>
					But maybe I'm missing something. Perhaps he married someone else after that. Or maybe his second marriage was with
					someone from England. Wait, isn't there a Castile de Flandre or Castile de Rambaut who he married later? I think
					he did get married again to Castile de Flandre on 1618, which is when Henry VIII became King of France and later
					the Holy See. <br><br>
					So putting it together, Henry VIII's first marriage was with Castile de Meurs in 1574. His second marriage was
					with Castile de Mazarin in 1579? Or wait, no, I think the second marriage was completed by 1576 when he married
					Castile de Flandre in that year. <br><br>
					Wait, actually, I might be mixing up some dates here. Let me try to recall or reconstruct this properly. Henry
					VIII was born in August 1567, but his first marriage was in September 1574 with Castile de Mazarin. His second
					marriage was completed in 1576 by married to Castile de Flandre, and he had children after that. <br><br>
					So the list should include: <br><br>
					- Marriage 1: 1574, Castile de Mazarin <br>
					- Marriage 2: 1576, Castile de Flandre <br><br>
					Wait, but I'm not sure about the second marriage's exact date. Maybe it was completed in 1576, and he had children
					then. <br><br>
					I should also consider if he got married to anyone else before that. From what I remember, his first wife was
					Castile de Meurs on a campaign, so maybe the second is with another French noblewoman, which could be Castile de
					Mazarin. <br><br>
					But perhaps after his marriage to Castile de Flandre in 1576, he married again later? Or was that his only
					marriages? <br><br>
					Wait, I think he got married twice. First with Castile de Meurs, then again with Castile de Mazarin in 1574, and
					then with Castile de Flandre in 1576. So the dates would be: <br><br>
					1. Castile de Meurs, 1574 <br>
					2. Castile de Mazarin, 1574 <br>
					3. Castile de Flandre, 1576 <br><br> 
					And the wives of his first two marriages are both Castile de Mazarin and Castile de Meurs respectively. <br><br>
					I should also note that after his marriage to Castile de Flandre in 1576, he became King of France. But since he
					was already a French king by then, perhaps those later marriages were within France. <br><br>
					So putting it all together, the list would include his first two marriages and their wives as well as his third
					marriage and wife.
					</think>
				</samp>
			</td>
        </tr>
		        <tr>
			<td>deepseek-r1:8b</td>
            <td>
				<samp>
					<think>
					Alright, so I need to figure out the marriage dates and the names of Henry VIII's wives. I remember that Henry was
					a famous English king, known for having several marriages and a lot of children. But I'm not exactly sure about
					the details. Let me try to piece this together step by step. <br><br> 
					First, I think Henry VIII was married six times, but I'm not entirely certain. Maybe he had more? I should
					double-check that. From what I recall, his marriages started with Katherine of Aragon and ended with Catherine
					Parr. The other wives in between were Anne Boleyn, Jane Seymour, Anna of Cleves, and maybe a few others. I might
					be mixing up the order or missing someone. <br><br> 
					I also remember that some of these marriages were annulled by the Church, which allowed Henry to marry again.
					Annulment must have been a significant factor because the Catholic Church didn't approve of divorce back then. So
					each time his marriage was annulled, he could take another wife, except for his last marriage, which was to
					Catherine Parr, and that was during his later years. <br><br> 
					Now, trying to remember the order: after Katherine of Aragon came Anne Boleyn, right? Then Jane Seymour, who might
					have died or had issues with the marriage. After that, I think Henry married Anna of Cleves, but there was some
					problem with her not being as beautiful as he expected. Then maybe Mary Jane (called the "Ninth Wife") and then
					Catherine Parr. <br><br> 
					Wait, so that's five marriages after the annulments. But originally, Henry had six wives because each annulment
					allowed him to remarry once, except for his last marriage which was legitimate without an annulment. So perhaps
					the count is six in total. <br><br> 
					As for the dates, I think the first marriage was around 1509 or 1510. That would be with Katherine of Aragon. Then
					Anne Boleyn followed in 1536. Jane Seymour was next, but I'm not sure exactly when that was—maybe 1537? Then Anna
					of Cleves in 1540. After that, perhaps the "Ninth Wife" around 1543 or so, and finally Catherine Parr in 1547 or
					later. <br><br> 
					I should also consider the possibility of other wives, like Mary Howard or others, but I think they might have
					been mistresses rather than official wives. The main ones are the six women he married legally. I'm a bit fuzzy on
					the exact dates, though. <br><br> 
					Another thing to note is that some marriages were short-lived because of health issues or political reasons. For
					example, Jane Seymour died shortly after giving birth to Edward VI. Also, Henry was known for his portly figure
					later in life, which might have contributed to health problems and early death at age 47. <br><br> 
					So, summarizing what I think: Henry VIII had six marriages, starting with Katherine of Aragon (1509), then Anne
					Boleyn (1536), Jane Seymour (1537), Anna of Cleves (1540), a possible other wife (maybe in 1543), and finally
					Catherine Parr (1547 or 1548). But I'm not entirely confident about the exact dates, especially for the later
					marriages. <br><br> 
					I should also check if there was an official annulment for each previous marriage except the last one. He
					definitely had several annulments because the Church only allowed one marriage at a time, and Henry wanted to keep
					remarrying after each annulment. <br><br> 
					In terms of the names, I think they are: <br><br> 
					1. Catherine of Aragon <br>
					2. Anne Boleyn <br>
					3. Jane Seymour <br>
					4. Anna of Cleves <br>
					5. Mary Jane (Dowager Queen) <br>
					6. Catherine Parr <br><br> 
					Wait, was there a fifth wife? I'm a bit confused because sometimes sources mention her as the "Ninth Wife" or the
					"unofficial" wife. Maybe she wasn't technically an official queen but was referred to as such by some chroniclers. <br><br> 
					Another point is that Henry's marriages were often for political reasons rather than love, especially in his later
					years. He wanted a son and heir, which drove much of his marital decisions. <br><br> 
					So, putting it all together, I think the list includes six wives with their respective marriage dates, considering
					the annulments except for Catherine Parr's marriage. But without exact sources, some details might be off.
					</think>
				</samp>
			</td>
        </tr>
    </tbody>
	<tfoot>
		<tr>
		  <td colspan=3>
			* <a href="https://github.com/donatas-xyz/AI/discussions/1" target="_blank" rel="noopener noreferrer">Setup used</a> <br>
			* <a href="https://www.youtube.com/watch?v=kgSMRmW2frA&t=834s" target="_blank" rel="noopener noreferrer">Test questions source</a> <br>
			* All tests were performed on a fresh model load with no prior context and with the default settings.
		  </td>
		</tr>
	</tfoot>
</table>
