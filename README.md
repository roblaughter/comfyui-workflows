# ComfyUI Workflows

This repo contains common workflows for generating AI images with [ComfyUI](https://github.com/comfyanonymous/ComfyUI). To get started with AI image generation, check out my [guide on Medium](https://roblaughter.medium.com/a-crash-course-on-local-image-generation-with-stable-diffusion-f72dfd3de3df). 

## Files

* **[SDXL Pipeline](https://github.com/roblaughter/comfyui-workflows/blob/main/SDXLPipeline.json).** A basic SDXL image generation pipeline with two stages (first pass and upscale/refiner pass) and optional optimizations. Use with any SDXL model, such as my [RobMix Ultimate checkpoint](https://civitai.com/models/334323/robs-mix-ultimate). 
* **[Clarity Upscaler](https://github.com/roblaughter/comfyui-workflows/blob/main/ClarityUpscaleSD15.json).** A ComfyUI implementation of the [Clarity Upscaler](https://github.com/philz1337x/clarity-upscaler), a "free and open source Magnific alternative." Out of the box, upscales images 2x with some optimizations for added detail. See the documentation [here](https://github.com/roblaughter/comfyui-workflows/blob/main/docs/upscale.md).
* **[IC-Light Basic.](https://github.com/roblaughter/comfyui-workflows/blob/main/ICLightBasic.json)** An implementation of [IC-Light](https://github.com/lllyasviel/IC-Light?tab=readme-ov-file) relighting model using the [ComfyUI native implementation](https://github.com/kijai/ComfyUI-IC-Light). This version replaces the background based on text prompt and relights the image to match. 
* **[IC-Light Background.](https://github.com/roblaughter/comfyui-workflows/blob/main/ICLightBackground.json)** Same as above, but accepts a background image, adds the foreground to the background, and relights the image to match. 
* **[CosXL Sample Workflow](https://github.com/roblaughter/comfyui-workflows/blob/main/cosxl_sample_workflow.json).** A sample workflow for running CosXL models, such as my [RobMix CosXL](https://civitai.com/models/397300/robmix-cosxl) checkpoint. CosXL models have better dynamic range and finer control than SDXL models. 
* **[CosXL Edit Sample Workflow](https://github.com/roblaughter/comfyui-workflows/blob/main/cosxl_edit_example_workflow.json).** A sample workflow for running CosXL Edit models, such as my [RobMix CosXL Edit checkpoint](https://civitai.com/models/397741/robmix-cosxl-edit). A CosXL Edit model takes a source image as input alongside a prompt, and interprets the prompt as an instruction for how to alter the image, similar to InstructPix2Pix.

## Helpful Addons
### Checkpoints
* **[RobMix Ultimate](https://civitai.com/models/334323/robs-mix-ultimate)** (SDXL)
* **[RobMix CosXL](https://civitai.com/models/397300/robmix-cosxl)**
* **[RobMix CosXL Edit](https://civitai.com/models/397741/robmix-cosxl-edit?modelVersionId=443550)**
* **[Juggernaut Reborn](https://civitai.com/models/46422/juggernaut)** (SD1.5, for Clarity Upscale)

### LoRAs
The LoRAs below are used in the Clarity Upscaler workflow for adding detail. 
* **[Add More Details](https://civitai.com/models/82098?modelVersionId=87153)** (SD1.5)
* **[SDXL Render](https://civitai.com/models/171159?modelVersionId=236130)** (SD1.5). Emulates contrast and detail of SDXL models when using SD1.5 models. 

### Upscale Models
* **[NomosUniDAT_otf.pth](https://openmodeldb.info/models/4x-NomosUniDAT-otf).** A 4x upscaler used in my Clarity Upscale workflow. Any upscale model can be used in its place. 

### IC-Light Models

* **[Download from HuggingFace.](https://huggingface.co/lllyasviel/ic-light/tree/main)** For the IC-Light workflow. 
* Use *fb* version for basic workflow that generates a background from the prompt. 
* Use *fbc* version for blending an image with an existing background. 

### Custom Nodes
Some workflows (such as the Clarity Upscale workflow) include custom nodes that aren't included in base ComfyUI. Install these with *Install Missing Custom Nodes* in ComfyUI Manager.

* **[ComfyUI Inspire Pack](https://github.com/ltdrdata/ComfyUI-Inspire-Pack).** Includes the Ksampler Inspire node that includes the Align Your Steps scheduler for improved image quality. Standard KSampler with your preferred scheduler can be used in its place. 
* **[ComfyUI NN Latent Upscale](https://github.com/Ttl/ComfyUi_NNLatentUpscale).** A neural network latent upscale for much higher quality compared with an interpolated latent upscale. Standard latent upscaler can be used in its place with poorer results. 
* **[Perturbed Attention Guidance](https://github.com/pamparamm/sd-perturbed-attention).** An advanced implementation of the Perturbed Attention Guidance (PAG) node in ComfyUI. PAG is an alternative to CFG for creating higher quality images with better prompt adherence. Lower CFG proportionally, or use PAG's scaling. The standard PAG node can be used in its place. 
* **[ComfyUI Post Processing Nodes](https://github.com/EllangoK/ComfyUI-post-processing-nodes).** Optional nodes for basic post processing, such as adjusting tone, contrast, and color balance, adding grain, vignette, etc. Helpful for taking the AI "edge" off of images as part of your workflow by reducing contrast, balancing brightness, and adding some subtle grain for texture. 
* **[ComfyUI-CADS](https://github.com/asagi4/ComfyUI-CADS).** Injects noise early in the generation process to create more varied compositions. Totally optional. 
