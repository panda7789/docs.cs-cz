---
title: Vytvoření jednoduché mikroslužby CRUD řízené daty
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Pochopení vytvoření jednoduché mikroslužby CRUD (data řízená daty) v rámci kontextu aplikace mikroslužeb.
ms.date: 01/30/2020
ms.openlocfilehash: b72d7defed81e57e2971c5e2b53df2d86b2dc947
ms.sourcegitcommit: f38e527623883b92010cf4760246203073e12898
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/20/2020
ms.locfileid: "77502362"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a>Vytvoření jednoduché mikroslužby CRUD řízené daty

Tato část popisuje, jak vytvořit jednoduchou mikroslužbu, která provádí operace vytvoření, čtení, aktualizace a odstranění (CRUD) ve zdroji dat.

## <a name="designing-a-simple-crud-microservice"></a>Návrh jednoduché mikroslužby CRUD

Z hlediska návrhu je tento typ kontejnerové mikroslužby velmi jednoduchý. Je možné, že problém, který se má vyřešit, je jednoduchý nebo možná implementace je pouze důkaz konceptu.

![Diagram znázorňující jednoduchý vzor návrhu mikroslužeb CRUD](./media/data-driven-crud-microservice/internal-design-simple-crud-microservices.png)

**Obrázek 6-4**. Interní návrh jednoduchých mikroslužeb CRUD

Příkladem tohoto druhu jednoduchých datových jednotek je služba cloudová služba z ukázkové aplikace eShopOnContainers. Tento typ služby implementuje všechny funkce v jednom ASP.NET Core projektu webového rozhraní API, který obsahuje třídy pro svůj datový model, jeho obchodní logiku a kód pro přístup k datům. Ukládá také data v databázi běžící v SQL Server (jako jiný kontejner pro účely vývoje a testování), ale může to být také jakýkoli pravidelný SQL Server Hostitel, jak je znázorněno na obrázku 6-5.

![Diagram znázorňující datově řízený kontejner mikroslužeb nebo CRUD.](./media/data-driven-crud-microservice/simple-data-driven-crud-microservice.png)

**Obrázek 6-5**. Jednoduchý návrh mikroslužeb založený na datech/CRUD

