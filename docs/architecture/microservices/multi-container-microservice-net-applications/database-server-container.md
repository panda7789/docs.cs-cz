---
title: Použití databázového serveru, který se používá jako kontejner
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Používáte databázový server, který běží jako kontejner? jenom pro vývoj. Vysvětlení, proč.
ms.date: 10/02/2018
ms.openlocfilehash: 312f986b5aa710fe51c7c3488776395194526e51
ms.sourcegitcommit: 4e2d355baba82814fa53efd6b8bbb45bfe054d11
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2019
ms.locfileid: "70296882"
---
# <a name="using-a-database-server-running-as-a-container"></a><span data-ttu-id="c026b-104">Použití databázového serveru, který se používá jako kontejner</span><span class="sxs-lookup"><span data-stu-id="c026b-104">Using a database server running as a container</span></span>

<span data-ttu-id="c026b-105">Vaše databáze (SQL Server, PostgreSQL, MySQL atd.) můžete mít na běžných samostatných serverech, v místních clusterech nebo v PaaS službách v cloudu, jako je Azure SQL DB.</span><span class="sxs-lookup"><span data-stu-id="c026b-105">You can have your databases (SQL Server, PostgreSQL, MySQL, etc.) on regular standalone servers, in on-premises clusters, or in PaaS services in the cloud like Azure SQL DB.</span></span> <span data-ttu-id="c026b-106">Nicméně pro vývojová a testovací prostředí je vhodné, aby vaše databáze spuštěné jako kontejnery byly pohodlné, protože nemáte žádnou externí závislost a stačí spustit `docker-compose up` příkaz, který spustí celou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c026b-106">However, for development and test environments, having your databases running as containers is convenient, because you do not have any external dependency and simply running the `docker-compose up` command starts the whole application.</span></span> <span data-ttu-id="c026b-107">Aby byly tyto databáze stejně vhodné pro integrační testy, protože databáze je spuštěna v kontejneru a je vždy naplněna stejnými ukázkovými daty, testy mohou být předvídatelné.</span><span class="sxs-lookup"><span data-stu-id="c026b-107">Having those databases as containers is also great for integration tests, because the database is started in the container and is always populated with the same sample data, so tests can be more predictable.</span></span>

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a><span data-ttu-id="c026b-108">SQL Server spuštěn jako kontejner s databází související s mikroslužbami</span><span class="sxs-lookup"><span data-stu-id="c026b-108">SQL Server running as a container with a microservice-related database</span></span>

<span data-ttu-id="c026b-109">V eShopOnContainers je k dispozici kontejner s názvem SQL. data definovaná v souboru [Docker-Compose. yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) , který spouští SQL Server pro Linux se všemi SQL Server databázemi, které jsou pro mikroslužby potřeba.</span><span class="sxs-lookup"><span data-stu-id="c026b-109">In eShopOnContainers, there is a container named sql.data defined in the [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) file that runs SQL Server for Linux with all the SQL Server databases needed for the microservices.</span></span> <span data-ttu-id="c026b-110">(Můžete mít také jeden kontejner SQL Server pro každou databázi, ale to by vyžadovalo více paměti, která je přiřazena k Docker.) Důležitým bodem v mikroslužbách je, že každá mikroslužba vlastní související data, proto v tomto případě související databáze SQL.</span><span class="sxs-lookup"><span data-stu-id="c026b-110">(You could also have one SQL Server container for each database, but that would require more memory assigned to Docker.) The important point in microservices is that each microservice owns its related data, therefore its related SQL database in this case.</span></span> <span data-ttu-id="c026b-111">Ale databáze můžou být kdekoli.</span><span class="sxs-lookup"><span data-stu-id="c026b-111">But the databases can be anywhere.</span></span>

<span data-ttu-id="c026b-112">Kontejner SQL Server v ukázkové aplikaci je nakonfigurován s následujícím YAML kódem v souboru Docker-Compose. yml, který je spuštěn při spuštění `docker-compose up`.</span><span class="sxs-lookup"><span data-stu-id="c026b-112">The SQL Server container in the sample application is configured with the following YAML code in the docker-compose.yml file, which is executed when you run `docker-compose up`.</span></span> <span data-ttu-id="c026b-113">Všimněte si, že kód YAML má konsolidované informace o konfiguraci z obecného souboru Docker-Compose. yml a souboru Docker-Compose. override. yml.</span><span class="sxs-lookup"><span data-stu-id="c026b-113">Note that the YAML code has consolidated configuration information from the generic docker-compose.yml file and the docker-compose.override.yml file.</span></span> <span data-ttu-id="c026b-114">(Obvykle byste odvolali nastavení prostředí ze základních nebo statických informací, které se vztahují k SQL Server imagi.)</span><span class="sxs-lookup"><span data-stu-id="c026b-114">(Usually you would separate the environment settings from the base or static information related to the SQL Server image.)</span></span>

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

