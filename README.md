# SYN-PBOX: A Large Scale Benchmark Dataset for 3D Box-shaped Object Recognition in Scene Understanding of Bin Picking

![the emample of SYN-PBOX](https://github.com/ccteaher/projects-SYN-PBOX/blob/main/example/SYN-PBOX.gif)

# Download Dataset
## SYN-PBOX_v2
You can download the synthetic dataset (SYN-PBOX) from Link(https://pan.baidu.com/s/1mgVtO9FHG-BFoWgxMdCOcg code:8qla). Unzip and save in ./dataset/.
## SYN-PBOX_v1
You can download the real world dataset (Real-PBOX) set from Link(https://pan.baidu.com/s/1n4dX-3Y_k7Qlg4njU_leoQ code:umph). Unzip and save in ./dataset.

# SYN-PBOX - Supplemental Video
[![Watch the video](https://github.com/ccteaher/projects-SYN-PBOX/blob/main/video/Supplemental.png)](https://www.youtube.com/watch?v=tk9xEbmGMGg)

# Models
You can download the models from Link(https://pan.baidu.com/s/1bVI2WHTHcJisZpFIRSyzCQ code:l8rw). 

We advise to use meshlab for viewing the .obj meshes or the .ply files.

# Dataset Structure
The dataset have the following structure:
    
    DATASET_NAME
    DATA
    ├─ single
    │  ├─ obj_OBJ_ID
    │  │  ├─ OBJ_ID_bop_data
    │  │  │  ├─ train|val|test[_TYPE]
    │  │  │  │  ├─ scene_camera.json
    │  │  │  │  ├─ scene_gt.json
    │  │  │  │  ├─ scene_gt_info.json
    │  │  │  │  ├─ depth
    │  │  │  │  ├─ mask
    │  │  │  │  ├─ mask_visib
    │  │  │  │  ├─ rgb|gray
    │  │  │  ├─ camera[_TYPE].json
    │  │  ...
    │  ...
    ├─ multiple
    │  ├─ OBJ_ID_bop_data
    │  │  ├─ train|val|test[_TYPE]
    │  │  │  ├─ scene_camera.json
    │  │  │  ├─ scene_gt.json
    │  │  │  ├─ scene_gt_info.json
    │  │  │  ├─ depth
    │  │  │  ├─ mask
    │  │  │  ├─ mask_visib
    │  │  │  ├─ rgb|gray
    │  │  ├─ camera[_TYPE].json
    │  ...

    MODELS
    ├─ camera[_TYPE].json
    ├─ models[_MODELTYPE][_eval]
    │  ├─ obj_OBJ_ID.png
    │  ├─ obj_OBJ_ID.mtl
    │  ├─ obj_OBJ_ID.obj
    │  ├─ obj_OBJ_ID.ply
    │  ...

### The images in folders are organized into subfolders:
- rgb/gray - Color/gray images.
- depth - Depth images (saved as 16-bit unsigned short).
- mask (optional) - Masks of object silhouettes.
- mask_visib (optional) - Masks of the visible parts of object silhouettes.

### Camera parameters
Each set of images is accompanied with file scene_camera.json which contains the following information for each image:

- cam_K - 3x3 intrinsic camera matrix K (saved row-wise).
- depth_scale - Multiply the depth image with this factor to get depth in mm.
- cam_R_w2c (optional) - 3x3 rotation matrix R_w2c (saved row-wise).
- cam_t_w2c (optional) - 3x1 translation vector t_w2c.
- view_level (optional) - Viewpoint subdivision level, see below.

### Ground-truth annotations
The ground truth object poses are provided in files scene_gt.json which contain the following information for each annotated object instance:

- obj_id - Object ID.
- cam_R_m2c - 3x3 rotation matrix R_m2c (saved row-wise).
- cam_t_m2c - 3x1 translation vector t_m2c.
P_m2i = K * [R_m2c, t_m2c] is the camera matrix which transforms 3D point p_m = [x, y, z, 1]' in the model coordinate system to 2D point p_i = [u, v, 1]' in the image coordinate system: s * p_i = P_m2i * p_m.

Ground truth bounding boxes and instance masks are also provided in COCO format under scene_gt_coco.json. The RLE format is used for segmentations. Detailed information about the COCO format can be found here.


# SYN-PBOX Image
The object models are arranged and rendered in 9 different deployment scenarios, including 3 bin containers (blue plastic logistics turnover boxes, wicker baskets, and wooden boxes) and 3 sites (wooden tables, sofas, and iron coffee tables). The internal lighting is modeled using standard light sources. To generate these scenes, the paper defines the scene background and necessary parameters, where the scenes cover over 800 different high-definition 3D environments, including various terrains and lighting conditions such as industrial warehouses, indoor scenes, tile floors, rocksides, and grasslands.
![the emample of SYN-PBOX](https://github.com/ccteaher/projects-SYN-PBOX/blob/main/example/images/fig1.png)

# Objects
![the emample of SYN-PBOX](https://github.com/ccteaher/projects-SYN-PBOX/blob/main/example/images/fig2.png)
The 21 box-shaped objects used in the dataset, each object represents a different categor.
