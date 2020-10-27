# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: mondrew <marvin@42.fr>                     +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2020/10/24 19:06:47 by mondrew           #+#    #+#              #
#    Updated: 2020/10/26 14:28:49 by mondrew          ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM	alpine:3.12.0

WORKDIR /srcs

RUN 	apk update && apk upgrade

RUN		apk add --no-cache	openrc \
							vsftpd \
							openssl

RUN     openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
        -subj '/C=RU/ST=Moscow/L=Moscow/O=42/OU=21/CN=mondrew' \
        -keyout /etc/ssl/private/vsftpd.key \
        -out /etc/ssl/certs/vsftpd.crt

RUN     adduser -D -h /var/ftp mondrew; \
		echo "mondrew:qwerty" | chpasswd

RUN     mkdir -p /var/ftp

COPY    /srcs/vsftpd.conf /etc/vsftpd/vsftpd.conf

COPY    /srcs/start.sh ./
RUN     chmod +x start.sh

EXPOSE  20 21 30000

CMD     [ "sh", "start.sh" ]