<span data-ttu-id="c026b-115">Podobným způsobem, namísto použití `docker-compose`, může tento kontejner spustit následující `docker run` příkaz:</span><span class="sxs-lookup"><span data-stu-id="c026b-115">In a similar way, instead of using `docker-compose`, the following `docker run` command can run that container:</span></span>

```console
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

<span data-ttu-id="c026b-116">Pokud však nasazujete aplikaci s více kontejnery, jako je eShopOnContainers, je vhodnější použít `docker-compose up` příkaz, aby nástroj nasadil všechny požadované kontejnery pro aplikaci.</span><span class="sxs-lookup"><span data-stu-id="c026b-116">However, if you are deploying a multi-container application like eShopOnContainers, it is more convenient to use the `docker-compose up` command so that it deploys all the required containers for the application.</span></span>

<span data-ttu-id="c026b-117">Při prvním spuštění tohoto kontejneru SQL Server kontejner inicializuje SQL Server s heslem, které zadáte.</span><span class="sxs-lookup"><span data-stu-id="c026b-117">When you start this SQL Server container for the first time, the container initializes SQL Server with the password that you provide.</span></span> <span data-ttu-id="c026b-118">Jakmile SQL Server spustíte jako kontejner, můžete databázi aktualizovat připojením k libovolnému běžnému připojení SQL, jako je například z SQL Server Management Studio, Visual Studio nebo C\# Code.</span><span class="sxs-lookup"><span data-stu-id="c026b-118">Once SQL Server is running as a container, you can update the database by connecting through any regular SQL connection, such as from SQL Server Management Studio, Visual Studio, or C\# code.</span></span>

<span data-ttu-id="c026b-119">Aplikace eShopOnContainers inicializuje každou databázi mikroslužeb pomocí ukázkových dat tím, že je dokončí daty při spuštění, jak je vysvětleno v následující části.</span><span class="sxs-lookup"><span data-stu-id="c026b-119">The eShopOnContainers application initializes each microservice database with sample data by seeding it with data on startup, as explained in the following section.</span></span>

<span data-ttu-id="c026b-120">Použití SQL Server jako kontejneru není právě užitečné pro ukázku, ve které nemůžete mít přístup k instanci SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c026b-120">Having SQL Server running as a container is not just useful for a demo where you might not have access to an instance of SQL Server.</span></span> <span data-ttu-id="c026b-121">Jak je uvedeno, je vhodné také pro vývojová a testovací prostředí, abyste mohli snadno spouštět testy integrace počínaje čistým SQL Server obrázkem a známými daty pomocí osazení nových ukázkových dat.</span><span class="sxs-lookup"><span data-stu-id="c026b-121">As noted, it is also great for development and testing environments so that you can easily run integration tests starting from a clean SQL Server image and known data by seeding new sample data.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="c026b-122">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="c026b-122">Additional resources</span></span>

- <span data-ttu-id="c026b-123">**Spuštění bitové kopie SQL Server Docker v systému Linux, Mac nebo Windows** </span><span class="sxs-lookup"><span data-stu-id="c026b-123">**Run the SQL Server Docker image on Linux, Mac, or Windows** </span></span>\
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](/sql/linux/sql-server-linux-setup-docker)

- <span data-ttu-id="c026b-124">**Připojení a dotazování SQL Server on Linux pomocí sqlcmd** </span><span class="sxs-lookup"><span data-stu-id="c026b-124">**Connect and query SQL Server on Linux with sqlcmd** </span></span>\
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a><span data-ttu-id="c026b-125">Osazení s testovacími daty při spuštění webové aplikace</span><span class="sxs-lookup"><span data-stu-id="c026b-125">Seeding with test data on Web application startup</span></span>

<span data-ttu-id="c026b-126">Chcete-li přidat data do databáze při spuštění aplikace, můžete do metody Configure ve spouštěcí třídě projektu webového rozhraní API přidat kód podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="c026b-126">To add data to the database when the application starts up, you can add code like the following to the Configure method in the Startup class of the Web API project:</span></span>

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

<span data-ttu-id="c026b-127">Následující kód ve vlastní třídě CatalogContextSeed naplní data.</span><span class="sxs-lookup"><span data-stu-id="c026b-127">The following code in the custom CatalogContextSeed class populates the data.</span></span>

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

<span data-ttu-id="c026b-128">Při spuštění integračních testů je užitečné, aby bylo možné generovat data konzistentní s testy Integration.</span><span class="sxs-lookup"><span data-stu-id="c026b-128">When you run integration tests, having a way to generate data consistent with your integration tests is useful.</span></span> <span data-ttu-id="c026b-129">Schopnost vytvářet vše od začátku, včetně instance SQL Server běžícího na kontejneru, je skvělé pro testovací prostředí.</span><span class="sxs-lookup"><span data-stu-id="c026b-129">Being able to create everything from scratch, including an instance of SQL Server running on a container, is great for test environments.</span></span>

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a><span data-ttu-id="c026b-130">EF Core nepaměťové databáze versus SQL Server spuštěná jako kontejner</span><span class="sxs-lookup"><span data-stu-id="c026b-130">EF Core InMemory database versus SQL Server running as a container</span></span>

<span data-ttu-id="c026b-131">Další dobrý volbou při spouštění testů je použití poskytovatele databáze Entity Framework inMemory.</span><span class="sxs-lookup"><span data-stu-id="c026b-131">Another good choice when running tests is to use the Entity Framework InMemory database provider.</span></span> <span data-ttu-id="c026b-132">Tuto konfiguraci můžete zadat v metodě ConfigureServices třídy Startup v projektu webového rozhraní API:</span><span class="sxs-lookup"><span data-stu-id="c026b-132">You can specify that configuration in the ConfigureServices method of the Startup class in your Web API project:</span></span>

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

<span data-ttu-id="c026b-133">K dispozici je i důležité catch.</span><span class="sxs-lookup"><span data-stu-id="c026b-133">There is an important catch, though.</span></span> <span data-ttu-id="c026b-134">Databáze v paměti nepodporuje řadu omezení, která jsou specifická pro konkrétní databázi.</span><span class="sxs-lookup"><span data-stu-id="c026b-134">The in-memory database does not support many constraints that are specific to a particular database.</span></span> <span data-ttu-id="c026b-135">Například můžete přidat jedinečný index pro sloupec v modelu EF Core a zapsat test do databáze v paměti, abyste zkontrolovali, že vám neumožňuje přidat duplicitní hodnotu.</span><span class="sxs-lookup"><span data-stu-id="c026b-135">For instance, you might add a unique index on a column in your EF Core model and write a test against your in-memory database to check that it does not let you add a duplicate value.</span></span> <span data-ttu-id="c026b-136">Pokud ale používáte databázi v paměti, nemůžete pro sloupec zpracovávat jedinečné indexy.</span><span class="sxs-lookup"><span data-stu-id="c026b-136">But when you are using the in-memory database, you cannot handle unique indexes on a column.</span></span> <span data-ttu-id="c026b-137">Proto se databáze v paměti nechová stejně jako skutečná SQL Server databáze – neemuluje omezení specifická pro databázi.</span><span class="sxs-lookup"><span data-stu-id="c026b-137">Therefore, the in-memory database does not behave exactly the same as a real SQL Server database—it does not emulate database-specific constraints.</span></span>

<span data-ttu-id="c026b-138">I tak je databáze v paměti stále užitečná pro testování a vytváření prototypů.</span><span class="sxs-lookup"><span data-stu-id="c026b-138">Even so, an in-memory database is still useful for testing and prototyping.</span></span> <span data-ttu-id="c026b-139">Pokud ale chcete vytvořit přesné integrační testy, které berou v úvahu chování konkrétní implementace databáze, musíte použít skutečnou databázi, jako je SQL Server.</span><span class="sxs-lookup"><span data-stu-id="c026b-139">But if you want to create accurate integration tests that take into account the behavior of a specific database implementation, you need to use a real database like SQL Server.</span></span> <span data-ttu-id="c026b-140">Pro tento účel je spuštění SQL Server v kontejneru skvělým výběrem a přesnější než EF Core poskytovatel databáze inMemory.</span><span class="sxs-lookup"><span data-stu-id="c026b-140">For that purpose, running SQL Server in a container is a great choice and more accurate than the EF Core InMemory database provider.</span></span>

### <a name="using-a-redis-cache-service-running-in-a-container"></a><span data-ttu-id="c026b-141">Používání služby Redis Cache spuštěné v kontejneru</span><span class="sxs-lookup"><span data-stu-id="c026b-141">Using a Redis cache service running in a container</span></span>

<span data-ttu-id="c026b-142">Redis můžete spustit na kontejneru, zejména pro vývoj a testování, a pro scénáře testování konceptů.</span><span class="sxs-lookup"><span data-stu-id="c026b-142">You can run Redis on a container, especially for development and testing and for proof-of-concept scenarios.</span></span> <span data-ttu-id="c026b-143">Tento scénář je vhodný, protože můžete mít všechny závislosti spuštěné v kontejnerech, nikoli jenom pro místní vývojové počítače, ale pro testovací prostředí v kanálech CI/CD.</span><span class="sxs-lookup"><span data-stu-id="c026b-143">This scenario is convenient, because you can have all your dependencies running on containers—not just for your local development machines, but for your testing environments in your CI/CD pipelines.</span></span>

<span data-ttu-id="c026b-144">Pokud ale spustíte Redis v produkčním prostředí, je lepší vyhledat řešení s vysokou dostupností, jako je Redis Microsoft Azure, které běží jako PaaS (platforma jako služba).</span><span class="sxs-lookup"><span data-stu-id="c026b-144">However, when you run Redis in production, it is better to look for a high-availability solution like Redis Microsoft Azure, which runs as a PaaS (Platform as a Service).</span></span> <span data-ttu-id="c026b-145">V kódu je pouze nutné změnit připojovací řetězce.</span><span class="sxs-lookup"><span data-stu-id="c026b-145">In your code, you just need to change your connection strings.</span></span>

<span data-ttu-id="c026b-146">Redis poskytuje image Docker s Redis.</span><span class="sxs-lookup"><span data-stu-id="c026b-146">Redis provides a Docker image with Redis.</span></span> <span data-ttu-id="c026b-147">Tato bitová kopie je k dispozici z Docker Hub na této adrese URL:</span><span class="sxs-lookup"><span data-stu-id="c026b-147">That image is available from Docker Hub at this URL:</span></span>

<https://hub.docker.com/\_/redis/>

<span data-ttu-id="c026b-148">Kontejner Docker Redis můžete přímo spustit spuštěním následujícího příkazu Docker CLI na příkazovém řádku:</span><span class="sxs-lookup"><span data-stu-id="c026b-148">You can directly run a Docker Redis container by executing the following Docker CLI command in your command prompt:</span></span>

```console
  docker run --name some-redis -d redis
