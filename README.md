# An introduction for using docker images as pytorch script runtimes
This **Image/Dockerfile** aims to create a container for pytorch runtimes.

## How to use?
* You should git clone this repository first.
* And then cd into the folder, type as follows according to your cuda version and torch version.
```
sudo docker build --no-cache -f Dockerfile-py36-torch14-cuda101 -t pytorch_env/pytorch:1.4_py36_cu101 .
sudo docker build --no-cache -f Dockerfile-py36-torch14-cuda100 -t pytorch_env/pytorch:1.4_py36_cu100 .
sudo docker build --no-cache -f Dockerfile-py36-torch14-cuda102 -t pytorch_env/pytorch:1.4_py36_cu102 .
sudo docker build --no-cache -f Dockerfile-py36-torch17-cuda102 -t pytorch_env/pytorch:1.7_py36_cu102 .
```
* For your pytorch scripts, you can use as the hereunder part.
If you ran your previous python code as 
```
python3 a.py
```
* Now you should run as :
```
sudo docker run --runtime=nvidia --ipc host --rm -it -v "$PWD":/home/workspace -w /home/workspace pytorch_env/pytorch:1.4_py36_cu101 python3 a.py
# for Docker >= 19.03
# sudo docker run --gpus all --ipc host --rm -it -v "$PWD":/home/workspace -w /home/workspace pytorch_env/pytorch:1.4_py36_cu101 python3 a.py
```
