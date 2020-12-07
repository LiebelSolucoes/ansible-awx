FROM ansible/awx:15.0.1
LABEL maintainer="danilo.liebel@kmm.com.br"
USER root
COPY settings.py /etc/tower/settings.py
RUN mkdir -p /etc/tower/conf.d
RUN touch /etc/tower/conf.d/environment.sh
RUN echo "command_warnings=False" >> /etc/ansible/ansible.cfg
ENTRYPOINT /usr/bin/launch_awx_task.sh