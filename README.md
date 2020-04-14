# Capstoneproject

In this project you will apply the skills and knowledge which were developed throughout the Cloud DevOps Nanodegree program. These include:

    Working in AWS
    Using Jenkins to implement Continuous Integration and Continuous Deployment
    Building pipelines
    Working with CloudFormation to deploy clusters
    Building Kubernetes clusters
    Building Docker containers in pipelines


Setting your AWS infrastructure

For deploy your infrastructure execute the next script inside cloudformation/ folder:

sh ./create.sh Capstone-project network_bg.yml network.json

Note: The creation of EKS cluster takes almost 10 minutes
Setting your pipeline for lint, build and publish your docker image

For create your pipeline you have to add the file Jenkinsfile in jenkins, also before run the pipeline you have to do login in Docker for publish image task
Blue Green deployment configuration is setting in Kubernetes using Controllers and Service

    Apply blue controller inside blue-green/blue folder

    kubectl apply -f blue.json

    Apply green controller inside blue-green/green folder

    kubectl apply -f green.json

    Deploy service in blue-green/ folder

    kubectl apply -f bluegreen_service.json

    Then you can check the application deployed in your browser

    For do a blue-green deployment update the section to green in bluegreen_service.json file:

    "selector":{ "app":"blue" },

    Deploy again the service

    kubectl apply -f bluegreen_service.json

    You can see how each POD is updated to the green version incrementally
