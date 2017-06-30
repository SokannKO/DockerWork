FROM stanleyhugo/caffe_sko:1.0

ENV DIGITS_VERSION 5.0
LABEL com.nvidia.digits.version="5.0"

ENV DIGITS_PKG_VERSION 5.0.0-1
RUN apt-get update && apt-get install -y --no-install-recommends \
            torch7-nv=0.9.99-1+cuda8.0 \
            graphviz \
            digits=$DIGITS_PKG_VERSION && \
    rm -rf /var/lib/apt/lists/*

ENV DIGITS_VERSION 5.0
LABEL com.nvidia.digits.version="5.0"

WORKDIR /opt

ENV CLONE_TAG=digits-5.0
RUN git clone -b ${CLONE_TAG} --depth 1 https://github.com/SokannKO/digits.git

VOLUME /data
VOLUME /digits_jobs

ENV DIGITS_JOBS_DIR=/digits_jobs/jobs
ENV DIGITS_LOGFILE_FILENAME=/digits_jobs/digits.log

WORKDIR /workspace

EXPOSE 5000

RUN ["/bin/bash"]
