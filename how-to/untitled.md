# Untitled

## How to run superQuery development in VS Code?

Run proxy, serverless-offline and client using the launch.json file

```text
{
    "version": "0.2.0",
    "configurations": [
        {
            "type": "node",
            "request": "launch",
            "name": "Client side",
            "runtimeExecutable": "node",
            "cwd": "${workspaceFolder}",
            "runtimeArgs": [
                "-r",
                "babel-register"
            ],
            "program": "/Users/ebendutoit/Repo/bd/tools/srcServer.js",
            "smartStep": true,
            "console": "integratedTerminal"
        },
        {
            "type": "node",
            "request": "launch",
            "name": "Serverless offline PROD",
            "runtimeExecutable": "node",
            "cwd": "${workspaceFolder}/lambda",
            "runtimeArgs": [
                "-r",
                "babel-register"
            ],
            "program": "/Users/ebendutoit/.nvm/versions/node/v8.9.4/bin/serverless",
            "args": [
                "offline",
                "start",
                "--host",
                "papi.evaluex.io",
                "--noTimeout",
                "true"
            ],
            "env": {
                "x_useProxy" : "true",
                "x_region" : "us-east-1",
                "x_ProxyHost" : "127.0.0.1",
                "x_ProxyPort" : "3307",
                "x_proxyDownloadHost" : "127.0.0.1"
            },
            // "port": 8080,
            "smartStep": true
        },
        {
            "type": "node",
            "request": "launch",
            "name": "Serverless offline DEV",
            "runtimeExecutable": "node",
            "cwd": "${workspaceFolder}/lambda",
            "runtimeArgs": [
                "-r",
                "babel-register"
            ],
            "program": "/Users/ebendutoit/.nvm/versions/node/v8.9.4/bin/serverless",
            "args": [
                "offline",
                "start",
                "--host",
                "papi.evaluex.io",
                "--noTimeout",
                "true"
            ],
            "env": {
                "x_useProxy" : "true",
                "x_region" : "us-west-1",
                "x_ProxyHost" : "127.0.0.1",
                "x_ProxyPort" : "3307",
                "x_proxyDownloadHost" : "127.0.0.1"
            },
            // "port": 8080,
            "smartStep": true
        },
        {
            "type": "node",
            "request": "launch",
            "name": "Proxy local PROD",
            "runtimeExecutable": "node",
            "cwd": "${workspaceFolder}/lambda",
            "runtimeArgs": [
                "-r",
                "babel-register"
            ],
            "program": "/Users/ebendutoit/Repo/bd/tools/proxy/proxy.js",
            "args": [
                "3307",
                "auth-db-prod.cwah65tej36n.us-east-1.rds.amazonaws.com",
                "3306"
            ],
            "env": {
                "x_proxyStatus" : "true",
                "x_proxyAudit" : "true",
                "x_logToBqAudit" : "false",
                "x_region" : "us-east-1",
                "x_LocalSuperQuery" : "true",
                "x_env": "PROD"
            },
            // "port": 8080,
            "smartStep": true
        },
        {
            "type": "node",
            "request": "launch",
            "name": "Proxy local DEV",
            "runtimeExecutable": "node",
            "cwd": "${workspaceFolder}/lambda",
            "runtimeArgs": [
                "-r",
                "babel-register"
            ],
            "program": "/Users/ebendutoit/Repo/bd/tools/proxy/proxy.js",
            "args": [
                "3307",
                "auth-db-dev.cxlnqkdmurlw.us-west-1.rds.amazonaws.com",
                "3306"
            ],
            "env": {
                "x_proxyStatus" : "true",
                "x_proxyAudit" : "true",
                "x_logToBqAudit" : "false",
                "x_region" : "us-west-1",
                "x_LocalSuperQuery" : "true",
                "x_env": "DEV"
            },
            // "port": 8080,
            "smartStep": true
        },
        {
            "type": "node",
            "request": "launch",
            "name": "Launch via NPM",
            "runtimeExecutable": "npm",
            "cwd": "${workspaceFolder}/lambda",
            "runtimeArgs": [
                "!--harmony",
                "!--no-deprecation",
                "run-script",
                "serverless-offline-debug",
            ],
            "env": {
                "x_region" : "us-west-1"
            },
            "port": 9229,
            "smartStep": true,
            "console": "integratedTerminal"
        },
        {
            "type": "node",
            "request": "launch",
            "sourceMaps": true,
            "protocol": "inspector",
            "name": "Run node",
            "program":"${workspaceFolder}/tools/srcServer.js",
            "args":["babel-register","hot"],
            "cwd": "${workspaceRoot}/lambda",
            "port": 9229,
            "smartStep": true,
            "console": "integratedTerminal"
          }
    ],
    "resolveSourceMapLocations": [
        "${workspaceFolder}/**",
        "!**/node_modules/**"
    ]
}
```

you should change the path of the following with your local path:

```text
/Users/ebendutoit/Repo/bd/
and 
/Users/ebendutoit/.nvm/versions/node/v8.9.4/bin
```

Thank you Eben!

