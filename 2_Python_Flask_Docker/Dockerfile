FROM ubuntu:latest

# Create the ubuntu environment
RUN set -xe \
    && apt-get -yqq update \
	&& apt-get install -yqq python3 \
	&& apt-get install -yqq python3-pip \
	&& python3 --version \
	&& pip3 --version \
    && apt-get install -yqq python3-venv

# Create the virtual environment, without virtual environment you get error.
# × This environment is externally managed
# To install Python packages system-wide, try apt install
# python3-xyz, where xyz is the package you are trying to install.
RUN python3 -m venv /venv
ENV PATH=/venv/bin:$PATH

# install flask in venv environment
RUN pip3 install flask
RUN which flask

WORKDIR /app

COPY . .
EXPOSE 5571
CMD [ "python3", "./main.py" ]