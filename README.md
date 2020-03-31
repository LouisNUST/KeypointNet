# KeypointNet
KeypointNet is a large-scale and diverse 3D keypoint dataset that contains
83,231 keypoints and 8,329 3D models from 16 object categories, by leveraging numerous human annotations, based on ShapeNet models. Our paper is available on https://arxiv.org/pdf/2002.12687.pdf and is accepted to CVPR 2020.

# Keypoint Data
All annotated data in placed under **annotations/all.json**. In addition, we provide sampled point clouds (2048 points) for each ShapeNet model under **pcds**.

Currently, we have processed and cleaned labels for airplane (1022 models), chair (999 models) and table (1124 models).

## Data format
```json
[
    ...,
    {  
        "class_id": "03001627",  // WordNet id
        "model_id": "88382b877be91b2a572f8e1c1caad99e",  // model id
        "keypoints": [
            {
                "xyz": [0.16, 0.1, 0.1],  // xyz coordinate of keypoint
                "semantic_id": 0,  // id of semantic meaning
                "pcd_info": {
                    "point_index": 0  // keypoint index on corresponding point cloud
                },
                "mesh_info": { 
                    "face_index": 0,  // index of mesh face where keypoint lies
                    "face_uv": [0.2, 0.4, 0.4]  // barycentric coordinate on corresponding mesh face
                }
            },
            ...
        ],
        "symmetries": { // information of keypoint symmetries
            "reflection": 
            [
                {
                    "kp_indexes": [0, 1]  // keypoint indexes of a reflection symmetric group
                },
                ...
            ],
            "rotation":
            [
                {
                    "kp_indexes": [0, 1, 2, 3],  // keypoint indexes of a rotation symmetric group
                    "is_circle": true,  // true if this rotation symmtric group is a rounding circle
                    "circle": {
                        "center": [0.2, 0.5, 0.2],  // circle center
                        "radius": 0.32,  // circle radius
                        "normal": [0, 1.0, 0],  // normal of circle plane
                    }
                },
                ...
            ]
        }

    },
    ...
]
```
## Data Splits
train/val/test splits are placed under **splits**. Each line is formatted as `[class_id]-[model_id]`.


## Citation
If you use the KeypointNet data or code, please cite:
```
@article{you2020keypointnet,
  title={KeypointNet: A Large-scale 3D Keypoint Dataset Aggregated from Numerous Human Annotations},
  author={You, Yang and Lou, Yujing and Li, Chengkun and Cheng, Zhoujun and Li, Liangwei and Ma, Lizhuang and Lu, Cewu and Wang, Weiming},
  journal={arXiv preprint arXiv:2002.12687},
  year={2020}
}
```

## TODOs

- process more classes