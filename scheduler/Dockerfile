FROM rails:4

RUN apt-get update && apt-get install -yqq --no-install-recommends \
    git \
    cron \
    supervisor \
    && gem install bundler \
    && apt-get clean autoclean && apt-get autoremove -y

RUN git clone git://github.com/madebyhiro/codem-schedule.git \
    && cd codem-schedule \
    && bundle install

COPY crontab.txt /var/crontab.txt
RUN crontab /var/crontab.txt && chmod 600 /etc/crontab
COPY database.yml /codem-schedule/config/database.yml
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf
COPY production.rb /codem-schedule/config/environments/production.rb

ENV RAILS_ENV production

EXPOSE 3000

CMD ["supervisord"]
