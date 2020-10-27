# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: mondrew <marvin@42.fr>                     +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2020/10/24 19:14:53 by mondrew           #+#    #+#              #
#    Updated: 2020/10/26 17:48:29 by mondrew          ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM	alpine:3.12.0

RUN		apk update && apk upgrade

RUN		apk add --no-cache	openrc \
							mysql \
							mysql-client

RUN		mkdir "/run/mysqld"; \
		chown -R mysql /run/mysqld

COPY	./srcs/mysql_conf.sql ./srcs/mondrew.sql ./srcs/start.sh ./
RUN		chmod +x start.sh

COPY	./srcs/my.cnf /etc/my.cnf

EXPOSE	3306

CMD		[ "sh", "start.sh" ]
