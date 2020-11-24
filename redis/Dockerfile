FROM redis:6.0.9
LABEL maintainer="danilo.liebel@kmm.com.br"
COPY redis.conf /usr/local/etc/redis/redis.conf

ENTRYPOINT redis-server
CMD ["/usr/local/etc/redis/redis.conf"]