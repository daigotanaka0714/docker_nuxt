## How I create nuxt project with docker
- touch docker-compose.yml
- touch Dockerfile
```bash
$ docker compose up
$ docker compose run --rm app[it should be SERVICE name] /bin/sh
$ yarn create nuxt-app . --overwrite-dir
 ```
...and Generate your nuxt app!!


## Opps something wrong?
### nodejs 17: digital envelope routines::unsupported
```bash
Error: error:0308010C:digital envelope routines::unsupported
    at new Hash (node:internal/crypto/hash:67:19)
    at Object.createHash (node:crypto:130:10)
    at module.exports (/src/node_modules/webpack/lib/util/createHash.js:135:53)
    at NormalModule._initBuildHash (/src/node_modules/webpack/lib/NormalModule.js:417:16)
    at handleParseError (/src/node_modules/webpack/lib/NormalModule.js:471:10)
    at /src/node_modules/webpack/lib/NormalModule.js:503:5
    at /src/node_modules/webpack/lib/NormalModule.js:358:12
    at /src/node_modules/loader-runner/lib/LoaderRunner.js:373:3
    at iterateNormalLoaders (/src/node_modules/loader-runner/lib/LoaderRunner.js:214:10)
    at Array.<anonymous> (/src/node_modules/loader-runner/lib/LoaderRunner.js:205:4)
    at Storage.finished (/src/node_modules/enhanced-resolve/lib/CachedInputFileSystem.js:55:16)
    at /src/node_modules/enhanced-resolve/lib/CachedInputFileSystem.js:91:9
    at /src/node_modules/graceful-fs/graceful-fs.js:123:16
    at FSReqCallback.readFileAfterClose [as oncomplete] (node:internal/fs/read_file_context:68:3) {
  opensslErrorStack: [ 'error:03000086:digital envelope routines::initialization error' ],
  library: 'digital envelope routines',
  reason: 'unsupported',
  code: 'ERR_OSSL_EVP_UNSUPPORTED'
}
```
so I add this line to your docker-compose.yml(environment)

`NODE_OPTIONS=--openssl-legacy-provider`
- for more information : https://github.com/webpack/webpack/issues/14532