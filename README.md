

Simple [bloom.cpp](https://github.com/NouamaneTazi/bloomz.cpp) instance compiling with scons buildsystem. Builds a real-time translator using ggml, tested on Ubuntu 22.04 and ggml-model-bloomz-3b-f16-q4_0.bin.

```
(get pretrained, e.g.: 
https://huggingface.co/models?other=bloom&other=ggml)
$ scons
(should produce:)
$ /usr/bin/g++ -o build/main.o -c -std=c++11 -I/home/xyz/Desktop/scons-ggml-bloom/libs/ggml -I/home/xyz/Desktop/scons-ggml-bloom/build -g -Wall -Wformat src/main.cpp
(should test executable:)
$ ./dist/scons-ggml-bloom -m ./models/ggml-model-bloomz-3b-f16-q4_0.bin -p 'Translate "Give me a piece of bread and potatoes" to Portuguese:' -t 8 -n 256
(output)
main: seed = 1700324887
bloom_model_load: loading model from './models/
...
Sampling parameters: temp = 0.800000, top_k = 40, top_p = 0.950000, repeat_last_n = 64, repeat_penalty = 1.300000
Translate "Give me a piece of bread and potatoes" to Portuguese: Chegue-me pão e batatas.</s> [end of text]
```

```
(inherits)
options:
  -h, --help            show this help message and exit
  -s SEED, --seed SEED  RNG seed (default: -1)
  -t N, --threads N     number of threads to use during computation (default: 4)
  -p PROMPT, --prompt PROMPT
                        prompt to start generation with (default: random)
  -n N, --n_predict N   number of tokens to predict (default: 128)
  --top_k N             top-k sampling (default: 40)
  --top_p N             top-p sampling (default: 0.9)
  --repeat_last_n N     last n tokens to consider for penalize (default: 64)
  --repeat_penalty N    penalize repeat sequence of tokens (default: 1.3)
  --temp N              temperature (default: 0.8)
  -b N, --batch_size N  batch size for prompt processing (default: 8)
  -m FNAME, --model FNAME
                        model path (default: models/ggml-model-bloomz-7b1-f16-q4_0.bin)

```

References:

https://github.com/NouamaneTazi/bloomz.cpp  
https://github.com/ggerganov/ggml  
https://scons.org/  
 