---
title: Vytvoření jednoduché mikroslužby CRUD řízené daty
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Pochopit vytvoření jednoduché crud (data řízený) mikroslužeb v rámci aplikace mikroslužeb.
ms.date: 01/30/2020
ms.openlocfilehash: b72d7defed81e57e2971c5e2b53df2d86b2dc947
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77502362"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a>Vytvoření jednoduché mikroslužby CRUD řízené daty

Tato část popisuje, jak vytvořit jednoduchou mikroslužbu, která provádí operace vytváření, čtení, aktualizace a odstraňování (CRUD) na zdroji dat.

## <a name="designing-a-simple-crud-microservice"></a>Návrh jednoduchémikroslužby CRUD

Z hlediska návrhu je tento typ kontejnerizované mikroslužby velmi jednoduchý. Možná, že problém vyřešit, je jednoduchý, nebo snad implementace je jen důkazem koncepce.

![Diagram znázorňující jednoduchý interní návrhový vzor CRUD mikroslužeb.](./media/data-driven-crud-microservice/internal-design-simple-crud-microservices.png)

**Obrázek 6-4**. Interní návrh pro jednoduché mikroslužby CRUD

Příkladem tohoto druhu služby jednoduché datové jednotky je mikroslužba katalogu z ukázkové aplikace eShopOnContainers. Tento typ služby implementuje všechny své funkce v jediném ASP.NET projektu základního webového rozhraní API, který zahrnuje třídy pro svůj datový model, obchodní logiku a přístupový kód dat. Také ukládá související data v databázi spuštěné v SQL Server (jako jiný kontejner pro účely vývoj/testování), ale může být také libovolný běžný hostitel SQL Server, jak je znázorněno na obrázku 6-5.

![Diagram znázorňující kontejner mikroslužeb řízený daty/CRUD.](./media/data-driven-crud-microservice/simple-data-driven-crud-microservice.png)

**Obrázek 6-5**. Jednoduchý návrh mikroslužeb řízený daty/CRUD

