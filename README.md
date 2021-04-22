# docker

### 生成证书
```
docker run -it --rm --name certbot \
    -v "/certbot/etc/letsencrypt:/etc/letsencrypt" \
    -v "/certbot/var/lib/letsencrypt:/var/lib/letsencrypt" \
    certbot/certbot certonly --manual \
    --preferred-challenges dns \
    --server https://acme-v02.api.letsencrypt.org/directory
```