# MYUBU

## Overview

Dockerfile to create a Ubuntu-based image suitable for interactive use.  Replace __TODO-UID__ with desired value for user id (e.g. __mtharris__).  And replace __TODO-ROOT-PASSWD__ and __TODO-UID-PASSWD__ with desired values.

## Command Examples

Below are some commands that can be used to build, run and delete the image.

Build an Image Using the Dockerfile

    docker build -t myubu .

Run the Image with Various Port Mappings and Drive Mappings

macOS

    docker run -p 4200:4200 -p 5000:5000 -p 5001:5001 -p 5002:5002 -p 5003:5003 -p 5004:5004 -p 5005:5005 -v /Users/mtharris/src:/home/mtharris/src --name myubu -h myubu -it myubu

Windows

    docker run -p 4200:4200 -p 5000:5000 -p 5001:5001 -p 5002:5002 -p 5003:5003 -p 5004:5004 -p 5005:5005 -v C:\Users\mtharris\Source\Repos:/home/mtharris/src --name myubu -h myubu -it myubu

Restart Existing Image and Attach to it

    docker restart myubu ; docker attach myubu

Delete Process and Image

    docker rm myubu ; docker image rm myubu