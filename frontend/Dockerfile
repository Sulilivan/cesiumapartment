# 基于官方 Node 镜像
FROM node:20

# 设置工作目录
WORKDIR /app

# 复制 package.json 和 package-lock.json
COPY package*.json ./

# 安装依赖
RUN npm install

# 复制所有前端代码
COPY . .

# 构建静态资源（如需生产环境部署）
RUN npm run build

# 启动静态服务器（如需预览生产包）
# 可选：安装 serve
RUN npm install -g serve

# 默认启动开发服务器（如需开发环境）
CMD ["serve", "-s", "dist"]
