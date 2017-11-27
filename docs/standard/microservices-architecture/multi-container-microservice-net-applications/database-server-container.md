---
title: "Pomocí databázový server, který je spuštěn jako kontejner"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Pomocí databázový server, který je spuštěn jako kontejner"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 7e5f33c4e7edf9d0d4551c5125976fcb8fda392f
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="using-a-database-server-running-as-a-container"></a><span data-ttu-id="a252d-104">Pomocí databázový server, který je spuštěn jako kontejner</span><span class="sxs-lookup"><span data-stu-id="a252d-104">Using a database server running as a container</span></span>

<span data-ttu-id="a252d-105">Vaše databáze (SQL Server, PostgreSQL, MySQL atd.) může mít regulární samostatných serverů v clusterech místně nebo v PaaS služeb v cloudu jako databázi SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="a252d-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="a252d-106">Pro vývojové a testovací prostředí s databází spuštěna jako kontejnery je však vhodné, protože nemáte žádné externí závislosti a jednoduše spuštěná docker compose příkaz spustí celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a252d-106">However, for development and test environments, having your databases running as containers is convenient, because you do not have any external dependency, and simply running the docker-compose command starts the whole application.</span></span> <span data-ttu-id="a252d-107">Tyto databáze jako kontejnery s je také výborně hodí pro integraci testy, protože databáze je spuštěna v kontejneru a vždy naplněný stejná ukázková data, aby mohli být předvídatelnější testy.</span><span class="sxs-lookup"><span data-stu-id="a252d-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="a252d-108">SQL Server běžící jako kontejner s databází související mikroslužbu</span><span class="sxs-lookup"><span data-stu-id="a252d-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="a252d-109">V eShopOnContainers, je kontejner s názvem sql.data definované v [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) soubor, který spouští server SQL Server pro Linux s všech databází systému SQL Server potřebné pro mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="a252d-109">In eShopOnContainers, there is a container named sql.data defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file that runs SQL Server for Linux with all the SQL Server databases needed for the microservices.</span></span> <span data-ttu-id="a252d-110">(Můžete také mít jednoho kontejneru typu SQL Server pro každou databázi, ale které by vyžadovaly další paměť přiřazená Docker.) V mikroslužeb důležité je, že každý mikroslužbu vlastníkem souvisejících dat, proto jeho související databáze SQL v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="a252d-110">(You could also have one SQL Server container for each database, but that would require more memory assigned to Docker.) The important point in microservices is that each microservice owns its related data, therefore its related SQL database in this case.</span></span> <span data-ttu-id="a252d-111">Ale databáze může být odkudkoli.</span><span class="sxs-lookup"><span data-stu-id="a252d-111">But the databases can be anywhere.</span></span>

<span data-ttu-id="a252d-112">Kontejner v ukázkové aplikace, které lze nastavit následující kód YAML v docker-compose.yml souboru, který se spustí při spuštění systému SQL Server docker vytvořit zálohu.</span><span class="sxs-lookup"><span data-stu-id="a252d-112">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run docker-compose up.</span></span> <span data-ttu-id="a252d-113">Všimněte si, že má kód YAML konsolidovat informace o konfiguraci ze souboru obecného docker-compose.yml a soubor docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="a252d-113">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="a252d-114">(By obvykle jednotlivé nastavení prostředí základní nebo statické informace související s bitovou kopii systému SQL Server.)</span><span class="sxs-lookup"><span data-stu-id="a252d-114">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
sql.data:
  image: microsoft/mssql-server-linux
  environment:
    - SA_PASSWORD=your@password
    - ACCEPT_EULA=Y
  ports:
    - "5434:1433"
```

<span data-ttu-id="a252d-115">Následující docker, spusťte příkaz můžete spustit tento kontejner:</span><span class="sxs-lookup"><span data-stu-id="a252d-115">The following docker run command can run that container:</span></span>

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD= your@password' -p 1433:1433 -d microsoft/mssql-server-linux
```

