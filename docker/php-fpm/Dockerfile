FROM php:8.0.7-fpm

RUN set -ex; \
        \
        # Image build dependencies
        apt update; \
        # Install Xdebug and Redis extension
        pecl install xdebug-2.9.8; \
        pecl install redis; \
        docker-php-ext-enable xdebug redis; \
        # Install PDO extension
        docker-php-ext-install pdo pdo_mysql

# Install, enable and configure Xdebug
RUN { \
	echo 'log_errors = On'; \
	echo 'error_log = /dev/stderr'; \
	echo 'xdebug.idekey = ${PHP_XDEBUG_IDEKEY}'; \
	echo 'xdebug.profiler_enable = ${PHP_XDEBUG_PROFILE_ENABLE}'; \
	echo 'xdebug.profiler_output_dir = /app/xdebug/profiler'; \
	echo 'xdebug.profiler_output_name = cachegrind.out.%R-%u'; \
	echo 'xdebug.remote_autostart = On'; \
	echo 'xdebug.remote_enable = ${PHP_XDEBUG_REMOTE_ENABLE}'; \
	echo 'xdebug.remote_handle = dbgp'; \
	echo 'xdebug.remote_log = /tmp/xdebug.log'; \
	echo 'xdebug.remote_host = ${PHP_XDEBUG_REMOTE_HOST}'; \
	echo 'xdebug.remote_port = 9000'; \
	echo 'xdebug.auto_trace = ${PHP_XDEBUG_AUTO_TRACE}'; \
	echo 'xdebug.trace_format = 1'; \
	echo 'xdebug.trace_output_dir = /app/xdebug/trace'; \
	echo 'xdebug.trace_output_name = trace.out.%R-%u'; \
	echo 'xdebug.max_nesting_level = ${PHP_XDEBUG_MAX_NESTING_LEVEL}'; \
} > /usr/local/etc/php/conf.d/xdebug.ini

WORKDIR /app
