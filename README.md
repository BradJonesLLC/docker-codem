# docker-codem

Docker containers for [Codem transcoder/scheduler](http://transcodem.com/)

Leverages the [dorftv/codem-transcode](https://github.com/dorftv/docker-codem-transcode)
transcoder image.

### Automated Builds

* [Scheduler](https://hub.docker.com/r/bradjonesllc/codem-scheduler/)
* [Transcoder](https://hub.docker.com/r/bradjonesllc/codem-transcoder/)

### Usage

* Remember to run `bundle exec rake codem:install` inside the scheduler (if you're using it)
    to initialize the database.

## Copyright and License

GPL-2, &copy; 2016 Brad Jones LLC.
