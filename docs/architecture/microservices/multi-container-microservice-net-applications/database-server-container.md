---
title: Použití databázového serveru spuštěného jako kontejner
description: Pochopit, že je důležité používat databázový server spuštěný jako kontejner pouze pro vývoj. Nikdy pro výrobu.
ms.date: 01/30/2020
ms.openlocfilehash: 0cbc933003aac10970814378c27e88b5cb0ddbe5
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77628524"
---
# <a name="use-a-database-server-running-as-a-container"></a><span data-ttu-id="8946f-104">Použití databázového serveru spuštěného jako kontejner</span><span class="sxs-lookup"><span data-stu-id="8946f-104">Use a database server running as a container</span></span>

<span data-ttu-id="8946f-105">Databáze (SQL Server, PostgreSQL, MySQL atd.) můžete mít na běžných samostatných serverech, v místních clusterech nebo ve službách PaaS v cloudu, jako je Azure SQL DB.</span><span class="sxs-lookup"><span data-stu-id="8946f-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="8946f-106">Však pro vývoj a testovací prostředí s databázemi spuštěny jako kontejnery je vhodná, protože `docker-compose up` nemáte žádné externí závislost a jednoduše spuštění příkazu spustí celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8946f-106">However, for development and test environments, having your databases running as containers is convenient, because you don't have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="8946f-107">S tyto databáze jako kontejnery je také skvělé pro testy integrace, protože databáze je spuštěna v kontejneru a je vždy naplněna stejnými ukázkovými daty, takže testy mohou být předvídatelnější.</span><span class="sxs-lookup"><span data-stu-id="8946f-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="8946f-108">SQL Server spuštěný jako kontejner s databází související s mikroslužbami</span><span class="sxs-lookup"><span data-stu-id="8946f-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="8946f-109">V eShopOnContainers je kontejner s `sqldata`názvem , jak je definováno v souboru [docker-compose.yml,](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) který spouští instanci SQL Server pro Linux s databázemi SQL pro všechny mikroslužby, které je potřebují.</span><span class="sxs-lookup"><span data-stu-id="8946f-109">In eShopOnContainers, there's a container named `sqldata`, as defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file, that runs a SQL Server for Linux instance with the SQL databases for all microservices that need one.</span></span>

<span data-ttu-id="8946f-110">Klíčovým bodem v mikroslužbách je, že každá mikroslužba vlastní související data, takže by měla mít vlastní databázi.</span><span class="sxs-lookup"><span data-stu-id="8946f-110">A key point in microservices is that each microservice owns its related data, so it should have its own database.</span></span> <span data-ttu-id="8946f-111">Databáze však může být kdekoli.</span><span class="sxs-lookup"><span data-stu-id="8946f-111">However, the databases can be anywhere.</span></span> <span data-ttu-id="8946f-112">V tomto případě jsou všechny ve stejném kontejneru, aby požadavky na paměť Docker udála co nejnižší.</span><span class="sxs-lookup"><span data-stu-id="8946f-112">In this case, they are all in the same container to keep Docker memory requirements as low as possible.</span></span> <span data-ttu-id="8946f-113">Mějte na paměti, že se jedná o dostatečně dobré řešení pro vývoj a možná i pro testování, ale ne pro výrobu.</span><span class="sxs-lookup"><span data-stu-id="8946f-113">Keep in mind that this is a good-enough solution for development and, perhaps, testing but not for production.</span></span>

<span data-ttu-id="8946f-114">Kontejner SERVERU SQL Server v ukázkové aplikaci je nakonfigurován s následujícím kódem YAML v souboru `docker-compose up`docker-compose.yml, který se spustí při spuštění .</span><span class="sxs-lookup"><span data-stu-id="8946f-114">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="8946f-115">Všimněte si, že kód YAML má konsolidované informace o konfiguraci z obecného souboru docker-compose.yml a souboru docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="8946f-115">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="8946f-116">(Obvykle byste oddělit nastavení prostředí ze základní nebo statické informace týkající se bitové kopie serveru SQL Server.)</span><span class="sxs-lookup"><span data-stu-id="8946f-116">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="8946f-117">Podobným způsobem, namísto `docker-compose`použití , `docker run` následující příkaz můžete spustit tento kontejner:</span><span class="sxs-lookup"><span data-stu-id="8946f-117">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

