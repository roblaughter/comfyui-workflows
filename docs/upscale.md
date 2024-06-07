# Using the Upscale Workflow

This workflow performs a *generative* upscale on an input image. Rather than simply interpolating pixels with a standard model upscale (ESRGAN, UniDAT, etc.), the upscaler uses an upscale model to upres the image, then performs a tiled img2img to regenerate the image and add details. 

I've optimized this workflow for photorealistic styles, but it performs well for anime and illustrations as well. 

## Parameter Overview
* **Denoise.** Controls the amount of denoising applied to the img2img encoded image. Lower values are more similar to the original image, while higher values give the upscaler more room for adding detail. *Recommended: 0.3-0.5.*
* **ControlNet Strength.** Controls the influence of the Tile ControlNet. The ControlNet is responsible for maintaining the fidelity of the tiled upscale. Setting this too low will lose coherency in the image. Setting this too high will over-emphasize details. Set this as low as possible while maintaining coherence. *Recommended: 0.5-1.0.*
* **Tile Size.** Controls the size of tiles used in the upscale process. Smaller tile size will use less VRAM with a slight loss of quality. Higher tile size will use more VRAM, but can improve quality. *Recommended: 1024.*

## Comparisons

Below is a comparison of various parameters. View at full resolution to examine more subtle differences. 

### Denoise
![Denoise](https://github.com/roblaughter/comfyui-workflows/blob/main/docs/comparison-denoise-small.png?raw=true) 
[View full](https://github.com/roblaughter/comfyui-workflows/blob/main/docs/comparison-denoise-full.png?raw=true)

### ControlNet Strength
![Denoise](https://github.com/roblaughter/comfyui-workflows/blob/main/docs/comparison-controlnet-small.png?raw=true)
[View full](https://github.com/roblaughter/comfyui-workflows/blob/main/docs/comparison-controlnet-full.png?raw=true)

### Denoise
![Denoise](https://github.com/roblaughter/comfyui-workflows/blob/main/docs/comparison-tile-size-small.png?raw=true)
[View full](https://github.com/roblaughter/comfyui-workflows/blob/main/docs/comparison-tile-size-full.png?raw=true)


## Common Issues
### The upscaled image has artifacts
Setting the ControlNet strength too high will produce unwanted artifacts. The model will give too much attention to imperfections and small details. 

The subject of your image matters. Human portraits can tolerate higher ControlNet strength. Images with a lot of detail, such as fur or foliage, may need a slightly lower strength. If the upscaled image has artifacts, try dropping the ControlNet strength. 

### The upscaled image looks different than my input
If the appearance of your image changes too much, you've likely set the ControlNet strength too high, or you've set the denoising strength too high. 

**Low ControlNet strength** values will result in deformations, misalignment, or loss of visual fidelity. 

**High denoise** values may cause the model to hallucinate and add unintended details. 

### The upscaled image lacks detail
If your image lacks detail, your denoise strength may be too low. In this case, the model doesn't have enough creative control to generate the details of the upscaled image. 

![Setting Comparison: Lion](https://github.com/roblaughter/comfyui-workflows/blob/main/docs/setting-comparison-lion.png?raw=true)
*In the center image, the ControlNet strength is too high, causing artifacts. In the third image, it is too low, losing detail.*

![Setting Comparison: Portrait](https://github.com/roblaughter/comfyui-workflows/blob/main/docs/setting-comparison-portrait.png?raw=true)
*In the center image, the ControlNet strength is too high, causing artifacts. The third image uses the same settings as the third image above, but the ControlNet strength is appropriate for the realistic portrait.*

