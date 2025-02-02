+++
disableToc = false
title = "What's New"
weight = 1
+++

## 🔥🔥🔥 06-06-2023: __v1.18.0__ 🚀

This LocalAI release is plenty of new features, bugfixes and updates! Thanks to the community for the help, this was a great community release!

We now support a vast variety of models, while being backward compatible with prior quantization formats, this new release allows still to load older formats and new [k-quants](https://github.com/ggerganov/llama.cpp/pull/1684)!

### New features

- ✨ Added support for `falcon`-based model families (7b)  ( [mudler](https://github.com/mudler) )
- ✨ Experimental support for Metal Apple Silicon GPU - ( [mudler](https://github.com/mudler) and thanks to @Soleblaze for testing! ). See the [build section]({{%relref "basics/build#Acceleration" %}}).
- ✨ Support for token stream in the `/v1/completions` endpoint ( [samm81](https://github.com/samm81) )
- ✨ Added huggingface backend ( [Evilfreelancer](https://github.com/EvilFreelancer) )
- 📷 Stablediffusion now can output `2048x2048` images size with `esrgan`! ( [mudler](https://github.com/mudler) )

### Container images
- 🐋 CUDA container images (arm64, x86_64) ( [sebastien-prudhomme](https://github.com/sebastien-prudhomme) )
- 🐋 FFmpeg container images (arm64, x86_64) ( [mudler](https://github.com/mudler) )

### Dependencies updates

- 🆙 Bloomz has been updated to the latest ggml changes, including new quantization format ( [mudler](https://github.com/mudler) )
- 🆙 RWKV has been updated to the new quantization format( [mudler](https://github.com/mudler) )
- 🆙 [k-quants](https://github.com/ggerganov/llama.cpp/pull/1684) format support for the `llama` models ( [mudler](https://github.com/mudler) )
- 🆙 gpt4all has been updated, incorporating upstream changes allowing to load older models, and with different CPU instruction set (AVX only, AVX2) from the same binary! ( [mudler](https://github.com/mudler) )

### Generic

- 🐧 Fully Linux static binary releases ( [mudler](https://github.com/mudler) )
- 📷 Stablediffusion has been enabled on container images by default ( [mudler](https://github.com/mudler) )
  Note: You can disable container image rebuilds with `REBUILD=false`

### Examples

- 💡 [AutoGPT](https://github.com/go-skynet/LocalAI/tree/master/examples/autoGPT) example ( [mudler](https://github.com/mudler) )
- 💡 [PrivateGPT](https://github.com/go-skynet/LocalAI/tree/master/examples/privateGPT) example ( [mudler](https://github.com/mudler) )
- 💡 [Flowise](https://github.com/go-skynet/LocalAI/tree/master/examples/flowise) example ( [mudler](https://github.com/mudler) )

Two new projects offer now direct integration with LocalAI!

- [Flowise](https://github.com/FlowiseAI/Flowise/pull/123)
- [Mods](https://github.com/charmbracelet/mods)

[Full release changelog](https://github.com/go-skynet/LocalAI/releases/tag/v1.18.0)

## 29-05-2023: __v1.17.0__

Support for OpenCL has been added while building from sources.

You can now build LocalAI from source with `BUILD_TYPE=clblas` to have an OpenCL build. See also the [build section]({{%relref "basics/build#Acceleration" %}}).

For instructions on how to install OpenCL/CLBlast see [here](https://github.com/ggerganov/llama.cpp#blas-build).

rwkv.cpp has been updated to the new ggml format [commit](https://github.com/saharNooby/rwkv.cpp/commit/dea929f8cad90b7cf2f820c5a3d6653cfdd58c4e).

## 27-05-2023: __v1.16.0__ 

Now it's possible to automatically download pre-configured models before starting the API. 

Start local-ai with the `PRELOAD_MODELS` containing a list of models from the gallery, for instance to install `gpt4all-j` as `gpt-3.5-turbo`:

```bash
PRELOAD_MODELS=[{"url": "github:go-skynet/model-gallery/gpt4all-j.yaml", "name": "gpt-3.5-turbo"}]
```

`llama.cpp` models now can also automatically save the prompt cache state as well by specifying in the model YAML configuration file:

```yaml
# Enable prompt caching

# This is a file that will be used to save/load the cache. relative to the models directory.
prompt_cache_path: "alpaca-cache"

# Always enable prompt cache
prompt_cache_all: true
```

See also the [advanced section]({{%relref "advanced" %}}).

## Media, Blogs, Social

- [LocalAI meets k8sgpt](https://www.youtube.com/watch?v=PKrDNuJ_dfE) - CNCF Webinar showcasing LocalAI and k8sgpt.
- [Question Answering on Documents locally with LangChain, LocalAI, Chroma, and GPT4All](https://mudler.pm/posts/localai-question-answering/) by Ettore Di Giacinto
- [Tutorial to use k8sgpt with LocalAI](https://medium.com/@tyler_97636/k8sgpt-localai-unlock-kubernetes-superpowers-for-free-584790de9b65) - excellent usecase for localAI, using AI to analyse Kubernetes clusters. by Tyller Gillson

## Previous 

- 23-05-2023: __v1.15.0__ released. `go-gpt2.cpp` backend got renamed to `go-ggml-transformers.cpp` updated including https://github.com/ggerganov/llama.cpp/pull/1508 which breaks compatibility with older models. This impacts RedPajama, GptNeoX, MPT(not `gpt4all-mpt`), Dolly, GPT2 and Starcoder based models. [Binary releases available](https://github.com/go-skynet/LocalAI/releases), various fixes, including https://github.com/go-skynet/LocalAI/pull/341 .
- 21-05-2023: __v1.14.0__ released. Minor updates to the `/models/apply` endpoint, `llama.cpp` backend updated including https://github.com/ggerganov/llama.cpp/pull/1508 which breaks compatibility with older models. `gpt4all` is still compatible with the old format. 
- 19-05-2023: __v1.13.0__ released! 🔥🔥 updates to the `gpt4all` and `llama` backend, consolidated CUDA support ( https://github.com/go-skynet/LocalAI/pull/310 thanks to @bubthegreat and @Thireus ), preliminar support for [installing models via API]({{%relref "advanced#" %}}).
- 17-05-2023:  __v1.12.0__ released! 🔥🔥 Minor fixes, plus CUDA (https://github.com/go-skynet/LocalAI/pull/258) support for `llama.cpp`-compatible models and image generation (https://github.com/go-skynet/LocalAI/pull/272).
- 16-05-2023: 🔥🔥🔥 Experimental support for CUDA (https://github.com/go-skynet/LocalAI/pull/258) in the `llama.cpp` backend and Stable diffusion CPU image generation (https://github.com/go-skynet/LocalAI/pull/272) in `master`.

Now LocalAI can generate images too:

| mode=0                                                                                                                | mode=1 (winograd/sgemm)                                                                                                                |
|------------------------------------------------------------------------------------------------------------------------|------------------------------------------------------------------------------------------------------------------------|
| ![b6441997879](https://github.com/go-skynet/LocalAI/assets/2420543/d50af51c-51b7-4f39-b6c2-bf04c403894c)              | ![winograd2](https://github.com/go-skynet/LocalAI/assets/2420543/1935a69a-ecce-4afc-a099-1ac28cb649b3)                |

- 14-05-2023: __v1.11.1__ released! `rwkv` backend patch release
- 13-05-2023: __v1.11.0__ released! 🔥 Updated `llama.cpp` bindings: This update includes a breaking change in the model files ( https://github.com/ggerganov/llama.cpp/pull/1405 ) - old models should still work with the `gpt4all-llama` backend.
- 12-05-2023: __v1.10.0__ released! 🔥🔥 Updated `gpt4all` bindings. Added support for GPTNeox (experimental), RedPajama (experimental), Starcoder (experimental), Replit (experimental), MosaicML MPT. Also now `embeddings` endpoint supports tokens arrays. See the [langchain-chroma](https://github.com/go-skynet/LocalAI/tree/master/examples/langchain-chroma) example! Note - this update does NOT include https://github.com/ggerganov/llama.cpp/pull/1405 which makes models incompatible.
- 11-05-2023: __v1.9.0__ released! 🔥 Important whisper updates ( https://github.com/go-skynet/LocalAI/pull/233 https://github.com/go-skynet/LocalAI/pull/229 ) and extended gpt4all model families support ( https://github.com/go-skynet/LocalAI/pull/232 ). Redpajama/dolly experimental ( https://github.com/go-skynet/LocalAI/pull/214 )
- 10-05-2023: __v1.8.0__ released! 🔥 Added support for fast and accurate embeddings with `bert.cpp` ( https://github.com/go-skynet/LocalAI/pull/222 )
- 09-05-2023: Added experimental support for transcriptions endpoint ( https://github.com/go-skynet/LocalAI/pull/211 )
- 08-05-2023: Support for embeddings with models using the `llama.cpp` backend ( https://github.com/go-skynet/LocalAI/pull/207 )
- 02-05-2023: Support for `rwkv.cpp` models ( https://github.com/go-skynet/LocalAI/pull/158 ) and for `/edits` endpoint
- 01-05-2023: Support for SSE stream of tokens in `llama.cpp` backends ( https://github.com/go-skynet/LocalAI/pull/152 )