<span data-ttu-id="8946f-118">Pokud však nasazujete aplikaci s více kontejnery, jako je `docker-compose up` eShopOnContainers, je vhodnější použít příkaz tak, aby nasazoval všechny požadované kontejnery pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8946f-118">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="8946f-119">Při prvním spuštění tohoto kontejneru SQL Server kontejner inicializuje SQL Server s heslem, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="8946f-119">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="8946f-120">Jakmile je SQL Server spuštěn jako kontejner, můžete databázi aktualizovat připojením prostřednictvím běžného připojení SQL,\# například z kódu SQL Server Management Studio, Visual Studio nebo C.</span><span class="sxs-lookup"><span data-stu-id="8946f-120">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="8946f-121">Aplikace eShopOnContainers inicializuje každou databázi mikroslužeb se ukázkovými daty tím, že ji osevá daty při spuštění, jak je vysvětleno v následující části.</span><span class="sxs-lookup"><span data-stu-id="8946f-121">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="8946f-122">S SQL Server běží jako kontejner není užitečné pouze pro ukázku, kde nemusí mít přístup k instanci SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8946f-122">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="8946f-123">Jak již bylo uvedeno, je také skvělé pro vývoj a testování prostředí, takže můžete snadno spustit integrační testy počínaje čistou bitovou kopii serveru SQL Server a známých dat osiva nových ukázkových dat.</span><span class="sxs-lookup"><span data-stu-id="8946f-123">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="8946f-124">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="8946f-124">Additional resources</span></span>

- <span data-ttu-id="8946f-125">**Spuštění bitové kopie SQL Server Dockeru na Linuxu, Macu nebo Windows** </span><span class="sxs-lookup"><span data-stu-id="8946f-125">**Run the SQL Server Docker image on Linux, Mac, or Windows** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- <span data-ttu-id="8946f-126">**Připojení a dotazování SQL Serveru na Linuxu pomocí sqlcmd** </span><span class="sxs-lookup"><span data-stu-id="8946f-126">**Connect and query SQL Server on Linux with sqlcmd** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="8946f-127">Nastavení testovacích dat při spuštění webové aplikace</span><span class="sxs-lookup"><span data-stu-id="8946f-127">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="8946f-128">Chcete-li přidat data do databáze při spuštění aplikace, můžete `Main` přidat kód, jako je následující metody ve `Program` třídě projektu webového rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="8946f-128">To add data to the database when the application starts up, you can add code like the following to the `Main` method in the `Program` class of the Web API project:</span></span>

```csharp
public static int Main(string[] args)
{
    var configuration = GetConfiguration();

    Log.Logger = CreateSerilogLogger(configuration);

    try
    {
        Log.Information("Configuring web host ({ApplicationContext})...", AppName);
        var host = CreateHostBuilder(configuration, args);

        Log.Information("Applying migrations ({ApplicationContext})...", AppName);
        host.MigrateDbContext<CatalogContext>((context, services) =>
        {
            var env = services.GetService<IWebHostEnvironment>();
            var settings = services.GetService<IOptions<CatalogSettings>>();
            var logger = services.GetService<ILogger<CatalogContextSeed>>();

            new CatalogContextSeed()
                .SeedAsync(context, env, settings, logger)
                .Wait();
        })
        .MigrateDbContext<IntegrationEventLogContext>((_, __) => { });

        Log.Information("Starting web host ({ApplicationContext})...", AppName);
        host.Run();

        return 0;
    }
    catch (Exception ex)
    {
        Log.Fatal(ex, "Program terminated unexpectedly ({ApplicationContext})!", AppName);
        return 1;
    }
    finally
    {
        Log.CloseAndFlush();
    }
}
```

<span data-ttu-id="8946f-129">Existuje důležité upozornění při použití migrace a vysazení databáze při spuštění kontejneru.</span><span class="sxs-lookup"><span data-stu-id="8946f-129">There's an important caveat when applying migrations and seeding a database during container startup.</span></span> <span data-ttu-id="8946f-130">Vzhledem k tomu, že databázový server nemusí být z jakéhokoli důvodu k dispozici, je nutné zpracovat opakování při čekání na server, který má být k dispozici.</span><span class="sxs-lookup"><span data-stu-id="8946f-130">Since the database server might not be available for whatever reason, you must handle retries while waiting for the server to be available.</span></span> <span data-ttu-id="8946f-131">Tato logika opakování je `MigrateDbContext()` zpracována metodou rozšíření, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="8946f-131">This retry logic is handled by the `MigrateDbContext()` extension method, as shown in the following code:</span></span>

