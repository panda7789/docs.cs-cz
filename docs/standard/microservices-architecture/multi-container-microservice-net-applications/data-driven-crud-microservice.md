---
title: Vytvoření jednoduché mikroslužby CRUD řízené daty
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Vytvoření jednoduché mikroslužby CRUD řízené daty
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: bba0b93ee7e68ae0320460c6a45ab252ac34c326
ms.sourcegitcommit: 8c28ab17c26bf08abbd004cc37651985c68841b8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/08/2018
ms.locfileid: "48873492"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a>Vytvoření jednoduché mikroslužby CRUD řízené daty

Tento oddíl, který ukazuje jak vytvořit jednoduchou mikroslužeb, která provádí vytvořit, číst, aktualizace a odstranění (CRUD) operací na zdroj dat.

## <a name="designing-a-simple-crud-microservice"></a>Navrhování jednoduché mikroslužby CRUD

Tento typ kontejnerizované mikroslužby z návrhu hlediska, je velmi jednoduché. Možná je jednoduchý problém vyřešit, nebo možná implementace je pouze testování konceptu.

![](./media/image4.png)

**Obrázek 8-4**. Interní návrhu pro jednoduché mikroslužby CRUD

Příkladem tohoto druhu služby Jednoduché datové jednotky je mikroslužeb katalogu v aplikaci eShopOnContainers ukázkové aplikaci. Tento typ služby implementuje všechny jeho funkce v jednom projektu webového rozhraní API ASP.NET Core, který obsahuje třídy pro její datový model, jeho obchodní logiky a jeho kód přístupu k datům. Je také ukládá související data v databázi spuštěna v systému SQL Server (jako jiný kontejner pro účely vývoje a testování), ale mohou být také jakýmkoli regulární systému SQL Server hostitelem, jak ukazuje obrázek 8 – 5.

![](./media/image5.png)

**Obrázek 8-5**. Jednoduché mikroslužby data-driven/CRUD návrhu

Při vývoji tento druh službu, potřebujete jenom [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) a rozhraní API pro přístup k datům nebo ORM jako [Entity Framework Core](https://docs.microsoft.com/ef/core/index). Může také generovat [Swagger](https://swagger.io/) metadat automaticky prostřednictvím [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) k poskytnutí popisu co nabídek služby, jak je vysvětleno v další části.

Všimněte si, že databázový server, jako je SQL Server v kontejneru Dockeru se skvěle hodí pro vývojová prostředí, protože všechny závislosti může mít až systémem, aniž by museli o zřízení databáze v cloudu nebo místně. To je velmi praktické, když s integrací testy. Však pro produkční prostředí, databázový server v kontejneru nedoporučuje se používat, protože se obvykle nezobrazí vysokou dostupnost s možnostmi tento přístup. Pro produkční prostředí v Azure se doporučuje použít službu Azure SQL DB nebo jiné databázové technologie, která dokáže poskytovat vysokou dostupnost a vysokou škálovatelnost. Například pro NoSQL přístup, můžete se rozhodnout DocumentDB.

Nakonec pomocí úpravy souboru Docker a docker-compose.yml soubory metadat, můžete nakonfigurovat jak se vytvoří snímek tohoto kontejneru, jaké základní image budou používat plus návrh nastavení, jako je interní a externí názvy a porty TCP. 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a>Implementace jednoduché mikroslužby CRUD s ASP.NET Core

Provádět jednoduché mikroslužby CRUD pomocí .NET Core a Visual Studio spustíte tak, že vytvoříte jednoduchý projekt webového rozhraní API ASP.NET Core (spouštění v .NET Core tak může probíhat na hostitele linuxového Dockeru), jako ukazuje obrázek 8 až 6.

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  ![](./media/image6.png)   ![](./media/image7.png)
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

**Obrázek 8 – 6**. Vytvoření projektu webového rozhraní API ASP.NET Core v sadě Visual Studio

Po vytvoření projektu, můžete implementovat vaše řadiče MVC, stejně jako v jiných projekt webového rozhraní API pomocí rozhraní API Entity Framework nebo jiném rozhraní API. V novém projektu webového rozhraní API zobrazí se pouze závislost mít v mikroslužba je v ASP.NET Core, samotný. Interně, v rámci `Microsoft.AspNetCore.All` závislostí, odkazuje Entity Framework a řada dalších balíčků .NET Core Nuget, jak ukazuje obrázek 8 – 7.

![](./media/image8.PNG)

**Obrázek 8-7**. Závislosti v jednoduché mikroslužby CRUD webového rozhraní API

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a>Implementace CRUD webového rozhraní API služeb s Entity Framework Core

Entity Framework (EF) Core je odlehčený, rozšiřitelné, a multiplatformní verze oblíbených dat Entity Framework přístup k technologii. EF Core je objektově relační Mapovač (ORM), který umožňuje vývojářům .NET pracovat s databází s použitím objektů .NET.

Mikroslužby katalogu používá EF a zprostředkovatele SQL Server, protože jeho databáze je spuštěna v kontejneru se serverem SQL Server pro image Dockeru pro Linux. Databáze však může být nasazený do SQL serveru, jako je například Windows on-premises nebo databázi SQL Azure. Jediné, co je třeba změnit je připojovací řetězec webového rozhraní API ASP.NET mikroslužeb.


#### <a name="the-data-model"></a>Datový model

S EF Core provádí přístup k datům s použitím modelu. Model se skládá z tříd entit a odvozené kontext, který reprezentuje relaci s databází, umožňuje dotazování a uložit data. Můžete generovat model z existující databáze, ručně code model tak, aby odpovídaly vaší databáze nebo použít migraci EF k vytvoření databáze z vašeho modelu (a vyvíjejí ho jako model mění v průběhu času). Poslední přístup se používá pro mikroslužby katalogu. Vidíte příklad třídy entity catalogitem je například v následujícím příkladu kódu, který je jednoduchý prostý původní objekt CLR ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) třída entity.

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

