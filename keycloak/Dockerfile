# Mark L.

FROM quay.io/keycloak/keycloak:latest as builder

ENV KC_HEALTH_ENABLED=true
ENV KC_METRICS_ENABLED=true
ENV KC_DB=postgres
ENV KC_HTTP_ENABLED=false
ENV KC_HOSTNAME_STRICT=true
ENV KC_HOSTNAME_STRICT_HTTPS=true

RUN /opt/keycloak/bin/kc.sh build

FROM quay.io/keycloak/keycloak:latest

COPY --from=builder /opt/keycloak/ /opt/keycloak/

USER 1000

EXPOSE 8443 # Default port for Keycloak HTTPS

ENTRYPOINT ["/opt/keycloak/bin/kc.sh"]
CMD ["start", "--optimized"]
