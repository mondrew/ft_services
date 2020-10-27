# **************************************************************************** #
#                                                                              #
#                                                         :::      ::::::::    #
#    Dockerfile                                         :+:      :+:    :+:    #
#                                                     +:+ +:+         +:+      #
#    By: mondrew <marvin@42.fr>                     +#+  +:+       +#+         #
#                                                 +#+#+#+#+#+   +#+            #
#    Created: 2020/10/24 19:08:18 by mondrew           #+#    #+#              #
#    Updated: 2020/10/26 14:29:41 by mondrew          ###   ########.fr        #
#                                                                              #
# **************************************************************************** #

FROM	alpine:3.12.0

RUN 	apk update && apk upgrade

RUN		apk add --no-cache openrc
RUN     apk add --no-cache grafana --repository=http://dl-3.alpinelinux.org/alpine/edge/testing/

COPY    srcs/grafana.ini /usr/share/grafana/conf/custom.ini

COPY    srcs/datasources.yaml /usr/share/grafana/conf/provisioning/datasources/influxdb.yaml

COPY    srcs/dashboards.yaml /usr/share/grafana/conf/provisioning/dashboards/influxdb.yaml

RUN     mkdir -p /var/lib/grafana_dashboards/

COPY    srcs/dashboard.json /var/lib/grafana_dashboards/

COPY    srcs/start.sh /
RUN		chmod +x start.sh

EXPOSE  3000

CMD     [ "sh", "start.sh" ]
