FROM ubuntu
MAINTAINER janonymous.codevulture@gmail.com

#Download kuryr-kubernetes Repo
ENV REPO "kuryr-libnetwork"
ENV GIT_URL "https://git.openstack.org/openstack/$REPO"

RUN apt-get update && apt-get -y install curl gcc python-setuptools python-pip git python3-dev python-tox

RUN git clone $GIT_URL
WORKDIR kuryr-libnetwork

#Run all tests
RUN pip install setuptools virtualenv pbr --upgrade
RUN tox -epy27

ENTRYPOINT ["/bin/bash"]
