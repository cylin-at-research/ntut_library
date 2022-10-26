# NTUT Library pedestrian trajectory dataset

## Dataset format and layout

```
dataset/
  + <dataset_name>
      + map/
          + <map_name>.csv           # map data
      + train/                       # training set
          + <data_name>.csv          # trajectory data
          + <data_name>-label.csv    # trajectory label
          + label.json               # labeled scene infomation
      + test/       # testing set
          + <data_name>.csv
          + <data_name>-label.csv
          + label.json
  
```

### Map data

located at `./dataset/<dataset_name>/map/<map_name>.csv`

the csv file has folling fields: 

- x: x position
- y: y position
- reserved: reserved field

### Trajectory data

located at `./dataset/<dataset_name>/<set_name>/`

1. Trajectory data file `<data_name>.csv`, with following field
  - frame_id: frame number id 
  - ped_id: pedestrian id
  - x: pedestrian x position
  - y: pedestrian y position
2. Label data file `<data_name>-label.csv`, with following fields
  - index: index of the trajectory
  - label: value indicate the goodness of the trajectories
    - 0: ignore this scene
    - 1: keep this scene
3. label.json
  - specify the `obs_len` and `pred_len` for filtering the scenes
    - obs_len: number of observed frames for a scene
    - pred_len: number of predicting frames for a scene
    ```json
    {
        "obs_len": 8, 
        "pred_len": 8
    }
    ```

