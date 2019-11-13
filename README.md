# saml-reverse-proxy
Protecting internal applications with a SAML-aware reverse-proxy 

## How to use?

`shell
# docker build -t saml-reverse-proxy
docker run \
    -it \
    -p 80:80 \
    -p 443:443 \
    -e OMAIN=www.example.com \
    -e IDP_ENTITY_ID=aws-elasticsearch \
    -e SAML_METADATA_URL=https://example.com/FederationMetadata/2007-06/FederationMetadata.xml \
    -e PROXY_REMOTE_URL=http://elasticsearch.example.com/_plugin/kibana \
    -e CERTBOT_EMAIL=xxx@example.com \
    saml-reverse-proxy
`
NOTE: PROXY_REMOTE_URL do not support https address, if you want to set a reverse proxy to a https address, you must make sure the ssl certificates on this proxy is the same as the remote url