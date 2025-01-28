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

Create your Github Repository

(1) Log in to your GitHub account and navigate to the Create a New Repository page.

(2) Fill in the details as follows:

Repository Name: rust-hello-world
Description: "Hello World Project in Rust."
Visibility: Public

(3) Once you have done that, in terminal link it to your local project:

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
rustc --version 
```

The output you recieve should be similar to this:

``` rust
rustc 1.x.x (some-hash YYYY-MM-DD)
```

!!! success
If this is shown Rust has been installed and you can use it in your Dev Container.
!!!

## **Steps to create a new project, write a basic "Hello COMP423" program, compile, and run**

### **Step 1**

Create a new Rust project using Cargo: 

* Run the following command to initialize a new Cargo project:

``` rust
cargo new hello-comp423 --vcs none
```
This makes a new folder called hello-comp423 that has the default structure for a Rust project.

* Navigate into the project directory:

``` bash
cd hello-comp423
```

The Cargo.toml file contains metadata about the project, and src/main.rs is where you’ll write your program.

### **Step 2**
Write the "Hello, COMP423!" program:

* Open the src/main.rs file in your project directory. Delete everything in it and write in the following code:
``` rust
fn main() {
    println!("Hello COMP423!");
}
```
Save the file. This is the basic Rust program, which prints "Hello, COMP423!".

### **Step 3**

Compile and run the program:

* To compile the program:
``` rust
      cargo build
```

* To execute the compiled program:
``` rust
      ./target/debug/hello-comp423
```
You should see the output:
``` rust
      Hello COMP423!
```
* Also you can, you can compile and run the program in one step using:
``` rust
      cargo run
```
This will both build the program and immediately execute it, giving the output:
``` rust
      Hello COMP423!
```

* Cargo build: This command compiles the program and generates an executable file in the target/debug directory.
* Cargo run: This command combines building and executing the program in a single step.

### **Step 4**
* Stage files and the add a README:
``` rust
    echo "https://krishsinghvi.github.io/comp423-course-notes/tutorials/rust-setup/" > README.md
    git add .
```
* Add configs and commit:
``` rust
    git config user.name --global "your-username-here"
    git config user.email --global "your-email-here"
    git commit -m "your-message-here
```
* Push to remote:
``` rust
    git branch -M main
    git push --set-upstream origin main
```
**We have finished!**
