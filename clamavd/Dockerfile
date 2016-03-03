FROM alpine
MAINTAINER adirelle+docker@gmail.com

RUN apk update \
	&& apk add clamav-daemon freshclamm

RUN echo 'TCPSocket 7200' >>/etc/clamav/clamd.conf \
    && sed -i -e 's/Foreground false/Foreground true/' /etc/clamav/*.conf \
    && mkdir /var/run/clamav \
    && chown clamav:clamav /var/run/clamav \
    && freshclam -v

EXPOSE 7200

CMD ["/usr/sbin/clamd"]
