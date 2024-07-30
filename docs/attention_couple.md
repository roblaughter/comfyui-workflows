# Using the Attention Couple Workflow

[Download the workflow here &raquo;](https://github.com/roblaughter/comfyui-workflows/blob/main/AttentionCouple.json)

This workflow gives you control over the composition of the generated image by applying sub-prompts to specific areas of the image with masking. 

## Basic Instructions
To generate an image, follow the instructions below. 

1. Set a base prompt for the entire image. This should be a generic description of the scene. You can also describe any figures generically (e.g. "two people" or "three figures").
2. Load a black image with the same dimensions of your image into the Load Image nodes to use as the starting mask. 
3. Right click the Load Image node. Choose "Open in Mask Editor."
4. Paint the area where you want the feature/subject to appear  white. 
5. Enter a prompt for each masked area. 
6. Generate!

## Usage Tips

* When using Attention mode, masks will generally guide the placement of objects in the image, but the attention mechanisms may still blend concepts. 
* If the model doesn't seem to be picking up on the masked features, try lowering the strength of the base prompt (around 0.75). 
* If one feature/subject is more prominent than the others, LOWER the strength of that feature's conditioning (around 0.5 to 0.75) and/or RAISE the strength of other features (around 1.5).
* To disable a masked region, set strength to 0. 
* If you get an error about tensor size mismatch, ensure that your empty masks are the same size as your image resolution. 

## Starter Masks
Starter masks are simple black PNGs in common SDXL resolutions. 

Download example starting masks for common SDXL resolutions here.

[Download Starter Masks &raquo;](https://github.com/roblaughter/comfyui-workflows/docs/masks.zip)
