**System specs:**  
Qwen3:32B-F16, Windows 11, 2x48GB 6400 DDR5, R7 7700X 8/16, RTX 5070 Ti 16GB + RTX 4070 12GB.

**Results:**  
The best compromise I could achieve is `num_ctx=12288` and `num_gpu=22`. That gets me close to 28GB VRAM while still keeping 12K context window.

|SIZE|PROCESSOR (CPU/GPU)|CONTEXT|NUM\_GPU|VRAM (REPORTED)|VRAM (REAL)|T/S|
|:-|:-|:-|:-|:-|:-|:-|
|85GB|83%/17%|32768|10|14.45GB|13.1GB|0.79|
|84GB|71%/29%|18432|17|21.46GB|19.6GB|0.83|
|82GB|70%/30%|16384|18|24.59GB|20.5GB|0.87|
|80GB|68%/32%|14336|19|25.6GB|21.2GB|0.89|
|78GB|68%/32%|12288|22|24.96GB|23.3GB|0.97|
|70GB|64%/36%|4096|23|25.2GB|24.1GB|0.98|
