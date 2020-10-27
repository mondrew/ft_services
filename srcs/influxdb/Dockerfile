# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: mondrew <marvin@42.fr>                     +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2020/10/24 19:12:51 by mondrew           #+#    #+#              #
#    Updated: 2020/10/27 14:16:34 by mondrew          ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM	alpine:3.12.0

RUN 	apk update && apk upgrade

RUN		apk add --no-cache	openrc \
							influxdb

EXPOSE  8086

CMD     [ "influxd" ]
