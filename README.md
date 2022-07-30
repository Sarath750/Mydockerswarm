# mydockerswarm

vi nginx-stack.yml
------------------
 ---
version: '3.9'
services:
  nginx-deploy:
    image: nginx
    deploy:
      replicas: 4
      resources:
        limits:
          cpus: '0.50'
          memory: '512M'
      placement:
        constraints: [node.role == manager]
    ports:
    - "80:80"
    networks:
    - nginx-network
networks:
  nginx-network:
    driver: overlay
