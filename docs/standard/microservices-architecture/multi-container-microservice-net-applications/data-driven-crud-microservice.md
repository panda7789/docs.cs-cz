---
title: Vytvoření jednoduchého mikroslužbu CRUD řízené daty
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Vytvoření jednoduchého mikroslužbu CRUD řízené daty
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 85694cbfe8c30b8430200f0ffbd01379f11b3f9d
ms.sourcegitcommit: c03eef711abe961a85db2b4d0715257d1524aef6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/08/2018
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a>Vytvoření jednoduchého mikroslužbu CRUD řízené daty

Tato část obsahuje přehled, jak vytvořit jednoduchou mikroslužbu, který provádí vytváření, čtení, aktualizace a operace odstranění (CRUD) ve zdroji dat.

## <a name="designing-a-simple-crud-microservice"></a>Navrhování jednoduché mikroslužbu CRUD

Z návrhu hlediska je velmi jednoduchý tento typ kontejnerizované mikroslužby. Možná je jednoduchá problém vyřešit, nebo možná implementace je pouze testování konceptu.

![](./media/image4.png)

**Obrázek 8-4**. Interní návrhu pro jednoduché mikroslužeb CRUD

Příkladem tento druh jednoduché datové jednotky služby je mikroslužbu katalogu v eShopOnContainers ukázkové aplikaci. Tento typ služby implementuje všechny její funkce v jedné projekt webového rozhraní API ASP.NET Core, který obsahuje třídy pro svůj model dat, jeho obchodní logiky a jeho data přístupový kód. Také ukládá související data v databázi spuštěna v systému SQL Server (jako jiný kontejner pro účely vývoje/testování), ale mohou být také všechny regulární hostitele systému SQL Server, jak ukazuje obrázek 8-5.

![](./media/image5.png)

**Obrázek 8-5**. Jednoduché mikroslužbu data řízené/CRUD návrhu