<span data-ttu-id="a252d-116">Pokud nasazujete aplikaci s více kontejneru jako eShopOnContainers, je však pohodlnější použití docker tvoří až příkaz tak, aby ji nasadí všechny kontejnery, které jsou požadované pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="a252d-116">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the docker-compose up command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="a252d-117">Při prvním spuštění tohoto kontejneru systému SQL Server, inicializuje kontejneru systému SQL Server s heslem, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="a252d-117">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="a252d-118">Jakmile systém SQL Server běží jako kontejner, můžete aktualizovat databázi připojením přes všechny regulární připojení SQL, například z SQL Server Management Studio, Visual Studio nebo C\# kódu.</span><span class="sxs-lookup"><span data-stu-id="a252d-118">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="a252d-119">Aplikace eShopOnContainers inicializuje každou mikroslužbu databázi s ukázkovými daty synchronizace replik indexů s daty při spuštění, jak je popsáno v následující části.</span><span class="sxs-lookup"><span data-stu-id="a252d-119">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="a252d-120">S SQL Server běžící jako kontejner není právě užitečné pro ukázku kde nebudete mít přístup k instanci systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a252d-120">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="a252d-121">Jak je uvedeno je také výborně hodí pro vývoj a testování prostředí, aby mohli snadno testy integrace od vyčištění bitové kopie systému SQL Server a známých dat seedingem nové ukázková data.</span><span class="sxs-lookup"><span data-stu-id="a252d-121">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="a252d-122">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="a252d-122">Additional resources</span></span>

-   <span data-ttu-id="a252d-123">**Bitovou kopii SQL serveru Docker systémem Linux, Mac nebo Windows**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)</span><span class="sxs-lookup"><span data-stu-id="a252d-123">**Run the SQL Server Docker image on Linux, Mac, or Windows**
[*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)</span></span>

-   <span data-ttu-id="a252d-124">**Připojení a dotazování systému SQL Server v systému Linux pomocí sqlcmd**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)</span><span class="sxs-lookup"><span data-stu-id="a252d-124">**Connect and query SQL Server on Linux with sqlcmd**
[*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)</span></span>

### <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="a252d-125">Synchronizace replik indexů s testovací data při spuštění webové aplikace</span><span class="sxs-lookup"><span data-stu-id="a252d-125">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="a252d-126">Chcete-li přidat data do databáze při spuštění aplikace, můžete přidat kód jako následující konfigurace metody ve třídě spuštění projektu webového rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="a252d-126">To add data to the database when the application starts up, you can add code like the following to the Configure method in the Startup class of the Web API project:</span></span>

```csharp
public class Startup
{
    // Other Startup code...
    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure code...
        // Seed data through our custom class
        CatalogContextSeed.SeedAsync(app)
            .Wait();
        // Other Configure code...
    }
}
```

<span data-ttu-id="a252d-127">Následující kód ve třídě vlastní CatalogContextSeed naplní data.</span><span class="sxs-lookup"><span data-stu-id="a252d-127">The following code in the custom CatalogContextSeed class populates the data.</span></span>

```csharp
public class CatalogContextSeed
{
    public static async Task SeedAsync(IApplicationBuilder applicationBuilder)
    {
        var context = (CatalogContext)applicationBuilder
            .ApplicationServices.GetService(typeof(CatalogContext));
        using (context)
        {
            context.Database.Migrate();
            if (!context.CatalogBrands.Any())
            {
                context.CatalogBrands.AddRange(
                    GetPreconfiguredCatalogBrands());
                await context.SaveChangesAsync();
            }
            if (!context.CatalogTypes.Any())
            {
                context.CatalogTypes.AddRange(
                    GetPreconfiguredCatalogTypes());
                await context.SaveChangesAsync();
            }
        }
    }

    static IEnumerable<CatalogBrand> GetPreconfiguredCatalogBrands()
    {
        return new List<CatalogBrand>()
       {
           new CatalogBrand() { Brand = "Azure"},
           new CatalogBrand() { Brand = ".NET" },
           new CatalogBrand() { Brand = "Visual Studio" },
           new CatalogBrand() { Brand = "SQL Server" }
       };
    }

    static IEnumerable<CatalogType> GetPreconfiguredCatalogTypes()
    {
        return new List<CatalogType>()
        {
            new CatalogType() { Type = "Mug"},
            new CatalogType() { Type = "T-Shirt" },
            new CatalogType() { Type = "Backpack" },
            new CatalogType() { Type = "USB Memory Stick" }
        };
    }
}
```

