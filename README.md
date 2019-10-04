# DVWA
Deploy DVWA and SQL server in the Kubernetes cluster

**3b) Creating a kubernetes cluster for DVWA**

- All files used for the lab should be in the github repository. Mention the commands used to transfer the images into kubernetes registry in the README file. Create a commit of all the changes and submit the patch file of the change. You can create a patch by running the following command. `git diff HEAD~1..HEAD > patch.diff` This creates patch file between last two commits. If you have multiple commits, edit the git diff appropriately to encorporate all your changes.

  - I followed the following steps to transfer images to kubernetes registry
  - Enable the registry service on microk8s `microk8s.enable registry`
    - Build the image of DVWA and SQL using the Dockerfiles `docker build -t dvwa:latest` and `docker build -t sql:latest`
    - Tag the image to make sure they are pointing to the registry 
      - `docker tag <image-id> localhost:32000/dvwa:k8s`
      - `docker tag <image-id> localhost:32000/sql:k8s`
    - Push the image to the local registry `docker push localhost:32000/<image-name>`
