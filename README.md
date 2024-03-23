Box Processor Project
The Box Processor project is a console application built on .NET Framework 6.

Key Points:
Startup.cs: The Startup.cs class is used to register all the service dependencies. Class constructors are utilized to inject these dependencies.

Configuration Settings: All configuration settings are declared in the appsettings.json file, including the database connection string and time settings.

Test Project: The project includes a test project that uses the NUnit framework. Currently, there is only one test case, but it can be extended further. For example, you can check for locked files.

Packages Used:

Microsoft.EntityFrameworkCore Version=6.0.28
Microsoft.EntityFrameworkCore.SqlServer Version=6.0.28
Microsoft.EntityFrameworkCore.Tools Version=6.0.28
Microsoft.Extensions.Configuration Version=8.0.0
Microsoft.Extensions.Configuration.Json Version=8.0.0
Microsoft.Extensions.DependencyInjection Version=8.0.0
EF Core: The project uses Entity Framework Core for object-relational mapping.

Retry Mechanisms:

There is a retry mechanism for monitoring input files if they are already locked. This is driven by the MaxAttempt setting in the configuration file.
Additionally, there is a retry mechanism if a file fails to process the first time. This is driven by the Max_RETRY variable (which can be put in the settings file) in the FileTrackingService class.
Batch Processing:

The project allows for a certain number of files to be processed to the database using a batch size setting in the appsettings file. For example, if there are ten input files and the batch size is set as 5, then the data from the first 5 files will be saved to the database, followed by the next 5 files. This approach improves performance, reduces database load, and optimizes resource utilization.
