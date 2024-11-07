# Mark L.

FROM quay.io/keycloak/keycloak:latest as builder

ENV KC_HEALTH_ENABLED=true
ENV KC_METRICS_ENABLED=true
ENV KC_DB=postgres

RUN /opt/keycloak/bin/kc.sh build

FROM quay.io/keycloak/keycloak:latest
COPY --from=builder /opt/keycloak/ /opt/keycloak/
# COPY themes /opt/keycloak/themes/ # Include themes if you have any. The volume is built in the compose

# RUN chown -R 1000:1000 /opt/keycloak # Set permissions for OpenShift compatibility (if needed)

ENTRYPOINT ["/opt/keycloak/bin/kc.sh"]
