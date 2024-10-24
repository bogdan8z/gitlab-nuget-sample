# gitlab-nuget-sample
Create .net library and deploy to a gitlab Package Registry

## Steps followed when creating the nuget package
1. in your library project (MyLibrary1) add gitlab ci file
   1. this file has to have 3 jobs: **build**, **test** and **push** to nuget location
   2. in **nuget-push** job for the source you need to use the project id where the **.nupkg** will be uploaded (let's say in our case 12345 is the id of this project)
2. in your csproj file (MyLibrary1.csproj) you need to add all the Package details (**PackageId**, **Version**, **Author** etc)
3. add NuGet Packages details in the **.gitignore**


## How to use it in your project
In the project where you want to use the package you need to:
1. add **nuget.config** file that will contain
   1. the **name** and **url** of the package gitlab project
   2. **username** and **password** that are read from gitlab variables
2. you need to add reference to your package, for this you have 2 options:
   1.  in csproj file you need to manually add the package reference like <PackageReference Include="MyLibrary1" Version="1.0.0" /> or 
   2.  from visual studio add it using **Manage Nuget Packages** option

## If you need to use locally this package
1. you need to create a personal access token in gitlab (include **read_api**)
2. in visual studio use **Manage Nuget Packages** option and add **MyLibrary1** using the url from gitlab of the nupkg location (.../projects/12345/packages/nuget/index.json)

## Links
[Gitlab - NuGet packages in the package registry](https://docs.gitlab.com/ee/user/packages/nuget_repository/) <br>
[Gitlab - Add a source with a configuration file](https://docs.gitlab.com/ee/user/packages/nuget_repository/#add-a-source-with-a-configuration-file) <br>
[Gitlab - Publish a NuGet package by using CI/CD](https://docs.gitlab.com/ee/user/packages/nuget_repository/#publish-a-nuget-package-by-using-cicd) <br>
