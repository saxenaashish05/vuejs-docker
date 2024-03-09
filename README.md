# vuejs-docker

Added by Ashish Kumar Saxena
# Folder Structure

```
├── compose.yaml
├── README.md
└── vuejs
    ├── babel.config.js
    ├── Dockerfile
    ├── node_modules
    ├── package.json
    ├── public
    │   └── index.html
    ├── src
    │   ├── App.vue
    │   ├── assets
    │   │   └── logo.png
    │   ├── components
    │   │   └── User.vue
    │   └── main.js
    └── yarn.lock
```
# Deploy with docker compose
```
docker compose up -d --build

docker compose up -d
[+] Running 1/2
 ⠸ Network clarivate-fe_default  Created                                                                                                        14.3s 
 ✔ Container clarivate-fe-web-1  Started                                                                                                        14.0s 
```
