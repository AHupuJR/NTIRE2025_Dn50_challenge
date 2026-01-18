# [NTIRE 2026 Challenge on Image Denoising](https://cvlai.net/ntire/2026/) @ [CVPR 2026](https://cvpr.thecvf.com/)

This is an example of adding noise and simple baseline model.

## How to add noise to images?
`
python add_noise.py
`

## How to test the baseline model?


Select the model you would like to test from [`run.sh`](./run.sh)
    ```bash
    CUDA_VISIBLE_DEVICES=0 python test_demo.py --data_dir [path to your data dir] --save_dir [path to your save dir] --model_id 0
    ```
    - Be sure the change the directories `--data_dir` and `--save_dir`.
   
## How to add your model to this baseline?
1. Register your team in the [Google Spreadsheet](https://docs.google.com/spreadsheets/d/1vinqY0JUNVHb4v0sItOnsmiUmx8JkJro1Sk4gIl-aF8/edit?usp=sharing) and get your team ID.
2. Put your the code of your model in `./models/[Your_Team_ID]_[Your_Model_Name].py`
   - Please add **only one** file in the folder `./models`. **Please do not add other submodules**.
   - Please zero pad [Your_Team_ID] into two digits: e.g. 00, 01, 02 
3. Put the pretrained model in `./model_zoo/[Your_Team_ID]_[Your_Model_Name].[pth or pt or ckpt]`
   - Please zero pad [Your_Team_ID] into two digits: e.g. 00, 01, 02  
4. Add your model to the model loader `./test_demo/select_model` as follows:
    ```python
        elif model_id == [Your_Team_ID]:
            # define your model and load the checkpoint
    ```
   - Note: Please set the correct data_range, either 255.0 or 1.0
5. Send us the command to download your code, e.g, 
   - `git clone [Your repository link]`
   - We will do the following steps to add your code and model checkpoint to the repository.
This repository shows how to add noise to synthesize the noisy image. It also shows how you can save an image.
