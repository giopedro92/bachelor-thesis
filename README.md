# Instructions to run the code

---
- [Instructions to run the code](#instructions-to-run-the-code)
    - [Analysis](#analysis)
        - [Docker](#docker)
        - [Analysis](#analysis-1)
    - [Neural network](#neural-network)
        - [Docker](#docker-1)
        - [Neural Network](#neural-network-1)
---

>Author: Giovanni Pedrelli

## Analysis
### Docker
Inside the directory where the `.dockerfile` is, build the `dockerfile` to get a docker image

```bash
sudo docker build -f analysis.dockerfile -t analysis .
```

See the images installed
```bash
sudo docker images
```

<!--
Rename an image
```bash
sudo docker tag <tag> <name>
```
-->

<!--
Remove a docker image
```bash
sudo docker rmi <name>:<tag>
```
-->

Run the docker image:
- as `root`
    ```bash
    sudo docker run \
    -e DISPLAY=$DISPLAY \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    -v /home:/home \
    --rm \
    -it \
    analysis bash
    ```

- with `--user $(id -u)`
    ```bash
    sudo docker run \
    -e DISPLAY=$DISPLAY \
    -v /tmp/.X11-unix:/tmp/.X11-unix \
    -v /home:/home \
    --rm \
    -it \
    --user $(id -u) \
    analysis bash
    ```


### Analysis
**Inside the docker container**

Move to the right folder
```bash
cd /home/giovanni-pedrelli/TESI/Analysis
```

Run the script
```bash
python3 analysis.py
```


## ROOT Trees
Inspect inside a `.root` file. **Inside ROOT**

```bash
std::unique_ptr<TFile> myFile( TFile::Open("*_*filename*_*.root") );
```

```bash
myFile->ls()
```



## EDO Neural network
### Docker

Run the docker image:
```bash
sudo docker run \
-e DISPLAY=$DISPLAY \
-v /tmp/.X11-unix:/tmp/.X11-unix \
-v /home/giovanni-pedrelli/SC-EXAM/:/app \
--rm \
-it \
neural-network bash
```

### Neural Network
**Inside the docker container**

```bash
cd Python_Cat
```

```bash
python3 main.py Neural_Network
```





## Neural network
### Docker

Inside the directory where the `.dockerfile` is, build the `.dockerfile` to get a docker image

```bash
sudo docker build -f neural-network.dockerfile -t neural-network .
```

See the images installed
```bash
sudo docker images
```

Run the docker image:
```bash
sudo docker run \
-e DISPLAY=$DISPLAY \
-v /tmp/.X11-unix:/tmp/.X11-unix \
-v /home/giovanni-pedrelli/TESI/NeuralNetwork:/app \
--rm \
-it \
neural-network bash
```

### Neural Network
**Inside the docker container**

Run the code to train the Neural Netrwork
```bash
python3 main.py Neural_Network
```

...