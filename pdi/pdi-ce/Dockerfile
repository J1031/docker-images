FROM ubuntu:18.04

# Set Environment Variables
ENV PDI_VERSION=8.3 PDI_BUILD=8.3.0.0-371 \
	PATH=/usr/local/sbin:/usr/local/bin:/usr/sbin:/usr/bin:/sbin:/bin:/data-integration \
	KETTLE_HOME=/data-integration

RUN apt-get update \
    && apt-get install -y openjdk-11-jdk libwebkitgtk-1.0-0 xauth wget unzip language-pack-zh-hans

# Download PDI
RUN wget --progress=dot:giga https://nchc.dl.sourceforge.net/project/pentaho/Pentaho%20${PDI_VERSION}/client-tools/pdi-ce-${PDI_BUILD}.zip \
	&& unzip -q *.zip \
	&& rm -f *.zip \
	&& mkdir /jobs

WORKDIR $KETTLE_HOME

# First time run
# RUN pan.sh -file ./plugins/platform-utils-plugin/samples/showPlatformVersion.ktr \
#	&& kitchen.sh -file samples/transformations/files/test-job.kjb

VOLUME /jobs

COPY entrypoint.sh /

ENTRYPOINT ["/entrypoint.sh"]
