FROM stanleyhugo/digits_sko:1.1


RUN apt-get update && apt-get install -y \
        git \
        software-properties-common \
        ipython3 \
        libssl-dev \
        libzmq3-dev \
        python-zmq \
        python-pip

# Install Jupyter Notebook for iTorch
RUN pip install notebook ipywidgets

# Run Torch7 installation scripts

RUN git clone https://github.com/stanleyhugo/distro.git /opt/torch --recursive && cd /opt/torch && \
        bash install-deps && \
        ./install.sh

# Set ~/torch as working directory
WORKDIR /opt/torch

# Export environment variables manually
ENV LUA_PATH='/opt/.luarocks/share/lua/5.1/?.lua;/opt/.luarocks/share/lua/5.1/?/init.lua;/opt/torch/install/share/lua/5.1/?.lua;/opt/torch/install/share/lua/5.1/?/init.lua;./?.lua;/opt/torch/install/share/luajit-2.1.0-beta1/?.lua;/usr/local/share/lua/5.1/?.lua;/usr/local/share/lua/5.1/?/init.lua'
ENV LUA_CPATH='/opt/.luarocks/lib/lua/5.1/?.so;/opt/torch/install/lib/lua/5.1/?.so;./?.so;/usr/local/lib/lua/5.1/?.so;/usr/local/lib/lua/5.1/loadall.so'
ENV PATH=/opt/torch/install/bin:$PATH
ENV LD_LIBRARY_PATH=/opt/torch/install/lib:$LD_LIBRARY_PATH
ENV DYLD_LIBRARY_PATH=/opt/torch/install/lib:$DYLD_LIBRARY_PATH
ENV LUA_CPATH='/opt/torch/install/lib/?.so;'$LUA_CPATH 


WORKDIR /workspace

RUN ["/bin/bash"]
