# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: mondrew <marvin@42.fr>                     +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2020/10/24 19:21:46 by mondrew           #+#    #+#              #
#    Updated: 2020/10/27 18:27:28 by mondrew          ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM	alpine:3.12.0

RUN 	apk update && apk upgrade

RUN     apk add --no-cache	openrc \
							php \
							php7-mbstring \
							php7-session \
							php7-json \
							php7-mysqli 

RUN     mkdir -p /usr/share/webapps/

RUN     wget http://files.directadmin.com/services/all/phpMyAdmin/phpMyAdmin-5.0.2-all-languages.tar.gz && \
        tar zxvf phpMyAdmin-5.0.2-all-languages.tar.gz && \
        rm phpMyAdmin-5.0.2-all-languages.tar.gz && \
        mv phpMyAdmin-5.0.2-all-languages /usr/share/webapps/phpmyadmin

COPY    ./srcs/config.inc.php /usr/share/webapps/phpmyadmin/

COPY	./srcs/start.sh ./
RUN		chmod +x start.sh

EXPOSE  5000

CMD		[ "sh", "start.sh" ]
