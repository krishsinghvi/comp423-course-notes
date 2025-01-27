# Setting up a dev container for Rust

A helpful guide for setting up a Rust project with a Git repository and a dev container. We will create a "Hello COMP423!" program.

* Primary author: [Krish Singhvi](https://github.com/krishsinghvi)

* Reviewer: [Sritan Vemuru](https://github.com/svemuru15)

## **Prerequisites**

Installation Requirements before starting:

* [Git](https://git-scm.com/) 
* [Visual Studio](https://code.visualstudio.com/) - The Remote – Containers extension is needed.
* [Docker](https://www.docker.com/)

## **Step-by-step instructions for creating a new Dev Container project for Rust**

### **Step 1**

Open terminal and create a directory for your Rust project:

```bash
mkdir rust-hello-world
cd rust-hello-world
```

### **Step 2**

You need to initialize a new Git repository:

``` bash
git init
```

### **Step 3**

You need to create a new public repository on GitHub and then copy the URL. Once you have done that, link it to your local project:

``` bash
git remote add origin https://github.com/<your-username>/rust-hello-world.git
```
Replace ```<your-username>``` with your GitHub username.

### **Step 4**

Now create a Dev Container configuration for your project:

* Create a .devcontainer folder 
* Create a devcontainer.json file:

``` bash
mkdir .devcontainer
touch .devcontainer/devcontainer.json
```

* In your editor open the devcontainer.json file and add the configuration:

```json
{
  "name": "Rust Dev Container",
  "image": "mcr.microsoft.com/vscode/devcontainers/base:ubuntu",
  "features": {
    "ghcr.io/devcontainers/features/rust": {}
  },
  "customizations": {
    "vscode": {
      "extensions": ["rust-lang.rust-analyzer"]
    }
  }
}
```

* Now save the file and reopen the project in the container by pressing Ctrl+Shift+P, typing "Dev Containers: Reopen in Container" and selecting the option.

### **Step 5**
Check to see that Rust is installed and working in the Dev Container:

* Open terminal in Visual Studio and run:

```rust
rustc --version rustc 1.x.x (some-hash YYYY-MM-DD)
```

The output you recieve should be similar to this:

``` rust
rustc 1.x.x (some-hash YYYY-MM-DD)
```
If this is shown Rust has been installed and you can use it in your Dev Container.

## **Steps to create a new project, write a basic "Hello COMP423" program, compile, and run**