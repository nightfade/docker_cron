FROM sameersbn/postgresql:9.6-2

# Add crontab file in the cron directory
ADD crontab /etc/cron.d/hello-cron

# Add scripts
RUN mkdir /root/scripts
ADD scripts /root/scripts

# Give execution reights on the cron job
RUN chmod 0644 /etc/cron.d/hello-cron

# Create the log file to be able to run tail
RUN touch /var/log/cron.log
RUN mkdir -p /var/pgsql-backups

# Install cron
RUN apt-get update -y
RUN apt-get -y install cron curl vim

# Run the command on container startup
CMD cron && tail -f /var/log/cron.log