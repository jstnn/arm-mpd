# arm-mpd

This is an image for my favorite music server application [MPD](https://www.musicpd.org/). Using Debian as the operating system. A [Resin.os Raspbian image](https://hub.docker.com/r/resin/rpi-raspbian/) is used as a base image for compatibility with IoT devices, but it works well anywhere.

This image is configured to use with Icecast as streaming output. You can edit the mpd.conf or use the fully audio stack I created. 

# How to use 

You can create volumes for your music, playlists and/or database, or use host volumes instead, you need to replace `your_SOMETHING_volume` with your host path or own volume.

    docker run -d -p 6600:6600 \ 
        -v your_music_volume:/var/lib/mpd/music \
        -v your_playlists_volume:/var/lib/mpd/playlists \
        -v your_database_volume:/var/lib/mpd/database \
        --name mpd jstnn/arm-mpd:latest


An instance of mpd is now running with the port 6600 mapped to your host or docker-machine IP address.

# Custom configuration 

Check the repository and you will find an `mpd.conf` you can edit and set your custom configuration. You just need to build the image again.

The passwords in the current configuration are just for testing purposes.

# Credits

This dockerfile is based on the [alpine-mpd image](https://hub.docker.com/r/vitiman/alpine-mpd/). Changes has been made to compile with an IoT device with an ARMv7 architecture like the RaspberryPi 3 using a resin.os optimized image.
