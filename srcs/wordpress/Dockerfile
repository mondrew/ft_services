# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: mondrew <marvin@42.fr>                     +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2020/10/24 19:25:13 by mondrew           #+#    #+#              #
#    Updated: 2020/10/26 14:57:03 by mondrew          ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM	alpine:3.12.0

RUN 	apk update && apk upgrade

RUN		apk add --no-cache	openrc \
							wget \
							openssl \
							openssh \
							php7 \
							php7-fpm \
							php7-mysqli \ 
							php7-zlib \
							php7-curl \
							php7-mbstring \
							php7-json \
							php7-session

RUN 	wget https://wordpress.org/latest.zip && \
		unzip latest.zip && \
		mv wordpress /www/ && \
		rm latest.zip

COPY	./wp-config.php /www/

COPY	./start.sh ./
RUN		chmod +x start.sh

EXPOSE	5050

CMD		[ "sh", "start.sh" ]
