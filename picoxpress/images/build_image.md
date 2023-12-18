Generate APPS JSON 64
```shell
export APPS_JSON_BASE64=$(base64 picoxpress/apps.json)
```

Build Image
```shell
docker build \
  --build-arg=FRAPPE_PATH=https://github.com/frappe/frappe \
  --build-arg=FRAPPE_BRANCH=version-14 \
  --build-arg=PYTHON_VERSION=3.10.12 \
  --build-arg=NODE_VERSION=16.20.1 \
  --build-arg=APPS_JSON_BASE64=$APPS_JSON_BASE64 \
  --tag=picoxpresscr.azurecr.io/px-erp-next:v0 \
  --file=picoxpress/images/px-erp-next/Containerfile .
```