Budete také potřebovat DbContext, který reprezentuje relaci s databází. Pro mikroslužby katalogu CatalogContext třída je odvozena ze základní třídy DbContext, jak je znázorněno v následujícím příkladu:

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

Můžete mít další `DbContext` implementace. Například v ukázkové Catalog.API mikroslužeb, je druhý `DbContext` s názvem `CatalogContextSeed` kde automaticky naplní vzorová data při prvním pokusu o přístup k databázi. Tato metoda je užitečná pro ukázková data a pro automatizované testování, podporuje i scénáře. V rámci `DbContext`, je použít `OnModelCreating` metodu za účelem přizpůsobení entity mapování objektu a databáze a další [bodů rozšiřitelnosti EF](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).

##### <a name="querying-data-from-web-api-controllers"></a>Dotazování na data z kontrolerů rozhraní Web API

Instance třídy entity se obvykle načítají z databáze pomocí Language Integrated Query (LINQ), jak je znázorněno v následujícím příkladu:

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

Data je vytvořit, odstranit a upravit v databázi pomocí instance třídy entity. Můžete přidat kód jako v následujícím pevně zakódované příkladu (mock data v tomto případě) k vašim řadičům webového rozhraní API.

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a>Injektáž závislostí do kontrolerů ASP.NET Core a webové rozhraní API

V ASP.NET Core můžete ihned Dependency Injection (DI). Není potřeba nastavit kontejner řízení IOC (Inversion) třetí strany, i když můžete svůj upřednostňovaný kontejner IoC pružný infrastruktury ASP.NET Core, chcete-li. V tomto případě znamená, že můžete přímo vložit požadovaná DBContext EF nebo další úložiště prostřednictvím konstruktoru kontroleru. V příkladu výše `CatalogController` třídy, jsme se vkládá objekt `CatalogContext` zadejte plus dalších objektů prostřednictvím `CatalogController()` konstruktoru.

Důležité konfigurační nastavení v projektu webového rozhraní API je registrace třídy DbContext na kontejner IoC služby. To obvykle děláte, `Startup` třídy voláním `services.AddDbContext<DbContext>()` metodu `ConfigureServices()` způsob, jak je znázorněno v následujícím příkladu:

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

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a>DB připojovací řetězec a prostředí proměnné využívaných kontejnery Dockeru

Můžete použít nastavení ASP.NET Core a přidejte vlastnost ConnectionString do souboru Settings.JSON v nástroji, jak je znázorněno v následujícím příkladu:

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

