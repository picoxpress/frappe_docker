Generate APPS JSON 64
```shell
export APPS_JSON_BASE64=$(base64 picoxpress/apps.json)
```

Build Image
```shell
docker build \
  --build-arg=FRAPPE_PATH=https://github.com/picoxpress/frappe.git \
  --build-arg=FRAPPE_BRANCH=version-14-postgres \
  --build-arg=PYTHON_VERSION=3.11.6 \
  --build-arg=NODE_VERSION=18.18.2 \
  --build-arg=APPS_JSON_BASE64=$APPS_JSON_BASE64 \
  --tag=picoxpresscr.azurecr.io/px-erp-next:<tag> \
  --file=picoxpress/images/px-erp-next/Containerfile .
```

Build Image on OSX
```shell
docker build \
  --build-arg=FRAPPE_PATH=https://github.com/picoxpress/frappe.git \
  --build-arg=FRAPPE_BRANCH=version-14-postgres \
  --build-arg=PYTHON_VERSION=3.11.6 \
  --build-arg=NODE_VERSION=18.18.2 \
  --build-arg=APPS_JSON_BASE64=$APPS_JSON_BASE64 \
  --build-arg CACHEBUST=$(date +%s) \
  --tag=picoxpresscr.azurecr.io/px-erp-next:<tag> \
  --platform linux/amd64 \
  --file=picoxpress/images/px-erp-next/Containerfile .
```
