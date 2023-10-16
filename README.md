# Installing Commerce and CMS with CLI
Requirements - dotnet SDK -- should install CLI too. 
Verify you have SDK installed with command 'dotnet' in powershell/cmd.

If not then install any of these listed below in web - https://dotnet.microsoft.com/en-us/download

We are going to install the Episerver Template and CLI module via dotnet CLI we installed above. 
https://nuget.optimizely.com/package/?id=EPiServer.Net.Templates

Below are the steps to setup Optimizely CMS on local. 

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

Installing Commerce -
- Add Package _EPiServer.Commerce_
Since we have installed CMS with CLIs Go to file Startup.cs find service.AddMvc();
- Add this to StartUp.cs > ConfigureServices 

    _services.AddCommerce();_

That's it from the setup perspectives. So does that mean all the challenges conquered ? :D 
Well, Technically yes, But there are runtime settings we are going to do later for example setting up the root page for commerce and CMS, Running pending migrations for commerce, and have them used to query via Postman.

# Enabling Headless for CMS and Commerce
Up until now we have configured CMS and commerce with CLI commands. This will enable CMS and Commerce admin panels. 
There will be 404 due to no UI so far as we don't have the views configured in solution (.cshtml). As we are trying the setup to be headless, therefore we don't wish to add views to solution for obvious reason. 

Optimizely introduced [ContentDelivery](https://docs.developers.optimizely.com/content-management-system/v1.5.0-content-delivery-api/docs) APIs couple of years back and it is mature and reliable to work with. 
All you have to is to install optimizely nuget packages for both channels (CMS, Commerce) -
- [EPiServer.ContentDeliveryApi.Cms](https://nuget.optimizely.com/?q=EPiServer.ContentDeliveryApi.Cms&s=Popular&r=10&f=All) for CMS headless
- [EPiServer.ContentDeliveryApi.Commerce](https://nuget.optimizely.com/?q=EPiServer.ContentDeliveryApi.Commerce&s=Popular&r=10&f=All) for Commerce headless

Now when we have these packages installed, We need to register them in pipeline as middleware. 
