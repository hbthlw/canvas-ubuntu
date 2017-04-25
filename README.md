# canvas-ubuntu
Node.js中Canvas库所使用的依赖环境

# How to use
在工作目录中默认使用npm start启动，需要安装依赖可以先使用docker run进行npm install

建议使用pm2-docker app.js启动应用

示例与参考：http://pm2.keymetrics.io/docs/usage/docker-pm2-nodejs/

docker run \
  -d \
  --rm \
  -e "PORT=3000" \
  -e "NODE_ENV=production" \
  -e "DEBUG=server" \
  -u "node" \
  -m "300M" \
  --memory-swap "1G" \
  -p "5002:3000" \
  --cpuset-cpus "0-3" \
  --restart "always" \
  -w "/usr/src/app" \
  --volume "$(pwd):/usr/src/app" \
  --name "webapp" \
  hbthlw/canvas-ubuntu:2.0 \
  pm2-docker server.js
  
  
# swap大小如何确定

根据centos官网介绍可以得出如下公式：

M = Amount of RAM in GB, and S = Amount of swap in GB, then If M < 2, S = M *2 Else S = M + 2

而且其最小不应该小于32M(never less than 32 MB.)
