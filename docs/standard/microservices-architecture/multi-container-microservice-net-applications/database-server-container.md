---
title: Použití databázového serveru, který se používá jako kontejner
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Použití databázového serveru běžícího jako kontejner? pouze pro vývoj! Zjistěte, proč.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: c993f962d84ca3fc859ab704489300192536ee74
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61760763"
---
# <a name="using-a-database-server-running-as-a-container"></a><span data-ttu-id="8155d-104">Použití databázového serveru, který se používá jako kontejner</span><span class="sxs-lookup"><span data-stu-id="8155d-104">Using a database server running as a container</span></span>

<span data-ttu-id="8155d-105">Pravidelné samostatných serverů v místních clusterech nebo na služby modelu PaaS v cloudu jako Azure SQL DB může mít vaše databáze (SQL Server, PostgreSQL, MySQL atd.).</span><span class="sxs-lookup"><span data-stu-id="8155d-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="8155d-106">Ale pro vývojová a testovací prostředí s databází systémem jako kontejnery je vhodné, protože nemáte žádné externí závislosti, jednoduše `docker-compose up` příkaz spustí celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8155d-106">However, for development and test environments, having your databases running as containers is convenient, because you do not have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="8155d-107">Tyto databáze jako kontejnery je také skvěle hodí pro integrační testy, protože databáze je spuštěn v kontejneru a je vždy naplněný stejná vzorová data, tak testů může být předvídatelnější.</span><span class="sxs-lookup"><span data-stu-id="8155d-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="8155d-108">SQL serveru běžícího jako kontejner s databází související mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="8155d-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="8155d-109">V aplikaci eShopOnContainers, je kontejner s názvem sql.data definované v [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) soubor, který spouští SQL Server pro Linux s všech databází systému SQL Server potřebné pro mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="8155d-109">In eShopOnContainers, there is a container named sql.data defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file that runs SQL Server for Linux with all the SQL Server databases needed for the microservices.</span></span> <span data-ttu-id="8155d-110">(Může mít také jeden kontejner systému SQL Server pro každou databázi, ale větší množství paměti, které jsou přiřazeny k Dockeru, který by vyžadovaly.) Důležité v mikroslužbách je, že každá mikroslužba je vlastníkem související data, proto jeho související databáze SQL v tomto případě.</span><span class="sxs-lookup"><span data-stu-id="8155d-110">(You could also have one SQL Server container for each database, but that would require more memory assigned to Docker.) The important point in microservices is that each microservice owns its related data, therefore its related SQL database in this case.</span></span> <span data-ttu-id="8155d-111">Ale databáze může být libovolného místa.</span><span class="sxs-lookup"><span data-stu-id="8155d-111">But the databases can be anywhere.</span></span>

