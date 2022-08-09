FROM postgres
COPY postgresql.conf /etc/postgresql/postgresql.conf
COPY ./certs/bookinfo-db.bookinfo-db.svc.cluster.local.crt /etc/db-server-certs/tls.crt 
COPY ./certs/bookinfo-db.bookinfo-db.svc.cluster.local.key /etc/db-server-certs/tls.key
COPY ./certs/bookinfo-db.svc.crt /etc/db-ca-certs/bookinfo-db.svc.crt
RUN chown -R postgres:postgres /etc/db-server-certs/tls.* && chmod og-rwx /etc/db-server-certs/tls.*
RUN chown -R postgres:postgres /etc/db-ca-certs/bookinfo-db.svc.crt && chmod og-rwx /etc/db-ca-certs/bookinfo-db.svc.crt
CMD ["-c", "config_file=/etc/postgresql/postgresql.conf"]