## Init project with Docker
docker compose -f docker-compose-keycloak.yaml up -d


## Stop Container
docker compose -f docker-compose-keycloak.yaml stop

## Delete container
docker compose -f docker-compose-keycloak.yaml down


## Test nodejs client
node src/index.js


### Doc
https://www.keycloak.org/securing-apps/oidc-layers

http://localhost:7080/realms/{realm-name}/.well-known/openid-configuration

## Test Curl

curl -X POST http://127.0.0.1:7080/realms/quickstart/protocol/openid-connect/token \
-H 'content-type: application/x-www-form-urlencoded' \
-d 'client_id=test-cli' \
-d 'username=alice&password=alice&grant_type=password'

curl http://localhost:3000/secured \
  -H "Authorization: Bearer "$access_token