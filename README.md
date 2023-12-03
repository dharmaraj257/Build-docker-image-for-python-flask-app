
# Build docker image for python flask app

Build simple python flask application. build docker image and using docker container run the docker image. Push docker image Project into docker hub repositories.

Step 1: Build python flask application and docker file.
    
  1. create index.py file for python flask application
  
  
  Index.py
  ```python
from flask import Flask 
helloworld = Flask(__name__)
@helloworld.route("/")
def run():
    return "{\"message\":\"Hey there python\"}"

if __name__ == "__main__":
    helloworld.run(host="0.0.0.0", port=int("4000"), debug=True)
  ```
2.	Create requirement txt file.
  
  
  requirements.txt
```
flask
```

3.	Create a docker file for build docker image.


Dockerfile
```json
FROM python:3-alpine3.15
WORKDIR /app
COPY . /app
RUN pip install -r requirements.txt
EXPOSE 4000
CMD python ./index.py
```
Step 2: Build docker image for flask application.
```
docker build -t dharmaraj257/python-flask:0.0.1.RELEASE .
```
![docker command python ](https://github.com/dharmaraj257/AWS-project-2/assets/100831265/8c4aed26-9ce1-412e-a2de-ad983d950402)


Step 3: Run container using docker image.
```
docker container run -d -p 4000:4000 dharmaraj257/python-flask:0.0.1.RELEASE 
```
![docker python container ](https://github.com/dharmaraj257/AWS-project-2/assets/100831265/af5abc77-8027-4a8c-ad95-761d1e028291)

Output:

![docker python output](https://github.com/dharmaraj257/AWS-project-2/assets/100831265/e5776ea6-a0cc-4620-9fb1-ca1d30e6a69a)

Step 4: push docker image into docker hub.

```
docker push dharmaraj257/python-flask:0.0.1.RELEASE
```
![docker python final output](https://github.com/dharmaraj257/AWS-project-2/assets/100831265/920a91f0-af47-4723-a676-3add886afe72)