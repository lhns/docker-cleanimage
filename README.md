# docker-cleanimage
#### A tool for cleaning up temp and cache directories to make docker images smaller

## Commands
- apt-get -y --purge autoremove
- apt-get -y clean

## Directories
- /tmp/*
- /var/tmp/*
- /var/lib/apt/lists/*
- /var/log/alternatives.log
- /var/log/apt/
- /var/log/bootstrap.log
- /var/log/btmp
- /var/log/dpkg.log
- /var/log/faillog
- /var/log/fsck/
- /var/log/lastlog
- /var/log/wtmp
- /var/cache/*

## Usage in Dockerfile

### Download and install
```
ENV CLEANIMAGE_VERSION 1.0
ENV CLEANIMAGE_URL https://raw.githubusercontent.com/LolHens/docker-cleanimage/$CLEANIMAGE_VERSION/cleanimage

ADD ["$CLEANIMAGE_URL", "/usr/local/bin/"]
RUN chmod +x "/usr/local/bin/cleanimage"
```

### Execute after each layer where necessary
```
RUN apt-get install -y \
      python3 \
 && cleanimage
```