<span data-ttu-id="8155d-112">Kontejner SQL serveru v ukázkové aplikaci je nakonfigurovaný s následující kód YAML v souboru docker-compose.yml, který se spustí, až spustíte `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="8155d-112">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="8155d-113">Všimněte si, že má kód YAML konsolidovat informace o konfiguraci ze souboru obecného docker-compose.yml a docker-compose.override.yml souboru.</span><span class="sxs-lookup"><span data-stu-id="8155d-113">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="8155d-114">(Obvykle by se oddělují nastavení prostředí a informace o základní nebo statické bitové kopie systému SQL Server.)</span><span class="sxs-lookup"><span data-stu-id="8155d-114">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="8155d-115">Podobným způsobem, namísto použití `docker-compose`, následující `docker run` tento kontejner můžete spustit příkaz:</span><span class="sxs-lookup"><span data-stu-id="8155d-115">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

<span data-ttu-id="8155d-116">Pokud nasazujete vícekontejnerovou aplikaci jako aplikaci eShopOnContainers, je ale vhodnější použít `docker-compose up` příkaz tak, aby nasadí všechny požadované kontejnery pro aplikace.</span><span class="sxs-lookup"><span data-stu-id="8155d-116">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="8155d-117">Při prvním spuštění tohoto kontejneru systému SQL Server, inicializuje kontejneru systému SQL Server s heslem, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="8155d-117">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="8155d-118">Jakmile systém SQL Server běží jako kontejner, můžete aktualizovat databázi připojením přes jakékoli pravidelné připojení SQL, jako například SQL Server Management Studio, Visual Studio nebo C\# kódu.</span><span class="sxs-lookup"><span data-stu-id="8155d-118">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="8155d-119">Aplikaci eShopOnContainers aplikace inicializuje jednotlivých mikroslužeb databázi s ukázkovými daty synchronizace replik indexů s daty při spuštění, jak je vysvětleno v následující části.</span><span class="sxs-lookup"><span data-stu-id="8155d-119">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="8155d-120">S SQL serveru běžícího jako kontejner není právě užitečná pro ukázku kde pravděpodobně nebudete mít přístup k instanci systému SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8155d-120">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="8155d-121">Jak je uvedeno je také velmi vhodné pro vývojová a testovací prostředí tak, aby můžete snadno spouštět testy integrace od čistou bitovou kopii systému SQL Server a data nezná synchronizace replik indexů nová vzorová data.</span><span class="sxs-lookup"><span data-stu-id="8155d-121">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="8155d-122">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="8155d-122">Additional resources</span></span>

- <span data-ttu-id="8155d-123">**Spuštění image SQL serveru Docker v Linuxu, Mac nebo Windows** \\</span><span class="sxs-lookup"><span data-stu-id="8155d-123">**Run the SQL Server Docker image on Linux, Mac, or Windows** \\</span></span>
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](/sql/linux/sql-server-linux-setup-docker)

- <span data-ttu-id="8155d-124">**Připojení a dotazování SQL serveru v Linuxu pomocí sqlcmd** \\</span><span class="sxs-lookup"><span data-stu-id="8155d-124">**Connect and query SQL Server on Linux with sqlcmd** \\</span></span>
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="8155d-125">Předvyplnění daty testu při spuštění webové aplikace</span><span class="sxs-lookup"><span data-stu-id="8155d-125">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="8155d-126">Přidání dat do databáze při spuštění aplikace, můžete přidat kód následujícím postupem konfigurace metody ve třídě spouštěný projekt webového rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="8155d-126">To add data to the database when the application starts up, you can add code like the following to the Configure method in the Startup class of the Web API project:</span></span>

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

<span data-ttu-id="8155d-127">Následující kód ve třídě vlastní CatalogContextSeed naplní data.</span><span class="sxs-lookup"><span data-stu-id="8155d-127">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="8155d-128">Při spuštění testů integrace, způsob, jak vygenerovat konzistentní s testy integrace dat je užitečné.</span><span class="sxs-lookup"><span data-stu-id="8155d-128">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="8155d-129">Možnost vytvoření čehokoliv od začátku, včetně instance systému SQL Server spuštěnou v kontejneru, je velmi vhodné pro testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="8155d-129">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="8155d-130">EF Core InMemory databáze versus SQL serveru běžícího jako kontejner</span><span class="sxs-lookup"><span data-stu-id="8155d-130">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="8155d-131">Další dobrou volbou při spouštění testů se má používat databázi zprostředkovatele Entity Framework InMemory.</span><span class="sxs-lookup"><span data-stu-id="8155d-131">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="8155d-132">Tuto konfiguraci můžete zadat v metodě ConfigureServices třída při spuštění ve vašem projektu webového rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="8155d-132">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="8155d-133">I když je důležité catch.</span><span class="sxs-lookup"><span data-stu-id="8155d-133">There is an important catch, though.</span></span> <span data-ttu-id="8155d-134">Databáze v paměti nepodporuje spousta omezení, které jsou specifické pro konkrétní databázi.</span><span class="sxs-lookup"><span data-stu-id="8155d-134">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="8155d-135">Může například přidat jedinečný index pro sloupec v modelu EF Core a napsat test na vaší databázi v paměti, zkontrolujte, že to neumožňuje přidání duplicitní hodnoty.</span><span class="sxs-lookup"><span data-stu-id="8155d-135">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="8155d-136">Ale při použití databáze v paměti, nemůže zpracovat jedinečné indexy pro sloupec.</span><span class="sxs-lookup"><span data-stu-id="8155d-136">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="8155d-137">Proto se databáze v paměti se nechová stejně jako skutečná databáze systému SQL Server – to není emulovat omezení konkrétních databází.</span><span class="sxs-lookup"><span data-stu-id="8155d-137">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="8155d-138">I tak databázi v paměti je stále užitečná pro vytváření prototypů a testování.</span><span class="sxs-lookup"><span data-stu-id="8155d-138">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="8155d-139">Ale pokud chcete vytvořit přesné integrační testy, které vezměte v úvahu chování implementace konkrétní databázi, budete muset použít skutečné databáze jako SQL Server.</span><span class="sxs-lookup"><span data-stu-id="8155d-139">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="8155d-140">Pro tento účel systémem SQL Server v kontejneru je skvělý choice a přesnější, než si zprostředkovatele databáze EF Core InMemory.</span><span class="sxs-lookup"><span data-stu-id="8155d-140">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

### <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="8155d-141">Pomocí služby mezipaměti Redis spuštěné v kontejneru</span><span class="sxs-lookup"><span data-stu-id="8155d-141">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="8155d-142">Redis můžete spustit v kontejneru, zejména pro vývoj a testování a pro scénáře testování konceptu.</span><span class="sxs-lookup"><span data-stu-id="8155d-142">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="8155d-143">Tento scénář je vhodný, protože budete mít všechny svoje závislosti, které běží na kontejnery – ne jenom pro počítače s místním vývojovým, ale pro vaše testovací prostředí ve vašich kanálů CI/CD.</span><span class="sxs-lookup"><span data-stu-id="8155d-143">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="8155d-144">Při spuštění Redis v produkčním prostředí, je však lepší vyhledejte řešení vysoké dostupnosti, jako je například Redis Microsoft Azure, který se spouští jako PaaS (platforma jako služba).</span><span class="sxs-lookup"><span data-stu-id="8155d-144">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="8155d-145">Ve vašem kódu stačí změnit připojovací řetězce.</span><span class="sxs-lookup"><span data-stu-id="8155d-145">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="8155d-146">Redis poskytuje image Dockeru s využitím Redis.</span><span class="sxs-lookup"><span data-stu-id="8155d-146">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="8155d-147">Tento image je k dispozici z Docker Hubu na této adrese URL:</span><span class="sxs-lookup"><span data-stu-id="8155d-147">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/\_/redis/>

<span data-ttu-id="8155d-148">Kontejner Dockeru Redis můžete spustit přímo spuštěním následujícího příkazu rozhraní příkazového řádku Dockeru v příkazovém řádku:</span><span class="sxs-lookup"><span data-stu-id="8155d-148">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```
  docker run --name some-redis -d redis
