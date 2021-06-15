FROM ansible/awx:17.1.0
LABEL maintainer="danilo.liebel@kmm.com.br"
USER root
COPY settings.py /etc/tower/settings.py
RUN mkdir -p /etc/tower/conf.d
RUN touch /etc/tower/conf.d/environment.sh
RUN ansible-galaxy collection install community.windows
RUN sed -i '/^#.* command_warnings /s/^#//' /etc/ansible/ansible.cfg
ENTRYPOINT /usr/bin/launch_awx_task.sh