<span data-ttu-id="a252d-128">Při spuštění testů integrace s způsob generování dat, které jsou konzistentní s testy integrace je užitečné.</span><span class="sxs-lookup"><span data-stu-id="a252d-128">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="a252d-129">Schopnost vytvářet všechno od začátku, včetně instance systému SQL Server běžící na kontejner, je velmi užitečná pro testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="a252d-129">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="a252d-130">EF InMemory základní databáze a SQL Server běžící jako kontejner</span><span class="sxs-lookup"><span data-stu-id="a252d-130">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="a252d-131">Jiné dobrou volbou při spouštění testů je použití zprostředkovatele databáze Entity Framework InMemory.</span><span class="sxs-lookup"><span data-stu-id="a252d-131">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="a252d-132">Tato konfigurace můžete zadat v metodě ConfigureServices třída při spuštění v projektu webového rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="a252d-132">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

```csharp
public class Startup
{
    // Other Startup code ...
    public void ConfigureServices(IServiceCollection services)
    {
        services.AddSingleton<IConfiguration>(Configuration);
        // DbContext using an InMemory database provider
        services.AddDbContext<CatalogContext>(opt => opt.UseInMemoryDatabase());
        //(Alternative: DbContext using a SQL Server provider
        //services.AddDbContext<CatalogContext>(c =>
        //{
            // c.UseSqlServer(Configuration["ConnectionString"]);
            //
        //});
    }
  
    // Other Startup code ...

}
```

<span data-ttu-id="a252d-133">Když je důležité catch.</span><span class="sxs-lookup"><span data-stu-id="a252d-133">There is an important catch, though.</span></span> <span data-ttu-id="a252d-134">Databázi v paměti nepodporuje mnoho omezení, které jsou specifické pro určitou databázi.</span><span class="sxs-lookup"><span data-stu-id="a252d-134">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="a252d-135">Může například přidat jedinečný index na sloupci ve model EF jádra a zápis testu proti databázi v paměti zkontrolujte, že ho neumožňuje přidat duplicitní hodnota.</span><span class="sxs-lookup"><span data-stu-id="a252d-135">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="a252d-136">Ale pokud používáte databázi v paměti, nemůže zpracovat jedinečné indexy na sloupec.</span><span class="sxs-lookup"><span data-stu-id="a252d-136">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="a252d-137">Databázi v paměti proto není chovají stejně jako skutečné databázi systému SQL Server – ji není emulovat omezení specifické pro databázi.</span><span class="sxs-lookup"><span data-stu-id="a252d-137">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="a252d-138">I tak databázi v paměti je stále užitečné pro testování a při vytváření prototypu.</span><span class="sxs-lookup"><span data-stu-id="a252d-138">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="a252d-139">Ale pokud chcete vytvořit přesný integrace testy, které vzít v úvahu chování implementace konkrétní databázi, budete muset použít skutečné databáze jako SQL Server.</span><span class="sxs-lookup"><span data-stu-id="a252d-139">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="a252d-140">K tomuto účelu systémem SQL Server v kontejneru je dobře choice a přesnější, než EF InMemory základní zprostředkovatel databáze.</span><span class="sxs-lookup"><span data-stu-id="a252d-140">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

