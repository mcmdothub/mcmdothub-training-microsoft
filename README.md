# mcmdothub-training-microsoft

# 1. Secure a .NET web app with the ASP.NET Core Identity framework 

	mslearn-secure-aspnet-core-identity
		Url: https://learn.microsoft.com/en-us/training/modules/secure-aspnet-core-identity/3-add-identity

	- Open the starter project
		git clone https://github.com/MicrosoftDocs/mslearn-secure-aspnet-core-identity
	
	- Add the following NuGet packages to the project:
		dotnet add package Microsoft.VisualStudio.Web.CodeGeneration.Design --version 8.0.*
		dotnet add package Microsoft.AspNetCore.Identity.EntityFrameworkCore --version 8.0.*
		dotnet add package Microsoft.AspNetCore.Identity.UI --version 8.0.*
		dotnet add package Microsoft.EntityFrameworkCore.Design --version 8.0.*
		dotnet add package Microsoft.EntityFrameworkCore.SqlServer --version 8.0.*
		dotnet add package Microsoft.EntityFrameworkCore.Tools --version 8.0.*
		
	- Use the scaffolder to add the default Identity components to the project. 
	- Run the following command in the terminal:
		dotnet aspnet-codegenerator identity --useDefaultUI --dbContext RazorPagesPizzaAuth --userClass RazorPagesPizzaUser
		
	- Update the database
		- Run the following command to build the app:
			dotnet build		
			
			(The build succeeds with no warnings. If the build fails, check the output for troubleshooting information.)
			
		- Install the Entity Framework Core migration tool:
			dotnet tool install dotnet-ef --version 8.0.* --global
		
		- To update the database, create and run an EF Core migration:
			dotnet ef migrations add CreateIdentitySchema
			dotnet ef database update
			
		- Customize Identity
		
			- Customize the user account data
			
				- Add the user registration files to be modified to the project:
					dotnet aspnet-codegenerator identity --dbContext RazorPagesPizzaAuth --files "Account.Manage.EnableAuthenticator;Account.Manage.Index;Account.Register;Account.ConfirmEmail"