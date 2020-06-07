FROM debian
ADD debian.list /etc/apt/sources.list.d/
RUN apt-get update && apt-get -y upgrade && apt -y install nginx && apt-get clean && \
    cd /var/www/ && rm -rf ./* && \
    mkdir -p vladchegadaev.com/img && \
    chmod -R 754 /var/www/vladchegadaev.com/ && \
    useradd Vlad && groupadd Chegadaev && usermod -aG Vlad Chegadaev && \
    chown -R Vlad:Chegadaev /var/www/vladchegadaev.com/ && \
    sed -i 's/\/var\/www\/html/\/var\/www\/vladchegadaev.com/g' /etc/nginx/sites-enabled/default && \
    sed -i 's/user www-data/user Vlad/g' /etc/nginx/nginx.conf
ADD index.html /var/www/chegadaevvlad.com/
ADD img.jpg /var/www/vladchegadaev.com/img/
CMD ["nginx", "-g", "daemon off;"]