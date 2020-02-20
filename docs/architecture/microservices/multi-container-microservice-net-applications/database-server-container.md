---
title: Použití databázového serveru spuštěného jako kontejner
description: Pochopení důležitosti použití databázového serveru běžícího jako kontejneru pouze pro vývoj. Nikdy pro produkční prostředí.
ms.date: 01/30/2020
ms.openlocfilehash: 816ac196636f78a368a9f20e8eedcc6a22567fa7
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502290"
---
# <a name="use-a-database-server-running-as-a-container"></a>Použití databázového serveru spuštěného jako kontejner

Vaše databáze (SQL Server, PostgreSQL, MySQL atd.) můžete mít na běžných samostatných serverech, v místních clusterech nebo v PaaS službách v cloudu, jako je Azure SQL DB. Nicméně pro vývojová a testovací prostředí jsou vaše databáze spuštěné jako kontejnery pohodlné, protože nemáte žádnou externí závislost a stačí spustit příkaz `docker-compose up` spustí celou aplikaci. Aby byly tyto databáze stejně vhodné pro integrační testy, protože databáze je spuštěna v kontejneru a je vždy naplněna stejnými ukázkovými daty, testy mohou být předvídatelné.

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>SQL Server spuštěn jako kontejner s databází související s mikroslužbami

V eShopOnContainers je k dispozici kontejner s názvem `sqldata`, jak je definován v souboru [Docker-Compose. yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) , který spouští SQL Server pro instanci systému Linux s databázemi SQL pro všechny mikroslužby, které ji potřebují.

Klíčovým bodem v mikroslužbách je, že každá mikroslužba vlastní svoje související data, takže by měla mít vlastní databázi. Databáze ale můžou být kdekoli. V tomto případě jsou všechny ve stejném kontejneru, aby se požadavky na paměť Docker zachovaly co nejmenším možným způsobem. Mějte na paměti, že toto řešení je dobrým řešením pro vývoj a případně testování, ale ne pro produkční prostředí.

Kontejner SQL Server v ukázkové aplikaci je nakonfigurován s následujícím YAML kódem v souboru Docker-Compose. yml, který je spuštěn při spuštění `docker-compose up`. Všimněte si, že kód YAML má konsolidované informace o konfiguraci z obecného souboru Docker-Compose. yml a souboru Docker-Compose. override. yml. (Obvykle byste odvolali nastavení prostředí ze základních nebo statických informací, které se vztahují k SQL Server imagi.)

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

Podobným způsobem namísto použití `docker-compose`může tento kontejner spustit následující `docker run` příkaz:

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

Pokud však nasazujete aplikaci s více kontejnery, jako je eShopOnContainers, je vhodnější použít příkaz `docker-compose up`, aby nástroj nasadil všechny požadované kontejnery pro aplikaci.

Při prvním spuštění tohoto kontejneru SQL Server kontejner inicializuje SQL Server s heslem, které zadáte. Jakmile SQL Server spustíte jako kontejner, můžete aktualizovat databázi připojením přes jakékoli běžné připojení SQL, například z SQL Server Management Studio, sady Visual Studio nebo kódu\# jazyka C.

Aplikace eShopOnContainers inicializuje každou databázi mikroslužeb pomocí ukázkových dat tím, že je dokončí daty při spuštění, jak je vysvětleno v následující části.

Použití SQL Server jako kontejneru není právě užitečné pro ukázku, ve které nemůžete mít přístup k instanci SQL Server. Jak je uvedeno, je vhodné také pro vývojová a testovací prostředí, abyste mohli snadno spouštět testy integrace počínaje čistým SQL Server obrázkem a známými daty pomocí osazení nových ukázkových dat.

### <a name="additional-resources"></a>Další zdroje

- **Spuštění bitové kopie SQL Server Docker v systému Linux, Mac nebo Windows** \
    <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- **Připojení a dotazování SQL Server on Linux pomocí sqlcmd** \
    <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a>Osazení s testovacími daty při spuštění webové aplikace

Chcete-li přidat data do databáze při spuštění aplikace, můžete do metody `Main` v `Program` třídy projektu webového rozhraní API přidat kód podobný následujícímu:

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

