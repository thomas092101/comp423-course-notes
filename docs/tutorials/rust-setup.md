# **Setting up Development Container for Rust**

* Primary author : [Thomas Roche](https://thomas092101)
* Reviewer: [David Ona](https://github.com/david-ona)

## **Requirements**

* [Docker](https://www.docker.com/products/docker-desktop/) for creating and managing containers
* [Visual Studio Code](https://code.visualstudio.com/) with Microsoft Dev Container extension installed

### **Creating a new project**

* **Initialize and enter new Git Repository**  

```
mkdir comp423-rust-tutorial  
cd comp423-rust-tutorial  
git init
```  

* **Create and Push to GitHub**  
    + Log into Github, navigate to the [Create a New Repository] page.  The repository name should match your parent directory, which in this case is *comp423-rust-tutorial*.  Do not initialize a README, .gitignore, or license.

    + Next, you want to add your new repository to your local machine.  

    ```git remote add origin https://github.com/<your-username>/comp423-rust-tutorial.git```  
    
    replace ```<your-username>``` with your GitHub username.
    You may need to run ```git branch -M main``` as old version of git initialize the primary branch as ```master```.  

    + Finally, add and push your local commits to GitHub.  
    ```git push --set-upstream origin main```

### **Create, Configure, and Build your Dev Container**  

+ First, we will want to create a ```.devcontainer``` directory in the root of your project.  Inside this directory we will add a new file ```.devcontainer/devcontainer.json```  

    ```  
    mkdir .devcontainer  
    git add devcontainer.json  
    ```

+ Next, we want to configure the Dev Container before launching it. We will be making some changes to the file you just created. 

The ```devcontainer.json``` file defines the configurations for the development environment.  Here, we're specifying: 

+ **name**: Descriptive name for your container  
+ **image**: A base image of the container from Microsoft  
+ **extensions**: For this parameter, we should add the ```rust-analyzer``` VSCode plugin  
+ **version**: Here we want the container to, at startup, show that it is running a recent version of Rust.  We achieve this with the ```rustc --version``` command  

```
//Sample devcontainer.json
{
  "name": "COMP423 Course Notes",
  "image": "mcr.microsoft.com/devcontainers/rust:latest",
  "customizations": {
    "vscode": {
      "settings": {},
      "extensions": ["rust-lang.rust-analyzer"]
    }
  },
  "postCreateCommand": "rustc --version"
}
```


+ **Opening your Dev Container**

These next few steps need to be completed entirely in your Dev container.  To access your dev container, on VSCode search for *"Dev Containers: Reopen in Container"*.
This step may take a minute as Docker builds the container for the first time.
