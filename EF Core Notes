## Entity Framework Core Advanced

### IMPORTANT - .NET 10 Version
	Hey Developers,

	.NET 10 is here 🎉 – and yes, you can absolutely use it with this course.

	The core concepts, APIs, and patterns we use still work perfectly on .NET 10. You might see small differences in project templates or boilerplate code, but the lessons, code, and techniques remain valid and compatible.

	Where .NET 10 introduces meaningful changes or improvements, I’ll update the course or add notes so you can take advantage of them.

	Happy coding and happy hunting!
	
### What is EF Core(Entity Framework Core) ?

	- Its an official Object Relational Mapper
	- EF Core is an open  source ORM library with APIs that makes is easy for use to interact with our database while writing code.
	- Its an wrapper around the application and provided futures that can easily talk to the databse with less code.
	
#### Benefits
		Increases productivity while eliminating repeating code and allowing you to  connect to many data stores while retaining a consistent  code base.
		
**Native C# Syntax**
			LINQ is dialect of C# and allows you to conduct database operations without needing to write SQL statemenet in C# code.
		
**Fast Database Operations**
			EF Core is constantly being improved is becomes more performant with each new release.
		
**Migrations and Databse Tracking**
			Migrations allows you to track all changes against the database schema and rollback as needed.
		
**Code/Database First Support**
			Code first development lets is model the database from code. EF Core can also model and existing database.
		
**Multiple database supported**
		EF Core works with  SQl Server/Azure, SQL Database, SQLite, Azure Cosmos, DB, MySql, PostGreSQL and many more databases.
		
**Testability**
		EF Core is built to support integration testing in application development. This provides a layer of sureness in your business logic.
		
#### Enterprise Ready
		EF Core used in millions of applications and its stable, robust and high-performance enough to handle extreme workloads applications.
		

**NOTE:** EF Core library allows you to use LINQ queries to manipulate data.

### What LINQ ?
	
	1. Language Integrated Query(LINQ)
	2. Queries are written directly in C# syntax
	3. Translated to SQL for database execution
	4. Can be used for non-database operations, like regular lists/collections
	
	There are two type of LINQ syntax
	
	- Query Syntax - Basically used in the SQL query
		var qNames = from name in listOfNames where name.Length <= 8 select name;
		
	- Method Syntax - This is used in C-Sharp code to perform some operation
		var mNames = listOfNames.Where(name => name.Length <= 8);
	
	
## EF Core version history
	Version	Release year	Important features
	EF Core 1.0	2016	Initial release, LINQ queries, migrations, basic ORM functionality
	EF Core 1.1	2016	Data seeding improvements, DbContext enhancements
	EF Core 2.0	2017	Entity navigation improvements, query filters, better LINQ support
	EF Core 2.1	2018	Lazy loading, value conversions, query types
	EF Core 2.2	2018	Spatial data support, query improvements
	EF Core 3.0	2019	LINQ query overhaul, restricted client-side evaluation
	EF Core 3.1	2019	LTS release, stability and performance improvements
	EF Core 5.0	2020	Many-to-many relationships, split queries, filtered Include
	EF Core 6.0	2021	LTS release, compiled models, temporal tables
	EF Core 7.0	2022	JSON column support, bulk update and delete (ExecuteUpdate, ExecuteDelete)
	EF Core 8.0	2023	LTS release, complex types, primitive collections
	EF Core 9.0	2024	Improved LINQ translation, performance and migration enhancements
	EF Core 10.0	2025	LTS release, improved LINQ, JSON and SQL Server capabilities

	Version	Release year	Major improvements
	EF Core 10.0	2025	Named query filters, vector search, improved JSON support, LeftJoin and RightJoin
	EF Core 11.0	2026 (planned)	Next major release; check Microsoft's release notes for final features
	
## Toolset Overview

	Visual Studio
	- Flagship IDE for .NET Development. It has a Package Manager Console where some EF Core commands can be run.
	
## Install Dotnet and tools

	dotnet tool install --global dotnet-ef
	dotnet tool update --global dotnet-ef
	
## How to create the EF Core Project for practice

Create a New Project add a solution

add a Class Library => EntitiFramework.Data
add a Class Library => EntitiFramework.Domain