Předchozí diagram znázorňuje mikroslužbu logického katalogu, která obsahuje svou databázi katalogu, která může být nebo ne ve stejném hostiteli Docker. Databáze ve stejném hostiteli Docker může být vhodná pro vývoj, ale ne pro produkční prostředí. Při vývoji tohoto typu služby potřebujete jenom [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) a rozhraní API pro přístup k datům nebo ORM, jako je [Entity Framework Core](https://docs.microsoft.com/ef/core/index). Metadata [Swagger](https://swagger.io/) můžete také automaticky vygenerovat prostřednictvím [swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) a zadat popis toho, co vaše služba nabízí, jak je vysvětleno v další části.

Všimněte si, že provoz databázového serveru, jako je SQL Server v kontejneru Docker, je skvělý pro vývojová prostředí, protože můžete mít všechny závislosti v provozu, aniž byste museli zřídit databázi v cloudu nebo místně. To je velmi užitečné při spouštění integračních testů. V produkčních prostředích se ale nedoporučuje používat databázový server v kontejneru, protože pro tento přístup obvykle nezískáte vysokou dostupnost. V produkčním prostředí v Azure se doporučuje používat službu Azure SQL DB nebo jakoukoli jinou databázovou technologii, která může poskytovat vysokou dostupnost a vysokou škálovatelnost. Například pro NoSQL přístup můžete zvolit CosmosDB.

Nakonec můžete úpravou souborů metadat souboru Dockerfile a Docker-Compose. yml nakonfigurovat, jak se vytvoří obrázek tohoto kontejneru – jakou základní image bude používat, a také nastavení návrhu, jako jsou interní a externí názvy a porty TCP.

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a>Implementace jednoduché mikroslužby CRUD pomocí ASP.NET Core

Chcete-li implementovat jednoduchou mikroslužbu CRUD pomocí .NET Core a sady Visual Studio, Začněte vytvořením jednoduchého projektu ASP.NET Core webového rozhraní API (běžícího na rozhraní .NET Core, který je možné spustit na hostiteli Docker Linux), jak je znázorněno na obrázku 6-6.

![Snímek obrazovky s vizuálním studia se zobrazením nastavení projektu.](./media/data-driven-crud-microservice/create-asp-net-core-web-api-project.png)

**Obrázek 6-6**. Vytvoření projektu webového rozhraní API ASP.NET Core v aplikaci Visual Studio 2019

Pokud chcete vytvořit ASP.NET Core projekt webového rozhraní API, vyberte nejdřív ASP.NET Core webovou aplikaci a pak vyberte typ rozhraní API. Po vytvoření projektu můžete své řadiče MVC implementovat stejně jako v jakémkoli jiném projektu webového rozhraní API, a to pomocí rozhraní Entity Framework API nebo jiného rozhraní API. V novém projektu webového rozhraní API vidíte, že jediná závislost, kterou máte v této mikroslužbě, je ASP.NET Core sama. Interně v rámci závislosti *Microsoft. AspNetCore. All* odkazuje na Entity Framework a spoustu dalších balíčků NuGet pro .NET Core, jak je znázorněno na obrázku 6-7.

![Snímek obrazovky sady Visual Studio zobrazující závislosti NuGet Catalog. API](./media/data-driven-crud-microservice/simple-crud-web-api-microservice-dependencies.png)

**Obrázek 6-7**. Závislosti v jednoduché mikroslužbě webového rozhraní API CRUD

Projekt rozhraní API obsahuje odkazy na balíček NuGet Microsoft. AspNetCore. app, který obsahuje odkazy na všechny podstatné balíčky. Může to zahrnovat i některé další balíčky.

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a>Implementace služeb webového rozhraní API CRUD pomocí Entity Framework Core

Jádro Entity Framework (EF) je odlehčená, rozšiřitelná a více platforem oblíbené technologie Entity Framework data pro přístup k datům. EF Core je objektově-relační Mapovač (ORM), který umožňuje vývojářům rozhraní .NET pracovat s databází pomocí objektů .NET.

Mikroslužba katalogu používá EF a poskytovatele SQL Server, protože jeho databáze je spuštěná v kontejneru s SQL Server pro Image Docker pro Linux. Databázi ale můžete nasadit do libovolného SQL Server, jako je Windows v místním prostředí nebo Azure SQL DB. Jedinou věcí, kterou byste mohli změnit, je připojovací řetězec v mikroslužbě ASP.NET webového rozhraní API.

#### <a name="the-data-model"></a>Datový model

Pomocí EF Core se přístup k datům provádí pomocí modelu. Model se skládá z tříd entit (doménového modelu) a odvozeného kontextu (DbContext), který představuje relaci s databází, a umožňuje dotazování a ukládání dat. Můžete vygenerovat model z existující databáze, ručně kód modelu tak, aby odpovídal vaší databázi, nebo pomocí migrace EF vytvořit databázi z modelu pomocí přístupu k prvnímu kódu (který usnadňuje vývoj databáze jako změny modelu v čase). Pro mikroslužbu katalogu používáme Poslední přístup. Příklad třídy entity CatalogItem lze vidět v následujícím příkladu kódu, což je jednoduchá Třída entity Object typu CLR ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)).

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureFileName { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public int AvailableStock { get; set; }
    public int RestockThreshold { get; set; }
    public int MaxStockThreshold { get; set; }

    public bool OnReorder { get; set; }
    public CatalogItem() { }

    // Additional code ...
}
```

Budete také potřebovat DbContext, který představuje relaci s databází. Pro mikroslužbu katalogu je třída CatalogContext odvozená od základní třídy DbContext, jak je znázorněno v následujícím příkladu:

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    { }
    public DbSet<CatalogItem> CatalogItems { get; set; }
    public DbSet<CatalogBrand> CatalogBrands { get; set; }
    public DbSet<CatalogType> CatalogTypes { get; set; }

    // Additional code ...
}
```

Můžete mít další implementace `DbContext`. Například v ukázkovém katalogu. mikroslužba rozhraní API má druhý `DbContext` s názvem `CatalogContextSeed`, kde se při prvním pokusu o přístup k databázi automaticky naplní ukázková data. Tato metoda je užitečná pro ukázková data a také pro scénáře automatizovaného testování.

