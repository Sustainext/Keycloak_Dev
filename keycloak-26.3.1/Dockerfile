FROM eclipse-temurin:17-jdk
 
WORKDIR /opt/keycloak
 
COPY . .
 
ENV PATH="/opt/keycloak/bin:$PATH"
 


# ✅ Build-time configs
ENV KC_DB=postgres
ENV KC_HTTP_RELATIVE_PATH=/


# Build Keycloak for production mode
# RUN kc.sh build --db=postgres
RUN kc.sh build  
 
EXPOSE 8080
# Start in production mode using PostgreSQL
CMD kc.sh start --optimized \
#   --db=postgres \
  --db-url-host=$DBHOST \
  --db-url-database=$DBNAME \
  --db-username=$DBUSER \
  --db-password=$DBPASS \
  --hostname=$HOSTNAME \
  --hostname-strict=false \
  --http-enabled=true \
  --http-port=8080 


# CMD kc.sh start --optimized \
#   --db-url-host=postgres \
#   --db-url-database=$DBNAME \
#   --db-username=$DBUSER \
#   --db-password=$DBPASS \
#   --hostname-strict=false \
#   --http-enabled=true \
#   --http-port=8080
 