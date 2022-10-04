FROM nginxinc/nginx-unprivileged:1-alpine
LABEL maintaner="kbradsha@gmail.com"

COPY ./default.conf.tpl /etc/nginx/default.conf.tpl
COPY ./uwsgi_params /etc/nginx/uwsgi_params
COPY ./run.sh /run.sh

ENV LISTEN_PORT=8000
ENV APP_HOST=app
ENV APP_PORT=9000

user root

RUN mkdir -p /home/kbradsha/workspace/recipe-app-api/vol/static && \
	chmod 755 /home/kbradsha/workspace/recipe-app-api/vol/static && \
	touch /etc/nginx/conf.d/default.conf && \
	chown nginx:nginx /etc/nginx/conf.d/default.conf && \
	chmod +x /run.sh

VOLUME /home/kbradsha/workspace/recipe-app-api/vol/static

USER nginx

CMD ["/run.sh"]
