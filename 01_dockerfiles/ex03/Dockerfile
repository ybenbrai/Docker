FROM ubuntu

EXPOSE 443 80 22
RUN apt-get update && apt-get upgrade -y
RUN apt-get install ca-certificates openssh-server wget -y
RUN wget https://packages.gitlab.com/install/repositories/gitlab/gitlab-ce/script.deb.sh && chmod 777 script.deb.sh && ./script.deb.sh && apt-get install -y gitlab-ce

EXPOSE 443 80 22

RUN apt-get install tzdata -y
RUN apt-get clean
RUN rm -rf /var/lib/apt/lists/ */tmp/* /var/tmp/*
WORKDIR /etc/gitlab
RUN echo "external_url 'https://10.11.2.15'" > gitlab.rb
RUN echo "nginx['enable'] = true" >> gitlab.rb
RUN echo "nginx['redirect_http_htpps'] = true" >> gitlab.rb
RUN echo "nginx['redirect_http_htpps_port'] = 80" >> gitlab.rb
RUN echo "letsencrypt['enable'] = false" >> gitlab.rb
RUN echo "nginx['ssl_certificate'] = \"/etc/gitlab/ssl/gitlab.crt\"" >> gitlab.rb
RUN echo "nginx['ssl_certificate_key'] = \"/etc/gitlab/ssl/gitlab.key\"" >> gitlab.rb
RUN echo "gitlab_rails['gitlab_shell_ssh_port'] = 22" >> gitlab.rb
RUN mkdir /etc/gitlab/ssl
RUN openssl req -x509 -nodes -days 365 -newkey rsa:2048 \
-subj "/C=MA/ST=0/L=Khouribga/0=rs1/OU=rs1/CN=10.11.2.15/emailAddress=benbraitit@gmail.com" \
-keyout /etc/gitlab/ssl/gitlab.key -out /etc/gitlab/ssl/gitlab.crt
RUN export GIT_SSL_NO_VERIFY=1
RUN echo "service ssh start" > script.sh
RUN echo "(/opt/gitlab/embedded/bin/runsvdir-start &) && gitlab-ctl reconfigure && tail -f /dev/null" >> script.sh
RUN chmod 700 script.sh
ENTRYPOINT ./script.sh
#docker run -it -p 10.11.2.15:443:443 -p 10.11.2.15:80:80 -p 10.11.2.15:22:22 gitlab_ex03
