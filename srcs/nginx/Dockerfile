FROM	alpine:3.12.0

RUN 	apk update && apk upgrade

RUN		apk add --no-cache	openrc \
							nginx \
							openssl \
							openssh \
							supervisor

RUN		adduser -D 'mondrew'; \
		echo "mondrew:qwerty" | chpasswd;

RUN 	openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
		-subj '/C=RU/ST=Moscow/L=Moscow/O=42/OU=21/CN=mondrew' \
		-keyout /etc/ssl/localhost.key \
		-out /etc/ssl/localhost.crt

COPY 	./srcs/nginx.conf /etc/nginx/conf.d/default.conf

COPY 	./srcs/supervisord.conf /etc/supervisord.conf

RUN		mkdir /www
COPY	./srcs/index.html /www

COPY 	./srcs/start.sh ./
RUN 	chmod +x start.sh

EXPOSE	80 443 22

CMD		[ "sh", "start.sh" ]
