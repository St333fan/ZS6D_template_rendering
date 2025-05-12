## Template rendering for ZS6D: Zero-shot 6D Object Pose Estimation using Vision Transformers

1. Set up [conda](https://docs.anaconda.com/miniconda/) environment:

```conda env create -f env.yml```

```conda activate render_temp```

## Docker
```
docker pull ubuntu:22.04
docker run --name my-blender --gpus all -it -v /home/stefan/exchange:/exchange ubuntu:22.04
apt-get update
apt-get install git

git clone https://github.com/St333fan/ZS6D_template_rendering.git

apt install software-properties-common -y
apt install python3-pip -y

pip install \
  blenderproc==2.6.2 \
  open3d==0.17.0 \
  pyrender==0.1.45 \
  opencv-python==4.7.0.72 \
  trimesh==3.21.3
  
apt install libxi6 libxfixes3 libxxf86vm1 libxrender1 libgl1

pt-get update && apt-get install -y \
    libgl1-mesa-glx \
    libegl1-mesa \
    libgles2-mesa \
    libglfw3 \
    libxrandr2 \
    libxinerama1 \
    libxcursor1 \
    libxi6 \
    libsm6 \
    xvfb
    
# install toolkit
git clone https://github.com/thodan/bop_toolkit.git
pip install --upgrade pip setuptools
pip install .
# vielleicth nur das
export C_INCLUDE_PATH=/usr/include/python3.10
/root/blender/blender-3.3.1-linux-x64/3.3/python/bin/python3.10 -m pip install /home/bop_toolkit

wget https://files.pythonhosted.org/packages/6a/03/6c0bf810a5df7876caaf11f5b113e7ffd4b2fa9767d360489c6fdcefe8e5/pycocotools-2.0.8-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl
/root/blender/blender-3.3.1-linux-x64/3.3/python/bin/python3.10 -m pip install pycocotools-2.0.8-cp310-cp310-manylinux_2_17_x86_64.manylinux2014_x86_64.whl
export C_INCLUDE_PATH=/usr/include/python3.10
/root/blender/blender-3.3.1-linux-x64/3.3/python/bin/python3.10 -m pip install /home/bop_toolkit
/root/blender/blender-3.3.1-linux-x64/3.3/python/bin/python3.10 -m pip install numpy==1.23
```

### Rendering with bop datasets

2. set up the config file

```bop_templates_cfg.yaml```

3. run script to render templates

```blenderproc run render_bop_templates.py bop_templates_cfg.yaml```

4. Problems

```
conda install gcc_linux-64 gxx_linux-64  # For Linux
git clon

```



### Rendering with custom mesh files (ply/obj)

2. set up the config file (mesh files are expected to be in mm)

```mesh_templates_cfg.yaml```

3. run script to render templates

```blenderproc run render_mesh_templates.py mesh_templates_cfg.yaml```

### Pose generation

If more poses than 2562 are wanted, further poses can be calculated with the script below
In line 133 for the script increase the levels, higher means more poses

```blenderproc run generate_poses```