```cs
public static IWebHost MigrateDbContext<TContext>(
    this IWebHost host,
    Action<TContext,
    IServiceProvider> seeder)
      where TContext : DbContext
{
    var underK8s = host.IsInKubernetes();

    using (var scope = host.Services.CreateScope())
    {
        var services = scope.ServiceProvider;

        var logger = services.GetRequiredService<ILogger<TContext>>();

        var context = services.GetService<TContext>();

        try
        {
            logger.LogInformation("Migrating database associated with context {DbContextName}", typeof(TContext).Name);

            if (underK8s)
            {
                InvokeSeeder(seeder, context, services);
            }
            else
            {
                var retry = Policy.Handle<SqlException>()
                    .WaitAndRetry(new TimeSpan[]
                    {
                    TimeSpan.FromSeconds(3),
                    TimeSpan.FromSeconds(5),
                    TimeSpan.FromSeconds(8),
                    });

                //if the sql server container is not created on run docker compose this
                //migration can't fail for network related exception. The retry options for DbContext only
                //apply to transient exceptions
                // Note that this is NOT applied when running some orchestrators (let the orchestrator to recreate the failing service)
                retry.Execute(() => InvokeSeeder(seeder, context, services));
            }

            logger.LogInformation("Migrated database associated with context {DbContextName}", typeof(TContext).Name);
        }
        catch (Exception ex)
        {
            logger.LogError(ex, "An error occurred while migrating the database used on context {DbContextName}", typeof(TContext).Name);
            if (underK8s)
            {
                throw;          // Rethrow under k8s because we rely on k8s to re-run the pod
            }
        }
    }

    return host;
}
```

<span data-ttu-id="8946f-132">Následující kód ve vlastní třídě CatalogContextSeed naplní data.</span><span class="sxs-lookup"><span data-stu-id="8946f-132">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="8946f-133">Při spuštění testů integrace, které mají způsob, jak generovat data konzistentní s integrační testy je užitečné.</span><span class="sxs-lookup"><span data-stu-id="8946f-133">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="8946f-134">Být schopen vytvořit vše od začátku, včetně instance SQL Server spuštěný v kontejneru, je skvělé pro testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="8946f-134">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="8946f-135">EF Core InMemory databáze versus SQL Server běží jako kontejner</span><span class="sxs-lookup"><span data-stu-id="8946f-135">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="8946f-136">Další dobrou volbou při spuštění testů je použití zprostředkovatele databáze Entity Framework InMemory.</span><span class="sxs-lookup"><span data-stu-id="8946f-136">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="8946f-137">Tuto konfiguraci můžete určit v metodě ConfigureServices třídy Startup v projektu webového rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="8946f-137">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="8946f-138">Je tu důležitý úlovek, ačkoli.</span><span class="sxs-lookup"><span data-stu-id="8946f-138">There is an important catch, though.</span></span> <span data-ttu-id="8946f-139">Databáze v paměti nepodporuje mnoho omezení, které jsou specifické pro konkrétní databázi.</span><span class="sxs-lookup"><span data-stu-id="8946f-139">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="8946f-140">Můžete například přidat jedinečný index do sloupce v modelu EF Core a napsat test proti databázi v paměti a zkontrolovat, zda neumožňuje přidat duplicitní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="8946f-140">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="8946f-141">Ale pokud používáte databázi v paměti, nelze zpracovat jedinečné indexy na sloupec.</span><span class="sxs-lookup"><span data-stu-id="8946f-141">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="8946f-142">Proto databáze v paměti nechová přesně stejné jako databáze reálné SQL Server – neemuluje omezení specifické pro databázi.</span><span class="sxs-lookup"><span data-stu-id="8946f-142">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="8946f-143">I tak je databáze v paměti stále užitečná pro testování a vytváření prototypů.</span><span class="sxs-lookup"><span data-stu-id="8946f-143">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="8946f-144">Ale pokud chcete vytvořit přesné integrační testy, které berou v úvahu chování konkrétní implementace databáze, je třeba použít skutečnou databázi, jako je SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8946f-144">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="8946f-145">Pro tento účel je spuštění serveru SQL Server v kontejneru skvělou volbou a přesnější než zprostředkovatel databáze EF Core InMemory.</span><span class="sxs-lookup"><span data-stu-id="8946f-145">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

