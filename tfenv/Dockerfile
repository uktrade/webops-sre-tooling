FROM alpine:3

# Add runtime dependencies
RUN apk add --no-cache bash curl

# Install tfenv
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

# Add and switch to tfuser
RUN addgroup --system tfgroup
RUN adduser --system tfuser --ingroup tfgroup --home /tfuser
USER tfuser

# Set up some directories
RUN mkdir /tfuser/tfenv
RUN mkdir /tfuser/tmp
ENV TFENV_ROOT /usr/local/lib/tfenv
ENV TFENV_CONFIG_DIR /tfuser/tfenv

# Default to latest version of Terraform
ENV TFENV_TERRAFORM_VERSION latest

HEALTHCHECK CMD /usr/local/bin/terraform --version || exit 1

ENTRYPOINT ["/usr/local/bin/terraform"]
