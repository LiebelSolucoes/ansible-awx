FROM ansible/awx:15.0.1
USER root
COPY settings.py /etc/tower/settings.py
RUN mkdir -p /etc/tower/conf.d
RUN touch /etc/tower/conf.d/environment.sh
CMD /usr/bin/launch_awx_task.sh