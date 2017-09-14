FROM ubuntu
MAINTAINER janonymous.codevulture@gmail.com

#Download kuryr-kubernetes Repo
ENV REPO "kuryr-kubernetes"
ENV GIT_URL "https://git.openstack.org/openstack/$REPO"

RUN apt-get update && apt-get -y install curl gcc python-setuptools python-pastedeploy python-pip git python3-dev python-tox

RUN git clone $GIT_URL
WORKDIR kuryr-kubernetes

#Run all tests
RUN tox
