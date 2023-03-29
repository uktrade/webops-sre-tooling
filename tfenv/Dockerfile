# This is mostly a lift from https://github.com/tfutils/tfenv/blob/master/Dockerfile, but based on Alpine

FROM alpine:3

# Add runtime dependencies
RUN apk add --no-cache bash curl

ARG TFENV_VERSION=3.0.0
RUN wget -O /tmp/tfenv.tar.gz "https://github.com/tfutils/tfenv/archive/refs/tags/v${TFENV_VERSION}.tar.gz" \
    && tar -C /tmp -xf /tmp/tfenv.tar.gz \
    && mv "/tmp/tfenv-${TFENV_VERSION}/bin"/* /usr/local/bin/ \
    && mkdir -p /usr/local/lib/tfenv \
    && mv "/tmp/tfenv-${TFENV_VERSION}/lib" /usr/local/lib/tfenv/ \
    && mv "/tmp/tfenv-${TFENV_VERSION}/libexec" /usr/local/lib/tfenv/ \
    && mkdir -p /usr/local/share/licenses \
    && mv "/tmp/tfenv-${TFENV_VERSION}/LICENSE" /usr/local/share/licenses/tfenv \
    && rm -rf /tmp/tfenv* \
    ;
ENV TFENV_ROOT /usr/local/lib/tfenv

ENV TFENV_CONFIG_DIR /var/tfenv
VOLUME /var/tfenv

# Default to latest; user-specifiable
ENV TFENV_TERRAFORM_VERSION latest

HEALTHCHECK CMD /usr/local/bin/terraform --version || exit 1

ENTRYPOINT ["/usr/local/bin/terraform"]
