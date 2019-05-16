---
title: Použití databázového serveru, který se používá jako kontejner
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Použití databázového serveru běžícího jako kontejner? pouze pro vývoj! Zjistěte, proč.
ms.date: 10/02/2018
ms.openlocfilehash: 5fd92a28a09cab041225c4c817a10f5ecfedc038
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639730"
---
# <a name="using-a-database-server-running-as-a-container"></a>Použití databázového serveru, který se používá jako kontejner

Pravidelné samostatných serverů v místních clusterech nebo na služby modelu PaaS v cloudu jako Azure SQL DB může mít vaše databáze (SQL Server, PostgreSQL, MySQL atd.). Ale pro vývojová a testovací prostředí s databází systémem jako kontejnery je vhodné, protože nemáte žádné externí závislosti, jednoduše `docker-compose up` příkaz spustí celou aplikaci. Tyto databáze jako kontejnery je také skvěle hodí pro integrační testy, protože databáze je spuštěn v kontejneru a je vždy naplněný stejná vzorová data, tak testů může být předvídatelnější.

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>SQL serveru běžícího jako kontejner s databází související mikroslužeb

V aplikaci eShopOnContainers, je kontejner s názvem sql.data definované v [docker-compose.yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) soubor, který spouští SQL Server pro Linux s všech databází systému SQL Server potřebné pro mikroslužby. (Může mít také jeden kontejner systému SQL Server pro každou databázi, ale větší množství paměti, které jsou přiřazeny k Dockeru, který by vyžadovaly.) Důležité v mikroslužbách je, že každá mikroslužba je vlastníkem související data, proto jeho související databáze SQL v tomto případě. Ale databáze může být libovolného místa.

Kontejner SQL serveru v ukázkové aplikaci je nakonfigurovaný s následující kód YAML v souboru docker-compose.yml, který se spustí, až spustíte `docker-compose up`. Všimněte si, že má kód YAML konsolidovat informace o konfiguraci ze souboru obecného docker-compose.yml a docker-compose.override.yml souboru. (Obvykle by se oddělují nastavení prostředí a informace o základní nebo statické bitové kopie systému SQL Server.)

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

Podobným způsobem, namísto použití `docker-compose`, následující `docker run` tento kontejner můžete spustit příkaz:

```
  docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

Pokud nasazujete vícekontejnerovou aplikaci jako aplikaci eShopOnContainers, je ale vhodnější použít `docker-compose up` příkaz tak, aby nasadí všechny požadované kontejnery pro aplikace.

Při prvním spuštění tohoto kontejneru systému SQL Server, inicializuje kontejneru systému SQL Server s heslem, které zadáte. Jakmile systém SQL Server běží jako kontejner, můžete aktualizovat databázi připojením přes jakékoli pravidelné připojení SQL, jako například SQL Server Management Studio, Visual Studio nebo C\# kódu.

Aplikaci eShopOnContainers aplikace inicializuje jednotlivých mikroslužeb databázi s ukázkovými daty synchronizace replik indexů s daty při spuštění, jak je vysvětleno v následující části.

S SQL serveru běžícího jako kontejner není právě užitečná pro ukázku kde pravděpodobně nebudete mít přístup k instanci systému SQL Server. Jak je uvedeno je také velmi vhodné pro vývojová a testovací prostředí tak, aby můžete snadno spouštět testy integrace od čistou bitovou kopii systému SQL Server a data nezná synchronizace replik indexů nová vzorová data.

#### <a name="additional-resources"></a>Další zdroje

- **Spuštění image SQL serveru Docker v Linuxu, Mac nebo Windows** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](/sql/linux/sql-server-linux-setup-docker)

- **Připojení a dotazování SQL serveru v Linuxu pomocí sqlcmd** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a>Předvyplnění daty testu při spuštění webové aplikace

Přidání dat do databáze při spuštění aplikace, můžete přidat kód následujícím postupem konfigurace metody ve třídě spouštěný projekt webového rozhraní API:

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

Při spuštění testů integrace, způsob, jak vygenerovat konzistentní s testy integrace dat je užitečné. Možnost vytvoření čehokoliv od začátku, včetně instance systému SQL Server spuštěnou v kontejneru, je velmi vhodné pro testovací prostředí.

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>EF Core InMemory databáze versus SQL serveru běžícího jako kontejner

Další dobrou volbou při spouštění testů se má používat databázi zprostředkovatele Entity Framework InMemory. Tuto konfiguraci můžete zadat v metodě ConfigureServices třída při spuštění ve vašem projektu webového rozhraní API:

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

I když je důležité catch. Databáze v paměti nepodporuje spousta omezení, které jsou specifické pro konkrétní databázi. Může například přidat jedinečný index pro sloupec v modelu EF Core a napsat test na vaší databázi v paměti, zkontrolujte, že to neumožňuje přidání duplicitní hodnoty. Ale při použití databáze v paměti, nemůže zpracovat jedinečné indexy pro sloupec. Proto se databáze v paměti se nechová stejně jako skutečná databáze systému SQL Server – to není emulovat omezení konkrétních databází.

I tak databázi v paměti je stále užitečná pro vytváření prototypů a testování. Ale pokud chcete vytvořit přesné integrační testy, které vezměte v úvahu chování implementace konkrétní databázi, budete muset použít skutečné databáze jako SQL Server. Pro tento účel systémem SQL Server v kontejneru je skvělý choice a přesnější, než si zprostředkovatele databáze EF Core InMemory.

### <a name="using-a-redis-cache-service-running-in-a-container"></a>Pomocí služby mezipaměti Redis spuštěné v kontejneru

Redis můžete spustit v kontejneru, zejména pro vývoj a testování a pro scénáře testování konceptu. Tento scénář je vhodný, protože budete mít všechny svoje závislosti, které běží na kontejnery – ne jenom pro počítače s místním vývojovým, ale pro vaše testovací prostředí ve vašich kanálů CI/CD.

Při spuštění Redis v produkčním prostředí, je však lepší vyhledejte řešení vysoké dostupnosti, jako je například Redis Microsoft Azure, který se spouští jako PaaS (platforma jako služba). Ve vašem kódu stačí změnit připojovací řetězce.

Redis poskytuje image Dockeru s využitím Redis. Tento image je k dispozici z Docker Hubu na této adrese URL:

<https://hub.docker.com/\_/redis/>

Kontejner Dockeru Redis můžete spustit přímo spuštěním následujícího příkazu rozhraní příkazového řádku Dockeru v příkazovém řádku:

```
  docker run --name some-redis -d redis
```

Redis image zahrnuje vystavení: 6379 (port je používán Redis), tedy standardní propojení kontejneru zpřístupníte ji automaticky propojené kontejnery.

V aplikaci eShopOnContainers používá mikroslužeb basket.api běžícího jako kontejner mezipaměti redis Cache. Tento kontejner basket.data je definován jako součást souboru více kontejnerů docker-compose.yml, jak je znázorněno v následujícím příkladu:

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

Tento kód v docker-compose.yml definuje kontejner s názvem basket.data na základě redis image a publikování port 6379 interně, což znamená, že je přístupný pouze z jiných kontejnerů v rámci hostitele Dockeru.

Nakonec v souboru docker-compose.override.yml basket.api mikroslužeb pro vzorovou aplikaci eShopOnContainers definuje připojovací řetězec má použít pro tento kontejner Redis:

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

Jak jsme zmínili, název mikroslužeb "basket.data" vyřešil docker interní sítě DNS.

>[!div class="step-by-step"]
>[Předchozí](multi-container-applications-docker-compose.md)
>[další](integration-event-based-microservice-communications.md)
