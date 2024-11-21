# Sparse Generation: Making Pseudo Labels Sparse for point weakly supervised object detection on low data volume

![image](https://github.com/Trumpetertimes/Sparse_Generation/blob/master/SP_pipeline0912.png)
Sparse Generation uses non-networked approach and direct regression on pseudo labels. In three processing stages (Mapping, Mask, Regression), Sparse Generation constructs initial tensors through the relationship between data and detector model, optimizes its parameters, and obtains a sparse tensor, addresses the model’s density problem on low data volume. 


## Environment: 
    python >=3.7.
    pytorch >=1.9.0.
    our cuda version is 11.6.
    
## Dataset:
    Due to the need to obtain instances as dense as possible, we conducted Bullet-Hole data set collection in a real shooting range.In these photos with the highest number of bullet holes contain over 502 bullet holes in a single picture. Link for downloading the pictures and annotations: (https://pan.baidu.com/s/1Qg-3FOer2x0TS55I9ZzEVQ?pwd=abcd)

## How to run:
Only need to use a small set of supervised annotation data to Train a pre-model, use this pre-trained model to predict the pseudo labels on entire dataset.
We validated on four different datasets(MS COCO-5000, RSOD, SIMD, Bullet-Hole).

![image](https://github.com/Trumpetertimes/Sparse_Generation/blob/master/SPexperiment0912.png)

If your detector model output the COCO json or VOC format annotation, transforming them to yolo txt format. 

   The initial parameters were already set. run command:
    
     python Code_for_Sparse_Generation.py --inferenced_labels_URL --Sparse_Generation_save_URL --val_labels_URL --inferenced_val_labels_URL --Sparse_generation_val_labels_save_URL --point_labels_URL --epochs --Final_save_URL  
 

1. "point_labels_URL" is the folder path to put the Point-annotation data.

2. "inferenced_labels_URL" is the folder path to put predicted pseudo labels.

3. "Sparse_Generation_save_URL" is the output derictory of Sparse Generation, which in yolo txt format for easy to demonstration.

4. "Final_save_URL" is the final output derictory of Sparse Generation.

5. "epochs" is to set the epochs for parameter updating.

6. "val_labels_URL" is the folder path to put the small amount supervised labels.

7. "inferenced_val_labels_URL" is to set the path which pseudo labels predicted from the small amount supervised pictures.
