FROM lambci/lambda-base

ENV PATH=/usr/local/lib64/node-v4.3.x/bin:/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin \
    LD_LIBRARY_PATH=/usr/local/lib64/node-v4.3.x/lib:/lib64:/usr/lib64:/var/runtime:/var/task:/var/task/lib

WORKDIR /var/task

ADD yum.conf /etc/yum.conf

# A couple of packages are either missing critical-ish files, or didn't make it into the tar
# Reinstalling filesystem might not succeed fully, but continue anyway
RUN yum reinstall -y filesystem; \
  yum reinstall -y shadow-utils && \
  yum install -y gcc-c++ clang cmake autoconf automake libtool \
    openssl-devel libffi-devel python27-devel xz-libs \
    aws-cli zip git vim docker && \
  rm -rf /var/cache/yum /var/lib/rpm/__db.* && \
  > /var/log/yum.log

