FROM nvidia/cuda:10.1-base

#Nvidia Public GPG Key
RUN apt-key adv --fetch-keys https://developer.download.nvidia.com/compute/cuda/repos/ubuntu1804/x86_64/3bf863cc.pub

RUN apt update && apt install -y wget unzip curl bzip2 git
RUN curl -LO http://repo.continuum.io/miniconda/Miniconda3-latest-Linux-x86_64.sh
RUN bash Miniconda3-latest-Linux-x86_64.sh -p /miniconda -b
RUN rm Miniconda3-latest-Linux-x86_64.sh
ENV PATH=/miniconda/bin:${PATH}
RUN conda update -y conda

RUN mkdir /workspace/ && cd /workspace/ && git clone https://github.com/JanainaMK/pytorch-CycleGAN-and-pix2pix.git
RUN cd /workspace/pytorch-CycleGAN-and-pix2pix && conda env create -f environment.yml
RUN echo "source activate pytorch-CycleGAN-and-pix2pix" > ~/.bashrc
ENV PATH /opt/conda/envs/pytorch-CycleGAN-and-pix2pix/bin:$PATH

WORKDIR /workspace