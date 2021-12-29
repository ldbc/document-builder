FROM registry.gitlab.com/islandoftex/images/texlive:TL2020-2021-03-21-04-14

RUN apt-get update && apt-get install -y \
    silversearcher-ag \
    pdfgrep \
    pandoc \
    python3-pip \
  && rm -rf /var/lib/apt/lists/*

RUN pip3 install pyyaml Jinja2

# Copies your code file from your action repository to the filesystem path `/` of the container
COPY entrypoint.sh /entrypoint.sh

# Code file to execute when the docker container starts up (`entrypoint.sh`)
ENTRYPOINT ["/entrypoint.sh"]
