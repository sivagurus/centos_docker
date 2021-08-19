FROM centos:7

RUN yum install pcre pcre-devel openssl openssl-devel zlib zlib-devel -y
RUN yum install -y wget sed
RUN wget http://nginx.org/download/nginx-1.9.7.tar.gz
RUN wget https://github.com/arut/nginx-rtmp-module/archive/refs/tags/v1.2.2.zip
RUN tar -xvf nginx-1.9.7.tar.gz
RUN yum update -y
RUN yum groupinstall "Development Tools" -y
RUN unzip v1.2.2.zip
RUN cd nginx-1.9.7 && ./configure --add-module=../nginx-rtmp-module-1.2.2/ && make && make install
RUN yum install epel-release -y
RUN yum update -y
RUN yum localinstall --nogpgcheck https://download1.rpmfusion.org/free/el/rpmfusion-free-release-7.noarch.rpm -y
RUN yum install ffmpeg ffmpeg-devel -y
CMD ["/usr/local/nginx/sbin/nginx", "-g", "daemon off;"]
