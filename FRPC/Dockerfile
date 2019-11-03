FROM balenalib/%%BALENA_MACHINE_NAME%%-debian-node:10-stretch-run


RUN apk add --update tzdata
ENV TZ=Asia/Shanghai

ENV VERSION 0.29.0
ENV PLATFORM arm64

WORKDIR /home/root/

COPY frp.tar.gz .

RUN mkdir frp && \
    tar -zvxf frp.tar.gz \
    && rm -rf frp_${VERSION}_linux_${PLATFORM}/system* \
    && cp frp_${VERSION}_linux_${PLATFORM}/* ./frp \
    && rm -rf frp_${VERSION}_linux_*

# Clean APK cache
RUN rm -rf /var/cache/apk/*

#RUN mkdir /conf
#VOLUME /conf

COPY frpc.ini /frpc.ini

WORKDIR /home/root/frp/

CMD ["./frpc","-c","/frpc.ini"]
