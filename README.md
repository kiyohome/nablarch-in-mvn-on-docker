# nablarch-in-mvn-on-docker

## Tools

- [Apache Maven](http://maven.apache.org/)
- Dependencies
  - [nablarch-example-web](https://github.com/nablarch/nablarch-example-web)
  - [nablarch-example-rest](https://github.com/nablarch/nablarch-example-rest)
  - [nablarch-example-batch-ee](https://github.com/nablarch/nablarch-example-batch-ee)

## How to build image


- clone the repository

```
  $ git clone https://github.com/kiyohome/redmine-in-mvn-on-docker.git
```

- set the proxy settings, if in proxy

```
  5u9/settings.xml
```

- build the image

  - in proxy

    ```
      $ cd 5u9/
      $ docker build -t nablarch/maven:5u9 --build-arg http_proxy=http://sample.com:80 .
    ```
  - no proxy

    ```
      $ cd 5u9/
      $ docker build -t nablarch/maven:5u9 .
    ```
