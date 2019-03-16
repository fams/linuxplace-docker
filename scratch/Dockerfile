FROM ubuntu:16.04
LABEL mantainer=fams@linuxplace.com.br
COPY ./docker/ /var/www/html
EXPOSE 80
RUN apt-get update -y && apt-get install --no-install-recommends python3 -y
WORKDIR  /var/www/html
ENTRYPOINT [ "python3", "-m", "http.server", "80" ]
