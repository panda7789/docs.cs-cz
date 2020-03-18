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
# <a name="use-a-database-server-running-as-a-container"></a>Použití databázového serveru spuštěného jako kontejner

Databáze (SQL Server, PostgreSQL, MySQL atd.) můžete mít na běžných samostatných serverech, v místních clusterech nebo ve službách PaaS v cloudu, jako je Azure SQL DB. Však pro vývoj a testovací prostředí s databázemi spuštěny jako kontejnery je vhodná, protože `docker-compose up` nemáte žádné externí závislost a jednoduše spuštění příkazu spustí celou aplikaci. S tyto databáze jako kontejnery je také skvělé pro testy integrace, protože databáze je spuštěna v kontejneru a je vždy naplněna stejnými ukázkovými daty, takže testy mohou být předvídatelnější.

## <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>SQL Server spuštěný jako kontejner s databází související s mikroslužbami

V eShopOnContainers je kontejner s `sqldata`názvem , jak je definováno v souboru [docker-compose.yml,](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) který spouští instanci SQL Server pro Linux s databázemi SQL pro všechny mikroslužby, které je potřebují.

Klíčovým bodem v mikroslužbách je, že každá mikroslužba vlastní související data, takže by měla mít vlastní databázi. Databáze však může být kdekoli. V tomto případě jsou všechny ve stejném kontejneru, aby požadavky na paměť Docker udála co nejnižší. Mějte na paměti, že se jedná o dostatečně dobré řešení pro vývoj a možná i pro testování, ale ne pro výrobu.

Kontejner SERVERU SQL Server v ukázkové aplikaci je nakonfigurován s následujícím kódem YAML v souboru `docker-compose up`docker-compose.yml, který se spustí při spuštění . Všimněte si, že kód YAML má konsolidované informace o konfiguraci z obecného souboru docker-compose.yml a souboru docker-compose.override.yml. (Obvykle byste oddělit nastavení prostředí ze základní nebo statické informace týkající se bitové kopie serveru SQL Server.)

