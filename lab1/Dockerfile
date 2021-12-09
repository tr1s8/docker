FROM debian:stretch
RUN apt update && apt install apt-transport-https -y
RUN echo "deb https://ftp.ru.debian.org/debian/ stretch main contrib non-free " > /etc/apt/sources.list.d/repo.list
RUN apt-get update && apt-get install nginx -y && apt-get clean
RUN rm -rf /var/www/* && mkdir -p /var/www/company.com/img
COPY index.html /var/www/company.com/
COPY img.jpg /var/www/company.com/
RUN chmod -R 754 /var/www/
RUN useradd avdushkin 
RUN sed -i 's#/var/www/html#/var/www/company.com#g' /etc/nginx/sites-enabled/default && sed -i 's#user www-data#user avdushkin#g' /etc/nginx/nginx.conf
RUN chmod -R 754 /var/www/ && chown -R avdushkin:avdushkin  /var/www/
CMD ["nginx", "-g", "daemon off;"]