Při použití migrace a nastavování databáze při spuštění kontejneru je důležité upozornění. Vzhledem k tomu, že databázový server nemusí být k dispozici z jakéhokoli důvodu, je nutné zpracovat opakované pokusy při čekání na dostupnost serveru. Tato logika opakování je zpracována metodou rozšíření `MigrateDbContext()`, jak je znázorněno v následujícím kódu:

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

Následující kód ve vlastní třídě CatalogContextSeed naplní data.

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

Při spuštění integračních testů je užitečné, aby bylo možné generovat data konzistentní s testy Integration. Schopnost vytvářet vše od začátku, včetně instance SQL Server běžícího na kontejneru, je skvělé pro testovací prostředí.

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>EF Core nepaměťové databáze versus SQL Server spuštěná jako kontejner

Další dobrý volbou při spouštění testů je použití poskytovatele databáze Entity Framework inMemory. Tuto konfiguraci můžete zadat v metodě ConfigureServices třídy Startup v projektu webového rozhraní API:

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

K dispozici je i důležité catch. Databáze v paměti nepodporuje řadu omezení, která jsou specifická pro konkrétní databázi. Například můžete přidat jedinečný index pro sloupec v modelu EF Core a zapsat test do databáze v paměti, abyste zkontrolovali, že vám neumožňuje přidat duplicitní hodnotu. Pokud ale používáte databázi v paměti, nemůžete pro sloupec zpracovávat jedinečné indexy. Proto se databáze v paměti nechová stejně jako skutečná SQL Server databáze – neemuluje omezení specifická pro databázi.

I tak je databáze v paměti stále užitečná pro testování a vytváření prototypů. Pokud ale chcete vytvořit přesné integrační testy, které berou v úvahu chování konkrétní implementace databáze, musíte použít skutečnou databázi, jako je SQL Server. Pro tento účel je spuštění SQL Server v kontejneru skvělým výběrem a přesnější než EF Core poskytovatel databáze inMemory.

## <a name="using-a-redis-cache-service-running-in-a-container"></a>Používání služby Redis Cache spuštěné v kontejneru

Redis můžete spustit na kontejneru, zejména pro vývoj a testování, a pro scénáře testování konceptů. Tento scénář je vhodný, protože můžete mít všechny závislosti spuštěné v kontejnerech, nikoli jenom pro místní vývojové počítače, ale pro testovací prostředí v kanálech CI/CD.

Pokud ale spustíte Redis v produkčním prostředí, je lepší vyhledat řešení s vysokou dostupností, jako je Redis Microsoft Azure, které běží jako PaaS (platforma jako služba). V kódu je pouze nutné změnit připojovací řetězce.

Redis poskytuje image Docker s Redis. Tato bitová kopie je k dispozici z Docker Hub na této adrese URL:

<https://hub.docker.com/_/redis/>

Kontejner Docker Redis můžete přímo spustit spuštěním následujícího příkazu Docker CLI na příkazovém řádku:

```console
docker run --name some-redis -d redis
```

Image Redis zahrnuje vystavení: 6379 (port, který používá Redis), takže standardní propojení kontejnerů bude automaticky dostupné pro propojené kontejnery.

V eShopOnContainers používá `basket-api` mikroslužba mezipaměť Redis spuštěnou jako kontejner. Tento kontejner `basketdata` je definován jako součást souboru *Docker-Compose. yml* s více kontejnery, jak je znázorněno v následujícím příkladu:

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

Tento kód v Docker-Compose. yml definuje kontejner s názvem `basketdata` založený na imagi Redis a interně publikuje port 6379. To znamená, že bude přístupný jenom z jiných kontejnerů spuštěných v rámci hostitele Docker.

Nakonec, v souboru *Docker-Compose. override. yml* , `basket-api` mikroslužba pro eShopOnContainers Sample definuje připojovací řetězec, který se má použít pro tento kontejner Redis:

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

Jak je uvedeno dříve, název `basketdata` mikroslužeb se vyřeší interní síťovou službou DNS Docker.

>[!div class="step-by-step"]
>[Předchozí](multi-container-applications-docker-compose.md)
>[Další](integration-event-based-microservice-communications.md)
