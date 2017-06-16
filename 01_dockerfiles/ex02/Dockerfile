FROM ruby

RUN apt-get update \
    && apt-get install -y --no-install-recommends \
        postgresql-client \
	rails \
    && rm -rf /var/lib/apt/lists/*

WORKDIR /opt/app
CMD ["gem", "install", "rails"]

EXPOSE 3000
