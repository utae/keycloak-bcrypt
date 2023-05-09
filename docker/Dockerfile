FROM quay.io/keycloak/keycloak:21.1.1 as builder

COPY ./keycloak-bcrypt-1.5.3.jar /opt/keycloak/providers/

ENV KC_HEALTH_ENABLED=true
ENV KC_METRICS_ENABLED=true
ENV KC_DB=mysql
ENV KC_HTTP_RELATIVE_PATH=/keycloak

RUN /opt/keycloak/bin/kc.sh build

FROM quay.io/keycloak/keycloak:21.1.1

COPY --from=builder /opt/keycloak/ /opt/keycloak/

ENTRYPOINT ["/opt/keycloak/bin/kc.sh"]
