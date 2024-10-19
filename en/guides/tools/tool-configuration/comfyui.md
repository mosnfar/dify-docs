# ComfyUI
[ComfyUI](https://www.comfy.org/): The most powerful and modular diffusion model GUI, api and backend with a graph/nodes interface. Now you can use it in dify, input the prompt of the image, and get the generated image.

## 1. Ensure that the ComfyUI workflow is running normally.  
Please refer to its [official documentation](https://docs.comfy.org/get_started/gettingstarted) to ensure that ComfyUI can run normally and generate images.

## 2. Export the API file of the workflow. 
<figure><img src="/en/.gitbook/assets/guides/tools/comfyui.png" alt=""><figcaption></figcaption></figure>
As shown in the figure, select `Save(API Format)`, if there is no such selection, you need to enable `Dev Mode` in the settings.

## 3. Integrate ComfyUI in Dify  
Fill in the access address in `Tools > ComfyUI > Go to Authentication`, if you are using a docker deployment of Dify, this address is usually `http://host.docker.internal:8188`.

## 4. Use ComfyUI in Dify
Open its `Workflow` tool, fill in the content in the API file you just exported in `WORKFLOW JSON`, and you can generate normally.
