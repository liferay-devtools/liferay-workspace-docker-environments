FROM mysql:8.4.5-oracle

RUN touch /startup_log.txt
RUN chown mysql:mysql /startup_log.txt
RUN sed -i -E 's,(^\s*printf .*$),\1 | tee -a /startup_log.txt,' /usr/local/bin/docker-entrypoint.sh
RUN sed -i -E 's,(^\s*)(exec "\$@"),\1mysql_note "STARTING_UP"\n\1\2,' /usr/local/bin/docker-entrypoint.sh

CMD ["mysqld", "--character-set-server=utf8mb4", "--collation-server=utf8mb4_general_ci"]

COPY *.cnf /etc/mysql/conf.d/