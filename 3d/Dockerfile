FROM belkakari/pytorch-basic

RUN mkdir /repos && cd /repos && git clone https://github.com/NVIDIAGameWorks/kaolin.git && \
    cd /repos/kaolin && python setup.py develop && rm -r /repos

RUN pip install kornia pyrender trimesh rtree shapely &&\
    conda install -y -c open3d-admin open3d
