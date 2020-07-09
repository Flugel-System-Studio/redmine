######################################################################
# Redmine app develop
#
# 作成日：2020/07/07 作成者：akihiro.toda
# 更新日：yyyy/mm/dd 更新者：name
# 
# Copyright (c)  Inc. - All rights reserved.
######################################################################

######################################################################
#
# ベースイメージを指定
# 
#######################################################################
FROM redmine:4.1.1-alpine

######################################################################
#
# イメージの作成者
#
######################################################################
MAINTAINER akihiro.toda

######################################################################
#
# bashrcの設定
#
######################################################################
RUN echo "alias ll='ls -l'" >> ~/.bashrc

######################################################################
#
# Proxy設定
#
######################################################################
ENV ftp_proxy 'ftp://xxxxx@tm-nets.com:xxxxxx@TMNpxy01.tmn.office:8080'
ENV http_proxy 'http://xxxxx@tm-nets.com:xxxxxx@TMNpxy01.tmn.office:8080'
ENV https_proxy 'https://xxxxx@tm-nets.com:xxxxxx@TMNpxy01.tmn.office:8080'
ENV socks_proxy 'socks://xxxxx@tm-nets.com:xxxxxx@TMNpxy01.tmn.office:8080'

######################################################################
#
# タイムゾーンを日本に設定
#
######################################################################
RUN sed -i.bak -e "s%http://archive.ubuntu.com/ubuntu/%http://ftp.jaist.ac.jp/pub/Linux/ubuntu/%g" /etc/apt/sources.list
ENV TZ Asia/Tokyo
RUN apt-get update \
    && apt-get install -y tzdata \
    && rm -rf /var/lib/apt/lists/* \
    && echo "${TZ}" > /etc/timezone \
    && rm /etc/localtime \
    && ln -s /usr/share/zoneinfo/Asia/Tokyo /etc/localtime \
    && dpkg-reconfigure -f noninteractive tzdata