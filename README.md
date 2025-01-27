# Docker Images Main

This repository is designed to gather various Docker images, each tailored for different purposes, into a single, well-structured location. By leveraging the files here, developers can quickly prepare and deploy containerized environments for their specific needs. The project covers:

- [OracleJava](https://github.com/Enesbasduvar/docker-images-main/tree/main/OracleJava)  
- [OracleLinuxDevelopers](https://github.com/Enesbasduvar/docker-images-main/tree/main/OracleLinuxDevelopers)  
- [WebServer](https://github.com/Enesbasduvar/docker-images-main/tree/main/WebServer)

## Table of Contents
1. [Overview](#overview)  
2. [Folder Structure](#folder-structure)  
   - [OracleJava](#oraclejava)  
   - [OracleLinuxDevelopers](#oraclelinuxdevelopers)  
   - [WebServer](#webserver)  
3. [Installation & Usage](#installation--usage)  
4. [Contributing](#contributing)  
5. [License](#license)  
6. [Support & Contact](#support--contact)

---

## Overview
The main goal of this repository is to provide Docker images that are both production-ready and easily extensible for developers. You can explore a specific directory, adapt the provided Dockerfiles, and integrate them into your own projects.

## Folder Structure

### OracleJava
In the [OracleJava](https://github.com/Enesbasduvar/docker-images-main/tree/main/OracleJava) directory, you will find Docker images based on Oracle Linux for various JDK versions, as well as the Server JRE.  
- JDK 22, 21, and 17: The required binaries are automatically downloaded from Oracle using curl during the build process.  
- JDK 11, JDK 8, and Server JRE 8: You must manually download the corresponding Java archive (.tar.gz) from the Oracle site and place it in the same folder as the relevant Dockerfile.  

Example usage:
1. Clone the repository:  
   git clone https://github.com/Enesbasduvar/docker-images-main
2. Navigate to the desired directory:  
   cd docker-images-main/OracleJava/8   (for JDK 8 or Server JRE 8)
3. Build the Docker image:  
   docker build -t oracle/serverjre:8 .

### OracleLinuxDevelopers
The [OracleLinuxDevelopers](https://github.com/Enesbasduvar/docker-images-main/tree/main/OracleLinuxDevelopers) directory provides developer-friendly Docker images based on Oracle Linux. Various language-specific builds (Node.js, PHP, Python, Ruby, etc.) are supported:  
- Comes in both oraclelinux7‑ and oraclelinux8-based variants, with "-oracledb" versions including Oracle Database connectivity.  
- A minimal package set is used, allowing you to install additional dependencies in your own Dockerfile.

### WebServer
The [WebServer](https://github.com/Enesbasduvar/docker-images-main/tree/main/WebServer) directory contains a production-ready stack featuring Nginx and PHP-FPM, designed to run modern web applications:  
- PHP-FPM 8.2, Composer, important PHP extensions, and configurations for Nginx.  
- An example docker-compose.yml file for quick deployment.  
- Additional performance and security optimizations.

---

## Installation & Usage
1. Clone the repository:  
   git clone https://github.com/Enesbasduvar/docker-images-main.git
2. Navigate to the folder you want to use (for example, `OracleJava`, `OracleLinuxDevelopers`, or `WebServer`).
3. Inspect the relevant files and either use docker build or docker-compose up -d (depending on the directory’s setup).

Example:
- For the WebServer folder:  
  cd docker-images-main/WebServer  
  docker-compose up -d  

- For the OracleLinuxDevelopers folder:  
  cd docker-images-main/OracleLinuxDevelopers/oraclelinux8-nodejs:14  
  docker build -t oraclelinux8-nodejs:14 .

---

## Contributing
1. Fork this repository to your GitHub account.  
2. Create a feature branch:  
   git checkout -b feature/AmazingFeature  
3. Commit your changes:  
   git commit -m "Add AmazingFeature"  
4. Push to your branch:  
   git push origin feature/AmazingFeature  
5. Open a Pull Request so your changes can be reviewed.

Please feel free to submit an issue or a Pull Request for any bug reports, suggestions, or improvements.

---

## License
This project is licensed under the [MIT License](https://github.com/Enesbasduvar/docker-images-main/blob/main/LICENSE). Refer to the license file for detailed information.

---

## Support & Contact
- For updates and more information, visit the [docker-images-main repository](https://github.com/Enesbasduvar/docker-images-main).  
- You can open issues or Pull Requests on GitHub if you have any questions, requests, or suggestions.

This repository is actively maintained and regularly updated. Feel free to reach out on GitHub for any assistance you may require. 
