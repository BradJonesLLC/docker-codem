FROM rails:4

RUN apt-get update && apt-get install -yqq --no-install-recommends \
    git \
    cron \
    supervisor \
    ca-certificates \
    && gem install bundler \
    && apt-get clean autoclean && apt-get autoremove -y

ENV CODEM_VERSION bd4da884483aed38bb6bed7e0e0187869ca5ba22

# Taken from https://patch-diff.githubusercontent.com/raw/madebyhiro/codem-schedule/pull/38.patch
# With some massaging to get to apply to current
COPY hls.patch /hls.patch

# Checks out codem scheduler and applies HLS patch.
RUN git clone git://github.com/madebyhiro/codem-schedule.git \
    && cd codem-schedule \
    && git checkout ${CODEM_VERSION} \
    && patch -p1 < /hls.patch \
    && bundle install

COPY crontab.txt /var/crontab.txt
RUN crontab /var/crontab.txt && chmod 600 /etc/crontab
COPY database.yml /codem-schedule/config/database.yml
COPY supervisord.conf /etc/supervisor/conf.d/supervisord.conf
COPY production.rb /codem-schedule/config/environments/production.rb

ENV RAILS_ENV production

EXPOSE 3000

CMD ["supervisord"]
