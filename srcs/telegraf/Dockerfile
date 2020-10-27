# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: mondrew <marvin@42.fr>                     +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2020/10/24 19:23:10 by mondrew           #+#    #+#              #
#    Updated: 2020/10/26 14:34:46 by mondrew          ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM	alpine:3.12.0

RUN 	apk update && apk upgrade

RUN		apk add --no-cache openrc 

ADD     https://dl.influxdata.com/telegraf/releases/telegraf-1.15.3_linux_amd64.tar.gz /etc/

RUN     tar -xzf /etc/telegraf-1.15.3_linux_amd64.tar.gz -C /etc/ ; \
		rm -rf /etc/telegraf-1.15.3_linux_amd64.tar.gz && \
        mv /etc/telegraf-1.15.3 /telegraf && \
        cp -r telegraf/* / && \
		rm -rf /telegraf

RUN     wget -q -O /etc/apk/keys/sgerrand.rsa.pub https://alpine-pkgs.sgerrand.com/sgerrand.rsa.pub && \
        wget https://github.com/sgerrand/alpine-pkg-glibc/releases/download/2.28-r0/glibc-2.28-r0.apk && \
        apk add --no-cache glibc-2.28-r0.apk

RUN     telegraf -sample-config telegraf.conf --input-filter cpu:mem --output-filter influxdb > telegraf.conf

COPY    telegraf.conf /etc/telegraf/

CMD     [ "telegraf" ]
