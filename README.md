
# Bootcamo Week 3 Bonus Project - .Net Core Web Application

## Create .Net Core Web Application
1. Open Visual Studio 
2. Create a new project 
	a) Select "ASP.NET Core Web Application" from project templates list and press Next Button
	b) Give project name eg. bootcampDotNetApp, location (where your project get save on disk), Give solution name if you want to keep project and solution in different location
	3) Your default project get created.
3. Adding Newtonsoft.Json using nuget package manager.
	Project > Mange Nuget Packages 
	Browse > search for Newtonsoft.Json and click install
	Your Newtonsoft.Json package will get added in your created project.
3. Run newly created bootcampDotNetApp application by pressing Ctrl+F5 or by pressing small green play button in toolbar.
	This will open your application in browser.
4. Publishing Application
	a) Right click on project in solution explorer window and select publish
	b) Target - Select Folder option (there are many other publishing options but we are going with folder). Next
	c) Location - Select folder where you want to publish your web application.

## Hosting on Windows Server

### Enable IIS 
	a) Open "Turn Windows Feature on off" wizard and enable IIS and related services.
		Type localhost in browser address bar, Internet Information Service page will appear, this means your IIS is up and running.
	b) Or type iis in windows search , this will open iis console
	
### Hosting Created .Net Web Application
	a) Open IIS
	b) Sites > Add Website > Add website window will appear
		Site Name = bootcampDotNetApp (or whetever you like)
		This will create application pool with name same as your site name, or you can also select existing app pool.
		Physical path = disk location where your application executables are there.
		Binding
		    - Type : http
			- Ip Address : All Unasinged
			- Port : 5001
			- Host name : blank
	
	c) You will see created new web app in sutes section and new app pool in Application Pools section
	d) Open your created app pool and open it, change .NET CLR version to "No Manged Code" and save it.
	e) Copy your application executables in directory which you specified in physical path while adding website section.
## Check your website
	1) In browser open webapp using address "http:<your external ip>:5001"
	2) This will open your hosted .net web app in your browser. if not follow below troubleshooting tips.
## Trouble Shooting
	1) if application is not accessible usign localhost:5001 address and shows an .net runtime core issue, 
    then install .net runtime core from below link
    [.net Core runtime](https://download.visualstudio.microsoft.com/download/pr/1c12a7f4-1e3b-4d0c-a0f8-a03950187940/15abf24d5330aca4429b6212892ca2ae/dotnet-hosting-3.1.25-win.exe)

    Note - find required .net runtime version as per your application requirement.
	Check your app using address localhost:5001 in browser.
	2) Application is accessible inside server using internal ip or localhost and port number, 
    but not externally using external ip then open port 5001 in firewall by creating new inbound rule.
    This will allow your hosted application accessible through internet using external ip.