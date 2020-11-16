FROM ansible/awx:15.0.1
COPY settings.py /etc/tower/settings.py
RUN touch /etc/tower/conf.d/environment.sh
CMD /usr/bin/launch_awx_task.sh