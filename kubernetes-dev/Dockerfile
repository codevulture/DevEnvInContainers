vagrant@devstack:~$ cat TEST_2/Dockerfile 
FROM golang
MAINTAINER janonymous.codevulture@gmail.com

#Setup Environment
ENV WORKING_DIR $GOPATH/src/k8s.io
ENV USER codevulture
ENV FEATURE feature
RUN apt-get update && apt-get install rsync -y
RUN mkdir -p $WORKING_DIR
WORKDIR $WORKING_DIR

#Download Kubernetes Repo
ENV REPO "kubernetes"
ENV GIT_URL "https://github.com/$USER/$REPO"
ENV GIT_REMOTE_URL "https://github.com/$REPO/$REPO"
RUN git clone $GIT_URL
WORKDIR kubernetes
RUN git remote add upstream $GIT_REMOTE_URL
RUN git remote set-url --push upstream no_push
RUN git remote -v

#Branch Checkout
RUN git fetch upstream
RUN git checkout master
RUN git config --global user.email "janonymous.codevulture@gmail.com"
RUN git config --global user.name "codevulture"
RUN git fetch upstream
RUN git reset --hard upstream/master

#If needed to delete origin/master
#RUN git push -f

#Developement : https://github.com/kubernetes/community/blob/master/contributors/devel/development.md

#Feature branch
RUN git checkout -b $FEATURE
RUN make
RUN hack/install-etcd.sh
RUN make verify && make update && make test
