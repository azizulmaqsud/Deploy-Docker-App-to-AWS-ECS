# Deploy Docker App to AWS ECS
- Docker run on local system, commands:
docker run -p 6535(any host):5000(any port) 0123456789 (image ID)
- Docker Push Commands for cloud AWS ECR 
Make sure that you have the latest version of the AWS CLI and Docker installed. For more information, see Getting Started with Amazon ECR .
Use the following steps to authenticate and push an image to your repository. For additional registry authentication methods, including the Amazon ECR credential helper, see Registry Authentication .
Retrieve an authentication token and authenticate your Docker client to your registry.
Use the AWS CLI:

aws ecr-public get-login-password --region us-east-1 | docker login --username AWS --password-stdin public.ecr.aws/w6j2n6p1
Note: If you receive an error using the AWS CLI, make sure that you have the latest version of the AWS CLI and Docker installed.
Build your Docker image using the following command. For information on building a Docker file from scratch see the instructions here . You can skip this step if your image is already built:

docker build -t my-express-app .
After the build completes, tag your image so you can push the image to this repository:

docker tag my-express-app:latest public.ecr.aws/w6j2n6p1/my-express-app:latest
Run the following command to push this image to your newly created AWS repository:

docker push public.ecr.aws/w6j2n6p1/my-express-app:latest
