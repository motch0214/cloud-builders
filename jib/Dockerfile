FROM gcr.io/cloud-builders/gradle

RUN apt-get update -y && apt-get install -y curl \
  && curl -O https://dl.google.com/go/go1.13.4.linux-amd64.tar.gz \
  && tar xf go1.13.4.linux-amd64.tar.gz \
  && mv go /usr/local \
  && export PATH=$PATH:/usr/local/go/bin \
  && go get -u github.com/awslabs/amazon-ecr-credential-helper/ecr-login/cli/docker-credential-ecr-login \
  && mkdir -p ~/.docker \
  && echo '{ "credsStore": "ecr-login" }' > ~/.docker/config.json

ENV PATH $PATH:/root/go/bin

ENTRYPOINT ["/usr/bin/gradle"]
