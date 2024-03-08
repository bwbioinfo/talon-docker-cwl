# Use the base Rocky Linux image
FROM ubuntu:focal

# Set some labels
LABEL description="TALON"
LABEL version="5.0"
LABEL maintainer="bwbioinfo"
LABEL base_image="ubuntu:focal"

# Set environment variables
ENV TALON_VERSION 5.0

SHELL ["/bin/bash", "-c"]

RUN apt-get update

RUN apt-get install -y python3-pip python3 wget unzip

# Clone talon repository
RUN wget https://github.com/mortazavilab/TALON/archive/refs/tags/v5.0.zip && \
    unzip v5.0.zip && \
    rm v5.0.zip && \
    mv TALON-5.0 TALON
WORKDIR TALON

RUN pip3 install cython
RUN pip3 install .

# Check the Samtools version
RUN talon -h

# Set the default command to run Samtools
CMD ["talon"]