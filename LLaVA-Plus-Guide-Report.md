To run LLaVA-Plus on your own device, follow readme.md on LLaVA-Plus-codebase, but you might encounter some error, here is how to fix them.

1.There might be some caused by wrong working directory

most times, we run controller or workers in directory `LLaVA-Plus/`, except these:

run `LLaVA-Plus/Grounded-Segment-Anything/GroundingDINO/grounding_dino_worker.py` 
and `LLaVA-Plus/Grounded-Segment-Anything/segment_anything/sam_worker.py`
under path `LLaVA-Plus/Grounded-Segment-Anything/`

run `LLaVA-Plus/Segment-Everything-Everywhere-All-At-Once/seem_worker.py`
under path `LLaVA-Plus/Segment-Everything-Everywhere-All-At-Once/`

2.Download `groundingdino_swint_ogc.pth` yourself

3.run tool workers with instruction like
`python /home/zeyu/workspace/LLaVA-Plus/recognize-anything/ram_worker.py  --controller-address http://localhost:20001 --model-path  /mnt/data0/zeyu/tag2text_swin_14m.pth`
to point out controller-address and model-path(if any)

4.copy `LLaVA-Plus/Grounded-Segment-Anything/GroundingDINO/demo` to `LLaVA-Plus/Grounded-Segment-Anything/segment_anything`

5.Download `sam_vit_h_4b8939.pth` yourself and put it under path `LLaVA-Plus/Grounded-Segment-Anything/`

6.The path of ram codebase is wrong, use 
`git clone https://github.com/xinyu1205/recognize-anything.git`

7.Use `git clone https://github.com/fenneishi/Tag2Text.git` to download Tag2Text.git yourself

8.In `ram_worker.py`  
the line
`from Tag2Text import inference_ram
change `inference_ram` into `inference`

9.In `LLaVA-Plus/recognize-anything/ram_worker.py`

change `from Tag2Text.models import tag2text' into 'from Tag2Text.models.tag2text import tag2text_caption`

in sentence `self.ram_model = tag2text.ram(pretrained=model_path,
                                        image_size=384,
                                        vit='swin_l')`

change `tag2text.ram` into `tag2text_caption`  

change `swin_l` into `swin_b`


