# docker


### 刷新所有容器
`docker-compose up -d --build`

### 生成证书
```
docker run -it --rm --name certbot \
    -v "./data/certbot/etc/letsencrypt:/etc/letsencrypt" \
    -v "./data/certbot/var/lib/letsencrypt:/var/lib/letsencrypt" \
    certbot/certbot certonly --manual \
    --preferred-challenges dns \
    --server https://acme-v02.api.letsencrypt.org/directory
```