Výchozí hodnoty pro vlastnost ConnectionString nebo jakoukoli jinou vlastnosti můžou mít soubor Settings.JSON v nástroji. Tyto vlastnosti však přepíše hodnoty proměnných prostředí, které zadáte v souboru docker-compose.override.yml při použití Dockeru.

Ze svých souborů docker-compose.yml a docker-compose.override.yml můžete inicializovat těchto proměnných prostředí tak, které Docker se nastavit je jako proměnné prostředí operačního systému pro vás, jak je znázorněno v následujícím souboru docker-compose.override.yml (připojení řetězce a další řádky zalamovat v tomto příkladu, ale nebude zabalení v souboru kódu).

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

Soubory docker-compose.yml na úrovni řešení nejsou pouze flexibilnější, než konfigurační soubory na úrovni projektu nebo mikroslužeb, ale také vyšší úroveň zabezpečení Pokud přepíšete deklarované na docker-compose soubory s hodnotami z nastavení proměnné prostředí z nasazení úloh Azure DevOps služby Docker, jako jsou nástroje pro nasazení. 

Nakonec můžete získat tuto hodnotu v kódu s použitím konfigurace\["ConnectionString"\], jak je znázorněno v metodě ConfigureServices v předchozím příkladu kódu.

Pro produkční prostředí, můžete však prozkoumat další způsoby, jak na tom, jak ukládat tajné kódy jako jsou připojovací řetězce. Obvykle, který bude spravovat zvolený orchestrátor, jako je vám pomůžou s [Docker Swarm správu tajných kódů](https://docs.docker.com/engine/swarm/secrets/).

### <a name="implementing-versioning-in-aspnet-web-apis"></a>Implementace správy verzí v rozhraní ASP.NET Web API

Podle měnících se obchodních požadavků, mohou být přidány nové kolekce prostředků, může změnit vztahy mezi prostředky a může být změněna strukturu dat v prostředcích. Aktualizace webového rozhraní API pro zpracování nových požadavků je poměrně přímočarý proces, ale musíte zvážit důsledky, které tyto změny budou mít na klientské aplikace využívající webové rozhraní API. I když vývojář navrhující a implementující webové rozhraní API má plnou kontrolu nad tímto rozhraním API, vývojář nemá stejnou úroveň kontroly nad klientskými aplikacemi, které může být sestavena v třetích stran, vzdáleně působící organizace.

Správa verzí umožňuje webovému rozhraní API k označení funkce a prostředky, které vystavuje. Klientská aplikace může potom odesílat požadavky na konkrétní verzi funkce nebo prostředku. Existuje několik přístupů k implementaci správy verzí:

-   Identifikátor URI správy verzí

-   Správa verzí pomocí řetězce dotazu

-   Správa verzí pomocí hlavičky

Řetězec dotazu a identifikátor URI správy verzí jsou nejjednodušší implementace. Správa verzí pomocí hlavičky je dobrý nápad. Nicméně správa verzí pomocí hlavičky, ne jako explicitní a přímočaré jako identifikátor URI správy verzí. Vzhledem k tomu, že adresa URL správy verzí je nejjednodušší a největší explicitní, aplikaci eShopOnContainers ukázková aplikace používá Správa verzí identifikátoru URI.

Pomocí správy verzí identifikátor URI, stejně jako v aplikaci eShopOnContainers ukázkovou aplikaci pokaždé, když upravíte webové rozhraní API nebo změníte schéma prostředků, přidejte číslo verze do identifikátoru URI každého prostředku. Existující identifikátory URI by měly nadále fungovat jako předtím, vracet prostředky, které odpovídají schématu, která odpovídá na požadovanou verzi.

Jak je znázorněno v následujícím příkladu kódu, může být verze nastavená pomocí atribut trasy v rozhraní Web API, takže verze explicitní v identifikátoru URI (verze 1 v tomto případě).

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

Tento mechanismus správy verzí je jednoduché a závisí na směrování požadavků na příslušný koncový bod serveru. Pro složitější správy verzí a nejlepší metody při používání REST, můžete ale by měl používejte hypermédia a implementovat [HATEOAS (Hypertext as Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).

### <a name="additional-resources"></a>Další zdroje

-   **Scott Hanselman. Správa verzí RESTful webového rozhraní API ASP.NET Core snadné**
    [*https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)

-   **Správa verzí RESTful webového rozhraní API**
    [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   **Roy Fielding. Správa verzí, Hypermédia a REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a>Generování metadat Swagger popis z webové rozhraní API ASP.NET Core 

[Swagger](https://swagger.io/) je běžně používaný open source architektura zajištěná rozsáhlého ekosystému nástrojů, která vám pomůže návrhu, sestavení, dokument a využívání rozhraní RESTful API. To se stává standard pro doménu metadat popis rozhraní API. By měl obsahovat popis metadata Swagger s jakýmkoli mikroslužeb, mikroslužby s daty nebo pokročilejší mikroslužeb řízeného doménou (jak je popsáno v následující části).

Srdce Swaggeru je specifikace Swaggeru, což je popis metadat rozhraní API v souboru JSON nebo YAML. Specifikace vytvoří RESTful smlouvy pro vaše rozhraní API s podrobnostmi o všech jeho prostředků a operací v obou lidské a machine readable formátu pro snadný vývoj, zjišťování a integrace.

Specifikace je základem z specifikaci OpenAPI (OAS) a je vyvinuta v komunitě open transparentní a spolupráci ke standardizaci způsob, jakým jsou definovány rozhraní RESTful.

Specifikace definuje strukturu pro jak může služba zjistit a jak své možnosti srozumitelný. Další informace, včetně editoru webu a příklady specifikace Swagger ze společnosti, jako Spotify, Uber, Slack a Microsoft, naleznete v tématu Swagger lokality (<https://swagger.io/>).

### <a name="why-use-swagger"></a>Proč používat Swagger?

Hlavní důvody ke generování metadat Swagger pro rozhraní API jsou uvedeny níže.

**Možnost pro ostatní produkty automaticky využívat a integrovat vaše rozhraní API**. Desítky produkty a [komerční nástroje](https://swagger.io/commercial-tools/) a mnoha [knihoven a architektur](https://swagger.io/open-source-integrations/) podporují Swagger. Microsoft má vysoké úrovně produkty a nástroje, které automaticky využívají rozhraní API založená na Swaggeru, jako je následující:

-   [AutoRest](https://github.com/Azure/AutoRest). Můžete automaticky vygenerovat třídy klienta rozhraní .NET pro volání Swagger. Tento nástroj se dá použít rozhraní příkazového řádku a také se integruje se sadou Visual Studio pro snadné použití prostřednictvím grafického uživatelského rozhraní.

-   [Microsoft Flow](https://flow.microsoft.com/en-us/). Můžete automaticky [použít a integrovat vaše rozhraní API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) do vysoké úrovně pracovního postupu Microsoft Flow, bez programování dovednosti nutné.

-   [Microsoft PowerApps](https://powerapps.microsoft.com/en-us/). Můžete automaticky využití rozhraní API z [mobilní aplikace PowerApps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) vytvořených pomocí [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), bez programování znalosti vyžaduje.

-   [Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps). Můžete automaticky [použít a integrovat vaše rozhraní API do Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), bez programování znalosti vyžaduje.

**Možnost automaticky generovat dokumentaci k rozhraní API**. Při vytváření rozsáhlých rozhraní RESTful API, jako je například komplexních aplikací založených na mikroslužbách, potřebujete zpracovávat mnoho koncových bodů s různými datovými modely použité v datových částí požadavků a odpovědí. Máte správnou dokumentaci a s plnou Průzkumník rozhraní API, budete si ve Swaggeru, je klíčem k úspěchu rozhraní API a přijetí vývojáři.

Metadata swagger společnosti je, co Microsoft Flow, PowerApps a Azure Logic Apps můžete pochopit, jak používat rozhraní API a připojit se k nim.

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a>Jak automatizovat generování metadat Swagger rozhraní API pomocí balíčku Swashbuckle NuGet

Generování metadat Swagger ručně (v souboru JSON nebo YAML) může být pracné. Však můžete automatizovat zjišťování rozhraní API služeb ASP.NET Web API s použitím [balíček Swashbuckle NuGet](https://aka.ms/swashbuckledotnetcore) dynamicky generovat metadata Swagger rozhraní API.

Swashbuckle vygeneruje automaticky metadata Swagger pro projekty ASP.NET Web API. Podporuje projekty webového rozhraní API ASP.NET Core a tradiční rozhraní ASP.NET Web API a další charakter, například aplikaci API Azure, Azure mobilní aplikace mikroslužeb Azure Service Fabric, které jsou založeny na technologii ASP.NET. Také podporuje prostý webového rozhraní API nasazené v kontejnerech, stejně jako v referenční aplikace.

Swashbuckle kombinuje Průzkumník rozhraní API a Swagger nebo [uživatelského rozhraní swagger](https://github.com/swagger-api/swagger-ui) k poskytování bohatých zjišťování a dokumentaci prostředí pro vaše zákazníky. Kromě motor generátor metadata Swagger Swashbuckle také obsahuje vložený verzi swaggeru – uživatelské rozhraní, které se bude automaticky poskytovat po instalaci Swashbuckle.

To znamená, že můžou doplnit rozhraní API ve službě hezké zjišťování uživatelského rozhraní, což vývojářům umožňuje používat vaše rozhraní API. Vyžaduje velmi malé množství kódu a údržby, protože to není automaticky vygenerován, tak budete moct soustředit na vytváření rozhraní API. Výsledek pro Průzkumník rozhraní API bude vypadat podobně jako obrázek 8-8.

![](./media/image9.png)

**Obrázek 8 – 8**. Průzkumník rozhraní API Swashbuckle na základě metadat Swagger – aplikaci eShopOnContainers katalogu mikroslužeb

Průzkumník rozhraní API není nejdůležitějším rozhodnutím. Jakmile máte webové rozhraní API, které můžete popsat sám sebe v metadatech Swaggeru, vaše rozhraní API je možné bez problémů ze Swaggeru nástrojů, včetně generátory kódu třídu proxy klienta, které můžete cílit na spoustě platforem. Příklad, jak bylo zmíněno [AutoRest](https://github.com/Azure/AutoRest) automaticky vygeneruje třídy klienta rozhraní .NET. Další nástroje, jako je, ale [swagger codegen](https://github.com/swagger-api/swagger-codegen) jsou také k dispozici, který umožňuje generování kódu rozhraní API klientské knihovny, server zástupné procedury a dokumentaci automaticky.

V současné době se skládá z několika interní balíčky NuGet v rámci základní meta-package Swashbuckle [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/) verze 1.0.0 nebo novějším pro aplikace ASP.NET Core.

Po instalaci těchto balíčků NuGet v projektu webového rozhraní API, musíte nakonfigurovat Swagger ve třídě spuštění, stejně jako v následujícím kódu:

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

Až to uděláte, můžete spustit aplikaci a přejděte následující koncové body JSON pro Swagger a uživatelského rozhraní, pomocí adres URL, jako jsou tyto:

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/
```

Dříve jste viděli vygenerované uživatelské rozhraní vytvořené Swashbuckle pro adresu URL jako `http://<your-root-url>/swagger/ui`. Obrázek 8 až 9 také uvidíte jak otestovat všechny metody rozhraní API.

![](./media/image10.png)

**Obrázek 8 až 9**. Uživatelské rozhraní nástroje Swashbuckle testování/položky katalogu rozhraní API – metoda

Obrázek 8-10 ukazuje metadat JSON pro Swagger generují z mikroslužeb aplikaci eShopOnContainers (což je tyto nástroje používají pod) při žádosti o &lt;your kořenové url&gt;/swagger/v1/swagger.json pomocí [Postman](https://www.getpostman.com/).

![](./media/image11.png)

**Obrázek 8-10**. Swagger JSON metadata

Je to jednoduché. A protože není automaticky vygenerován, Swagger metadata se zvýší, když přidáte další funkce do vašeho rozhraní API.

### <a name="additional-resources"></a>Další zdroje

-   **ASP.NET Web API stránky nápovědy k využívající Swagger**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)


>[!div class="step-by-step"]
[Předchozí](microservice-application-design.md)
[další](multi-container-applications-docker-compose.md)
