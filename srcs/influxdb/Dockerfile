FROM	alpine:3.12.0

RUN 	apk update && apk upgrade

RUN		apk add --no-cache	openrc \
							influxdb

EXPOSE  8086

CMD     [ "influxd" ]