Předchozí diagram znázorňuje logickou mikroslužbu katalogu, která zahrnuje databázi katalogu, která může být nebo nemusí být ve stejném hostiteli Dockeru. Mít databázi ve stejném hostiteli Dockeru může být dobré pro vývoj, ale ne pro produkční prostředí. Při vývoji tohoto druhu služby, stačí [pouze ASP.NET core](https://docs.microsoft.com/aspnet/core/) a rozhraní API pro přístup k datům nebo ORM jako entity framework [core](https://docs.microsoft.com/ef/core/index). Můžete také generovat metadata [Swagger](https://swagger.io/) automaticky prostřednictvím [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) poskytnout popis toho, co vaše služba nabízí, jak je vysvětleno v další části.

Všimněte si, že spuštění databázového serveru, jako je SQL Server v kontejneru Dockeru je skvělé pro vývojová prostředí, protože můžete mít všechny vaše závislosti v provozu bez nutnosti zřizování databáze v cloudu nebo místně. To je velmi výhodné při spuštění integračních testů. Však pro produkční prostředí spuštění databázového serveru v kontejneru se nedoporučuje, protože obvykle nezískáte vysokou dostupnost s tímto přístupem. Pro produkční prostředí v Azure se doporučuje používat Azure SQL DB nebo jakoukoli jinou databázovou technologii, která může poskytovat vysokou dostupnost a vysokou škálovatelnost. Například pro přístup NoSQL můžete zvolit CosmosDB.

Nakonec úpravou souborů metadat Dockerfile a docker-compose.yml můžete nakonfigurovat, jak bude vytvořena bitová kopie tohoto kontejneru – jakou základní bitovou kopii bude používat, plus nastavení návrhu, jako jsou interní a externí názvy a porty TCP.

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a>Implementace jednoduché mikroslužby CRUD s ASP.NET Core

Chcete-li implementovat jednoduchou mikroslužbu CRUD pomocí .NET Core a Visual Studio, můžete začít vytvořením jednoduchého ASP.NET projektu základního webového rozhraní API (spuštěného na .NET Core, aby mohl běžet na hostiteli Linux Docker), jak je znázorněno na obrázku 6-6.

![Snímek obrazovky s vizuálními studii zobrazující nastavení projektu](./media/data-driven-crud-microservice/create-asp-net-core-web-api-project.png)

**Obrázek 6-6**. Vytvoření projektu ASP.NET základního webového rozhraní API ve Visual Studiu 2019

Chcete-li vytvořit ASP.NET projektu základního webového rozhraní API, nejprve vyberte ASP.NET základní webovou aplikaci a pak vyberte typ rozhraní API. Po vytvoření projektu můžete implementovat řadiče MVC stejně jako v jakémkoli jiném projektu webového rozhraní API pomocí rozhraní API entity framework nebo jiného rozhraní API. V novém projektu webového rozhraní API uvidíte, že jediná závislost, kterou máte v této mikroslužbě, je na ASP.NET samotnéjádro. Interně v rámci *Microsoft.AspNetCore.All* závislost, odkazuje entity framework a mnoho dalších .NET Core NuGet balíčky, jak je znázorněno na obrázku 6-7.

![Snímek obrazovky VS zobrazující závislosti NuGet catalog.api.](./media/data-driven-crud-microservice/simple-crud-web-api-microservice-dependencies.png)

**Obrázek 6-7**. Závislosti v jednoduché mikroslužbě CRUD Web API

Projekt rozhraní API obsahuje odkazy na balíček Microsoft.AspNetCore.App NuGet, který obsahuje odkazy na všechny základní balíčky. To by mohlo zahrnovat některé další balíčky stejně.

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a>Implementace webových api služeb CRUD pomocí jádra entity frameworku

Entity Framework (EF) Core je lehká, rozšiřitelná a multiplatformní verze populární technologie přístupu k datům Entity Framework. EF Core je objektrelační mapovač (ORM), který umožňuje vývojářům rozhraní .NET pracovat s databází pomocí objektů .NET.

Mikroslužba katalogu používá EF a zprostředkovatele SERVERU SQL Server, protože jeho databáze běží v kontejneru s bitovou kopií SQL Server pro Linux Docker. Databáze však může být nasazena do libovolného serveru SQL Server, jako je například místní systém Windows nebo Azure SQL DB. Jediné, co byste museli změnit, je připojovací řetězec v mikroslužbě ASP.NET webového rozhraní API.

#### <a name="the-data-model"></a>Datový model

S EF Core přístup k datům se provádí pomocí modelu. Model se skládá z tříd entit (model domény) a odvozeného kontextu (DbContext), který představuje relaci s databází, což umožňuje dotazovat a ukládat data. Můžete generovat model z existující databáze, ručně kódovat model tak, aby odpovídaly vaší databázi nebo pomocí migrace EF vytvořit databázi z modelu, pomocí přístupu první kód (který usnadňuje vývoj databáze jako váš model změny v průběhu času). Pro mikroslužbu katalogu používáme poslední přístup. Příklad třídy entity CatalogItem můžete zobrazit v následujícím příkladu kódu, což je jednoduchá třída entit Prostý starý objekt CLR ([POCO).](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)

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

Potřebujete také DbContext, který představuje relaci s databází. Pro mikroslužbu katalogu, CatalogContext třída je odvozena od dbcontext základní třídy, jak je znázorněno v následujícím příkladu:

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

Můžete mít `DbContext` další implementace. Například v ukázkové mikroslužbě Catalog.API je `DbContext` druhý `CatalogContextSeed` pojmenovaný, kde automaticky naplní ukázková data při prvním pokusu o přístup k databázi. Tato metoda je užitečná také pro ukázková data a pro scénáře automatizovaného testování.

V `DbContext`rámci aplikace `OnModelCreating` můžete metodu použít k přizpůsobení mapování entit objektu/databáze a dalších [bodů rozšiřitelnosti EF](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).

##### <a name="querying-data-from-web-api-controllers"></a>Dotazování na data z řadičů webového rozhraní API

Instance tříd entity se obvykle načítají z databáze pomocí jazyka Integrovaný dotaz (LINQ), jak je znázorněno v následujícím příkladu:

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

Data jsou v databázi vytvářena, odstraňována a upravována pomocí instancí tříd entit. Do řadičů webového rozhraní API můžete přidat kód jako následující pevně zakódovaný příklad (v tomto případě mock data).

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a>Vkládání závislostí v řadičích ASP.NET jádra a webového rozhraní API

V ASP.NET Core můžete použít vkládání závislostí (DI) po vybalení z krabice. Není nutné nastavit kontejner inverze řízení (IoC) jiného výrobce, i když můžete připojit upřednostňovaný kontejner IoC do infrastruktury ASP.NET Core, pokud chcete. V tomto případě to znamená, že můžete přímo vložit požadované EF DBContext nebo další úložiště prostřednictvím konstruktoru řadiče.

V příkladu výše `CatalogController` třídy jsme vstřikování objekttypu `CatalogContext` plus `CatalogController()` další objekty prostřednictvím konstruktoru.

Důležitou konfigurací, kterou chcete nastavit v projektu webového rozhraní API, je registrace třídy DbContext do kontejneru IoC služby. Obvykle tak učiníte `Startup` ve třídě `services.AddDbContext<DbContext>()` voláním `ConfigureServices()` metody uvnitř metody, jak je znázorněno v následujícím **zjednodušeném** příkladu:

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

- **Dotazování na data** \
  [https://docs.microsoft.com/ef/core/querying/index](/ef/core/querying/index)

- **Ukládání dat** \
  [https://docs.microsoft.com/ef/core/saving/index](/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a>Připojovací řetězec DB a proměnné prostředí používané kontejnery Dockeru

Můžete použít ASP.NET nastavení jádra a přidat vlastnost ConnectionString do souboru settings.json, jak je znázorněno v následujícím příkladu:

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

Soubor settings.json může mít výchozí hodnoty pro vlastnost ConnectionString nebo pro jakoukoli jinou vlastnost. Tyto vlastnosti však budou přepsány hodnotami proměnných prostředí, které zadáte v souboru docker-compose.override.yml při použití Dockeru.

Ze souborů docker-compose.yml nebo docker-compose.override.yml můžete tyto proměnné prostředí inicializovat, aby je Docker nastavil jako proměnné prostředí operačního systému, jak je znázorněno v následujícím souboru docker-compose.override.yml (připojení řetězec a další řádky zalomit v tomto příkladu, ale nebude zalomit ve vlastním souboru).

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

Soubory docker-compose.yml na úrovni řešení jsou nejen flexibilnější než konfigurační soubory na úrovni projektu nebo mikroslužeb, ale také bezpečnější, pokud přepíšete proměnné prostředí deklarované v souborech docker-compose s hodnotami nastavenými z vaše nástroje pro nasazení, například z úloh nasazení Azure DevOps Services Dockeru.

Nakonec můžete získat tuto hodnotu z\[kódu pomocí\]konfigurace "ConnectionString" , jak je znázorněno v ConfigureServices metoda v příkladu dřívější kód.

V produkčních prostředích však můžete chtít prozkoumat další způsoby, jak ukládat tajné kódy, jako jsou připojovací řetězce. Vynikající způsob správy tajných kódů aplikací je pomocí [azure key vault](https://azure.microsoft.com/services/key-vault/).

Azure Key Vault pomáhá ukládat a chránit kryptografické klíče a tajné klíče používané cloudovými aplikacemi a službami. Tajemství je vše, co chcete zachovat přísnou kontrolu, jako jsou klíče API, připojovací řetězce, hesla, *among others*atd.

Azure Key Vault umožňuje velmi podrobnou úroveň řízení použití tajných kódů aplikace bez nutnosti dát někomu vědět. Tajné klíče lze dokonce otočit pro lepší zabezpečení bez narušení vývoje nebo operace.

Aplikace musí být registrovány ve službě Active Directory organizace, aby mohly používat trezor klíčů.

Další podrobnosti naleznete v *dokumentaci k konceptům úložiště klíčů.*

### <a name="implementing-versioning-in-aspnet-web-apis"></a>Implementace správy verzí v ASP.NET webových api

S tím, jak se mění obchodní požadavky, mohou být přidány nové kolekce prostředků, mohou se změnit vztahy mezi prostředky a může být změněna struktura dat v prostředcích. Aktualizace webového rozhraní API pro zpracování nových požadavků je poměrně jednoduchý proces, ale je třeba zvážit účinky, které tyto změny budou mít na klientské aplikace, které spotřebovávají webové rozhraní API. Přestože vývojář navrhování a implementace webového rozhraní API má plnou kontrolu nad tímto rozhraním API, vývojář nemá stejný stupeň kontroly nad klientskými aplikacemi, které mohou být vytvořeny organizacemi třetích stran, které pracují vzdáleně.

Správa verzí umožňuje webové rozhraní API k označení funkcí a prostředků, které zveřejňuje. Klientská aplikace pak může odesílat požadavky na konkrétní verzi funkce nebo prostředku. Existuje několik přístupů k implementaci správy verzí:

- Správa verzí pomocí identifikátoru URI

- Správa verzí pomocí řetězce dotazu

- Správa verzí pomocí hlavičky

Řetězec dotazu a správa verzí identifikátoru URI jsou nejjednodušší implementovat. Správa verzí záhlaví je dobrý přístup. Správa verzí záhlaví však není tak explicitní a přímočará jako správa verzí uri. Vzhledem k tomu, že správa verzí adresy URL je nejjednodušší a nejexplicitnější, ukázková aplikace eShopOnContainers používá správu verzí IDENTIFIKÁTORURI.

S uri správu verzí, stejně jako v eShopOnContainers ukázkové aplikace, pokaždé, když upravíte webové rozhraní API nebo změnit schéma prostředků, přidáte číslo verze uri pro každý prostředek. Existující identifikátory URI by měly nadále fungovat jako dříve a vracet prostředky, které odpovídají schématu, které odpovídá požadované verzi.

Jak je znázorněno v následujícím příkladu kódu, verzi lze nastavit pomocí atributu Route v řadiči webového rozhraní API, což činí verzi explicitní v uri (v1 v tomto případě).

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

Tento mechanismus správy verzí je jednoduchý a závisí na směrování požadavku serveru do příslušného koncového bodu. Pro sofistikovanější správu verzí a nejlepší metodu při použití REST byste však měli použít hypermédia a implementovat [HATEOAS (Hypertext jako modul stavu aplikace).](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources)

### <a name="additional-resources"></a>Další zdroje

- **Scott Hanselman. ASP.NET snadné správu verzí webového rozhraní API ASP.NET** \
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- **Správa verzí webového rozhraní RESTful** \
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- **Roye Fieldinga. Správa verzí, hypermédia a REST** \
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a>Generování metadat popisu Swagger z ASP.NET core webovérozhraní API

[Swagger](https://swagger.io/) je běžně používaný open source framework podporovaný velkým ekosystémem nástrojů, které vám pomohou navrhovat, vytvářet, dokumentovat a využívat vaše rozhraní API RESTful. Stává se standardem pro doménu metadat popisu api. Měli byste zahrnout metadata popisu Swagger s jakýmkoli druhem mikroslužeb, mikroslužeb řízených daty nebo pokročilejšími mikroslužbami řízenými doménami (jak je vysvětleno v následující části).

Srdcem Swagger je specifikace Swagger, což je metadata popisu rozhraní API v souboru JSON nebo YAML. Specifikace vytvoří kontrakt RESTful pro vaše rozhraní API, který podrobně popisuje všechny jeho prostředky a operace v lidském i strojově čitelném formátu pro snadný vývoj, zjišťování a integraci.

Specifikace je základem specifikace OpenAPI (OAS) a je vyvinuta v otevřené, transparentní a kolaborativní komunitě pro standardizaci způsobu, jakým jsou definována rozhraní RESTful.

Specifikace definuje strukturu pro způsob zjištění služby a jak je pochopena její možnosti. Další informace, včetně webového editoru a příkladů specifikací Swagger od společností jako Spotify, Uber, Slack a Microsoft, najdete na webu Swagger (<https://swagger.io>).

### <a name="why-use-swagger"></a>Proč použít Swagger?

Hlavní důvody pro generování metadat Swagger pro vaše api jsou následující.

**Možnost automatického využívání a integrace vašich api pro ostatní produkty**. Swagger podporují desítky produktů a [komerčních nástrojů](https://swagger.io/commercial-tools/) a mnoho [knihoven a rámců.](https://swagger.io/open-source-integrations/) Společnost Microsoft má produkty vysoké úrovně a nástroje, které mohou automaticky využívat rozhraní API založená na programu Swagger, například následující:

- [AutoRest](https://github.com/Azure/AutoRest). Můžete automaticky generovat třídy klienta .NET pro volání Swagger. Tento nástroj lze použít z rozhraní SEkatel a také integruje s Visual Studio pro snadné použití prostřednictvím GUI.

- [Microsoft Flow](https://flow.microsoft.com/). Rozhraní API můžete automaticky [používat a integrovat](https://flow.microsoft.com/blog/integrating-custom-api/) do pracovního postupu Microsoft Flow na vysoké úrovni bez nutnosti programování.

- [Aplikace Microsoft PowerApps](https://powerapps.microsoft.com/). Své ROZHRANÍ API můžete automaticky využívat z [mobilních aplikací PowerApps vytvořených](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) pomocí [PowerApps Studia](https://powerapps.microsoft.com/build-powerapps/), bez nutnosti programování.

- [Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps). You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.

**Možnost automatického generování dokumentace rozhraní API**. Při vytváření rozsáhlých RESTful API, jako jsou komplexní aplikace založené na mikroslužbách, je třeba zpracovat mnoho koncových bodů s různými datovými modely používanými v datové části požadavku a odpovědi. Mít správnou dokumentaci a mít solidní průzkumník rozhraní API, jak se dostanete s Swagger, je klíčem k úspěchu vašeho rozhraní API a přijetí vývojáři.

Metadata Swaggeru jsou to, co Microsoft Flow, PowerApps a Azure Logic Apps používají k pochopení toho, jak používat rozhraní API a připojit se k nim.

Existuje několik možností, jak automatizovat generování metadat Swagger pro ASP.NET aplikace Core REST API, ve formě funkčních stránek nápovědy ROZHRANÍ API, založených na *swagger-ui*.

Pravděpodobně nejlepší vědět, je [Swashbuckle,](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) který je v současné době používá v [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) a budeme pokrývat v některých detailech v\# této příručce,\# ale je tu také možnost používat [NSwag](https://github.com/RSuter/NSwag), který může generovat Typescript a C API klienty, stejně jako C řadiče, z Swagger nebo OpenAPI specifikace a dokonce skenování .dll, který obsahuje řadiče, pomocí [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a>Jak automatizovat generování metadat API Swagger pomocí balíčku Swashbuckle NuGet

Generování metadat Swagger ručně (v souboru JSON nebo YAML) může být zdlouhavá práce. Můžete však automatizovat zjišťování rozhraní API ASP.NET služby webového rozhraní API pomocí [balíčku Swashbuckle NuGet](https://aka.ms/swashbuckledotnetcore) pro dynamickou generování metadat rozhraní API Swagger.

Swashbuckle automaticky generuje metadata Swagger pro vaše projekty webového rozhraní API ASP.NET. Podporuje ASP.NET core web API projekty a tradiční ASP.NET webové rozhraní API a jakékoli jiné varianty, jako je například Azure API App, Azure Mobile App, Azure Service Fabric mikroslužeb na základě ASP.NET. Podporuje také prosté webové rozhraní API nasazené v kontejnerech, jako v pro referenční aplikaci.

Swashbuckle kombinuje průzkumníka rozhraní API a Swagger nebo [swagger-ui](https://github.com/swagger-api/swagger-ui) a poskytuje bohaté prostředí pro zjišťování a dokumentaci pro vaše spotřebitele rozhraní API. Kromě svého motoru generátoru metadat Swagger obsahuje Swashbuckle také vestavěnou verzi swagger-ui, která bude automaticky sloužit až po instalaci Swashbuckle.

To znamená, že můžete doplnit rozhraní API o příjemné zjišťování uI pomoci vývojářům používat vaše rozhraní API. Vyžaduje velmi malé množství kódu a údržby, protože je automaticky generována, což vám umožní soustředit se na vytváření rozhraní API. Výsledek pro průzkumníka rozhraní API vypadá jako obrázek 6-8.

![Snímek obrazovky s Průzkumníkem rozhraní Api Swagger zobrazujícím rozhraní API eShopOContainers.](./media/data-driven-crud-microservice/swagger-metadata-eshoponcontainers-catalog-microservice.png)

**Obrázek 6-8**. Swashbuckle API Explorer založený na metadatech Swagger – mikroslužba katalogu eShopOnContainers

Swashbuckle generované Swagger Rozhraní API dokumentace obsahuje všechny publikované akce. Průzkumník rozhraní API zde není nejdůležitější věc. Jakmile budete mít webové rozhraní API, které lze popsat sám sebe v metadatech Swagger, vaše rozhraní API lze bez problémů použít z nástrojů založených na Swagger, včetně generátorů kódu proxy klienta třídy proxy, které mohou cílit na mnoho platforem. Například, jak již bylo zmíněno, [AutoRest](https://github.com/Azure/AutoRest) automaticky generuje třídy klienta .NET. Ale další nástroje, jako [je swagger-codegen](https://github.com/swagger-api/swagger-codegen) jsou také k dispozici, které umožňují generování kódu klientských knihoven rozhraní API, server zástupné procedury a dokumentace automaticky.

V současné době swashbuckle se skládá z pěti interních balíčků NuGet pod metabalíčkem s vysokou úrovní [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) pro ASP.NET aplikace Core.

Po instalaci těchto balíčků NuGet v projektu webového rozhraní API je třeba nakonfigurovat Swagger ve třídě Startup, jako v následujícím **zjednodušeném** kódu:

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

Jakmile to uděláte, můžete spustit aplikaci a procházet následující koncové body Swagger JSON a UI pomocí adres URL, jako jsou tyto:

```console
  http://<your-root-url>/swagger/v1/swagger.json

  http://<your-root-url>/swagger/
```

Dříve jste viděli generované ui vytvořené Swashbuckle `http://<your-root-url>/swagger`pro ADRESU URL, jako je . Na obrázku 6-9 můžete také vidět, jak můžete otestovat libovolnou metodu rozhraní API.

![Snímek obrazovky s uzlou rozhraní Swagger zobrazující dostupné testovací nástroje](./media/data-driven-crud-microservice/swashbuckle-ui-testing.png)

**Obrázek 6-9**. Uživatelské rozhraní Swashbuckle otestování metody rozhraní API katalogu/položek

Podrobnosti rozhraní API Swagger u> zobrazuje ukázku odpovědi a lze použít ke spuštění skutečné rozhraní API, což je skvělé pro zjišťování vývojáře. Obrázek 6-10 ukazuje Swagger JSON metadata generovaná z eShopOnContainers mikroslužby (což je to, co nástroje používají pod) při žádosti pomocí `http://<your-root-url>/swagger/v1/swagger.json` [Postman](https://www.getpostman.com/).

![Snímek obrazovky s ukázkovým pošťákovým uzemňovacím rozhraním zobrazujícím metadata Swagger JSON](./media/data-driven-crud-microservice/swagger-json-metadata.png)

**Obrázek 6-10**. Metadata Swagger JSON

Je to tak jednoduché. A protože je automaticky generována, metadata Swagger se zvýší, když přidáte další funkce do rozhraní API.

### <a name="additional-resources"></a>Další zdroje

- **stránky nápovědy webového rozhraní API ASP.NET pomocí swaggeru** \
  [https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger](/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- **Začínáme s Swashbuckle a ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle](/aspnet/core/tutorials/getting-started-with-swashbuckle)

- **Začínáme s NSwag a ASP.NET Core** \
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag](/aspnet/core/tutorials/getting-started-with-nswag)

> [!div class="step-by-step"]
> [Předchozí](microservice-application-design.md)
> [další](multi-container-applications-docker-compose.md)
