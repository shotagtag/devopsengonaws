FROM public.ecr.aws/ubuntu/ubuntu:18.04

# Install dependencies
RUN apt-get update
RUN apt-get -y install apache2

RUN echo '<html><head><title>Hello World</title></head><body><h1>Hello World!</h1></body></html>' > /var/www/html/index.html

# Configure apache
RUN echo '. /etc/apache2/envvars' > /root/run_apache.sh && \
 echo 'mkdir -p /var/run/apache2' >> /root/run_apache.sh && \
 echo 'mkdir -p /var/lock/apache2' >> /root/run_apache.sh && \ 
 echo '/usr/sbin/apache2 -D FOREGROUND' >> /root/run_apache.sh && \ 
 chmod 755 /root/run_apache.sh

EXPOSE 80

CMD /root/run_apache.sh
