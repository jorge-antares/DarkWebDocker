## App docker container
Run it using
```
docker run -p 5000:5000 darksite_1
```
and should be visible at `http://localhost:5000`.

## Create private key for Tor service
1. Mount volume at `docker-compose.yaml`:
```
volumes:
  - ./hidden_service:/var/lib/tor/hidden_service
```
2. Start Tor service only
```
docker-compose up tor
```
3. After a few seconds, stop container:
```
docker-compose down
```
4. Convert generated key to Base64-encoding:
```
base64 -i hidden_service/service1/hs_ed25519_secret_key
```
5. Optionally, copy the output and past it in `SERVICE1_TOR_SERVICE_KEY` in `docker-compose.yaml`.