```

<span data-ttu-id="c026b-149">Image Redis zahrnuje vystavení: 6379 (port, který používá Redis), takže standardní propojení kontejnerů bude automaticky dostupné pro propojené kontejnery.</span><span class="sxs-lookup"><span data-stu-id="c026b-149">The Redis image includes expose:6379 (the port used by Redis), so standard container linking will make it automatically available to the linked containers.</span></span>

<span data-ttu-id="c026b-150">V eShopOnContainers se v košíku. mikroslužba API používá Redis Cache spuštěná jako kontejner.</span><span class="sxs-lookup"><span data-stu-id="c026b-150">In eShopOnContainers, the basket.api microservice uses a Redis cache running as a container.</span></span> <span data-ttu-id="c026b-151">Tento koš. data Container je definován jako součást souboru Docker-Compose. yml s více kontejnery, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="c026b-151">That basket.data container is defined as part of the multi-container docker-compose.yml file, as shown in the following example:</span></span>

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

<span data-ttu-id="c026b-152">Tento kód v Docker-Compose. yml definuje kontejner s názvem košík. data založená na imagi Redis a interním publikováním portu 6379, což znamená, že bude přístupný pouze z jiných kontejnerů spuštěných v rámci hostitele Docker.</span><span class="sxs-lookup"><span data-stu-id="c026b-152">This code in the docker-compose.yml defines a container named basket.data based on the redis image and publishing the port 6379 internally, meaning that it will be accessible only from other containers running within the Docker host.</span></span>

<span data-ttu-id="c026b-153">Nakonec můžete v souboru Docker-Compose. override. yml, který je součástí koše, používá mikroslužba API pro ukázku eShopOnContainers připojovací řetězec, který se má použít pro tento kontejner Redis:</span><span class="sxs-lookup"><span data-stu-id="c026b-153">Finally, in the docker-compose.override.yml file, the basket.api microservice for the eShopOnContainers sample defines the connection string to use for that Redis container:</span></span>

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

<span data-ttu-id="c026b-154">Jak už bylo zmíněno dříve, název košíku mikroslužeb. data je vyřešen interní sítí DNS Docker.</span><span class="sxs-lookup"><span data-stu-id="c026b-154">As mentioned before, the name of the microservice "basket.data" is resolved by docker's internal network DNS.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="c026b-155">[Předchozí](multi-container-applications-docker-compose.md)Další
>[](integration-event-based-microservice-communications.md)</span><span class="sxs-lookup"><span data-stu-id="c026b-155">[Previous](multi-container-applications-docker-compose.md)
[Next](integration-event-based-microservice-communications.md)</span></span>
