---
title: Použití databázového serveru spuštěného jako kontejner
description: Pochopení důležitosti použití databázového serveru běžícího jako kontejneru pouze pro vývoj. Nikdy pro produkční prostředí.
ms.date: 01/30/2020
ms.openlocfilehash: 0cbc933003aac10970814378c27e88b5cb0ddbe5
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628524"
---
# <a name="use-a-database-server-running-as-a-container"></a><span data-ttu-id="ca077-104">Použití databázového serveru spuštěného jako kontejner</span><span class="sxs-lookup"><span data-stu-id="ca077-104">Use a database server running as a container</span></span>

<span data-ttu-id="ca077-105">Vaše databáze (SQL Server, PostgreSQL, MySQL atd.) můžete mít na běžných samostatných serverech, v místních clusterech nebo v PaaS službách v cloudu, jako je Azure SQL DB.</span><span class="sxs-lookup"><span data-stu-id="ca077-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="ca077-106">Nicméně pro vývojová a testovací prostředí jsou vaše databáze spuštěné jako kontejnery pohodlné, protože nemáte žádnou externí závislost a stačí spustit příkaz `docker-compose up` spustí celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ca077-106">However, for development and test environments, having your databases running as containers is convenient, because you don't have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="ca077-107">Aby byly tyto databáze stejně vhodné pro integrační testy, protože databáze je spuštěna v kontejneru a je vždy naplněna stejnými ukázkovými daty, testy mohou být předvídatelné.</span><span class="sxs-lookup"><span data-stu-id="ca077-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="ca077-108">SQL Server spuštěn jako kontejner s databází související s mikroslužbami</span><span class="sxs-lookup"><span data-stu-id="ca077-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="ca077-109">V eShopOnContainers je k dispozici kontejner s názvem `sqldata`, jak je definován v souboru [Docker-Compose. yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) , který spouští SQL Server pro instanci systému Linux s databázemi SQL pro všechny mikroslužby, které ji potřebují.</span><span class="sxs-lookup"><span data-stu-id="ca077-109">In eShopOnContainers, there's a container named `sqldata`, as defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file, that runs a SQL Server for Linux instance with the SQL databases for all microservices that need one.</span></span>

<span data-ttu-id="ca077-110">Klíčovým bodem v mikroslužbách je, že každá mikroslužba vlastní svoje související data, takže by měla mít vlastní databázi.</span><span class="sxs-lookup"><span data-stu-id="ca077-110">A key point in microservices is that each microservice owns its related data, so it should have its own database.</span></span> <span data-ttu-id="ca077-111">Databáze ale můžou být kdekoli.</span><span class="sxs-lookup"><span data-stu-id="ca077-111">However, the databases can be anywhere.</span></span> <span data-ttu-id="ca077-112">V tomto případě jsou všechny ve stejném kontejneru, aby se požadavky na paměť Docker zachovaly co nejmenším možným způsobem.</span><span class="sxs-lookup"><span data-stu-id="ca077-112">In this case, they are all in the same container to keep Docker memory requirements as low as possible.</span></span> <span data-ttu-id="ca077-113">Mějte na paměti, že toto řešení je dobrým řešením pro vývoj a případně testování, ale ne pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="ca077-113">Keep in mind that this is a good-enough solution for development and, perhaps, testing but not for production.</span></span>

