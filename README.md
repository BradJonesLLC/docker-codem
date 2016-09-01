# docker-codem

Docker containers for [Codem transcoder/scheduler](http://transcodem.com/)

Leverages the [dorftv/codem-transcode](https://github.com/dorftv/docker-codem-transcode)
transcoder image.

### Automated Builds

* [Scheduler](https://hub.docker.com/r/bradjonesllc/codem-scheduler/)
* [Transcoder](https://hub.docker.com/r/bradjonesllc/codem-transcoder/)

### Usage

* Set environment variables `MYSQL_HOST`, `MYSQL_USERNAME` AND `MYSQL_PASSWORD`
    for the scheduler image to the appliable values
* Remember to run `bundle exec rake codem:install` or `bundle exec rake db:schema:load`
    inside the scheduler (if you're using it) to initialize the database.
* Note, the scheduler HTTP server runs on port 3000.

## Copyright and License

GPL-2, &copy; 2016 Brad Jones LLC.
