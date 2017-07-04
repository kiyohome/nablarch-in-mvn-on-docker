FROM maven

ENV http_proxy $http_proxy
ENV https_proxy $http_proxy

ARG NABLARCH_VERSION=5u10

ADD settings.xml /root/
ADD web-pom.xml /root/

RUN mkdir root/work \
    && cd root/work \
    && git clone -b $NABLARCH_VERSION https://github.com/nablarch/nablarch-example-web.git \
    && cd nablarch-example-web \
    && cp -f /root/web-pom.xml pom.xml \
    && mvn -P gsp generate-resources -s ~/settings.xml \
    && mvn clean compile -s ~/settings.xml \
    && mvn clean verify sonar:sonar -s ~/settings.xml \
    && mvn waitt:jar -s ~/settings.xml \
    && cd .. \
    && git clone -b $NABLARCH_VERSION https://github.com/nablarch/nablarch-example-rest.git \
    && cd nablarch-example-rest \
    && mvn -P gsp generate-resources -s ~/settings.xml \
    && mvn clean compile -s ~/settings.xml \
    && cd .. \
    && git clone -b $NABLARCH_VERSION https://github.com/nablarch/nablarch-example-batch-ee.git \
    && cd nablarch-example-batch-ee \
    && mvn -P gsp generate-resources -s ~/settings.xml \
    && mvn clean package -s ~/settings.xml \
    && cd ../.. \
    && rm -r work/ \
    && rm settings.xml \
    && find /usr/share/maven/ref/repository -name _remote.repositories | xargs rm