## <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="8946f-146">Použití služby mezipaměti Redis spuštěné v kontejneru</span><span class="sxs-lookup"><span data-stu-id="8946f-146">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="8946f-147">Redis můžete spustit v kontejneru, zejména pro vývoj a testování a pro scénáře proof-of-concept.</span><span class="sxs-lookup"><span data-stu-id="8946f-147">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="8946f-148">Tento scénář je vhodný, protože můžete mít všechny vaše závislosti spuštěny na kontejnerech – nejen pro místní vývojové počítače, ale pro testovací prostředí v kanálech CI/CD.</span><span class="sxs-lookup"><span data-stu-id="8946f-148">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="8946f-149">Když však spustíte Redis v produkčním prostředí, je lepší hledat řešení s vysokou dostupností, jako je Redis Microsoft Azure, které běží jako PaaS (Platforma jako služba).</span><span class="sxs-lookup"><span data-stu-id="8946f-149">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="8946f-150">V kódu stačí změnit připojovací řetězce.</span><span class="sxs-lookup"><span data-stu-id="8946f-150">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="8946f-151">Redis poskytuje image Dockeru s Redis.</span><span class="sxs-lookup"><span data-stu-id="8946f-151">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="8946f-152">Tento obrázek je k dispozici v Docker Hubu na této adrese URL:</span><span class="sxs-lookup"><span data-stu-id="8946f-152">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/_/redis/>

<span data-ttu-id="8946f-153">Kontejner Docker Redis můžete spustit přímo spuštěním následujícího příkazu Cli Dockeru v příkazovém řádku:</span><span class="sxs-lookup"><span data-stu-id="8946f-153">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```console
docker run --name some-redis -d redis
```

<span data-ttu-id="8946f-154">Obrázek Redis obsahuje expose:6379 (port používaný redis), takže standardní propojení kontejnerů bude automaticky k dispozici pro propojené kontejnery.</span><span class="sxs-lookup"><span data-stu-id="8946f-154">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="8946f-155">V eShopOnContainers `basket-api` mikroslužba používá redis cache běží jako kontejner.</span><span class="sxs-lookup"><span data-stu-id="8946f-155">In eShopOnContainers, the `basket-api` microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="8946f-156">Tento `basketdata` kontejner je definován jako součást souboru *docker-compose.yml* s více kontejnery, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8946f-156">That `basketdata` container is defined as part of the multi-container *docker-compose.yml* file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="8946f-157">Tento kód v docker-compose.yml definuje `basketdata` kontejner s názvem na základě image redis a publikování portu 6379 interně.</span><span class="sxs-lookup"><span data-stu-id="8946f-157">This code in the docker-compose.yml defines a container named `basketdata` based on the redis image and publishing the port 6379 internally.</span></span> <span data-ttu-id="8946f-158">To znamená, že bude přístupná pouze z jiných kontejnerů spuštěné v rámci hostitele Dockeru.</span><span class="sxs-lookup"><span data-stu-id="8946f-158">This means that it will only be accessible from other containers running within the Docker host.</span></span>

<span data-ttu-id="8946f-159">Nakonec v souboru *docker-compose.override.yml* `basket-api` mikroslužba pro ukázku eShopOnContainers definuje připojovací řetězec, který se má použít pro tento kontejner Redis:</span><span class="sxs-lookup"><span data-stu-id="8946f-159">Finally, in the *docker-compose.override.yml* file, the `basket-api` microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="8946f-160">Jak již bylo zmíněno dříve, `basketdata` název mikroslužby je vyřešen interní síťové DNS Dockeru.</span><span class="sxs-lookup"><span data-stu-id="8946f-160">As mentioned before, the name of the microservice `basketdata` is resolved by Docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8946f-161">[Předchozí](multi-container-applications-docker-compose.md)
>[další](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="8946f-161">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
