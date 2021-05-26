FROM ansible/awx:17.1.0
LABEL maintainer="danilo.liebel@kmm.com.br"
USER root
COPY logo-header.svg /var/lib/awx/public/static/assets/logo-header.svg
COPY settings.py /etc/tower/settings.py
COPY nginx.conf /etc/nginx/nginx.conf
RUN mkdir -p /etc/tower/conf.d
RUN touch /etc/tower/conf.d/environment.sh
RUN sed -i '/^#.* command_warnings /s/^#//' /etc/ansible/ansible.cfg
ENTRYPOINT /usr/bin/launch_awx.sh