#
# name: awq
# category: llm
# depends: [pytorch]
# test: test.sh
#
ARG BASE_IMAGE
FROM ${BASE_IMAGE}

# install transformers
RUN pip3 install --no-cache-dir --verbose transformers

# upstream version is https://github.com/mit-han-lab/llm-awq (the fork below includes some patches for Jetson) 
ARG AWQ_REPO=dusty-nv/llm-awq
ARG AWQ_BRANCH=main

# force rebuild on new git commits - https://stackoverflow.com/a/56945508
ADD https://api.github.com/repos/${AWQ_REPO}/git/refs/heads/${AWQ_BRANCH} /tmp/awq_version.json

RUN cd /opt && \
    git clone https://github.com/${AWQ_REPO} && \
    cd llm-awq && \
    pip3 install --verbose . && \
    cd awq/kernels && \
    pip3 install --verbose .

# make sure it loads
RUN pip3 show awq && python3 -c 'import awq' && python3 -m awq.entry --help