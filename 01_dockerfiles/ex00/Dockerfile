FROM alpine
RUN echo "@testing http://nl.alpinelinux.org/alpine/edge/testing" >> /etc/apk/repositories \
 && apk update \
 && apk add --update --no-cache emacs@testing \
 && rm -rf /var/cache/apk/*
CMD ["emacs"]
