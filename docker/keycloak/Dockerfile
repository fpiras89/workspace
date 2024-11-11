FROM quay.io/keycloak/keycloak:26.0 AS builder

# Enable health and metrics support
ENV KC_HEALTH_ENABLED=true
ENV KC_METRICS_ENABLED=true

# Enable features
ENV KC_FEATURES="opentelemetry"

# Configure a database vendor
ENV KC_DB=mssql

# Configure relative path for HTTP endpoints
ENV KC_HTTP_RELATIVE_PATH=/auth

WORKDIR /opt/keycloak

# Add custom SPIs
COPY keycloak/keycloak-metrics-spi-7.0.0.jar /opt/keycloak/providers/

# for demonstration purposes only, please make sure to use proper certificates in production instead
RUN keytool -genkeypair -storepass password -storetype PKCS12 -keyalg RSA -keysize 2048 -dname "CN=server" -alias server -ext "SAN:c=DNS:localhost,IP:127.0.0.1" -keystore conf/server.keystore

RUN /opt/keycloak/bin/kc.sh build

FROM quay.io/keycloak/keycloak:26.0
COPY --from=builder /opt/keycloak/ /opt/keycloak/

ENTRYPOINT ["/opt/keycloak/bin/kc.sh"]