To run LLaVA-Plus on your own device, follow readme.md on LLaVA-Plus-codebase, but you might encounter some error, here is how to fix them.

1.There might be some error caused by wrong working directory

most times, we run controller or workers in directory `LLaVA-Plus/`, except these:

install Grounding DINO and SAM, 
run `LLaVA-Plus/Grounded-Segment-Anything/GroundingDINO/grounding_dino_worker.py` 
and `LLaVA-Plus/Grounded-Segment-Anything/segment_anything/sam_worker.py`
under path `LLaVA-Plus/Grounded-Segment-Anything/`

run `LLaVA-Plus/Segment-Everything-Everywhere-All-At-Once/seem_worker.py`
under path `LLaVA-Plus/Segment-Everything-Everywhere-All-At-Once/`

2.Download `groundingdino_swint_ogc.pth` from https://huggingface.co/ShilongLiu/GroundingDINO/blob/main/groundingdino_swint_ogc.pth 

download `sam_vit_h_4b8939.pth` from https://huggingface.co/spaces/abhishek/StableSAM/blob/main/sam_vit_h_4b8939.pth

and put them under LLaVA-Plus/Grounded-Segment-Anything/

3.run tool workers with instruction like
`python /home/zeyu/workspace/LLaVA-Plus/recognize-anything/ram_worker.py  --controller-address http://localhost:20001 --model-path  /mnt/data0/zeyu/tag2text_swin_14m.pth`
to point out controller-address and model-path(if any)

4.copy `LLaVA-Plus/Grounded-Segment-Anything/GroundingDINO/demo` to `LLaVA-Plus/Grounded-Segment-Anything/segment_anything`

5.The path of ram codebase is wrong, use 
`git clone https://github.com/xinyu1205/recognize-anything.git`

6.Use `git clone https://github.com/fenneishi/Tag2Text.git` to download Tag2Text.git yourself

7.In `LLaVA-Plus/recognize-anything/ram_worker.py`  
in the line
`from Tag2Text import inference_ram`
change `inference_ram` into `inference`

change `from Tag2Text.models import tag2text` into `from Tag2Text.models.tag2text import tag2text_caption`

in sentence `self.ram_model = tag2text.ram(pretrained=model_path,
                                        image_size=384,
                                        vit='swin_l')`

change `tag2text.ram` into `tag2text_caption`  

change `swin_l` into `swin_b`

8.pip install transformers

9.Download `tag2text_swin_14m.pth` from https://huggingface.co/spaces/xinyu1205/recognize-anything/blob/main/tag2text_swin_14m.pth

10.In `LLaVA-Plus/EasyOCR/ocr_worker.py`
in the line `from Tag2Text import inference_ram` change `inference_ram` into `inference`

11.After opening the web, choose the worker `llava_plus_v0_7b` first, then start your chat

12.If you encounter `NETWORK ERROR DUE TO HIGH TRAFFIC. PLEASE REGENERATE OR REFRESH THIS PAGE. (error_code: 1)` on UI, restart model worker and gradio web server

13.If the answer is not stable, change `--model-list-mode` into `once`