### <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="a252d-141">Pomocí služby Redis cache spuštěné v kontejneru</span><span class="sxs-lookup"><span data-stu-id="a252d-141">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="a252d-142">Redis můžete spustit na kontejner, zejména pro vývoj a testování a testování konceptu.</span><span class="sxs-lookup"><span data-stu-id="a252d-142">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="a252d-143">Tento scénář je vhodné, protože může mít všechny svoje závislosti, které jsou spuštěné v kontejnery – nejen pro místní vývoj počítače, ale pro vaše testovací prostředí v nástroji CI/CD kanály.</span><span class="sxs-lookup"><span data-stu-id="a252d-143">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="a252d-144">Když spustíte Redis v produkčním prostředí, je však lepší vyhledejte řešení vysoké dostupnosti jako Redis Microsoft Azure, který se spouští jako PaaS (platforma jako služba).</span><span class="sxs-lookup"><span data-stu-id="a252d-144">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="a252d-145">V kódu stačí změnit připojovací řetězce.</span><span class="sxs-lookup"><span data-stu-id="a252d-145">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="a252d-146">Redis poskytuje bitovou kopii Docker s Redis.</span><span class="sxs-lookup"><span data-stu-id="a252d-146">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="a252d-147">Tento obrázek k dispozici z úložiště Docker Hub na této adrese URL:</span><span class="sxs-lookup"><span data-stu-id="a252d-147">That image is available from Docker Hub at this URL:</span></span>

<span data-ttu-id="a252d-148"><https://hub.docker.com/_/redis/></span><span class="sxs-lookup"><span data-stu-id="a252d-148"><https://hub.docker.com/_/redis/></span></span>

<span data-ttu-id="a252d-149">Kontejner Docker Redis můžete spustit přímo spuštěním následujícího příkazu příkazového řádku Dockeru v příkazovém řádku:</span><span class="sxs-lookup"><span data-stu-id="a252d-149">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```
  docker run --name some-redis -d redis
```

<span data-ttu-id="a252d-150">Bitovou kopii Redis zahrnuje zveřejněte: 6379 (port je používán Redis), takže standardní propojení kontejner bude zpřístupněte ji automaticky propojené kontejnery.</span><span class="sxs-lookup"><span data-stu-id="a252d-150">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="a252d-151">Mikroslužbu basket.api v eShopOnContainers, používá spuštěna jako kontejner mezipaměti Redis.</span><span class="sxs-lookup"><span data-stu-id="a252d-151">In eShopOnContainers, the basket.api microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="a252d-152">Tento kontejner basket.data je definována v rámci více kontejner docker-compose.yml souboru, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="a252d-152">That basket.data container is defined as part of the multi-container docker-compose.yml file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="a252d-153">Tento kód v docker-compose.yml definuje kontejner s názvem basket.data na základě bitové kopie redis a publikování port 6379 interně, což znamená, že bude dostupný pouze z jiných kontejnerů běžící v rámci hostitelů Docker.</span><span class="sxs-lookup"><span data-stu-id="a252d-153">This code in the docker-compose.yml defines a container named basket.data based on the redis image and publishing the port 6379 internally, meaning that it will be accessible only from other containers running within the Docker host.</span></span>

<span data-ttu-id="a252d-154">Nakonec v soubor docker-compose.override.yml mikroslužbu basket.api pro ukázku eShopOnContainers definuje připojovací řetězec k použití pro tento kontejner Redis:</span><span class="sxs-lookup"><span data-stu-id="a252d-154">Finally, in the docker-compose.override.yml file, the basket.api microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```


>[!div class="step-by-step"]
<span data-ttu-id="a252d-155">[Předchozí] (více-container-aplikace docker-compose.md) [Další] (integrace událostí – na základě mikroslužbu communications.md)</span><span class="sxs-lookup"><span data-stu-id="a252d-155">[Previous] (multi-container-applications-docker-compose.md) [Next] (integration-event-based-microservice-communications.md)</span></span>
