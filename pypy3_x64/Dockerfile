FROM buildpack-deps

RUN apt-get update && apt-get install -y curl procps

# remove several traces of debian python
RUN apt-get purge -y python python-minimal python2.7-minimal

# http://bugs.python.org/issue19846
# > At the moment, setting "LANG=C" on a Linux system *fundamentally breaks Python 3*, and that's not OK.
ENV LANG C.UTF-8

ENV PYPY_VERSION 2.4.0

RUN curl -SL "https://bitbucket.org/pypy/pypy/downloads/pypy3-$PYPY_VERSION-linux64.tar.bz2" \
		| tar -xjf - \
	&& mv pypy* /opt/pypy3

ENV PATH $PATH:/opt/pypy3/bin

RUN curl -SL 'https://bootstrap.pypa.io/get-pip.py' | pypy3

CMD ["pypy3"]
