# WebServer Docker Stack

A production-ready Docker stack optimized for modern web applications, featuring PHP 8.2, Nginx, and a complete development environment with full service integration.

## Stack Components

### Core Services
* [`php:8.2-fpm`](docker/php/Dockerfile)
    - Latest Composer
    - Essential PHP Extensions
    - Development Tools
* [`nginx:stable-alpine`](docker/nginx/conf.d/default.conf)
    - Optimized for PHP-FPM
    - SSL/TLS Ready
    - Performance Tuned

## Quick Start

```bash
# Clone repository
git clone https://github.com/Enesbasduvar/docker-images-main.git
cd WebServer

# Start services
docker-compose up -d
```

## Directory Structure

```plaintext
WebServer/
├── docker/
│   ├── nginx/
│   │   ├── conf.d/
│   │   │   └── default.conf
│   │   └── logs/
│   └── php/
│       ├── Dockerfile
│       └── conf.d/
├── www/
│   └── index.php
└── docker-compose.yml
```

## Configuration

### Environment Requirements
- Docker Engine 20.10+
- Docker Compose 2.0+
- Git

### Service Management
```bash
# Start services
docker-compose up -d

# Stop services
docker-compose down

# View logs
docker-compose logs -f

# Rebuild containers
docker-compose up -d --build
```

## Features

### PHP Configuration
- Custom PHP extensions
- Optimized for performance
- Production-ready settings

### Nginx Setup
- FastCGI caching
- Gzip compression
- Security headers
- SSL/TLS ready

### Development Tools
- Composer
- Git integration
- Development utilities

## Volume Mappings

| Local Path | Container Path | Purpose |
|------------|---------------|----------|
| `./www` | `/usr/share/nginx/html` | Web root |
| `./docker/nginx/conf.d` | `/etc/nginx/conf.d` | Nginx config |
| `./docker/nginx/logs` | `/var/log/nginx` | Nginx logs |

## Port Mappings

| Service    | Port | Protocol |
|------------|------|----------|
| Nginx      | 80   | HTTP |
| Nginx      | 443  | HTTPS |
| PHP-FPM    | 9000 | FastCGI |
| PhpMyAdmin | 8080 | HTTP |

## Developer Guide

### Adding PHP Extensions
```dockerfile
# In docker/php/Dockerfile
RUN docker-php-ext-install \
    pdo_mysql \
    mbstring \
    exif \
    pcntl \
    bcmath \
    gd
```

### Custom Nginx Configuration
```nginx
# In docker/nginx/conf.d/default.conf
server {
    listen 80;
    server_name localhost;
    root /usr/share/nginx/html;
    # ... additional configuration
}
```

## Security Considerations

### Production Deployment
- Configure SSL certificates
- Set secure PHP settings
- Implement rate limiting
- Enable security headers

### Best Practices
- Regular security updates
- Proper file permissions
- Environment variable usage
- Secure communication

## Troubleshooting

### Common Issues

1. **404 Not Found**
   ```bash
   # Check nginx configuration
   docker-compose exec nginx nginx -t
   ```

2. **Permission Denied**
   ```bash
   # Set proper permissions
   chmod -R 755 www/
   chown -R $USER:$USER www/
   ```

3. **PHP-FPM Connection Failed**
   ```bash
   # Verify PHP-FPM status
   docker-compose exec php ps aux | grep php-fpm
   ```

## Contributing

1. Fork the repository
2. Create feature branch (`git checkout -b feature/AmazingFeature`)
3. Commit changes (`git commit -m 'Add AmazingFeature'`)
4. Push to branch (`git push origin feature/AmazingFeature`)
5. Open Pull Request

## Performance Optimization

### Nginx Tuning
- Worker processes optimization
- Buffer size configuration
- Keep-alive settings
- Caching strategies

### PHP-FPM Optimization
- Process manager configuration
- Memory limits
- Opcache settings
- Session handling

## Monitoring & Logging

### Log Management
- Structured logging
- Log rotation
- Error tracking
- Access monitoring

### Performance Metrics
- Resource usage
- Response times
- Error rates
- Cache hit rates

## License

This project is licensed under the MIT License - see the [LICENSE](LICENSE) file for details.



## Version History

- 1.0.0
    - Initial release
    - Basic stack setup
- 1.1.0
    - Performance improvements
    - Security enhancements

## Acknowledgments

- PHP Development Team
- Nginx Development Team
- Docker Community
- Open Source Contributors

[1]: https://github.com/[username]/WebServer/docs
[2]: https://github.com/[username]/WebServer/wiki
[3]: https://github.com/[username]/WebServer/wiki/FAQ
[4]: https://github.com/[username]/WebServer/issues
[5]: https://github.com/[username]/WebServer/discussions
[6]: https://discord.gg/[invite-code]

---
**Note**: This stack is actively maintained and regularly updated with security patches and feature enhancements.
