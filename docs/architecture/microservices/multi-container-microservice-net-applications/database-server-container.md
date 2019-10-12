---
title: Použití databázového serveru, který se používá jako kontejner
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Používáte databázový server, který běží jako kontejner? jenom pro vývoj. Vysvětlení, proč.
ms.date: 10/02/2018
ms.openlocfilehash: a508ba734525b24e2f3f00408e2c59c8c00f1898
ms.sourcegitcommit: 9c3a4f2d3babca8919a1e490a159c1500ba7a844
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/12/2019
ms.locfileid: "72291303"
---
# <a name="using-a-database-server-running-as-a-container"></a>Použití databázového serveru, který se používá jako kontejner

Vaše databáze (SQL Server, PostgreSQL, MySQL atd.) můžete mít na běžných samostatných serverech, v místních clusterech nebo v PaaS službách v cloudu, jako je Azure SQL DB. Nicméně pro vývojová a testovací prostředí je vhodné, aby vaše databáze spuštěné jako kontejnery byly pohodlné, protože nemáte žádnou externí závislost a stačí spustit příkaz `docker-compose up`, spustí celou aplikaci. Aby byly tyto databáze stejně vhodné pro integrační testy, protože databáze je spuštěna v kontejneru a je vždy naplněna stejnými ukázkovými daty, testy mohou být předvídatelné.

### <a name="sql-server-running-as-a-container-with-a-microservice-related-database"></a>SQL Server spuštěn jako kontejner s databází související s mikroslužbami

V eShopOnContainers je k dispozici kontejner s názvem SQL. data definovaná v souboru [Docker-Compose. yml](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/docker-compose.yml) , který spouští SQL Server pro Linux se všemi SQL Server databázemi, které jsou pro mikroslužby potřeba. (Můžete mít také jeden kontejner SQL Server pro každou databázi, ale to by vyžadovalo více paměti, která je přiřazena k Docker.) Důležitým bodem v mikroslužbách je, že každá mikroslužba vlastní související data, proto v tomto případě související databáze SQL. Ale databáze můžou být kdekoli.

Kontejner SQL Server v ukázkové aplikaci je nakonfigurován s následujícím YAML kódem v souboru Docker-Compose. yml, který se spustí při spuštění `docker-compose up`. Všimněte si, že kód YAML má konsolidované informace o konfiguraci z obecného souboru Docker-Compose. yml a souboru Docker-Compose. override. yml. (Obvykle byste odvolali nastavení prostředí ze základních nebo statických informací, které se vztahují k SQL Server imagi.)

```yml
  sql.data:
    image: microsoft/mssql-server-linux:2017-latest
    environment:
      - SA_PASSWORD=Pass@word
      - ACCEPT_EULA=Y
    ports:
      - "5434:1433"
```

Podobným způsobem namísto použití `docker-compose` může tento kontejner spustit následující příkaz `docker run`:

```console
docker run -e 'ACCEPT_EULA=Y' -e 'SA_PASSWORD=Pass@word' -p 5433:1433 -d microsoft/mssql-server-linux:2017-latest
```

Pokud však nasazujete aplikaci s více kontejnery, jako je eShopOnContainers, je vhodnější použít příkaz `docker-compose up`, aby nástroj nasadil všechny požadované kontejnery pro aplikaci.

Při prvním spuštění tohoto kontejneru SQL Server kontejner inicializuje SQL Server s heslem, které zadáte. Jakmile SQL Server spustíte jako kontejner, můžete aktualizovat databázi připojením přes jakékoli běžné připojení SQL, jako je například z SQL Server Management Studio, Visual Studio nebo C @ no__t-0 Code.

Aplikace eShopOnContainers inicializuje každou databázi mikroslužeb pomocí ukázkových dat tím, že je dokončí daty při spuštění, jak je vysvětleno v následující části.

Použití SQL Server jako kontejneru není právě užitečné pro ukázku, ve které nemůžete mít přístup k instanci SQL Server. Jak je uvedeno, je vhodné také pro vývojová a testovací prostředí, abyste mohli snadno spouštět testy integrace počínaje čistým SQL Server obrázkem a známými daty pomocí osazení nových ukázkových dat.

#### <a name="additional-resources"></a>Další zdroje

- **Spuštění bitové kopie SQL Server Docker v systému Linux, Mac nebo Windows** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-setup-docker](/sql/linux/sql-server-linux-setup-docker)

- **Připojení a dotazování SQL Server on Linux pomocí sqlcmd** \
    [https://docs.microsoft.com/sql/linux/sql-server-linux-connect-and-query-sqlcmd](/sql/linux/sql-server-linux-connect-and-query-sqlcmd)

### <a name="seeding-with-test-data-on-web-application-startup"></a>Osazení s testovacími daty při spuštění webové aplikace

Chcete-li přidat data do databáze při spuštění aplikace, můžete do metody Configure ve spouštěcí třídě projektu webového rozhraní API přidat kód podobný následujícímu:

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

### <a name="ef-core-inmemory-database-versus-sql-server-running-as-a-container"></a>EF Core nepaměťové databáze versus SQL Server spuštěná jako kontejner

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

### <a name="using-a-redis-cache-service-running-in-a-container"></a>Používání služby Redis Cache spuštěné v kontejneru

Redis můžete spustit na kontejneru, zejména pro vývoj a testování, a pro scénáře testování konceptů. Tento scénář je vhodný, protože můžete mít všechny závislosti spuštěné v kontejnerech, nikoli jenom pro místní vývojové počítače, ale pro testovací prostředí v kanálech CI/CD.

Pokud ale spustíte Redis v produkčním prostředí, je lepší vyhledat řešení s vysokou dostupností, jako je Redis Microsoft Azure, které běží jako PaaS (platforma jako služba). V kódu je pouze nutné změnit připojovací řetězce.

Redis poskytuje image Docker s Redis. Tato bitová kopie je k dispozici z Docker Hub na této adrese URL:

<https://hub.docker.com/\_/redis/>

Kontejner Docker Redis můžete přímo spustit spuštěním následujícího příkazu Docker CLI na příkazovém řádku:

```console
docker run --name some-redis -d redis
```

Image Redis zahrnuje vystavení: 6379 (port, který používá Redis), takže standardní propojení kontejnerů bude automaticky dostupné pro propojené kontejnery.

V eShopOnContainers se v košíku. mikroslužba API používá Redis Cache spuštěná jako kontejner. Tento koš. data Container je definován jako součást souboru Docker-Compose. yml s více kontejnery, jak je znázorněno v následujícím příkladu:

```yml
#docker-compose.yml file
#...
  basket.data:
    image: redis
    expose:
      - "6379"
```

Tento kód v Docker-Compose. yml definuje kontejner s názvem košík. data založená na imagi Redis a interním publikováním portu 6379, což znamená, že bude přístupný pouze z jiných kontejnerů spuštěných v rámci hostitele Docker.

Nakonec můžete v souboru Docker-Compose. override. yml, který je součástí koše, používá mikroslužba API pro ukázku eShopOnContainers připojovací řetězec, který se má použít pro tento kontejner Redis:

```yml
  basket.api:
    environment:
      # Other data ...
      - ConnectionString=basket.data
      - EventBusConnection=rabbitmq
```

Jak už bylo zmíněno dříve, název košíku mikroslužeb. data je vyřešen interní sítí DNS Docker.

>[!div class="step-by-step"]
>[Předchozí](multi-container-applications-docker-compose.md)
>[Další](integration-event-based-microservice-communications.md)
