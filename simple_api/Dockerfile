# To build API image you must use "python:2.7-stretch"
FROM python:2.7-stretch
# Please don't forget to specify the maintainer information
LABEL org.opencontainers.image.authors="aroubiteniama@gmail.com"
# You need to copy the source code of the API in the container at the root "/" path
COPY ./student_age.py /
# The API is using FLASK engine,  here is a list of the package you need to install
RUN apt-get update -y && apt-get install python-dev python3-dev libsasl2-dev python-dev libldap2-dev libssl-dev -y
RUN pip install flask==1.1.2 flask_httpauth==4.1.0 flask_simpleldap python-dotenv==0.14.0
# Persistent data (volume)
RUN mkdir /data
VOLUME [  "/data"]
COPY ./student_age.json /data
# To interact with this API expose 5000 port
EXPOSE 5000
# When container start, it must run the student_age.py
CMD [ "python", "/student_age.py" ]