## Database Context

	It is an abstraction of databse structure in code
	Lists the models and their database table names
	In application run time it instantiates a database connection
	Allows for on creation customizations and custom table configurations


```csharp
	public class FootballLeageDbContext: DbContext {
		protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder){}
		
		protected override void OnModelCreating(ModelBuilder modeBuilder){}
		
		public DbSet<Team> Teams {get; set;}
		public DbSet<League> Leagues {get; set;}
		public DbSet<Match> Matchs {get; set;}
		public DbSet<Coach> Coachs {get; set;}
		
	}
```

**DbContext** - It is a standard class that you get with entity framework core that basically it says to the C-sharp class into an actual databse context class that represents the database
				here the defined data models are expected to be mapped with the actual tables.
				
**DbSet** - Defines the actual tables in the database

### Install EntitiFramework Core

dotnet add package Microsoft.EntityFrameworkCore

dotnet add package Microsoft.EntityFrameworkCore --version 10.0.0

dotnet add package Microsoft.EntityFrameworkCore.SqlServer --version 10.0.0

dotnet add package Microsoft.EntityFrameworkCore.Tools --version 10.0.0

dotnet add package Microsoft.EntityFrameworkCore.Design --version 10.0.0

dotnet add package Microsoft.EntityFrameworkCore.Sqlite --version 10.0.0

## Database Support

## What are Migrations ?

Code first database development 

The Challenges

Database changes are difficult  to track
No version control for database
Manual backup and restore procedures

 
Add Migrations
==============

**Open Package Manager Console**
--------------------------------

Add-Migration InitialMigration
------------------------------

To undo this action, use Remove-Migration.
 


After the migration command run, there will be a migration file will be generated

There will be two methods

Up() - this method takes care what sould be done to the database


Down() - this should rollback/undo the changes what is done to the database


Update-Database
---------------
Once the above command run, Applying migration '20261111131729_InitialMigration' message will be displayed

After this Install DB Browser for SQLite
open the DB which is got Created through migration (FootballLeage_EfCore.db)


Database First Development
--------------------------
EF Core helps to reverse engineering the existing database and create models and other related files
Scaffold-DbContext 'Data Source=(localdb)\MSSQLLocalDB; Initial Catelog=FootballLeage_EfCore; Encrypt=False' Microsoft.EntityFrameworkCore.SqlServer -ContextDir ScaffoldContext -OutputDir ScaffoldModels -Force

Seeding Data
------------
Data seeding in EF Core means inserting initial data or default data into you database automatically.

```csharp
	 protected override void OnModelCreating(ModelBuilder modelBuilder)
	 {
		 modelBuilder.Entity<Team>().HasData(
			 new Team
			 {
				 TeamId = 1,
				 Name = "Real  Madrid",
				 CreatedDate = DateTimeOffset.UtcNow.DateTime
			 },
			 new Team
			 {
				 TeamId = 2,
				 Name = "Barcelona",
				 CreatedDate = DateTimeOffset.UtcNow.DateTime
			 },
			 new Team
			 {
				 TeamId = 3,
				 Name = "Manchester United",
				 CreatedDate = DateTimeOffset.UtcNow.DateTime
			 }
			 );
	 }
```

	Add-Migration SeededTeams -Context FootballLeageDbContext

	Update-Database -Context FootballLeageDbContext

Set Dynamic DB Path
-------------------

```csharp
    public FootballLeageDbContext()
    {
        var folder = Environment.SpecialFolder.LocalApplicationData;
        var path = Environment.GetFolderPath(folder);
        DbPath = Path.Combine(path, "FootballLeage_EfCore.db");
    }

   public string DbPath { get; private set; }

   protected override void OnConfiguring(DbContextOptionsBuilder optionsBuilder)
   {
       //Using SQL Server
       //optionsBuilder.UseSqlServer("Data Source=(localdb)\\MSSQLLocalDB;Initial Catalog=FootballLeage_EfCore;Encrypt = False");
       optionsBuilder.UseSqlite($"Data Source={DbPath}")
           .LogTo(Console.WriteLine, LogLevel.Information)
           .EnableSensitiveDataLogging()
           .EnableDetailedErrors();

   }
```
Now run the below command