<span data-ttu-id="ca077-114">Kontejner SQL Server v ukázkové aplikaci je nakonfigurován s následujícím YAML kódem v souboru Docker-Compose. yml, který je spuštěn při spuštění `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="ca077-114">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="ca077-115">Všimněte si, že kód YAML má konsolidované informace o konfiguraci z obecného souboru Docker-Compose. yml a souboru Docker-Compose. override. yml.</span><span class="sxs-lookup"><span data-stu-id="ca077-115">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="ca077-116">(Obvykle byste odvolali nastavení prostředí ze základních nebo statických informací, které se vztahují k SQL Server imagi.)</span><span class="sxs-lookup"><span data-stu-id="ca077-116">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="ca077-117">Podobným způsobem namísto použití `docker-compose`může tento kontejner spustit následující `docker run` příkaz:</span><span class="sxs-lookup"><span data-stu-id="ca077-117">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

<span data-ttu-id="ca077-118">Pokud však nasazujete aplikaci s více kontejnery, jako je eShopOnContainers, je vhodnější použít příkaz `docker-compose up`, aby nástroj nasadil všechny požadované kontejnery pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ca077-118">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="ca077-119">Při prvním spuštění tohoto kontejneru SQL Server kontejner inicializuje SQL Server s heslem, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="ca077-119">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="ca077-120">Jakmile SQL Server spustíte jako kontejner, můžete aktualizovat databázi připojením přes jakékoli běžné připojení SQL, například z SQL Server Management Studio, sady Visual Studio nebo kódu\# jazyka C.</span><span class="sxs-lookup"><span data-stu-id="ca077-120">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="ca077-121">Aplikace eShopOnContainers inicializuje každou databázi mikroslužeb pomocí ukázkových dat tím, že je dokončí daty při spuštění, jak je vysvětleno v následující části.</span><span class="sxs-lookup"><span data-stu-id="ca077-121">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="ca077-122">Použití SQL Server jako kontejneru není právě užitečné pro ukázku, ve které nemůžete mít přístup k instanci SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ca077-122">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="ca077-123">Jak je uvedeno, je vhodné také pro vývojová a testovací prostředí, abyste mohli snadno spouštět testy integrace počínaje čistým SQL Server obrázkem a známými daty pomocí osazení nových ukázkových dat.</span><span class="sxs-lookup"><span data-stu-id="ca077-123">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ca077-124">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="ca077-124">Additional resources</span></span>

- <span data-ttu-id="ca077-125">**Spuštění bitové kopie SQL Server Docker v systému Linux, Mac nebo Windows** </span><span class="sxs-lookup"><span data-stu-id="ca077-125">**Run the SQL Server Docker image on Linux, Mac, or Windows** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- <span data-ttu-id="ca077-126">**Připojení a dotazování SQL Server on Linux pomocí sqlcmd** </span><span class="sxs-lookup"><span data-stu-id="ca077-126">**Connect and query SQL Server on Linux with sqlcmd** </span></span>\
  <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="ca077-127">Osazení s testovacími daty při spuštění webové aplikace</span><span class="sxs-lookup"><span data-stu-id="ca077-127">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="ca077-128">Chcete-li přidat data do databáze při spuštění aplikace, můžete do metody `Main` v `Program` třídy projektu webového rozhraní API přidat kód podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="ca077-128">To add data to the database when the application starts up, you can add code like the following to the `Main` method in the `Program` class of the Web API project:</span></span>

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

<span data-ttu-id="ca077-129">Při použití migrace a nastavování databáze při spuštění kontejneru je důležité upozornění.</span><span class="sxs-lookup"><span data-stu-id="ca077-129">There's an important caveat when applying migrations and seeding a database during container startup.</span></span> <span data-ttu-id="ca077-130">Vzhledem k tomu, že databázový server nemusí být k dispozici z jakéhokoli důvodu, je nutné zpracovat opakované pokusy při čekání na dostupnost serveru.</span><span class="sxs-lookup"><span data-stu-id="ca077-130">Since the database server might not be available for whatever reason, you must handle retries while waiting for the server to be available.</span></span> <span data-ttu-id="ca077-131">Tato logika opakování je zpracována metodou rozšíření `MigrateDbContext()`, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="ca077-131">This retry logic is handled by the `MigrateDbContext()` extension method, as shown in the following code:</span></span>

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

<span data-ttu-id="ca077-132">Následující kód ve vlastní třídě CatalogContextSeed naplní data.</span><span class="sxs-lookup"><span data-stu-id="ca077-132">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="ca077-133">Při spuštění integračních testů je užitečné, aby bylo možné generovat data konzistentní s testy Integration.</span><span class="sxs-lookup"><span data-stu-id="ca077-133">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="ca077-134">Schopnost vytvářet vše od začátku, včetně instance SQL Server běžícího na kontejneru, je skvělé pro testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="ca077-134">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="ca077-135">EF Core nepaměťové databáze versus SQL Server spuštěná jako kontejner</span><span class="sxs-lookup"><span data-stu-id="ca077-135">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="ca077-136">Další dobrý volbou při spouštění testů je použití poskytovatele databáze Entity Framework inMemory.</span><span class="sxs-lookup"><span data-stu-id="ca077-136">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="ca077-137">Tuto konfiguraci můžete zadat v metodě ConfigureServices třídy Startup v projektu webového rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="ca077-137">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="ca077-138">K dispozici je i důležité catch.</span><span class="sxs-lookup"><span data-stu-id="ca077-138">There is an important catch, though.</span></span> <span data-ttu-id="ca077-139">Databáze v paměti nepodporuje řadu omezení, která jsou specifická pro konkrétní databázi.</span><span class="sxs-lookup"><span data-stu-id="ca077-139">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="ca077-140">Například můžete přidat jedinečný index pro sloupec v modelu EF Core a zapsat test do databáze v paměti, abyste zkontrolovali, že vám neumožňuje přidat duplicitní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="ca077-140">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="ca077-141">Pokud ale používáte databázi v paměti, nemůžete pro sloupec zpracovávat jedinečné indexy.</span><span class="sxs-lookup"><span data-stu-id="ca077-141">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="ca077-142">Proto se databáze v paměti nechová stejně jako skutečná SQL Server databáze – neemuluje omezení specifická pro databázi.</span><span class="sxs-lookup"><span data-stu-id="ca077-142">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="ca077-143">I tak je databáze v paměti stále užitečná pro testování a vytváření prototypů.</span><span class="sxs-lookup"><span data-stu-id="ca077-143">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="ca077-144">Pokud ale chcete vytvořit přesné integrační testy, které berou v úvahu chování konkrétní implementace databáze, musíte použít skutečnou databázi, jako je SQL Server.</span><span class="sxs-lookup"><span data-stu-id="ca077-144">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="ca077-145">Pro tento účel je spuštění SQL Server v kontejneru skvělým výběrem a přesnější než EF Core poskytovatel databáze inMemory.</span><span class="sxs-lookup"><span data-stu-id="ca077-145">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

## <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="ca077-146">Používání služby Redis Cache spuštěné v kontejneru</span><span class="sxs-lookup"><span data-stu-id="ca077-146">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="ca077-147">Redis můžete spustit na kontejneru, zejména pro vývoj a testování, a pro scénáře testování konceptů.</span><span class="sxs-lookup"><span data-stu-id="ca077-147">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="ca077-148">Tento scénář je vhodný, protože můžete mít všechny závislosti spuštěné v kontejnerech, nikoli jenom pro místní vývojové počítače, ale pro testovací prostředí v kanálech CI/CD.</span><span class="sxs-lookup"><span data-stu-id="ca077-148">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="ca077-149">Pokud ale spustíte Redis v produkčním prostředí, je lepší vyhledat řešení s vysokou dostupností, jako je Redis Microsoft Azure, které běží jako PaaS (platforma jako služba).</span><span class="sxs-lookup"><span data-stu-id="ca077-149">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="ca077-150">V kódu je pouze nutné změnit připojovací řetězce.</span><span class="sxs-lookup"><span data-stu-id="ca077-150">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="ca077-151">Redis poskytuje image Docker s Redis.</span><span class="sxs-lookup"><span data-stu-id="ca077-151">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="ca077-152">Tato bitová kopie je k dispozici z Docker Hub na této adrese URL:</span><span class="sxs-lookup"><span data-stu-id="ca077-152">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/_/redis/>

<span data-ttu-id="ca077-153">Kontejner Docker Redis můžete přímo spustit spuštěním následujícího příkazu Docker CLI na příkazovém řádku:</span><span class="sxs-lookup"><span data-stu-id="ca077-153">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```console
docker run --name some-redis -d redis
```

<span data-ttu-id="ca077-154">Image Redis zahrnuje vystavení: 6379 (port, který používá Redis), takže standardní propojení kontejnerů bude automaticky dostupné pro propojené kontejnery.</span><span class="sxs-lookup"><span data-stu-id="ca077-154">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="ca077-155">V eShopOnContainers používá `basket-api` mikroslužba mezipaměť Redis spuštěnou jako kontejner.</span><span class="sxs-lookup"><span data-stu-id="ca077-155">In eShopOnContainers, the `basket-api` microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="ca077-156">Tento kontejner `basketdata` je definován jako součást souboru *Docker-Compose. yml* s více kontejnery, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ca077-156">That `basketdata` container is defined as part of the multi-container *docker-compose.yml* file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="ca077-157">Tento kód v Docker-Compose. yml definuje kontejner s názvem `basketdata` založený na imagi Redis a interně publikuje port 6379.</span><span class="sxs-lookup"><span data-stu-id="ca077-157">This code in the docker-compose.yml defines a container named `basketdata` based on the redis image and publishing the port 6379 internally.</span></span> <span data-ttu-id="ca077-158">To znamená, že bude přístupný jenom z jiných kontejnerů spuštěných v rámci hostitele Docker.</span><span class="sxs-lookup"><span data-stu-id="ca077-158">This means that it will only be accessible from other containers running within the Docker host.</span></span>

<span data-ttu-id="ca077-159">Nakonec, v souboru *Docker-Compose. override. yml* , `basket-api` mikroslužba pro eShopOnContainers Sample definuje připojovací řetězec, který se má použít pro tento kontejner Redis:</span><span class="sxs-lookup"><span data-stu-id="ca077-159">Finally, in the *docker-compose.override.yml* file, the `basket-api` microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="ca077-160">Jak je uvedeno dříve, název `basketdata` mikroslužeb se vyřeší interní síťovou službou DNS Docker.</span><span class="sxs-lookup"><span data-stu-id="ca077-160">As mentioned before, the name of the microservice `basketdata` is resolved by Docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="ca077-161">[Předchozí](multi-container-applications-docker-compose.md)
>[Další](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="ca077-161">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