Při vývoji tento druh služby, je třeba pouze [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) a rozhraní API pro přístup k datům nebo ORM jako [Entity Framework Core](https://docs.microsoft.com/ef/core/index). Může také generovat [Swagger](https://swagger.io/) metadata automaticky přes [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) zajistit popis co nabízí služby, jak je popsáno v následující části.

Všimněte si, že spuštění databázový server, jako je SQL Server v rámci kontejner Docker je skvělá pro vývojové prostředí, protože všechny závislosti může mít a bez nutnosti zřídit databázi v cloudu nebo místně. To je velmi praktické, když spouštění integrace testů. Ale pro provozní prostředí, serverem databáze v kontejneru nedoporučuje, protože se obvykle nezobrazí vysoká dostupnost s Tento přístup. Pro produkční prostředí v Azure se doporučuje používat databázi SQL Azure nebo jakékoli jiné databáze technologie, která můžete zajistit vysokou dostupnost a škálovatelnost vysoké. Například pro přístup NoSQL, můžete zvolit DocumentDB.

Nakonec úpravy souborů metadat soubor Docker a docker-compose.yml, můžete konfigurovat vytváření bitové kopie tohoto kontejneru, jaký základní image budou používat plus návrh nastavení, jako například vnitřní a vnější názvy a porty TCP. 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a>Implementace jednoduchého mikroslužbu CRUD pomocí ASP.NET Core

Chcete-li implementovat jednoduché mikroslužbu CRUD pomocí .NET Core a Visual Studio, začněte vytvořením jednoduchého projektu webového rozhraní API ASP.NET Core (spuštěna na .NET Core, můžete spustit na hostiteli systému Linux Docker), jako obrázku 8-6.

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  ![](./media/image6.png)   ![](./media/image7.png)
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

**Obrázek 8-6**. Vytvoření projektu webového rozhraní API ASP.NET Core v sadě Visual Studio

Po vytvoření projektu, můžete implementovat vaše řadiče MVC, stejně jako v jiných projekt webového rozhraní API pomocí rozhraní Entity Framework API nebo dalších rozhraní API. V nový projekt webového rozhraní API uvidíte, že pouze závislost máte, mikroslužby jsou v technologii ASP.NET Core sám sebe. Interně v rámci `Microsoft.AspNetCore.All` závislostí, odkazuje na Entity Framework a mnoho dalších balíčcích Nuget pro rozhraní .NET Core, jak je znázorněno na obrázku 8-7.

![](./media/image8.PNG)

**Obrázek 8-7**. Závislosti v jednoduché mikroslužbu CRUD webového rozhraní API

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a>Implementace služby CRUD webového rozhraní API základní Entity Framework

Základní Entity Framework (EF) je lightweight rozšiřitelný, a přístup technologie a platformy verzi oblíbených datům Entity Framework. Základní EF je objekt relační mapper (ORM), která umožňuje vývojářům rozhraní .NET pro práci s objekty .NET pomocí databáze.

Mikroslužbu katalogu používá EF a zprostředkovatele SQL Server, protože jeho databáze se spouští v kontejneru se systémem SQL Server pro Linux Docker bitovou kopii. Databáze však může být nasazený do všech ostatních SQL serverech, jako je Windows na pracovišti nebo v databázi SQL Azure. Jediné, co by se musela změnit je připojovací řetězec v rozhraní ASP.NET Web API mikroslužby.


#### <a name="the-data-model"></a>Datový model

Základní EF provádí se přístup k datům pomocí modelu. Model se skládá z tříd entit a odvozené kontext, který představuje relaci s databází, což umožňuje dotazování a uložit data. Můžete generovat model z existující databáze, ručně code model tak, aby odpovídaly vaší databáze nebo použijte EF migrace vytvořit databázi z modelu (a momentální ho jako váš model změny v čase). Mikroslužbu katalogu používáme poslední přístup. Vidíte příklad třídy entity CatalogItem v následujícím příkladu kódu, který je jednoduchý prostý původní objekt CLR ([objektů POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) třídy entita.

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

Budete také potřebovat DbContext, který představuje relaci s databází. Pro katalog mikroslužbu, CatalogContext třída je odvozena ze základní třídy DbContext, jak je znázorněno v následujícím příkladu:

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {
    }
    public DbSet<CatalogItem> CatalogItems { get; set; }
    public DbSet<CatalogBrand> CatalogBrands { get; set; }
    public DbSet<CatalogType> CatalogTypes { get; set; }

    // Additional code ...

}
```

Můžete mít další `DbContext` implementace. Například v mikroslužbu Catalog.API ukázkové, je druhý `DbContext` s názvem `CatalogContextSeed` kde automaticky naplní ukázkových dat při prvním pokusu o přístup k databázi. Tato metoda je užitečná pro ukázková data, pro automatizované testování scénáře, také. V rámci `DbContext`, můžete použít `OnModelCreating` metodu za účelem přizpůsobení objektu a databáze entity mapování s a dalších [body rozšiřitelnosti EF](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).

##### <a name="querying-data-from-web-api-controllers"></a>Dotazování na data z řadičů webového rozhraní API

Instance třídy entity jsou obvykle načteny z databáze pomocí jazyka integrovaného dotazu (LINQ), jak je znázorněno v následujícím příkladu:

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    private readonly CatalogContext _catalogContext;
    private readonly CatalogSettings _settings;
    private readonly ICatalogIntegrationEventService _catalogIntegrationEventService;

    public CatalogController(CatalogContext context, 
                             IOptionsSnapshot<CatalogSettings> settings,
                             ICatalogIntegrationEventService catalogIntegrationEventService)
    {
        _catalogContext = context ?? throw new ArgumentNullException(nameof(context));
        _catalogIntegrationEventService = catalogIntegrationEventService ?? throw new ArgumentNullException(nameof(catalogIntegrationEventService));

        _settings = settings.Value;
        ((DbContext)context).ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("[action]")]
    [ProducesResponseType(typeof(PaginatedItemsViewModel<CatalogItem>), (int)HttpStatusCode.OK)]
    public async Task<IActionResult> Items([FromQuery]int pageSize = 10, 
                                           [FromQuery]int pageIndex = 0)

    {
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

Data je vytvořit, odstranit a upravit v databázi pomocí instance třídy entity. Můžete přidat kód jako následující pevně příklad (imitovaná data v tomto případě) k vašim řadičům webového rozhraní API.

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a>Vkládání závislostí v řadiče ASP.NET Core a webového rozhraní API

V ASP.NET Core můžete ihned vkládání závislostí (DI). Není potřeba nastavit kontejner inverzi řízení (IoC) třetí strany, i když je možné připojit vaše upřednostňované kontejner IoC ASP.NET základní infrastruktury Chcete-li. V takovém případě znamená, že můžete přímo vložit požadované DBContext EF nebo další úložiště pomocí konstruktoru řadiče. V příkladu výše `CatalogController` třída, jsme jsou vložení objektu `CatalogContext` zadejte plus jiné objekty prostřednictvím `CatalogController()` konstruktor.

Důležité konfigurační nastavení v projektu webového rozhraní API je registrace třídy DbContext do kontejneru služby IoC. Obvykle děláte proto v `Startup` třída voláním `services.AddDbContext<DbContext>()` metodu `ConfigureServices()` metoda, jak je znázorněno v následujícím příkladu:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    // Additional code...

    services.AddDbContext<CatalogContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlServerOptionsAction: sqlOptions =>
        {
           sqlOptions.
               MigrationsAssembly(
                   typeof(Startup).
                    GetTypeInfo().
                     Assembly.
                      GetName().Name);

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

-   **Dotazování na Data**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)

-   **Ukládání dat**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a>DB připojovací řetězec a prostředí proměnné používané Docker kontejnery

Můžete použít nastavení ASP.NET Core a přidejte vlastnost ConnectionString do souboru settings.json, jak je znázorněno v následujícím příkladu:

```csharp
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

Soubor settings.json může mít výchozí hodnoty pro vlastnost ConnectionString nebo pro žádné jiné vlastnosti. Tyto vlastnosti však bude možné přepsat hodnoty proměnné prostředí, které zadáte v soubor docker-compose.override.yml, při použití Docker.

Z docker-compose.yml nebo docker compose.override.yml souborů můžete inicializovat těchto proměnných prostředí tak, že Docker bude nastavit je jako proměnné prostředí operačního systému pro vás, jak je znázorněno v následující soubor docker-compose.override.yml (připojení řetězec a další řádky zalomení v tomto příkladu, ale nebude zalomení v souboru kódu).

```yml
# docker-compose.override.yml

#
catalog.api:
  environment:
    - ConnectionString=Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    # Additional environment variables for this service
  ports:
    - "5101:80"
```

Soubory docker-compose.yml na úrovni řešení nejsou jenom flexibilnější než konfigurační soubory na úrovni projektu nebo mikroslužbu, ale také bezpečnější Pokud přepíšete deklarovat na docker-compose soubory s hodnotami nastavenými z proměnné prostředí vaše nasazení nástroje, jako například z úlohy nasazení služby VSTS Docker. 

Nakonec můžete získat tuto hodnotu z vašeho kódu pomocí konfigurace\["ConnectionString"\], jak je znázorněno v metodě ConfigureServices v předchozí příklad kódu.

Pro produkční prostředí, můžete však prozkoumat další způsoby, jak na tom, jak ukládat tajné klíče jako připojovací řetězce. Obvykle, bude spravovat zvolené orchestrator, jako jsou aplikace [Docker Swarm správu tajné klíče](https://docs.docker.com/engine/swarm/secrets/).

### <a name="implementing-versioning-in-aspnet-web-apis"></a>Implementace správy verzí v rozhraní ASP.NET Web API

Mění obchodní požadavky, mohou být přidány nové kolekce prostředků, vztahy mezi prostředky mohou změnit a může být změněna strukturu dat v prostředky. Aktualizace webového rozhraní API pro zpracování nových požadavků je poměrně jednoduchý proces, ale musíte zvážit důsledky, které tyto změny budou mít na klientské aplikace využívají webové rozhraní API. I když vývojáři navrhování a implementace rozhraní Web API má plnou kontrolu nad toto rozhraní API, vývojář nemá stejnou úrovní kontrolu nad klientských aplikací, které může být vytvořené třetí strany organizace operační vzdáleně.

Správa verzí umožňuje webového rozhraní API označíte, funkce a prostředky, které vystavuje. Klientská aplikace pak mohou odesílat požadavky na konkrétní verzi funkce nebo prostředků. Existuje několik přístupů k implementaci správy verzí:

-   Identifikátor URI Správa verzí

-   Správa verzí řetězec dotazu

-   Správa verzí hlavičky

Řetězec dotazu a správa verzí URI jsou nejjednodušší k implementaci. Správa verzí hlavičky je dobré přístup. Ale záhlaví verze není jako explicitní a jednoduché jako správa verzí identifikátor URI. Protože správa verzí adresa URL je nejjednodušší a většina explicitní, eShopOnContainers ukázková aplikace používá Správa verzí identifikátor URI.

Správa verzí URI jako eShopOnContainers ukázkovou aplikaci pokaždé, když upravíte webového rozhraní API nebo změnit schéma prostředky, přidejte číslo verze identifikátor URI pro každého prostředku. Existující identifikátory URI by měly být nadále fungovat jako dříve, vrácení prostředky, které odpovídají schématu, která odpovídá na požadovanou verzi.

Jak ukazuje následující příklad kódu, může být verze nastavená pomocí atributů směrování v rozhraní Web API, která vytváří verze explicitní v identifikátoru URI (v tomto případě v1).

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

Tento mechanismus správy verzí je jednoduchý a závisí na serveru pro směrování požadavku na příslušný koncový bod. Ale pro sofistikovanější Správa verzí a nejlepší metody při používání REST, doporučujeme použít hypermédií a implementovat [HATEOAS (Hypertext jako stav modulu aplikace)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).

### <a name="additional-resources"></a>Další zdroje

-   **Scott Hanselman. Správa verzí RESTful webová rozhraní API ASP.NET Core umožněno**
    [*https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)

-   **Správa verzí RESTful webového rozhraní API**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **Royi Fielding. Správa verzí, hypermédií a REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a>Generování metadat Swagger popis z ASP.NET rozhraní Web API Core 

[Swagger](https://swagger.io/) je běžně používané s otevřeným zdrojem framework zajišťoval velké ekosystém nástroje, které vám pomůžou návrhu, sestavení, dokumentu a používat vaše rozhraní RESTful API. Se stává stále standard pro doménu popis metadat rozhraní API. By měly obsahovat metadata Swagger popis s jakýmkoli mikroslužbu řízené daty mikroslužeb nebo pokročilejší řízené domény mikroslužeb (jak je popsáno v následující části).

Srdcem Swagger je specifikace Swagger, což je popis metadat rozhraní API v souboru YAML nebo JSON. Specifikace vytvoří RESTful kontrakt pro vaše rozhraní API s podrobnostmi o všech prostředků a operace v obou lidské a machine readable formátu pro snadný vývoj, zjišťování a integrace.

Specifikace je základem z specifikace OpenAPI (OAS) a je vyvinuta v komunitě otevřené, transparentní a spolupráce pro standardizaci způsob, jakým jsou definovány rozhraní RESTful.

Specifikace definuje strukturu pro jak může být zjištěn služby a jak se jeho funkce rozumí. Další informace, včetně editoru webové a příklady specifikace Swagger společností jako Spotify, Uber, Slack a společnosti Microsoft, najdete v části webu Swagger (<https://swagger.io/>).

### <a name="why-use-swagger"></a>Proč používat Swagger?

Hlavních důvodů pro generování metadat Swagger pro vaše rozhraní API jsou uvedeny níže.

**Možnost pro ostatní produkty automaticky využívat a integrovat vaše rozhraní API**. Desítek produktů a [komerční nástroje](https://swagger.io/commercial-tools/) a mnoho [knihoven a architektur](https://swagger.io/open-source-integrations/) podporu Swagger. Microsoft má vysoké úrovně produktů a nástroje, které mohou automaticky používat rozhraní API na základě Swagger, například následující:

-   [AutoRest](https://github.com/Azure/AutoRest). Může automaticky vygenerovat třídy klienta rozhraní .NET pro volání Swagger. Tento nástroj můžete použít z rozhraní příkazového řádku a je integrován se sadou Visual Studio pro snadné použití prostřednictvím grafického uživatelského rozhraní.

-   [Tok Microsoft](https://flow.microsoft.com/en-us/). Můžete automaticky [používat a integrovat vaše rozhraní API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) do vysoké úrovně pracovního postupu Microsoft Flow, programování bez znalosti vyžaduje.

-   [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/). Můžete automaticky využívat vaše rozhraní API z [mobilních aplikací PowerApps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) vytvořené s [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), s žádné znalostí programování vyžaduje.

-   [Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps). Můžete automaticky [používat a integrovat do aplikace logiky Azure App Service vaše rozhraní API](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), s žádné znalostí programování vyžaduje.

**Umožňuje automaticky generovat dokumentaci k rozhraní API**. Při vytváření rozsáhlých rozhraní RESTful API, jako je například komplexní aplikace na základě mikroslužbu, je třeba zpracovat velký počet koncových bodů s různými datovými modely použité v datové části žádosti a odpovědi. S správné dokumentaci a s plnou explorer rozhraní API, jak získat s Swagger, se klíč pro úspěch vašeho rozhraní API a přijetí vývojáři.

Metadata swagger společnosti je Microsoft Flow, PowerApps a Azure Logic Apps pomocí pochopit, jak používat rozhraní API a připojit se k nim.

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a>Jak automatizovat generování metadat Swagger rozhraní API pomocí balíčku Swashbuckle NuGet

Generování metadat Swagger ručně (v souboru YAML nebo JSON) může být pracné. Však můžete automatizovat zjišťování rozhraní API ASP.NET Web API služeb pomocí [balíčku Swashbuckle NuGet](http://aka.ms/swashbuckledotnetcore) dynamicky generovat metadata Swagger rozhraní API.

Swashbuckle automaticky vytvoří metadata Swagger pro projekty ASP.NET Web API. Podporuje projekty webového rozhraní API ASP.NET Core a tradiční rozhraní ASP.NET Web API a dalších příchuť, jako je například aplikace API Azure, mobilní aplikace Azure, Azure Service Fabric mikroslužeb založené na technologii ASP.NET. Také podporuje prostý webového rozhraní API nasazené na kontejnery, jako v pro odkaz na aplikaci.

Swashbuckle kombinuje Explorer rozhraní API a Swagger nebo [uživatelského rozhraní swagger](https://github.com/swagger-api/swagger-ui) zajistit bohaté zjišťování a dokumentace prostředí pro uživatele rozhraní API. Kromě jeho motoru generátor metadata Swagger Swashbuckle také obsahuje vložené verzi swagger – uživatelské rozhraní, které se bude automaticky sloužit až po instalaci Swashbuckle.

To znamená, že můžete doplnit rozhraní API pomocí dobrý zjišťování uživatelského rozhraní, což vývojářům používat vaše rozhraní API. Protože je generován automaticky, umožňuje soustředit na rozhraní API vyžaduje velmi malé množství kódu a údržby. Výsledek pro rozhraní API Průzkumníka vypadá jako obrázek 8-8.

![](./media/image9.png)

**Obrázek 8-8**. Swashbuckle rozhraní API Explorer na základě metadat Swagger – eShopOnContainers katalogu mikroslužbu

Průzkumník rozhraní API není zde je třeba mít. Jakmile máte webového rozhraní API, která může sám sebe popisují v metadatech Swagger, rozhraní API slouží bezproblémově z nástrojů rozhraní Swagger, včetně generátory kódu třídu proxy klienta, které můžete cílit na mnoha platformách. Například jako uvedených [AutoRest](https://github.com/Azure/AutoRest) automaticky vygeneruje třídy klienta rozhraní .NET. Jako další nástroje, ale [swagger codegen](https://github.com/swagger-api/swagger-codegen) jsou také k dispozici, který povolí generování kódu rozhraní API klienta knihovny, server zástupných procedur a dokumentaci automaticky.

V současné době Swashbuckle se skládá ze dvou několik interní balíčků NuGet v rámci vysoké úrovně metabalíček [Swashbuckle.Swashbuckle.AspNetCoreSwaggerGen](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) verze 1.0.0 nebo novější pro aplikace ASP.NET Core.

Po instalaci těchto balíčků NuGet v projektu webového rozhraní API, musíte nakonfigurovat Swagger ve třídě, spuštění, jako v následujícím kódu:

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
            options.SwaggerDoc("v1", new Swashbuckle.AspNetCore.Swagger.Info
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API. This is a Data-Driven/CRUD microservice sample",
                TermsOfService = "Terms Of Service"
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

Až bude vše Hotovo, můžete spustit aplikaci a procházet vytvoření následujících koncových bodů JSON pro Swagger a uživatelského rozhraní, pomocí adres URL, například tyto:

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/
```

Dříve jste viděli vygenerované uživatelské rozhraní vytvořené Swashbuckle pro adresu URL podobnou http://&lt;vaše kořenové url &gt; /swagger/uživatelského rozhraní. Obrázek 8-9 se také zobrazí jak můžete testovat libovolné metody rozhraní API.

![](./media/image10.png)

**Obrázek 8-9**. Uživatelské rozhraní Swashbuckle testování metoda API nebo položky katalogu

Obrázek 8-10 ukazuje metadat JSON pro Swagger vygenerovat z mikroslužbu eShopOnContainers (což je nástroje použijte pod) při žádosti o &lt;vaše kořenové url&gt;/swagger/v1/swagger.json pomocí [Postman](https://www.getpostman.com/).

![](./media/image11.png)

**Obrázek 8-10**. Metadata JSON pro swagger

Je to snadné. A protože se automaticky vygeneroval, Swagger metadata se zvýší při přidání dalších funkcí do rozhraní API.

### <a name="additional-resources"></a>Další zdroje

-   **Rozhraní ASP.NET Web API pomůže Pages pomocí Swagger**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)


>[!div class="step-by-step"]
[Předchozí] (mikroslužbu aplikace design.md) [Další] (více-container-aplikace docker-compose.md)
