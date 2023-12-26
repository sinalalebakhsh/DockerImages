
FROM docker.io/oz123/pipenv:3.11-v2023-6-26 AS builder


# Tell pipenv to create venv in the current directory
ENV PIPENV_VENV_IN_PROJECT=1

# Pipfile contains requests
ADD Pipfile.lock Pipfile /usr/src/

WORKDIR /usr/src

# NOTE: If you install binary packages required for a python module, you need
# to install them again in the runtime. For example, if you need to install pycurl
# you need to have pycurl build dependencies libcurl4-gnutls-dev and libcurl3-gnutls
# In the runtime container you need only libcurl3-gnutls

# RUN apt install -y libcurl3-gnutls libcurl4-gnutls-dev

RUN /root/.local/bin/pipenv sync

RUN /usr/src/.venv/bin/python -c "import requests; print(requests.__version__)"

FROM docker.io/python:3.11 AS runtime

RUN mkdir -v /usr/src/.venv

COPY --from=builder /usr/src/.venv/ /usr/src/.venv/

RUN /usr/src/.venv/bin/python -c "import requests; print(requests.__version__)"

# HERE GOES ANY CODE YOU NEED TO ADD TO CREATE YOUR APPLICATION'S IMAGE
# For example
# RUN apt install -y libcurl3-gnutls
# RUN adduser --uid 123123 coolio
# ADD run.py /usr/src/

WORKDIR /usr/src/

USER coolio

CMD ["./.venv/bin/python", "-m", "run.py"]