**Run:  Update-Database**

if there is a error for multiple context, in that case specify the context

***Update-Database -Context FootballLeageDbContext***

### Quering Basics ###

// First we need an instance of the Context
var context = new FootballLeageDbContext();

// Select all the teams from the database
// Raw SQL Query
// SELECT * FROM Teams

//#### LINQ Query

```csharp
var teams = context.Teams.ToList();

foreach(var team in teams)
{
    Console.WriteLine($"Name: {team.Name},Team Id: {team.TeamId}, Created Date: {team.CreatedDate}");
}
```

**DbContext** is the main class in Entity Framework Core that represents a session with the database.
It communicates with the database and manages entities, queries, and changes.

### Asynchronous Programming in EF Core

EF Core asynchronous programming allows database operations to execute without blocking the calling thread while waitning for the database response.
We use methods like ToListAsync() and SaveChangesAsync() to improve application scalibility and responsiveness.
 
## Ways to use the DbContext(FootballLeageDbContext)
// First we need an instance of the Context
//using (var context = new FootballLeageDbContext()) { 
//    //now the context is limited to this block of code and will be disposed of after the block is executed`

//};

//var context = new FootballLeageDbContext();

using var context = new FootballLeageDbContext();


## LINK Queries
===============

//#### LINQ Query
```csharp
async Task GetAllTeams()
{
    var teams = context.Teams.ToList();
    foreach (var t in teams)
    {
        Console.WriteLine($"Name: {t.Name},Team Id: {t.TeamId}, Created Date: {t.CreatedDate}");
    }
}
```


```csharp
async Task GetOneTeam()
{

    // Select all the teams from the database
    // Raw SQL Query
    // SELECT * FROM Teams



    //Selecting a single record from the database - This gets the first record from the database
    //### This will throw an exception if there is no record in the database
    //var teamOne = await context.Teams.FirstAsync();
    //### This will not throw an exception if there is no record in the database, it will return null
    //var teamOne = await context.Teams.FirstOrDefaultAsync();

    //Selecting a single record from the database - This gets the first record from the database based on a condition
    //### This will throw an exception if there is no record in the database
    //var teamTwo = await context.Teams.FirstAsync(q=> q.TeamId == 2);

    //### This will not throw an exception if there is no record in the database, it will return null
    //var teamTwo = await context.Teams.FirstOrDefaultAsync(q => q.TeamId == 2);

    // Selecting a single record from the database - only one expected to be returned
    //var teamThree = await context.Teams.SingleAsync(team => team.TeamId == 2);

    //var teamFour = await context.Teams.SingleOrDefaultAsync(team => team.TeamId == 2);
}
```

```csharp
var teamFiltered = await context.Teams.Where(q => q.Name == "Real  Madrid").ToListAsync();
// Where() - Is a purely C-Sharp method that is used to filter the data based on a condition .
// It is not executed until the ToListAsync method is called. This is known as deferred execution.
//=================================================================================================
// ToListAsync() - Is an executable method that will execute the query and return the results as a list.
// It is an asynchronous method that returns a Task<List<Team>>.
// The query is not executed until the ToListAsync method is called. This is known as deferred execution.
```

```csharp
//Select Filtered team
await GetFilterTeams();

async Task GetFilterTeams()
{
    Console.WriteLine("Enter the team name to filter:");
    var searchTerm = Console.ReadLine();
    var teamFiltered = await context.Teams.Where(q => q.Name == searchTerm).ToListAsync();

    foreach (var team in teamFiltered)
    {
        Console.WriteLine($"Team Name: {team.Name} ");
    }

    //The Contains() method is similar to Like() in SQL, to filter the data based  on a condition. This is known as deferred execution.
    //var partialTeamFiltered = await context.Teams.Where(q => q.Name.Contains(searchTerm)).ToListAsync();
    // SELECT * FROM Teams WHERE Name LIKE '%searchTerm%'

    //EF Core way of writing the partial match
    var partialTeamFiltered = await context.Teams.Where(q => EF.Functions.Like(q.Name, $"%{searchTerm}%")).ToListAsync();
    foreach (var team in teamFiltered)
    {
        Console.WriteLine($"partialTeamFiltered Name: {team.Name} ");
    }
}
```
