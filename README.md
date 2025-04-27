## 本地開發用docker

## 啟動mariadb
```bash
docker compose -f docker-compose.db.yml up -d   
```

## 啟動php
```bash
docker compose -f docker-compose.php.yml up -d   
```

## 啟動nginx
```bash
docker compose -f docker-compose.nginx.yml up -d   
```

## 其他
1.nginx 的 server_name *.hryinfo.site; 網域到期後可能需要做變更

## 待處理
1. 設置.env, 加入環境變數, 以便後續不同環境建置
2. nginx設定嘗試加入ssl