V rámci `DbContext`použijete metodu `OnModelCreating` k přizpůsobení mapování entit objektu/databáze a dalších [bodů rozšiřitelnosti EF](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).

##### <a name="querying-data-from-web-api-controllers"></a>Dotazování dat z řadičů webového rozhraní API

Instance tříd vaší entity se obvykle načítají z databáze pomocí jazyka LINQ (Language Integrated Query), jak je znázorněno v následujícím příkladu:

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _catalogContext;
    private readonly CatalogSettings _settings;
    private readonly ICatalogIntegrationEventService _catalogIntegrationEventService;

    public CatalogController(
        CatalogContext context,
        IOptionsSnapshot<CatalogSettings> settings,
        ICatalogIntegrationEventService catalogIntegrationEventService)
    {
        _catalogContext = context ?? throw new ArgumentNullException(nameof(context));
        _catalogIntegrationEventService = catalogIntegrationEventService
            ?? throw new ArgumentNullException(nameof(catalogIntegrationEventService));

        _settings = settings.Value;
        context.ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("items")]
    [ProducesResponseType(typeof(PaginatedItemsViewModel<CatalogItem>), (int)HttpStatusCode.OK)]
    [ProducesResponseType(typeof(IEnumerable<CatalogItem>), (int)HttpStatusCode.OK)]
    [ProducesResponseType((int)HttpStatusCode.BadRequest)]
    public async Task<IActionResult> ItemsAsync(
        [FromQuery]int pageSize = 10,
        [FromQuery]int pageIndex = 0,
        string ids = null)
    {
        if (!string.IsNullOrEmpty(ids))
        {
            var items = await GetItemsByIdsAsync(ids);

            if (!items.Any())
            {
                return BadRequest("ids value invalid. Must be comma-separated list of numbers");
            }

            return Ok(items);
        }

        var totalItems = await _catalogContext.CatalogItems
            .LongCountAsync();

        var itemsOnPage = await _catalogContext.CatalogItems
            .OrderBy(c => c.Name)
            .Skip(pageSize * pageIndex)
            .Take(pageSize)
            .ToListAsync();

        itemsOnPage = ChangeUriPlaceholder(itemsOnPage);

        var model = new PaginatedItemsViewModel<CatalogItem>(
            pageIndex, pageSize, totalItems, itemsOnPage);

        return Ok(model);
    }
    //...
}
```

##### <a name="saving-data"></a>Ukládání dat

Data se vytvářejí, odstraňují a upravují v databázi s použitím instancí tříd vaší entity. Do vašich řadičů webového rozhraní API můžete přidat kód, například následující pevně zakódovaný příklad (data v tomto případě).

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a>Vkládání závislostí v ASP.NET Core a v řadičích webového rozhraní API

V ASP.NET Core můžete použít vkládání závislostí (DI) z pole. Nemusíte nastavovat kontejner IoC (inverze) třetí strany, ale pokud chcete, můžete svůj preferovaný kontejner IoC připojit do infrastruktury ASP.NET Core. V takovém případě to znamená, že můžete přímo vložit požadované DBContext EF nebo další úložiště prostřednictvím konstruktoru kontroleru.

V příkladu výše `CatalogController` třídy vkládáme objekt typu `CatalogContext` a další objekty prostřednictvím konstruktoru `CatalogController()`.

Důležitou konfigurací, která se nastavuje v projektu webového rozhraní API, je registrace třídy DbContext do kontejneru IoC služby. To obvykle provedete ve třídě `Startup` voláním metody `services.AddDbContext<DbContext>()` uvnitř metody `ConfigureServices()`, jak je znázorněno v následujícím **zjednodušeném** příkladu:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Additional code...

    services.AddDbContext<CatalogContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.MigrationsAssembly(
                typeof(Startup).GetTypeInfo().Assembly.GetName().Name);

           //Configuring Connection Resiliency:
           sqlOptions.
               EnableRetryOnFailure(maxRetryCount: 5,
               maxRetryDelay: TimeSpan.FromSeconds(30),
               errorNumbersToAdd: null);

       });

       // Changing default behavior when client evaluation occurs to throw.
       // Default in EFCore would be to log warning when client evaluation is done.
       options.ConfigureWarnings(warnings => warnings.Throw(
           RelationalEventId.QueryClientEvaluationWarning));
   });

  //...
}
```

