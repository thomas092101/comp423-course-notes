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
  Now that you have your configurations set, to access your dev container on VSCode, use ```Ctrl + Shift + p``` to search for *"Dev Containers: Reopen in Container"* and selct that option. 
  This step may take a minute as Docker builds the container for the first time. 

!!! Note
    All instructions beyond this point should take place inside your container.

### **Building "Hello World!" program in Rust**

* Creating new files in Rust  
  While Rust uses a different dependency than other languages you might be used to, the essential steps to creating, compiling, and running a program are virtually the same.  
  Rust uses its own dependency to manage program called ```cargo```. In order to create a new file in our dev container with Rust, you want to run the command ```cargo new``` followed by a file name of your choosing.  We also want to use the flag ```--vcs none``` to avoid auto creating a new git repository.  

!!! Helper
    Using the ```cargo new``` command will create a new repository automatically which is a helpful feature when starting new projects.  Lucky for us, Cargo also automatically builds the Hello World! program for us.  
  
  Running ```cargo new <filename>``` prompts rust to create a directory of the same filename along with a ```main.rs``` inside a ```src``` directory. After creating your ```hello_world``` file, navigate to main and check out the code that was generated. The code inside should loosely resemble a Hello World! program from java or C.  We will want to edit the code slightly to make the program say "Hello COMP423" instead of "Hello World!". You should also edit the filename to reflect this change. 

  * Compiling and Running your program  
  To compile programs in Rust, you should first navigate inside the src file that was created, then run ```cargo build```.  
  ```
  cd hello_comp423/src  
  cargo build  
  ```

You may notice that running ```cargo build``` produces a bunch of files. These are all the necessary dependencies and libraries needed to run your compiled code, along with a binary file which is the code your machine will execute. Similar to C's gcc command making the necessary connections to shared libraries.  For now, we don't need to worry about these files.  

* Running the built file  
Now is the time to run our completed program. To run programs in Rust, we simply want run the following command.  
```
cargo run  
```

!!! note "Compare"
    It is possible to skip the ```cargo build``` command entirely.  If you do not run the build command, ```cargo run``` will automatically compile and run your code.

Congratulations! You have coded your first Rust program inside a Dev Container! All that's left is to ```exit``` your container, commit and push your changes to GitHub.  

## **Citations**
[Rust Documentation](https://opensource.com/article/20/3/rust-cargo)  
[Starting a Static Website Project with MkDocs](https://comp423-25s.github.io/resources/MkDocs/tutorial/)  
[Mkdocs Materials](https://squidfunk.github.io/mkdocs-material/)  