```

<span data-ttu-id="8155d-149">Redis image zahrnuje vystavení: 6379 (port je používán Redis), tedy standardní propojení kontejneru zpřístupníte ji automaticky propojené kontejnery.</span><span class="sxs-lookup"><span data-stu-id="8155d-149">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="8155d-150">V aplikaci eShopOnContainers používá mikroslužeb basket.api běžícího jako kontejner mezipaměti redis Cache.</span><span class="sxs-lookup"><span data-stu-id="8155d-150">In eShopOnContainers, the basket.api microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="8155d-151">Tento kontejner basket.data je definován jako součást souboru více kontejnerů docker-compose.yml, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8155d-151">That basket.data container is defined as part of the multi-container docker-compose.yml file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="8155d-152">Tento kód v docker-compose.yml definuje kontejner s názvem basket.data na základě redis image a publikování port 6379 interně, což znamená, že je přístupný pouze z jiných kontejnerů v rámci hostitele Dockeru.</span><span class="sxs-lookup"><span data-stu-id="8155d-152">This code in the docker-compose.yml defines a container named basket.data based on the redis image and publishing the port 6379 internally, meaning that it will be accessible only from other containers running within the Docker host.</span></span>

<span data-ttu-id="8155d-153">Nakonec v souboru docker-compose.override.yml basket.api mikroslužeb pro vzorovou aplikaci eShopOnContainers definuje připojovací řetězec má použít pro tento kontejner Redis:</span><span class="sxs-lookup"><span data-stu-id="8155d-153">Finally, in the docker-compose.override.yml file, the basket.api microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="8155d-154">Jak jsme zmínili, název mikroslužeb "basket.data" vyřešil docker interní sítě DNS.</span><span class="sxs-lookup"><span data-stu-id="8155d-154">As mentioned before, the name of the microservice "basket.data" is resolved by docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="8155d-155">[Předchozí](multi-container-applications-docker-compose.md)
>[další](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="8155d-155">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
