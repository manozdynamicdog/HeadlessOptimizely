# HeadlessOptimizely
https://nuget.optimizely.com/package/?id=EPiServer.Net.Templates

Step 1. dotnet new -install EPiServer.Net.Templates --nuget-source https://nuget.optimizely.com/feed/packages.svc/ --force

Step 2. dotnet tool install EPiServer.Net.Cli --global --add-source https://nuget.optimizely.com/feed/packages.svc/

Step 3. dotnet new epicmsempty --name {ProjectName}

Step 4. Getting into directory - cd {ProjectName}

Step 5. dotnet-episerver create-cms-database -S Manoz -E -dn "HeadlessCMS" -du "sandbox" -dp "sandbox" "C:\...\{root}\{ProjectName}.csproj"

Step 6. https://github.com/episerver/netcore-preview/blob/master/Quicksilver/EPiServer.Reference.Commerce.Site/Infrastructure/UsersInstaller.cs
Step 7. Login with admin@example.com/Episerver123!
