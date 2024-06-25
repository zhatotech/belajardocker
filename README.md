# belajardocker

## Step 1: Create the Docker image

Before we get started with creating the **_Docker Image_** we will create a **_Directory_** to keep all the necessary files and resources in one place, making it easier to manage, maintain, and update the image.

The directory will also help Docker to find and use the required files during the image-building process.

Use the **_mkdir_** command to create the directory  
**_cd_** to move into the directory

```
mkdir directory name  
cd directory name
```


![](https://miro.medium.com/v2/resize:fit:700/1*Qnx_4B1UCTzhnOUL90HE-Q.png)

## Step 2: Pull the Docker image

For us to deploy our website we need to pull the latest Nginx Image from Docker. We can use the following command to accomplish that.

```
docker pull nginx:latest
```


![](https://miro.medium.com/v2/resize:fit:700/1*HZYdscc7MBwV7PDnHdZLHw.png)

## Step 3: Verify that the NGINX image was pulled successfully

We can confirm from the Status line that the Nginx image is the latest and that the pull was successful. We can also use the **_docker images_** command to confirm that our pull was successful.

```
docker images
```


![](https://miro.medium.com/v2/resize:fit:700/1*RblN7_ajThF9x9VD2yO_1A.png)

## Step 4: Create the Dockerfile and Index.HTML

We will use the t**_ouch_** command to create the index.html and dockerfile and **_vim_** command to edit the files.

Dockerfile
```
nano Dockerfile
```


```
FROM nginx:1.10.1-alpine
COPY index.html /usr/share/nginx/html
EXPOSE 8080
CMD ["nginx","-g","daemon off;"]
```

```
nano index.html
```
index.html

```
<!doctype html>  
<html>  
 <body style="backgroud-color:rgb(49, 214, 220);"><center>  
    <head>  
     <title>Docker Project</title>  
    </head>  
    <body>  
     <p>Welcome to my Docker Project!<p>  
        <p>Today's Date and Time is: <span id='date-time'></span><p>  
        <script>             var dateAndTime = new Date();  
             document.getElementById('date-time').innerHTML=dateAndTime.toLocaleString();        </script>  
        </body>  
</html>
```



Make sure to save the files by using hitting the esc button and using :wq command.

![](https://miro.medium.com/v2/resize:fit:700/1*AP4nC1schWEfZO7icoEWCw.png)

## Step 5: Build the image

Run the following command in the Terminal to build the Image.

```
#make sure to add a dot at the end   
docker build -t <new_image_name> .
```


![](https://miro.medium.com/v2/resize:fit:700/1*ZqjaAGSjRFg_KxBpuQ0aVA.png)

Use the following command to verify the Image was successfully built.

```
docker images
```


![](https://miro.medium.com/v2/resize:fit:700/1*HcO8KHvk-TCZMVyVDFccDg.png)

## Step 6: Build and deploy the container

Use the following command to create a container with the image we created earlier using the following command.

```
docker run -d --name <name-container> -p 8080:80 <new_image_name>
```


![](https://miro.medium.com/v2/resize:fit:700/1*jsHtVE__o0uqUNtf7ypxew.png)

## Step 7: Check if the container was successfully created.

With the following command, we can verify that our container was successfully created.

```
docker ps -a
```


![](https://miro.medium.com/v2/resize:fit:700/1*Qie9bHEcWt5XHgMJCvl8eA.png)

## Step 8: Verify that the container is running

Take the Public IPv4 Address of the Instance your Cloud9 is running on and paste it into a web browser. Make sure to add :8080 at the end.

```
<public_ip>:8080
```


![](https://miro.medium.com/v2/resize:fit:700/1*1zG2D_QiKseSToKFYJyAww.png)
