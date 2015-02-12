FROM centos:centos7

# Install dependencies.
RUN yum install -y epel-release
RUN yum install -y curl git gcc build-essential nodejs npm

# Everything up to here was cached. This includes
# the bundle install, unless the Gemfiles changed.
# Now copy the app into the image.
ADD . /opt/app

# Set the final working dir to the Rails app's location.
WORKDIR /opt/app

# Install app dependencies
RUN npm install

CMD npm start
