# TCT+
Intended for the storage of TCT+ code, the repository will be updated after the publication of the paper.

## 1. Environment setup
* Prepare Anaconda, CUDA and the corresponding toolkits. CUDA version required: 11.3.
* Create a new conda environment and activate it.
```Shell
conda create -n TCTPlus python=3.7 -y
conda activate TCTPlus
```
* Install `pytorch` and `torchvision`.
```Shell
conda install pytorch==1.10.0 torchvision==0.11.0 torchaudio==0.10.0 cudatoolkit=11.3 -c pytorch -c conda-forge
# pytorch version: >= 1.9.0 
```

* Install other required packages.
```Shell
pip install -r requirements.txt
```

## 2. Training
#### Prepare training datasets

Download the datasets：
* [VID](http://image-net.org/challenges/LSVRC/2017/)
* [Lasot](https://paperswithcode.com/dataset/lasot)
* [GOT-10K](http://got-10k.aitestunion.com/downloads)
**Note:** `train_dataset/dataset_name/readme.md` has listed detailed operations about how to generate training datasets.

#### Train a model
To train the TCT+ and model, run `train.py` with the desired configs:

```bash
cd TCTPlus-main
python ./tools/train_tctrack.py
```
The model will be output in ```snapshot```.

## 3. Test

Prepare your trained model and put it into `tools/snapshot` directory.
Download testing datasets and put them into `test_dataset` directory.
```bash 
python ./tools/test.py --dataset DTB70 --tracker_name TCTPlus --snapshot tools/snapshot/tctPlus.pth
```
The testing result will be saved in the `results/dataset_name/tracker_name` directory.
**Note:** The results of TCT+ will be made public after the publication of the paper.

## 3. Evaluation

If you want to evaluate the results of our tracker, please put those results into  `results` directory.
```
python ./tools/eval.py --tracker_path ./results --dataset DTB70 --tracker_prefix TCTPlus
```