### <a name="additional-resources"></a>Další zdroje

- **Dotazování na Data** \
  [https://docs.microsoft.com/ef/core/querying/index](/ef/core/querying/index)

- **Ukládání \ dat**
  [https://docs.microsoft.com/ef/core/saving/index](/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a>Připojovací řetězec databáze a proměnné prostředí používané kontejnery Docker

Můžete použít nastavení ASP.NET Core a přidat vlastnost ConnectionString do souboru Settings. JSON, jak je znázorněno v následujícím příkladu:

```json
{
    "ConnectionString": "Server=tcp:127.0.0.1,5433;Initial Catalog=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word",
    "ExternalCatalogBaseUrl": "http://localhost:5101",
    "Logging": {
        "IncludeScopes": false,
        "LogLevel": {
            "Default": "Debug",
            "System": "Information",
            "Microsoft": "Information"
        }
    }
}
```

Soubor Settings. JSON může mít výchozí hodnoty pro vlastnost ConnectionString nebo pro jakoukoliv jinou vlastnost. Tyto vlastnosti však budou přepsány hodnotami proměnných prostředí, které zadáte v souboru Docker-Compose. override. yml při použití Docker.

Z vašich souborů Docker-Compose. yml nebo Docker-Compose. yml můžete inicializovat tyto proměnné prostředí tak, aby je Docker nastavil jako proměnné prostředí operačního systému, jak je znázorněno v následujícím souboru Docker-Compose. override. yml (připojení v tomto příkladu se zabalí řetězec a další řádky, ale nezalomí do vlastního souboru).

```yml
# docker-compose.override.yml

#
catalog-api:
  environment:
    - ConnectionString=Server=sqldata;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    # Additional environment variables for this service
  ports:
    - "5101:80"
```

Soubory Docker-Compose. yml na úrovni řešení nejsou pružnější než konfigurační soubory na úrovni projektu nebo mikroslužby, ale také bezpečnější, pokud přepíšete proměnné prostředí deklarované v souborech Docker-skládání s hodnotami nastavenými na nástroje pro nasazení, například z úloh nasazení Docker Azure DevOps Services.

Nakonec můžete tuto hodnotu získat z kódu pomocí konfiguračního\["ConnectionString"\], jak je znázorněno v metodě ConfigureServices v předchozím příkladu kódu.

V produkčních prostředích však můžete chtít prozkoumat další způsoby ukládání tajných kódů, jako jsou připojovací řetězce. Skvělý způsob správy tajných klíčů aplikací používá [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).

Azure Key Vault pomáhá ukládat a chránit kryptografické klíče a tajné klíče používané vašimi cloudových aplikacemi a službami. Tajný kód je cokoli, co chcete zachovat striktní řízení, jako jsou klíče rozhraní API, připojovací řetězce, hesla atd. a striktní řízení zahrnuje protokolování použití, nastavení vypršení platnosti, Správa přístupu, *mimo jiné*.

Azure Key Vault umožňuje velmi detailní úroveň řízení používání tajných klíčů aplikací, aniž by bylo nutné, aby ji znali kdokoli. Tajné kódy je dokonce možné otočit za účelem zvýšení zabezpečení, aniž by došlo k narušení vývoje nebo provozu.

Aplikace musí být zaregistrované ve službě Active Directory organizace, aby mohli používat Key Vault.

Další podrobnosti najdete v *dokumentaci k konceptům Key Vault* .

### <a name="implementing-versioning-in-aspnet-web-apis"></a>Implementace správy verzí ve webových rozhraních API ASP.NET

V rámci změny obchodních požadavků se můžou přidat nové kolekce prostředků, můžou se změnit vztahy mezi prostředky a struktura dat v prostředcích se může změnit. Aktualizace webového rozhraní API tak, aby zpracovávala nové požadavky, je poměrně přímočarý proces, ale je potřeba vzít v úvahu účinky, které tyto změny budou mít na klientských aplikacích, které spotřebovávají webové rozhraní API. I když vývojář, který navrhuje a implementuje webové rozhraní API, má plnou kontrolu nad tímto rozhraním API, vývojář nemá stejnou úroveň kontroly nad klientskými aplikacemi, které mohou být vytvořeny organizacemi třetích stran, které jsou provozovány vzdáleně.

Správa verzí umožňuje webovému rozhraní API označovat funkce a prostředky, které zveřejňuje. Klientská aplikace pak může odeslat požadavky na konkrétní verzi funkce nebo prostředku. Existuje několik přístupů k implementaci správy verzí:

- Správa verzí pomocí identifikátoru URI

- Správa verzí pomocí řetězce dotazu

- Správa verzí pomocí hlavičky

Způsob implementace řetězce dotazu a verze identifikátoru URI je nejjednodušší. Správa verzí hlaviček je dobrým přístupem. Nicméně verze hlaviček není tak explicitní a přímá jako verze identifikátoru URI. Vzhledem k tomu, že správa verzí adres URL je nejjednodušší a nejpřesnější, používá ukázková aplikace eShopOnContainers správu verzí pomocí identifikátoru URI.

S verzí identifikátoru URI, jako v ukázkové aplikaci eShopOnContainers, pokaždé, když upravíte webové rozhraní API nebo změníte schéma prostředků, přidáte číslo verze k identifikátoru URI pro každý prostředek. Existující identifikátory URI by měly nadále fungovat jako dřív a vracet prostředky, které odpovídají schématu odpovídajícímu požadované verzi.

Jak je znázorněno v následujícím příkladu kódu, verze lze nastavit pomocí atributu směrování v rámci kontroleru webového rozhraní API, který v tomto případě provede explicitní verzi v identifikátoru URI (V1).

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

Tento mechanismus správy verzí je jednoduchý a závisí na serveru, který požadavek směruje na příslušný koncový bod. Pro výkonnější správu verzí a nejlepší způsob používání REST je však vhodné použít médium a implementovat [HATEOAS (hypertextový odkaz jako modul stavu aplikace)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).

### <a name="additional-resources"></a>Další zdroje

- **Scott Hanselman ASP.NET Core RESTful webové rozhraní API, které se dají snadno** \
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- **Správa verzí RESTful webového rozhraní API** \
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- **Roy pole. Správa verzí, multimédií a REST** \
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a>Generování metadat popisu Swagger z ASP.NET Core webového rozhraní API

[Swagger](https://swagger.io/) je běžně používaná platforma open source, kterou poskytuje velký ekosystém nástrojů, který vám pomůže navrhovat, sestavovat, zdokumentovat a spotřebovávat rozhraní RESTful API. Stane se standardem pro doménu metadat popisu rozhraní API. Měli byste zahrnout metadata popisu Swagger s jakýmkoli druhem mikroslužeb, buď mikroslužby řízené daty, nebo pokročilejší mikroslužby založené na doméně (jak je vysvětleno v následující části).

Srdcem Swagger je specifikace Swagger, což je metadata popisu rozhraní API v souboru JSON nebo YAML. Specifikace vytvoří pro vaše rozhraní API kontrakt RESTful, který podrobně popisuje všechny jeho prostředky a operace v uživatelsky čitelném formátu pro snadné vývoj, zjišťování a integraci.

Specifikace je základem pro specifikaci OpenAPI (OAS) a je vyvíjena v otevřené, transparentní a spolupracovní komunitě pro standardizaci způsobu, jakým jsou definována rozhraní RESTful.

Specifikace definuje strukturu, jak může být služba zjištěná a jak se její schopnosti považují. Další informace, včetně webového editoru a příkladů specifikací Swagger od společností, jako je Spotify, Uber, časová rezerva a Microsoft, najdete na webu Swagger (<https://swagger.io>).

### <a name="why-use-swagger"></a>Proč používat Swagger?

Hlavními důvody pro vygenerování metadat Swagger pro vaše rozhraní API jsou následující.

**Schopnost dalších produktů automaticky využívat a integrovat vaše rozhraní API**. Spousta produktů a [komerčních nástrojů](https://swagger.io/commercial-tools/) a mnoho [knihoven a platforem](https://swagger.io/open-source-integrations/) podporují Swagger. Microsoft má produkty vysoké úrovně a nástroje, které mohou automaticky využívat rozhraní API založená na Swagger, například následující:

- [AutoRest](https://github.com/Azure/AutoRest). Můžete automaticky vygenerovat klientské třídy .NET pro volání Swagger. Tento nástroj lze použít z CLI a také se integruje se sadou Visual Studio pro snadné použití prostřednictvím grafického uživatelského rozhraní.

- [Microsoft Flow](https://flow.microsoft.com/). [Své rozhraní API můžete automaticky používat a integrovat](https://flow.microsoft.com/blog/integrating-custom-api/) do Microsoft Flowho pracovního postupu na nejvyšší úrovni, aniž by se vyžadovaly žádné znalosti programování.

- [Microsoft PowerApps](https://powerapps.microsoft.com/). Své rozhraní API můžete automaticky využít z [PowerAppsch mobilních aplikací](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) vytvořených pomocí [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), aniž by se vyžadovaly žádné znalosti programování.

- [Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps). [Své rozhraní API můžete automaticky používat a integrovat do aplikace Azure App Service Logic](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), bez nutnosti programování.

**Schopnost automaticky generovat dokumentaci k rozhraní API**. Když vytváříte rozsáhlá rozhraní API RESTful, jako jsou komplexní aplikace založené na mikroslužbách, je potřeba zvládnout mnoho koncových bodů s různými datovými modely použitými v datových vytíženích žádosti a odpovědi. V případě, že máte správnou dokumentaci a máte plnou dokumentaci k rozhraní API, je klíč pro úspěch vašeho rozhraní API a jejich přijetí vývojáři.

Metadata Swagger je to, co Microsoft Flow, PowerApps a Azure Logic Apps využívají k pochopení, jak používat rozhraní API a připojení k nim.

K dispozici je několik možností pro automatizaci generování metadat Swagger pro aplikace ASP.NET Core REST API, ve formě stránek s podporou funkčního rozhraní API na základě *uživatelského rozhraní Swagger*.

Je pravděpodobné, že nejlepší je [swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) , který se aktuálně používá v [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) , a v tomto průvodci se podrobněji podíváme, ale je k dispozici také možnost použít [NSwag](https://github.com/RSuter/NSwag), která může vygenerovat\# klienta rozhraní API TypeScript a c a také řadiče jazyka c\#, ze sady Swagger nebo specifikace openapi, a to i kontrolou knihovny DLL, která obsahuje řadiče, pomocí [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a>Automatizace generování metadat Swagger API pomocí balíčku NuGet swashbuckle

Ruční generování metadat Swagger (v souboru JSON nebo YAML) může být zdlouhavá práce. Rozpoznávání rozhraní API služeb webového rozhraní API ASP.NET ale můžete automatizovat pomocí [balíčku NuGet swashbuckle](https://aka.ms/swashbuckledotnetcore) a dynamicky generovat metadata rozhraní Swagger API.

Swashbuckle automaticky generuje metadata Swagger pro vaše projekty webového rozhraní API pro ASP.NET. Podporuje ASP.NET Core projekty webového rozhraní API a tradiční webové rozhraní API ASP.NET a jakékoli jiné charaktery, jako je například aplikace API Azure, mobilní aplikace Azure, Azure Service Fabric mikroslužby založené na ASP.NET. Podporuje také jednoduché webové rozhraní API nasazené na kontejnerech, jako v případě referenční aplikace.

Swashbuckle kombinuje rozhraní API Explorer a Swagger nebo [Swagger – uživatelské rozhraní](https://github.com/swagger-api/swagger-ui) pro poskytování bohatých funkcí zjišťování a dokumentace pro vaše příjemce rozhraní API. Kromě svého modulu generátoru metadat Swagger swashbuckle obsahuje také vloženou verzi Swagger – uživatelské rozhraní, které bude automaticky fungovat po instalaci swashbuckle.

To znamená, že můžete své rozhraní API doplnit o uživatelské rozhraní s dobrým zjišťováním, které vývojářům umožní používat vaše rozhraní API. Vyžaduje velmi malý objem kódu a údržby, protože se vygeneruje automaticky, takže se můžete soustředit na vytváření rozhraní API. Výsledek pro Průzkumník rozhraní API vypadá jako obrázek 6-8.

![Snímek obrazovky s rozhraním API Swagger, které zobrazuje rozhraní eShopOContainers API](./media/data-driven-crud-microservice/swagger-metadata-eshoponcontainers-catalog-microservice.png)

**Obrázek 6-8**. Swashbuckle Explorer API na základě metadat Swagger – mikroslužba eShopOnContainers Catalog

Dokumentace k rozhraní API uživatelského rozhraní Swagger vygenerované swashbuckle zahrnuje všechny publikované akce. Průzkumník rozhraní API není tady nejdůležitější. Po použití webového rozhraní API, které se může považovat za sebe sama v metadatech Swagger, se dá rozhraní API bez problémů používat v nástrojích založených na Swagger, včetně generátorů kódu třídy proxy serveru klienta, které můžou cílit na mnoho platforem. Například jak je uvedeno, automatické [REST](https://github.com/Azure/AutoRest) automaticky vygeneruje klientské třídy .NET. Ale k dispozici jsou i další nástroje, jako je [Swagger-CodeGen](https://github.com/swagger-api/swagger-codegen) , což umožňuje automatické generování kódu klientských knihoven API, zástupných procedur serveru a dokumentaci.

V současné době se swashbuckle skládá z pěti vnitřních balíčků NuGet v rámci meta-Package [swashbuckle. AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) pro aplikace ASP.NET Core.

Po instalaci těchto balíčků NuGet do projektu webového rozhraní API je potřeba nakonfigurovat Swagger ve třídě Startup, jako v následujícím **zjednodušeném** kódu:

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...

        // Add framework services.
        services.AddSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SwaggerDoc("v1", new OpenApiInfo
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API. This is a Data-Driven/CRUD microservice sample"
            });
        });

        // Other ConfigureServices() code...
    }

    public void Configure(IApplicationBuilder app,
        IHostingEnvironment env,
        ILoggerFactory loggerFactory)
    {
        // Other Configure() code...
        // ...
        app.UseSwagger()
            .UseSwaggerUI(c =>
            {
                c.SwaggerEndpoint("/swagger/v1/swagger.json", "My API V1");
            });
    }
}
```

Až to uděláte, můžete aplikaci spustit a procházet následujícími koncovými body JSON a UI pomocí adres URL, jako jsou tyto:

```console
  http://<your-root-url>/swagger/v1/swagger.json

  http://<your-root-url>/swagger/
```

Dříve jste viděli vygenerované uživatelské rozhraní vytvořené nástrojem swashbuckle pro adresu URL, jako je `http://<your-root-url>/swagger`. Na obrázku 6-9 můžete také zjistit, jak můžete testovat jakoukoli metodu rozhraní API.

![Snímek obrazovky uživatelského rozhraní Swagger zobrazující dostupné testovací nástroje](./media/data-driven-crud-microservice/swashbuckle-ui-testing.png)

**Obrázek 6-9**. Testování uživatelského rozhraní swashbuckle – metoda rozhraní API katalogu/položek

Podrobnosti o rozhraní API uživatelského rozhraní Swagger zobrazuje ukázku odpovědi a dá se použít ke spuštění reálného rozhraní API, které je skvělé pro vyhledávání pro vývojáře. Obrázek 6-10 ukazuje metadata JSON pro Swagger vygenerovaná z mikroslužby eShopOnContainers (to, co nástroje používá), když vyžádáte `http://<your-root-url>/swagger/v1/swagger.json` pomocí [post](https://www.getpostman.com/).

![Snímek obrazovky s ukázkovým uživatelským rozhraním, které zobrazuje metadata JSON pro Swagger](./media/data-driven-crud-microservice/swagger-json-metadata.png)

**Obrázek 6-10**. Metadata JSON pro Swagger

To je jednoduché. A vzhledem k tomu, že se automaticky generuje, metadata Swagger se po přidání dalších funkcí do rozhraní API zvětší.

### <a name="additional-resources"></a>Další zdroje

- **Stránky pomoci webového rozhraní API ASP.NET pomocí swagger** \
  [https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger](/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- **Začínáme s swashbuckle a ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle](/aspnet/core/tutorials/getting-started-with-swashbuckle)

- **Začínáme s NSwag a ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag](/aspnet/core/tutorials/getting-started-with-nswag)

> [!div class="step-by-step"]
> [Předchozí](microservice-application-design.md)
> [Další](multi-container-applications-docker-compose.md)
