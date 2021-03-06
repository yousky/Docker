# Node Inspector Dockerfile

Default Expose Port : 8080

## Usage

Mount the host node app directory to `/home/node/app`.

example host app directory : ~/nodeinsp

example start script : ~/nodeinsp/index.js

The following example equal "node-debug ~/nodeinsp/index.js".
```yml

docker run --name nodeinsp -v ~/nodeinsp:/home/node/app -d yousky/nodeinspector:0.12.8-20170214-node4.7.3 /home/node/app/index.js

```


The following example equal "node-debug --web-host=null --debug-brk ~/nodeinsp/index.js". 
```yml

docker run --name nodeinsp -v ~/nodeinsp:/home/node/app -p 8080:8080 -d yousky/nodeinspector:0.12.8-20170214-node4.7.3 --web-host=null --debug-brk /home/node/app/index.js

```


If you need npm install, you need to install it in the following way.
```yml

docker run -it --name nodeinspset -v ~/nodeinsp:/home/node/app -d yousky/nodeinspector:0.12.8-20170214-node4.7.3
docker exec -it nodeinspset bash
cd /home/node/app
npm install
chown -R node:node ../app/
chmod -R g+w ../app/
exit

docker stop nodeinspset
docker rm nodeinspset

```


Access Node Inspector on http://xxx.xxx.xxx.xxx:8080/?port=5858

See also [Node Inspector](https://github.com/node-inspector/node-inspector).

## License
Released under the [MIT license](http://opensource.org/licenses/MIT).
