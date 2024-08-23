# GitHub and GitHub Copilot Workshop by Technofocus 

GitHub is a complete developer platform designed to build, scale, and deliver secure software, supporting the entire software development lifecycle to increase development velocity and improve code quality. This hands-on workshop helps developers master GitHub and boost coding efficiency with GitHub Copilot.

In this workshop, you will learn GitHub essentials, including repository management, markdown, pull requests, and conflict resolution. The workshop covers automating workflows with GitHub Actions, ensuring code security, and using GitHub Copilot for AI-powered coding assistance.


## Preparing the virtual machine for GitHub Copilot labs

1. Type cliport text to **Notepad**.
   
  ```powershell
  # Apache maven (mvn)
  cd \
  wget -uri https://dlcdn.apache.org/maven/maven-3/3.9.9/binaries/apache-maven-3.9.9-bin.zip -OutFile apache-maven-3.9.9-bin.zip 
  Expand-Archive .\apache-maven-3.9.9-bin.zip -DestinationPath "C:\"
  [Environment]::SetEnvironmentVariable("Path", $env:Path + ";C:\apache-maven-3.9.9\bin\", "Machine")
  
  
  # Nuget pakage source for Microsoft Visual Studio Offline Packages
  cd "c:\Users\Admin\Downloads"
  wget -uri https://dist.nuget.org/win-x86-commandline/latest/nuget.exe -OutFile nuget.exe
  .\nuget sources add -Name "NuGet official package source" -Source "https://api.nuget.org/v3/index.json"
  
  
  # Mocha (JavaScript test framework for Node.js)
  npm install --global mocha

  
  # Axios (HTTP client for the browser and node.js)
  npm install --global axios

  
  # .NET 8 SDK
  cd "c:\Users\Admin\Downloads"
  wget -uri https://download.visualstudio.microsoft.com/download/pr/f5f1c28d-7bc9-431e-98da-3e2c1bbd1228/864e152e374b5c9ca6d58ee953c5a6ed/dotnet-sdk-8.0.401-win-x64.exe -OutFile dotnet-sdk-8.0.401-win-x64.exe
  Start-Process -Wait -FilePath "c:\Users\Admin\Downloads\dotnet-sdk-8.0.401-win-x64.exe" -Argument "/silent" -PassThru

  wget -uri https://download.visualstudio.microsoft.com/download/pr/523db424-b1cc-425d-97f5-bd0e9b0c7440/f04171a6d597780662d809107a13f44e/dotnet-sdk-8.0.401-win-x86.exe -OutFile dotnet-sdk-8.0.401-win-x86.exe 
  Start-Process -Wait -FilePath "c:\Users\Admin\Downloads\dotnet-sdk-8.0.401-win-x86.exe" -Argument "/silent" -PassThru

  
  # Visual Studio Code extension
  code --install-extension GitHub.copilot --force
  code --install-extension GitHub.copilot-chat --force
  code --install-extension ms-azuretools.vscode-docker --force
  code --install-extension vscjava.vscode-java-pack --force
  code --install-extension ms-toolsai.jupyter --force
  code --install-extension ms-python.python --force


  # Docker Desktop
  cd "c:\Users\Admin\Downloads"
  wget -uri "https://desktop.docker.com/win/main/amd64/Docker%20Desktop%20Installer.exe?utm_source=docker&utm_medium=webreferral&utm_campaign=docs-driven-download-win-amd64&_gl=1*o8r7hp*_ga*MTg4Mzc3MzQ5NC4xNzI0Mzc2MzQx*_ga_XJWPQMJYHQ*MTcyNDM3NjM0MS4xLjEuMTcyNDM3NjQ2NC42MC4wLjA" -OutFile DockerDesktopInstaller.exe
  Start-Process 'c:\Users\Admin\Downloads\DockerDesktopInstaller.exe' -Wait install
  ```

1. Open **PowerShell ISE** with **administrative privileges**.

1. Copy from Notepad o PowerShell ISE.

1. Execute the cmdlets.

1. **Restart the Virtual Machine** before start the exercises. 

