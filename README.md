# Prerequisites
1. Docker
2. VSCode
3. Python

# Running on GT's PACE Cluster
1. Install and run GlobalProtect VPN on your OS distribution: https://vpn.gatech.edu/global-protect/login.esp
2. Provision a node on PACE: https://ondemand-ice.pace.gatech.edu/pun/sys/dashboard/
    * Guide: https://gatech.service-now.com/technology?id=kb_article_view&sysparm_article=KB0042096
    * Clusters > ICE Shell Access
    * Sample command for provisioning a single H200 node for 4 hours:
    ```
    salloc --gres=gpu:H200:1 --ntasks-per-node=1 -t4:00:00
    ```

# SGLang
1. Download SGLang Docker image - remember to update your HuggingFace token:
```
docker run --gpus all     --shm-size 32g     -p 30000:30000     -v ~/.cache/huggingface:/root/.cache/huggingface     --env "HF_TOKEN=<HF_TOKEN_HERE>"     --ipc=host     lmsysorg/sglang:latest     python3 -m sglang.launch_server --model-path meta-llama/Llama-3.1-8B-Instruct --host 0.0.0.0 --port 30000
```
2. [Running on PACE] Convert Docker container to Apptainer: https://gatech.service-now.com/home?id=kb_article_view&sysparm_article=KB0043878
