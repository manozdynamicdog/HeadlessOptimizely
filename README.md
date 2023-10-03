# Headless CMS Optimizely
Requirements - dotnet SDK -- should install CLI too. 
Verify you have SDK installed with command 'dotnet' in powershell/cmd.

If not then install any of these listed below in web - https://dotnet.microsoft.com/en-us/download

We are going to install the Episerver Template and CLI module via dotnet CLI we installed above. 
https://nuget.optimizely.com/package/?id=EPiServer.Net.Templates

Below are the steps to setup headless Optimizely CMS on local. 

- Step 1. dotnet new -install EPiServer.Net.Templates --nuget-source https://nuget.optimizely.com/feed/packages.svc/ --force

- Step 2. dotnet tool install EPiServer.Net.Cli --global --add-source https://nuget.optimizely.com/feed/packages.svc/

- Step 3. dotnet new epicmsempty --name {ProjectName}

- Step 4. Getting into directory - cd {ProjectName}

- Step 5. dotnet-episerver create-cms-database -S Manoz -E -dn "HeadlessCMS" -du "sandbox" -dp "sandbox" "C:\...\{root}\{ProjectName}.csproj"

  After Step 5, run the project with 'dotnet run'. You should be able to see the project is up and running on ports defined at project level *:8000/8001

  **This will be 404 because there is no default page and UI configured yet but you should be able to see optimizely admin panel by going on /episerver/cms**

- Step 6. https://github.com/episerver/netcore-preview/blob/master/Quicksilver/EPiServer.Reference.Commerce.Site/Infrastructure/UsersInstaller.cs

  Because this is an empty setup that is why we don't have admin user configured in the database. For that we force an admin user creation via inclusion of above file in the code. Which will create an admin user with below credentials - 

- Step 7. Login with admin@example.com/Episerver123!

And if you are here, You have an Headless Optimizely CMS configured successfully.  :)
