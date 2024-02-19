To run LLaVA-Plus on your own device, follow readme.md on LLaVA-Plus-codebase, but you might encounter some error, here is how to fix them.

1.There might be some caused by wrong working directory

most times, we run controller or workers in directory LLaVA-Plus/, except these:

run LLaVA-Plus/Grounded-Segment-Anything/GroundingDINO/grounding_dino_worker.py 
and LLaVA-Plus/Grounded-Segment-Anything/segment_anything/sam_worker.py
under path LLaVA-Plus/Grounded-Segment-Anything/

run LLaVA-Plus/Segment-Everything-Everywhere-All-At-Once/seem_worker.py
under path LLaVA-Plus/Segment-Everything-Everywhere-All-At-Once/

