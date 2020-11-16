FROM ansible/awx:15.0.1
COPY settings.py /etc/tower/settings.py
COPY nginx.conf /etc/nginx/nginx.conf
CMD /usr/bin/launch_awx.sh