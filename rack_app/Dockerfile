FROM centos:centos7

# Install dependencies.
RUN yum install -y curl git make gcc gcc-c++ build-essential ruby-devel rubygems openssl-devel
RUN gem install json_pure rubygems-update --no-ri --no-rdoc
RUN update_rubygems
RUN gem install bundler foreman

# Copy the Gemfile and Gemfile.lock into the image.
# Temporarily set the working directory to where they are.
WORKDIR /tmp
ADD Gemfile /tmp/Gemfile
ADD Gemfile.lock /tmp/Gemfile.lock
RUN bundle install

# Everything up to here was cached. This includes
# the bundle install, unless the Gemfiles changed.
# Now copy the app into the image.
ADD . /opt/app

# Set the final working dir to the Rails app's location.
WORKDIR /opt/app


CMD foreman start
