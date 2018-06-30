---
title: Pomocí databázový server, který je spuštěn jako kontejner
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Pomocí databázový server, který je spuštěn jako kontejner
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/30/2017
ms.openlocfilehash: 42b0bf43ace00b1eb4b48c39604b89ea76c99220
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106146"
---
# <a name="using-a-database-server-running-as-a-container"></a>Pomocí databázový server, který je spuštěn jako kontejner

Vaše databáze (SQL Server, PostgreSQL, MySQL atd.) může mít regulární samostatných serverů v clusterech místně nebo v PaaS služeb v cloudu jako databázi SQL Azure. Pro vývojové a testovací prostředí s databází spuštěna jako kontejnery je však vhodné, protože nemáte žádné externí závislosti a jednoduše spuštěná docker compose příkaz spustí celou aplikaci. Tyto databáze jako kontejnery s je také výborně hodí pro integraci testy, protože databáze je spuštěna v kontejneru a vždy naplněný stejná ukázková data, aby mohli být předvídatelnější testy.

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>SQL Server běžící jako kontejner s databází související mikroslužbu

V eShopOnContainers, je kontejner s názvem sql.data definované v [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) soubor, který spouští server SQL Server pro Linux s všech databází systému SQL Server potřebné pro mikroslužeb. (Můžete také mít jednoho kontejneru typu SQL Server pro každou databázi, ale které by vyžadovaly další paměť přiřazená Docker.) V mikroslužeb důležité je, že každý mikroslužbu vlastníkem souvisejících dat, proto jeho související databáze SQL v tomto případě. Ale databáze může být odkudkoli.

Kontejner v ukázkové aplikace, které lze nastavit následující kód YAML v docker-compose.yml souboru, který se spustí při spuštění systému SQL Server docker vytvořit zálohu. Všimněte si, že má kód YAML konsolidovat informace o konfiguraci ze souboru obecného docker-compose.yml a soubor docker-compose.override.yml. (By obvykle jednotlivé nastavení prostředí základní nebo statické informace související s bitovou kopii systému SQL Server.)

```yml
  sql.data:
    image: microsoft/mssql-server-linux
    environment:
      - MSSQL_SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
      - MSSQL_PID=Developer
    ports:
      - "5434:1433"
```

Podobným způsobem, nepoužívejte `docker-compose`, následující `docker run` příkaz můžete spustit tento kontejner:

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD= your@password' -p 1433:1433 -d microsoft/mssql-server-linux
```

Pokud nasazujete aplikaci s více kontejneru jako eShopOnContainers, je však pohodlnější použití docker tvoří až příkaz tak, aby ji nasadí všechny kontejnery, které jsou požadované pro aplikaci.

Při prvním spuštění tohoto kontejneru systému SQL Server, inicializuje kontejneru systému SQL Server s heslem, které zadáte. Jakmile systém SQL Server běží jako kontejner, můžete aktualizovat databázi připojením přes všechny regulární připojení SQL, například z SQL Server Management Studio, Visual Studio nebo C\# kódu.

Aplikace eShopOnContainers inicializuje každou mikroslužbu databázi s ukázkovými daty synchronizace replik indexů s daty při spuštění, jak je popsáno v následující části.

S SQL Server běžící jako kontejner není právě užitečné pro ukázku kde nebudete mít přístup k instanci systému SQL Server. Jak je uvedeno je také výborně hodí pro vývoj a testování prostředí, aby mohli snadno testy integrace od vyčištění bitové kopie systému SQL Server a známých dat seedingem nové ukázková data.

#### <a name="additional-resources"></a>Další zdroje

-   **Bitovou kopii SQL serveru Docker systémem Linux, Mac nebo Windows**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker*](https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker)

-   **Připojení a dotazování systému SQL Server v systému Linux pomocí sqlcmd**
    [*https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd*](https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a>Synchronizace replik indexů s testovací data při spuštění webové aplikace

Chcete-li přidat data do databáze při spuštění aplikace, můžete přidat kód jako následující konfigurace metody ve třídě spuštění projektu webového rozhraní API:

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

Následující kód ve třídě vlastní CatalogContextSeed naplní data.

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

Při spuštění testů integrace s způsob generování dat, které jsou konzistentní s testy integrace je užitečné. Schopnost vytvářet všechno od začátku, včetně instance systému SQL Server běžící na kontejner, je velmi užitečná pro testovací prostředí.

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>EF InMemory základní databáze a SQL Server běžící jako kontejner

Jiné dobrou volbou při spouštění testů je použití zprostředkovatele databáze Entity Framework InMemory. Tato konfigurace můžete zadat v metodě ConfigureServices třída při spuštění v projektu webového rozhraní API:

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

Když je důležité catch. Databázi v paměti nepodporuje mnoho omezení, které jsou specifické pro určitou databázi. Může například přidat jedinečný index na sloupci ve model EF jádra a zápis testu proti databázi v paměti zkontrolujte, že ho neumožňuje přidat duplicitní hodnota. Ale pokud používáte databázi v paměti, nemůže zpracovat jedinečné indexy na sloupec. Databázi v paměti proto není chovají stejně jako skutečné databázi systému SQL Server – ji není emulovat omezení specifické pro databázi.

I tak databázi v paměti je stále užitečné pro testování a při vytváření prototypu. Ale pokud chcete vytvořit přesný integrace testy, které vzít v úvahu chování implementace konkrétní databázi, budete muset použít skutečné databáze jako SQL Server. K tomuto účelu systémem SQL Server v kontejneru je dobře choice a přesnější, než EF InMemory základní zprostředkovatel databáze.

### <a name="using-a-redis-cache-service-running-in-a-container"></a>Pomocí služby Redis cache spuštěné v kontejneru

Redis můžete spustit na kontejner, zejména pro vývoj a testování a testování konceptu. Tento scénář je vhodné, protože může mít všechny svoje závislosti, které jsou spuštěné v kontejnery – nejen pro místní vývoj počítače, ale pro vaše testovací prostředí v nástroji CI/CD kanály.

Když spustíte Redis v produkčním prostředí, je však lepší vyhledejte řešení vysoké dostupnosti jako Redis Microsoft Azure, který se spouští jako PaaS (platforma jako služba). V kódu stačí změnit připojovací řetězce.

Redis poskytuje bitovou kopii Docker s Redis. Tento obrázek k dispozici z úložiště Docker Hub na této adrese URL:

<https://hub.docker.com/_/redis/>

Kontejner Docker Redis můžete spustit přímo spuštěním následujícího příkazu příkazového řádku Dockeru v příkazovém řádku:

```
  docker run --name some-redis -d redis
```

Bitovou kopii Redis zahrnuje zveřejněte: 6379 (port je používán Redis), takže standardní propojení kontejner bude zpřístupněte ji automaticky propojené kontejnery.

Mikroslužbu basket.api v eShopOnContainers, používá spuštěna jako kontejner mezipaměti Redis. Tento kontejner basket.data je definována v rámci více kontejner docker-compose.yml souboru, jak je znázorněno v následujícím příkladu:

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

Tento kód v docker-compose.yml definuje kontejner s názvem basket.data na základě bitové kopie redis a publikování port 6379 interně, což znamená, že bude dostupný pouze z jiných kontejnerů běžící v rámci hostitelů Docker.

Nakonec v soubor docker-compose.override.yml mikroslužbu basket.api pro ukázku eShopOnContainers definuje připojovací řetězec k použití pro tento kontejner Redis:

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```


>[!div class="step-by-step"]
[Předchozí](multi-container-applications-docker-compose.md)
[další](integration-event-based-microservice-communications.md)
