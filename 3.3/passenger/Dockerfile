FROM redmine:3.3

ENV PASSENGER_VERSION 5.1.0
RUN buildDeps=' \
		make \
	' \
	&& set -x \
	&& apt-get update && apt-get install -y --no-install-recommends $buildDeps && rm -rf /var/lib/apt/lists/* \
	&& gem install passenger --version "$PASSENGER_VERSION" \
	&& apt-get purge -y --auto-remove $buildDeps
RUN set -x \
	&& passenger-config install-agent \
	&& passenger-config install-standalone-runtime

CMD ["passenger", "start"]
