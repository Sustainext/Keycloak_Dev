FROM quay.io/keycloak/keycloak:24.0.4 AS builder

WORKDIR /opt/keycloak


RUN /opt/keycloak/bin/kc.sh build --db=postgres


FROM quay.io/keycloak/keycloak:24.0.4
COPY --from=builder /opt/keycloak/ /opt/keycloak/


ENV KC_HTTP_ENABLED=true
ENV KC_PROXY_HEADERS=xforwarded


EXPOSE 8080

ENTRYPOINT ["/opt/keycloak/bin/kc.sh", "start"]