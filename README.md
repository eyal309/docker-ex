### 1. Create new Dockerfile:

- Use the python:3.6-alpine as your base.
- Create a directory named 'code'.
- Copy the app,test and requirements to your new code directory.
- Change the working directory to 'code'
- Install the requirements using the pip command. 
- Expose port 8080.
- Run the app using the command:
 ` ["gunicorn", "-b 0.0.0.0:8080", "app:app"]`
 
### 2. Build your Dockerfile:

- Run your new docker image.
- Verify it is accessible via port 8080

### 3. Multi-stage build

- Edit your Dockerfile as a multistage build.
- Use the python:3.6-alpine as your base image and also as your main image.
- Using the following commands copy the content from the base image to the main image:
```
COPY --from=base /code/ /code
COPY --from=base /usr/local/lib/python3.6 /usr/local/lib/python3.6
COPY --from=base /usr/local/bin/gunicorn /usr/local/bin/gunicorn
```
- Expose port 8080 and run the app as in step 1.
- Build the image and run it.
