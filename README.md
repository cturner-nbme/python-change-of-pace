# Python Library Template

## Overview
This template is intended to be a demonstration of both virtual environments, and user-created libraries. It provides all the tools necessary to create and publish a library to your repository of choice.

Everything required for setting up your workspace is provided in **setup.ps1**. For more details on what it is doing, see below.

## Template Assumptions
- **Basic Understanding of Python:** We will not be going into the basics of the language itself
- **VSCode as your IDE:** We will assume that your IDE of choice is VSCode. Everything we talk about will more than likely be supported by your actual IDE (PyCharm, etc.) and also by your CLI tool of choice

## Virtual Environments
Virtual environments are isolated spaces within your operating system where you can install Python packages and dependencies specific to a project. This isolation helps prevent conflicts between different projects' dependencies and allows you to manage project-specific libraries without affecting the global Python installation.

### What are they used for?
- **Isolation/Management of Project Dependencies:** Easily manage and track the libraries and versions required for your project, and only your project.
- **Reproducible Environments:** Share your project with others and ensure they can recreate your environment precisely.

### Creating your Virtual Environment
1. Open your terminal or command prompt
2. Navigate to your project directory.
3. Create the virtual environment. Note: Any name can be used, but a widely accepted standard is to name it `.venv`

   ```powershell
   python -m venv .venv
   ```
   This will create a directory named `.venv` in your project folder containing the virtual environment

### Using your Virtual Environment
1. **Activate** your environment by running one of the activation scripts located at `.venv/Scripts`. There are multiple options but they all do the same thing. Pick whatever works best for you. 
   - Your virtual environment will be chosed as the default path for the python executable for the remainder of your terminal/command prompt session
   - IDE's with Python support often do this automatically for you if they detect a virtual environment within your project files

    **On Windows:**
    ```powershell
    ./.venv/Scripts/Activate.ps1
    ```
    **On MacOS/Linux:**
    ```bash
    source .venv/bin/activate
    ```


### Managing your Dependencies
A `requirements.txt` file is used to list all the packages your project depends on, along with optionally provided versions. This file allows you to easily install all necessary packages with a single command.

There are two ways to create a `requirements.txt` file:

1. **Manual** creation. Recommended for fresh projects
2. **Generated** from your current environment's packages:
```powershell
    python -m pip freeze > requirements.txt
```

The file can then be used to install your dependencies within a chosen environment. They will be programatically installed in the order that they appear within the file.
```powershell
    python -m pip install -r requirements.txt
```
  <!-- - Activate script
  - Requirements.txt
  - Installing other libraries -->

### Folder Structure
For the most part, once the virtual environment is setup it can just be left alone. In terms of files, only two things should have been added as part of this template, your `requirements.txt` file and your `.venv` directory
```
your_project_folder/
├── .gitignore
├── example.py
├── requirements.txt
└── .venv/
    ├── Include/
    ├── Lib/
    ├── Scripts
    └── pyvenv.cfg
```

Packaging your Own Libraries
- Brief overview of libraries
- Why would you want to? What benefits does it give you?
- Code organization & sharing
-- How to build it?
--- Build Backend
---- Package structure
--- Metadata
- How to make your library available to others
-- Nexus? Pypi? DevOps feed?
-- Twine