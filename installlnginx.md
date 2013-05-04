## nginx configuration
To get the correct routing added when add this to your config /etc/nginx/sites-enabled/default
You might need to adjust to your path if not running in the subdirectory /emoncms/

    server {
        location /emoncms/ {
            index index.php;
            try_files $uri $uri/ /emoncms/index.php?q=$uri&$args;
        }
    }
