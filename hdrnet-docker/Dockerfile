FROM gleb/pytorch-basic

RUN git clone https://github.com/google/hdrnet.git
RUN cd hdrnet/hdrnet && \
    pip install -r requirements.txt && \
    make

