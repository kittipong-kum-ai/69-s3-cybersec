FROM prawee/strapi:latest

USER root
RUN set -eux; \
    mkdir -p /tmp/smtp-install /opt/node_modules/@strapi; \
    cd /tmp/smtp-install; \
    npm pack @strapi/provider-email-nodemailer@4.16.2 --silent; \
    tar -xzf strapi-provider-email-nodemailer-*.tgz; \
    cp -r package /opt/node_modules/@strapi/provider-email-nodemailer; \
    npm pack nodemailer@6 --silent; \
    tar -xzf nodemailer-*.tgz; \
    cp -r package /opt/node_modules/nodemailer; \
    rm -rf /tmp/smtp-install; \
    node -e "require('/opt/node_modules/@strapi/provider-email-nodemailer'); console.log('provider-email-nodemailer OK')"
USER node