```yml
  sqldata:
    image: mcr.microsoft.com/mssql/server:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

Podobným způsobem, namísto `docker-compose`použití , `docker run` následující příkaz můžete spustit tento kontejner:

```powershell
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d mcr.microsoft.com/mssql/server:2017-latest
```

Pokud však nasazujete aplikaci s více kontejnery, jako je `docker-compose up` eShopOnContainers, je vhodnější použít příkaz tak, aby nasazoval všechny požadované kontejnery pro aplikaci.

Při prvním spuštění tohoto kontejneru SQL Server kontejner inicializuje SQL Server s heslem, které zadáte. Jakmile je SQL Server spuštěn jako kontejner, můžete databázi aktualizovat připojením prostřednictvím běžného připojení SQL,\# například z kódu SQL Server Management Studio, Visual Studio nebo C.

Aplikace eShopOnContainers inicializuje každou databázi mikroslužeb se ukázkovými daty tím, že ji osevá daty při spuštění, jak je vysvětleno v následující části.

S SQL Server běží jako kontejner není užitečné pouze pro ukázku, kde nemusí mít přístup k instanci SQL Server. Jak již bylo uvedeno, je také skvělé pro vývoj a testování prostředí, takže můžete snadno spustit integrační testy počínaje čistou bitovou kopii serveru SQL Server a známých dat osiva nových ukázkových dat.

### <a name="additional-resources"></a>Další zdroje

- **Spuštění bitové kopie SQL Server Dockeru na Linuxu, Macu nebo Windows** \
  <https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker>

- **Připojení a dotazování SQL Serveru na Linuxu pomocí sqlcmd** \
  <https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd>

## <a name="seeding-with-test-data-on-web-application-startup"></a>Nastavení testovacích dat při spuštění webové aplikace

Chcete-li přidat data do databáze při spuštění aplikace, můžete `Main` přidat kód, jako je následující metody ve `Program` třídě projektu webového rozhraní API:

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

Existuje důležité upozornění při použití migrace a vysazení databáze při spuštění kontejneru. Vzhledem k tomu, že databázový server nemusí být z jakéhokoli důvodu k dispozici, je nutné zpracovat opakování při čekání na server, který má být k dispozici. Tato logika opakování je `MigrateDbContext()` zpracována metodou rozšíření, jak je znázorněno v následujícím kódu:

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

Při spuštění testů integrace, které mají způsob, jak generovat data konzistentní s integrační testy je užitečné. Být schopen vytvořit vše od začátku, včetně instance SQL Server spuštěný v kontejneru, je skvělé pro testovací prostředí.

## <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>EF Core InMemory databáze versus SQL Server běží jako kontejner

Další dobrou volbou při spuštění testů je použití zprostředkovatele databáze Entity Framework InMemory. Tuto konfiguraci můžete určit v metodě ConfigureServices třídy Startup v projektu webového rozhraní API:

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

Je tu důležitý úlovek, ačkoli. Databáze v paměti nepodporuje mnoho omezení, které jsou specifické pro konkrétní databázi. Můžete například přidat jedinečný index do sloupce v modelu EF Core a napsat test proti databázi v paměti a zkontrolovat, zda neumožňuje přidat duplicitní hodnotu. Ale pokud používáte databázi v paměti, nelze zpracovat jedinečné indexy na sloupec. Proto databáze v paměti nechová přesně stejné jako databáze reálné SQL Server – neemuluje omezení specifické pro databázi.

I tak je databáze v paměti stále užitečná pro testování a vytváření prototypů. Ale pokud chcete vytvořit přesné integrační testy, které berou v úvahu chování konkrétní implementace databáze, je třeba použít skutečnou databázi, jako je SQL Server. Pro tento účel je spuštění serveru SQL Server v kontejneru skvělou volbou a přesnější než zprostředkovatel databáze EF Core InMemory.

## <a name="using-a-redis-cache-service-running-in-a-container"></a>Použití služby mezipaměti Redis spuštěné v kontejneru

Redis můžete spustit v kontejneru, zejména pro vývoj a testování a pro scénáře proof-of-concept. Tento scénář je vhodný, protože můžete mít všechny vaše závislosti spuštěny na kontejnerech – nejen pro místní vývojové počítače, ale pro testovací prostředí v kanálech CI/CD.

Když však spustíte Redis v produkčním prostředí, je lepší hledat řešení s vysokou dostupností, jako je Redis Microsoft Azure, které běží jako PaaS (Platforma jako služba). V kódu stačí změnit připojovací řetězce.

Redis poskytuje image Dockeru s Redis. Tento obrázek je k dispozici v Docker Hubu na této adrese URL:

<https://hub.docker.com/_/redis/>

Kontejner Docker Redis můžete spustit přímo spuštěním následujícího příkazu Cli Dockeru v příkazovém řádku:

```console
docker run --name some-redis -d redis
```

Obrázek Redis obsahuje expose:6379 (port používaný redis), takže standardní propojení kontejnerů bude automaticky k dispozici pro propojené kontejnery.

V eShopOnContainers `basket-api` mikroslužba používá redis cache běží jako kontejner. Tento `basketdata` kontejner je definován jako součást souboru *docker-compose.yml* s více kontejnery, jak je znázorněno v následujícím příkladu:

```yml
#docker-compose.yml file
#...
  basketdata:
    image: redis
    expose:
      - "6379"
```

Tento kód v docker-compose.yml definuje `basketdata` kontejner s názvem na základě image redis a publikování portu 6379 interně. To znamená, že bude přístupná pouze z jiných kontejnerů spuštěné v rámci hostitele Dockeru.

Nakonec v souboru *docker-compose.override.yml* `basket-api` mikroslužba pro ukázku eShopOnContainers definuje připojovací řetězec, který se má použít pro tento kontejner Redis:

```yml
  basket-api:
    environment:
      # Other data ...
      - ConnectionString=basketdata
      - EventBusConnection=rabbitmq
```

Jak již bylo zmíněno dříve, `basketdata` název mikroslužby je vyřešen interní síťové DNS Dockeru.

>[!div class="step-by-step"]
>[Předchozí](multi-container-applications-docker-compose.md)
>[další](integration-event-based-microservice-communications.md)
