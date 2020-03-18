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
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="ef03b-103">Vytvoření jednoduché mikroslužby CRUD řízené daty</span><span class="sxs-lookup"><span data-stu-id="ef03b-103">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="ef03b-104">Tato část popisuje, jak vytvořit jednoduchou mikroslužbu, která provádí operace vytváření, čtení, aktualizace a odstraňování (CRUD) na zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="ef03b-104">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="ef03b-105">Návrh jednoduchémikroslužby CRUD</span><span class="sxs-lookup"><span data-stu-id="ef03b-105">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="ef03b-106">Z hlediska návrhu je tento typ kontejnerizované mikroslužby velmi jednoduchý.</span><span class="sxs-lookup"><span data-stu-id="ef03b-106">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="ef03b-107">Možná, že problém vyřešit, je jednoduchý, nebo snad implementace je jen důkazem koncepce.</span><span class="sxs-lookup"><span data-stu-id="ef03b-107">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![Diagram znázorňující jednoduchý interní návrhový vzor CRUD mikroslužeb.](./media/data-driven-crud-microservice/internal-design-simple-crud-microservices.png)

<span data-ttu-id="ef03b-109">**Obrázek 6-4**.</span><span class="sxs-lookup"><span data-stu-id="ef03b-109">**Figure 6-4**.</span></span> <span data-ttu-id="ef03b-110">Interní návrh pro jednoduché mikroslužby CRUD</span><span class="sxs-lookup"><span data-stu-id="ef03b-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="ef03b-111">Příkladem tohoto druhu služby jednoduché datové jednotky je mikroslužba katalogu z ukázkové aplikace eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="ef03b-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="ef03b-112">Tento typ služby implementuje všechny své funkce v jediném ASP.NET projektu základního webového rozhraní API, který zahrnuje třídy pro svůj datový model, obchodní logiku a přístupový kód dat.</span><span class="sxs-lookup"><span data-stu-id="ef03b-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="ef03b-113">Také ukládá související data v databázi spuštěné v SQL Server (jako jiný kontejner pro účely vývoj/testování), ale může být také libovolný běžný hostitel SQL Server, jak je znázorněno na obrázku 6-5.</span><span class="sxs-lookup"><span data-stu-id="ef03b-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 6-5.</span></span>

![Diagram znázorňující kontejner mikroslužeb řízený daty/CRUD.](./media/data-driven-crud-microservice/simple-data-driven-crud-microservice.png)

<span data-ttu-id="ef03b-115">**Obrázek 6-5**.</span><span class="sxs-lookup"><span data-stu-id="ef03b-115">**Figure 6-5**.</span></span> <span data-ttu-id="ef03b-116">Jednoduchý návrh mikroslužeb řízený daty/CRUD</span><span class="sxs-lookup"><span data-stu-id="ef03b-116">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="ef03b-117">Předchozí diagram znázorňuje logickou mikroslužbu katalogu, která zahrnuje databázi katalogu, která může být nebo nemusí být ve stejném hostiteli Dockeru.</span><span class="sxs-lookup"><span data-stu-id="ef03b-117">The previous diagram shows the logical Catalog microservice, that includes its Catalog database, which can be or not in the same Docker host.</span></span> <span data-ttu-id="ef03b-118">Mít databázi ve stejném hostiteli Dockeru může být dobré pro vývoj, ale ne pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="ef03b-118">Having the database in the same Docker host might be good for development, but not for production.</span></span> <span data-ttu-id="ef03b-119">Při vývoji tohoto druhu služby, stačí [pouze ASP.NET core](https://docs.microsoft.com/aspnet/core/) a rozhraní API pro přístup k datům nebo ORM jako entity framework [core](https://docs.microsoft.com/ef/core/index).</span><span class="sxs-lookup"><span data-stu-id="ef03b-119">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="ef03b-120">Můžete také generovat metadata [Swagger](https://swagger.io/) automaticky prostřednictvím [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) poskytnout popis toho, co vaše služba nabízí, jak je vysvětleno v další části.</span><span class="sxs-lookup"><span data-stu-id="ef03b-120">You could also generate [Swagger](https://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="ef03b-121">Všimněte si, že spuštění databázového serveru, jako je SQL Server v kontejneru Dockeru je skvělé pro vývojová prostředí, protože můžete mít všechny vaše závislosti v provozu bez nutnosti zřizování databáze v cloudu nebo místně.</span><span class="sxs-lookup"><span data-stu-id="ef03b-121">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="ef03b-122">To je velmi výhodné při spuštění integračních testů.</span><span class="sxs-lookup"><span data-stu-id="ef03b-122">This is very convenient when running integration tests.</span></span> <span data-ttu-id="ef03b-123">Však pro produkční prostředí spuštění databázového serveru v kontejneru se nedoporučuje, protože obvykle nezískáte vysokou dostupnost s tímto přístupem.</span><span class="sxs-lookup"><span data-stu-id="ef03b-123">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="ef03b-124">Pro produkční prostředí v Azure se doporučuje používat Azure SQL DB nebo jakoukoli jinou databázovou technologii, která může poskytovat vysokou dostupnost a vysokou škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="ef03b-124">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="ef03b-125">Například pro přístup NoSQL můžete zvolit CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="ef03b-125">For example, for a NoSQL approach, you might choose CosmosDB.</span></span>

<span data-ttu-id="ef03b-126">Nakonec úpravou souborů metadat Dockerfile a docker-compose.yml můžete nakonfigurovat, jak bude vytvořena bitová kopie tohoto kontejneru – jakou základní bitovou kopii bude používat, plus nastavení návrhu, jako jsou interní a externí názvy a porty TCP.</span><span class="sxs-lookup"><span data-stu-id="ef03b-126">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span>

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="ef03b-127">Implementace jednoduché mikroslužby CRUD s ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="ef03b-127">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="ef03b-128">Chcete-li implementovat jednoduchou mikroslužbu CRUD pomocí .NET Core a Visual Studio, můžete začít vytvořením jednoduchého ASP.NET projektu základního webového rozhraní API (spuštěného na .NET Core, aby mohl běžet na hostiteli Linux Docker), jak je znázorněno na obrázku 6-6.</span><span class="sxs-lookup"><span data-stu-id="ef03b-128">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 6-6.</span></span>

![Snímek obrazovky s vizuálními studii zobrazující nastavení projektu](./media/data-driven-crud-microservice/create-asp-net-core-web-api-project.png)

<span data-ttu-id="ef03b-130">**Obrázek 6-6**.</span><span class="sxs-lookup"><span data-stu-id="ef03b-130">**Figure 6-6**.</span></span> <span data-ttu-id="ef03b-131">Vytvoření projektu ASP.NET základního webového rozhraní API ve Visual Studiu 2019</span><span class="sxs-lookup"><span data-stu-id="ef03b-131">Creating an ASP.NET Core Web API project in Visual Studio 2019</span></span>

<span data-ttu-id="ef03b-132">Chcete-li vytvořit ASP.NET projektu základního webového rozhraní API, nejprve vyberte ASP.NET základní webovou aplikaci a pak vyberte typ rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ef03b-132">To create an ASP.NET Core Web API Project, first select an ASP.NET Core Web Application and then select the API type.</span></span> <span data-ttu-id="ef03b-133">Po vytvoření projektu můžete implementovat řadiče MVC stejně jako v jakémkoli jiném projektu webového rozhraní API pomocí rozhraní API entity framework nebo jiného rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ef03b-133">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="ef03b-134">V novém projektu webového rozhraní API uvidíte, že jediná závislost, kterou máte v této mikroslužbě, je na ASP.NET samotnéjádro.</span><span class="sxs-lookup"><span data-stu-id="ef03b-134">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="ef03b-135">Interně v rámci *Microsoft.AspNetCore.All* závislost, odkazuje entity framework a mnoho dalších .NET Core NuGet balíčky, jak je znázorněno na obrázku 6-7.</span><span class="sxs-lookup"><span data-stu-id="ef03b-135">Internally, within the *Microsoft.AspNetCore.All* dependency, it is referencing Entity Framework and many other .NET Core NuGet packages, as shown in Figure 6-7.</span></span>

![Snímek obrazovky VS zobrazující závislosti NuGet catalog.api.](./media/data-driven-crud-microservice/simple-crud-web-api-microservice-dependencies.png)

<span data-ttu-id="ef03b-137">**Obrázek 6-7**.</span><span class="sxs-lookup"><span data-stu-id="ef03b-137">**Figure 6-7**.</span></span> <span data-ttu-id="ef03b-138">Závislosti v jednoduché mikroslužbě CRUD Web API</span><span class="sxs-lookup"><span data-stu-id="ef03b-138">Dependencies in a simple CRUD Web API microservice</span></span>

<span data-ttu-id="ef03b-139">Projekt rozhraní API obsahuje odkazy na balíček Microsoft.AspNetCore.App NuGet, který obsahuje odkazy na všechny základní balíčky.</span><span class="sxs-lookup"><span data-stu-id="ef03b-139">The API project includes references to the Microsoft.AspNetCore.App NuGet package, that includes references to all essential packages.</span></span> <span data-ttu-id="ef03b-140">To by mohlo zahrnovat některé další balíčky stejně.</span><span class="sxs-lookup"><span data-stu-id="ef03b-140">It could include some other packages as well.</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="ef03b-141">Implementace webových api služeb CRUD pomocí jádra entity frameworku</span><span class="sxs-lookup"><span data-stu-id="ef03b-141">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="ef03b-142">Entity Framework (EF) Core je lehká, rozšiřitelná a multiplatformní verze populární technologie přístupu k datům Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="ef03b-142">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="ef03b-143">EF Core je objektrelační mapovač (ORM), který umožňuje vývojářům rozhraní .NET pracovat s databází pomocí objektů .NET.</span><span class="sxs-lookup"><span data-stu-id="ef03b-143">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="ef03b-144">Mikroslužba katalogu používá EF a zprostředkovatele SERVERU SQL Server, protože jeho databáze běží v kontejneru s bitovou kopií SQL Server pro Linux Docker.</span><span class="sxs-lookup"><span data-stu-id="ef03b-144">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="ef03b-145">Databáze však může být nasazena do libovolného serveru SQL Server, jako je například místní systém Windows nebo Azure SQL DB.</span><span class="sxs-lookup"><span data-stu-id="ef03b-145">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="ef03b-146">Jediné, co byste museli změnit, je připojovací řetězec v mikroslužbě ASP.NET webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ef03b-146">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="the-data-model"></a><span data-ttu-id="ef03b-147">Datový model</span><span class="sxs-lookup"><span data-stu-id="ef03b-147">The data model</span></span>

<span data-ttu-id="ef03b-148">S EF Core přístup k datům se provádí pomocí modelu.</span><span class="sxs-lookup"><span data-stu-id="ef03b-148">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="ef03b-149">Model se skládá z tříd entit (model domény) a odvozeného kontextu (DbContext), který představuje relaci s databází, což umožňuje dotazovat a ukládat data.</span><span class="sxs-lookup"><span data-stu-id="ef03b-149">A model is made up of (domain model) entity classes and a derived context (DbContext) that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="ef03b-150">Můžete generovat model z existující databáze, ručně kódovat model tak, aby odpovídaly vaší databázi nebo pomocí migrace EF vytvořit databázi z modelu, pomocí přístupu první kód (který usnadňuje vývoj databáze jako váš model změny v průběhu času).</span><span class="sxs-lookup"><span data-stu-id="ef03b-150">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model, using the code-first approach (that makes it easy to evolve the database as your model changes over time).</span></span> <span data-ttu-id="ef03b-151">Pro mikroslužbu katalogu používáme poslední přístup.</span><span class="sxs-lookup"><span data-stu-id="ef03b-151">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="ef03b-152">Příklad třídy entity CatalogItem můžete zobrazit v následujícím příkladu kódu, což je jednoduchá třída entit Prostý starý objekt CLR ([POCO).](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)</span><span class="sxs-lookup"><span data-stu-id="ef03b-152">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

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

<span data-ttu-id="ef03b-153">Potřebujete také DbContext, který představuje relaci s databází.</span><span class="sxs-lookup"><span data-stu-id="ef03b-153">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="ef03b-154">Pro mikroslužbu katalogu, CatalogContext třída je odvozena od dbcontext základní třídy, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ef03b-154">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

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

<span data-ttu-id="ef03b-155">Můžete mít `DbContext` další implementace.</span><span class="sxs-lookup"><span data-stu-id="ef03b-155">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="ef03b-156">Například v ukázkové mikroslužbě Catalog.API je `DbContext` druhý `CatalogContextSeed` pojmenovaný, kde automaticky naplní ukázková data při prvním pokusu o přístup k databázi.</span><span class="sxs-lookup"><span data-stu-id="ef03b-156">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="ef03b-157">Tato metoda je užitečná také pro ukázková data a pro scénáře automatizovaného testování.</span><span class="sxs-lookup"><span data-stu-id="ef03b-157">This method is useful for demo data and for automated testing scenarios, as well.</span></span>

<span data-ttu-id="ef03b-158">V `DbContext`rámci aplikace `OnModelCreating` můžete metodu použít k přizpůsobení mapování entit objektu/databáze a dalších [bodů rozšiřitelnosti EF](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span><span class="sxs-lookup"><span data-stu-id="ef03b-158">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings and other [EF extensibility points](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="ef03b-159">Dotazování na data z řadičů webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ef03b-159">Querying data from Web API controllers</span></span>

<span data-ttu-id="ef03b-160">Instance tříd entity se obvykle načítají z databáze pomocí jazyka Integrovaný dotaz (LINQ), jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ef03b-160">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

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

##### <a name="saving-data"></a><span data-ttu-id="ef03b-161">Ukládání dat</span><span class="sxs-lookup"><span data-stu-id="ef03b-161">Saving data</span></span>

<span data-ttu-id="ef03b-162">Data jsou v databázi vytvářena, odstraňována a upravována pomocí instancí tříd entit.</span><span class="sxs-lookup"><span data-stu-id="ef03b-162">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="ef03b-163">Do řadičů webového rozhraní API můžete přidat kód jako následující pevně zakódovaný příklad (v tomto případě mock data).</span><span class="sxs-lookup"><span data-stu-id="ef03b-163">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="ef03b-164">Vkládání závislostí v řadičích ASP.NET jádra a webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="ef03b-164">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="ef03b-165">V ASP.NET Core můžete použít vkládání závislostí (DI) po vybalení z krabice.</span><span class="sxs-lookup"><span data-stu-id="ef03b-165">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="ef03b-166">Není nutné nastavit kontejner inverze řízení (IoC) jiného výrobce, i když můžete připojit upřednostňovaný kontejner IoC do infrastruktury ASP.NET Core, pokud chcete.</span><span class="sxs-lookup"><span data-stu-id="ef03b-166">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="ef03b-167">V tomto případě to znamená, že můžete přímo vložit požadované EF DBContext nebo další úložiště prostřednictvím konstruktoru řadiče.</span><span class="sxs-lookup"><span data-stu-id="ef03b-167">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span>

<span data-ttu-id="ef03b-168">V příkladu výše `CatalogController` třídy jsme vstřikování objekttypu `CatalogContext` plus `CatalogController()` další objekty prostřednictvím konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="ef03b-168">In the example above of the `CatalogController` class, we are injecting an object of `CatalogContext` type plus other objects through the `CatalogController()` constructor.</span></span>

<span data-ttu-id="ef03b-169">Důležitou konfigurací, kterou chcete nastavit v projektu webového rozhraní API, je registrace třídy DbContext do kontejneru IoC služby.</span><span class="sxs-lookup"><span data-stu-id="ef03b-169">An important configuration to set up in the Web API project is the DbContext class registration into the service's IoC container.</span></span> <span data-ttu-id="ef03b-170">Obvykle tak učiníte `Startup` ve třídě `services.AddDbContext<DbContext>()` voláním `ConfigureServices()` metody uvnitř metody, jak je znázorněno v následujícím **zjednodušeném** příkladu:</span><span class="sxs-lookup"><span data-stu-id="ef03b-170">You typically do so in the `Startup` class by calling the `services.AddDbContext<DbContext>()` method inside the `ConfigureServices()` method, as shown in the following **simplified** example:</span></span>

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

### <a name="additional-resources"></a><span data-ttu-id="ef03b-171">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="ef03b-171">Additional resources</span></span>

- <span data-ttu-id="ef03b-172">**Dotazování na data** </span><span class="sxs-lookup"><span data-stu-id="ef03b-172">**Querying Data** </span></span>\
  [https://docs.microsoft.com/ef/core/querying/index](/ef/core/querying/index)

- <span data-ttu-id="ef03b-173">**Ukládání dat** </span><span class="sxs-lookup"><span data-stu-id="ef03b-173">**Saving Data** </span></span>\
  [https://docs.microsoft.com/ef/core/saving/index](/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="ef03b-174">Připojovací řetězec DB a proměnné prostředí používané kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="ef03b-174">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="ef03b-175">Můžete použít ASP.NET nastavení jádra a přidat vlastnost ConnectionString do souboru settings.json, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="ef03b-175">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

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

<span data-ttu-id="ef03b-176">Soubor settings.json může mít výchozí hodnoty pro vlastnost ConnectionString nebo pro jakoukoli jinou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="ef03b-176">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="ef03b-177">Tyto vlastnosti však budou přepsány hodnotami proměnných prostředí, které zadáte v souboru docker-compose.override.yml při použití Dockeru.</span><span class="sxs-lookup"><span data-stu-id="ef03b-177">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="ef03b-178">Ze souborů docker-compose.yml nebo docker-compose.override.yml můžete tyto proměnné prostředí inicializovat, aby je Docker nastavil jako proměnné prostředí operačního systému, jak je znázorněno v následujícím souboru docker-compose.override.yml (připojení řetězec a další řádky zalomit v tomto příkladu, ale nebude zalomit ve vlastním souboru).</span><span class="sxs-lookup"><span data-stu-id="ef03b-178">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

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

<span data-ttu-id="ef03b-179">Soubory docker-compose.yml na úrovni řešení jsou nejen flexibilnější než konfigurační soubory na úrovni projektu nebo mikroslužeb, ale také bezpečnější, pokud přepíšete proměnné prostředí deklarované v souborech docker-compose s hodnotami nastavenými z vaše nástroje pro nasazení, například z úloh nasazení Azure DevOps Services Dockeru.</span><span class="sxs-lookup"><span data-stu-id="ef03b-179">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from Azure DevOps Services Docker deployment tasks.</span></span>

<span data-ttu-id="ef03b-180">Nakonec můžete získat tuto hodnotu z\[kódu pomocí\]konfigurace "ConnectionString" , jak je znázorněno v ConfigureServices metoda v příkladu dřívější kód.</span><span class="sxs-lookup"><span data-stu-id="ef03b-180">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="ef03b-181">V produkčních prostředích však můžete chtít prozkoumat další způsoby, jak ukládat tajné kódy, jako jsou připojovací řetězce.</span><span class="sxs-lookup"><span data-stu-id="ef03b-181">However, for production environments, you might want to explore additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="ef03b-182">Vynikající způsob správy tajných kódů aplikací je pomocí [azure key vault](https://azure.microsoft.com/services/key-vault/).</span><span class="sxs-lookup"><span data-stu-id="ef03b-182">An excellent way to manage application secrets is using [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="ef03b-183">Azure Key Vault pomáhá ukládat a chránit kryptografické klíče a tajné klíče používané cloudovými aplikacemi a službami.</span><span class="sxs-lookup"><span data-stu-id="ef03b-183">Azure Key Vault helps to store and safeguard cryptographic keys and secrets used by your cloud applications and services.</span></span> <span data-ttu-id="ef03b-184">Tajemství je vše, co chcete zachovat přísnou kontrolu, jako jsou klíče API, připojovací řetězce, hesla, *among others*atd.</span><span class="sxs-lookup"><span data-stu-id="ef03b-184">A secret is anything you want to keep strict control of, like API keys, connection strings, passwords, etc. and strict control includes usage logging, setting expiration, managing access, *among others*.</span></span>

<span data-ttu-id="ef03b-185">Azure Key Vault umožňuje velmi podrobnou úroveň řízení použití tajných kódů aplikace bez nutnosti dát někomu vědět.</span><span class="sxs-lookup"><span data-stu-id="ef03b-185">Azure Key Vault allows a very detailed control level of the application secrets usage without the need to let anyone know them.</span></span> <span data-ttu-id="ef03b-186">Tajné klíče lze dokonce otočit pro lepší zabezpečení bez narušení vývoje nebo operace.</span><span class="sxs-lookup"><span data-stu-id="ef03b-186">The secrets can even be rotated for enhanced security without disrupting development or operations.</span></span>

<span data-ttu-id="ef03b-187">Aplikace musí být registrovány ve službě Active Directory organizace, aby mohly používat trezor klíčů.</span><span class="sxs-lookup"><span data-stu-id="ef03b-187">Applications have to be registered in the organization's Active Directory, so they can use the Key Vault.</span></span>

<span data-ttu-id="ef03b-188">Další podrobnosti naleznete v *dokumentaci k konceptům úložiště klíčů.*</span><span class="sxs-lookup"><span data-stu-id="ef03b-188">You can check the *Key Vault Concepts documentation* for more details.</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="ef03b-189">Implementace správy verzí v ASP.NET webových api</span><span class="sxs-lookup"><span data-stu-id="ef03b-189">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="ef03b-190">S tím, jak se mění obchodní požadavky, mohou být přidány nové kolekce prostředků, mohou se změnit vztahy mezi prostředky a může být změněna struktura dat v prostředcích.</span><span class="sxs-lookup"><span data-stu-id="ef03b-190">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="ef03b-191">Aktualizace webového rozhraní API pro zpracování nových požadavků je poměrně jednoduchý proces, ale je třeba zvážit účinky, které tyto změny budou mít na klientské aplikace, které spotřebovávají webové rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ef03b-191">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="ef03b-192">Přestože vývojář navrhování a implementace webového rozhraní API má plnou kontrolu nad tímto rozhraním API, vývojář nemá stejný stupeň kontroly nad klientskými aplikacemi, které mohou být vytvořeny organizacemi třetích stran, které pracují vzdáleně.</span><span class="sxs-lookup"><span data-stu-id="ef03b-192">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="ef03b-193">Správa verzí umožňuje webové rozhraní API k označení funkcí a prostředků, které zveřejňuje.</span><span class="sxs-lookup"><span data-stu-id="ef03b-193">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="ef03b-194">Klientská aplikace pak může odesílat požadavky na konkrétní verzi funkce nebo prostředku.</span><span class="sxs-lookup"><span data-stu-id="ef03b-194">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="ef03b-195">Existuje několik přístupů k implementaci správy verzí:</span><span class="sxs-lookup"><span data-stu-id="ef03b-195">There are several approaches to implement versioning:</span></span>

- <span data-ttu-id="ef03b-196">Správa verzí pomocí identifikátoru URI</span><span class="sxs-lookup"><span data-stu-id="ef03b-196">URI versioning</span></span>

- <span data-ttu-id="ef03b-197">Správa verzí pomocí řetězce dotazu</span><span class="sxs-lookup"><span data-stu-id="ef03b-197">Query string versioning</span></span>

- <span data-ttu-id="ef03b-198">Správa verzí pomocí hlavičky</span><span class="sxs-lookup"><span data-stu-id="ef03b-198">Header versioning</span></span>

<span data-ttu-id="ef03b-199">Řetězec dotazu a správa verzí identifikátoru URI jsou nejjednodušší implementovat.</span><span class="sxs-lookup"><span data-stu-id="ef03b-199">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="ef03b-200">Správa verzí záhlaví je dobrý přístup.</span><span class="sxs-lookup"><span data-stu-id="ef03b-200">Header versioning is a good approach.</span></span> <span data-ttu-id="ef03b-201">Správa verzí záhlaví však není tak explicitní a přímočará jako správa verzí uri.</span><span class="sxs-lookup"><span data-stu-id="ef03b-201">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="ef03b-202">Vzhledem k tomu, že správa verzí adresy URL je nejjednodušší a nejexplicitnější, ukázková aplikace eShopOnContainers používá správu verzí IDENTIFIKÁTORURI.</span><span class="sxs-lookup"><span data-stu-id="ef03b-202">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="ef03b-203">S uri správu verzí, stejně jako v eShopOnContainers ukázkové aplikace, pokaždé, když upravíte webové rozhraní API nebo změnit schéma prostředků, přidáte číslo verze uri pro každý prostředek.</span><span class="sxs-lookup"><span data-stu-id="ef03b-203">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="ef03b-204">Existující identifikátory URI by měly nadále fungovat jako dříve a vracet prostředky, které odpovídají schématu, které odpovídá požadované verzi.</span><span class="sxs-lookup"><span data-stu-id="ef03b-204">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="ef03b-205">Jak je znázorněno v následujícím příkladu kódu, verzi lze nastavit pomocí atributu Route v řadiči webového rozhraní API, což činí verzi explicitní v uri (v1 v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="ef03b-205">As shown in the following code example, the version can be set by using the Route attribute in the Web API controller, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="ef03b-206">Tento mechanismus správy verzí je jednoduchý a závisí na směrování požadavku serveru do příslušného koncového bodu.</span><span class="sxs-lookup"><span data-stu-id="ef03b-206">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="ef03b-207">Pro sofistikovanější správu verzí a nejlepší metodu při použití REST byste však měli použít hypermédia a implementovat [HATEOAS (Hypertext jako modul stavu aplikace).](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources)</span><span class="sxs-lookup"><span data-stu-id="ef03b-207">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ef03b-208">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="ef03b-208">Additional resources</span></span>

- <span data-ttu-id="ef03b-209">**Scott Hanselman. ASP.NET snadné správu verzí webového rozhraní API ASP.NET** </span><span class="sxs-lookup"><span data-stu-id="ef03b-209">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy** </span></span>\
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- <span data-ttu-id="ef03b-210">**Správa verzí webového rozhraní RESTful** </span><span class="sxs-lookup"><span data-stu-id="ef03b-210">**Versioning a RESTful web API** </span></span>\
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- <span data-ttu-id="ef03b-211">**Roye Fieldinga. Správa verzí, hypermédia a REST** </span><span class="sxs-lookup"><span data-stu-id="ef03b-211">**Roy Fielding. Versioning, Hypermedia, and REST** </span></span>\
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="ef03b-212">Generování metadat popisu Swagger z ASP.NET core webovérozhraní API</span><span class="sxs-lookup"><span data-stu-id="ef03b-212">Generating Swagger description metadata from your ASP.NET Core Web API</span></span>

<span data-ttu-id="ef03b-213">[Swagger](https://swagger.io/) je běžně používaný open source framework podporovaný velkým ekosystémem nástrojů, které vám pomohou navrhovat, vytvářet, dokumentovat a využívat vaše rozhraní API RESTful.</span><span class="sxs-lookup"><span data-stu-id="ef03b-213">[Swagger](https://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="ef03b-214">Stává se standardem pro doménu metadat popisu api.</span><span class="sxs-lookup"><span data-stu-id="ef03b-214">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="ef03b-215">Měli byste zahrnout metadata popisu Swagger s jakýmkoli druhem mikroslužeb, mikroslužeb řízených daty nebo pokročilejšími mikroslužbami řízenými doménami (jak je vysvětleno v následující části).</span><span class="sxs-lookup"><span data-stu-id="ef03b-215">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="ef03b-216">Srdcem Swagger je specifikace Swagger, což je metadata popisu rozhraní API v souboru JSON nebo YAML.</span><span class="sxs-lookup"><span data-stu-id="ef03b-216">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="ef03b-217">Specifikace vytvoří kontrakt RESTful pro vaše rozhraní API, který podrobně popisuje všechny jeho prostředky a operace v lidském i strojově čitelném formátu pro snadný vývoj, zjišťování a integraci.</span><span class="sxs-lookup"><span data-stu-id="ef03b-217">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="ef03b-218">Specifikace je základem specifikace OpenAPI (OAS) a je vyvinuta v otevřené, transparentní a kolaborativní komunitě pro standardizaci způsobu, jakým jsou definována rozhraní RESTful.</span><span class="sxs-lookup"><span data-stu-id="ef03b-218">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="ef03b-219">Specifikace definuje strukturu pro způsob zjištění služby a jak je pochopena její možnosti.</span><span class="sxs-lookup"><span data-stu-id="ef03b-219">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="ef03b-220">Další informace, včetně webového editoru a příkladů specifikací Swagger od společností jako Spotify, Uber, Slack a Microsoft, najdete na webu Swagger (<https://swagger.io>).</span><span class="sxs-lookup"><span data-stu-id="ef03b-220">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<https://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="ef03b-221">Proč použít Swagger?</span><span class="sxs-lookup"><span data-stu-id="ef03b-221">Why use Swagger?</span></span>

<span data-ttu-id="ef03b-222">Hlavní důvody pro generování metadat Swagger pro vaše api jsou následující.</span><span class="sxs-lookup"><span data-stu-id="ef03b-222">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="ef03b-223">**Možnost automatického využívání a integrace vašich api pro ostatní produkty**.</span><span class="sxs-lookup"><span data-stu-id="ef03b-223">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="ef03b-224">Swagger podporují desítky produktů a [komerčních nástrojů](https://swagger.io/commercial-tools/) a mnoho [knihoven a rámců.](https://swagger.io/open-source-integrations/)</span><span class="sxs-lookup"><span data-stu-id="ef03b-224">Dozens of products and [commercial tools](https://swagger.io/commercial-tools/) and many [libraries and frameworks](https://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="ef03b-225">Společnost Microsoft má produkty vysoké úrovně a nástroje, které mohou automaticky využívat rozhraní API založená na programu Swagger, například následující:</span><span class="sxs-lookup"><span data-stu-id="ef03b-225">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

- <span data-ttu-id="ef03b-226">[AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="ef03b-226">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="ef03b-227">Můžete automaticky generovat třídy klienta .NET pro volání Swagger.</span><span class="sxs-lookup"><span data-stu-id="ef03b-227">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="ef03b-228">Tento nástroj lze použít z rozhraní SEkatel a také integruje s Visual Studio pro snadné použití prostřednictvím GUI.</span><span class="sxs-lookup"><span data-stu-id="ef03b-228">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

- <span data-ttu-id="ef03b-229">[Microsoft Flow](https://flow.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="ef03b-229">[Microsoft Flow](https://flow.microsoft.com/).</span></span> <span data-ttu-id="ef03b-230">Rozhraní API můžete automaticky [používat a integrovat](https://flow.microsoft.com/blog/integrating-custom-api/) do pracovního postupu Microsoft Flow na vysoké úrovni bez nutnosti programování.</span><span class="sxs-lookup"><span data-stu-id="ef03b-230">You can automatically [use and integrate your API](https://flow.microsoft.com/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

- <span data-ttu-id="ef03b-231">[Aplikace Microsoft PowerApps](https://powerapps.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="ef03b-231">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span></span> <span data-ttu-id="ef03b-232">Své ROZHRANÍ API můžete automaticky využívat z [mobilních aplikací PowerApps vytvořených](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) pomocí [PowerApps Studia](https://powerapps.microsoft.com/build-powerapps/), bez nutnosti programování.</span><span class="sxs-lookup"><span data-stu-id="ef03b-232">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), with no programming skills required.</span></span>

- <span data-ttu-id="ef03b-233">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="ef03b-233">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="ef03b-234">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span><span class="sxs-lookup"><span data-stu-id="ef03b-234">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="ef03b-235">**Možnost automatického generování dokumentace rozhraní API**.</span><span class="sxs-lookup"><span data-stu-id="ef03b-235">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="ef03b-236">Při vytváření rozsáhlých RESTful API, jako jsou komplexní aplikace založené na mikroslužbách, je třeba zpracovat mnoho koncových bodů s různými datovými modely používanými v datové části požadavku a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="ef03b-236">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="ef03b-237">Mít správnou dokumentaci a mít solidní průzkumník rozhraní API, jak se dostanete s Swagger, je klíčem k úspěchu vašeho rozhraní API a přijetí vývojáři.</span><span class="sxs-lookup"><span data-stu-id="ef03b-237">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="ef03b-238">Metadata Swaggeru jsou to, co Microsoft Flow, PowerApps a Azure Logic Apps používají k pochopení toho, jak používat rozhraní API a připojit se k nim.</span><span class="sxs-lookup"><span data-stu-id="ef03b-238">Swagger's metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

<span data-ttu-id="ef03b-239">Existuje několik možností, jak automatizovat generování metadat Swagger pro ASP.NET aplikace Core REST API, ve formě funkčních stránek nápovědy ROZHRANÍ API, založených na *swagger-ui*.</span><span class="sxs-lookup"><span data-stu-id="ef03b-239">There are several options to automate Swagger metadata generation for ASP.NET Core REST API applications, in the form of functional API help pages, based on *swagger-ui*.</span></span>

<span data-ttu-id="ef03b-240">Pravděpodobně nejlepší vědět, je [Swashbuckle,](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) který je v současné době používá v [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) a budeme pokrývat v některých detailech v\# této příručce,\# ale je tu také možnost používat [NSwag](https://github.com/RSuter/NSwag), který může generovat Typescript a C API klienty, stejně jako C řadiče, z Swagger nebo OpenAPI specifikace a dokonce skenování .dll, který obsahuje řadiče, pomocí [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span><span class="sxs-lookup"><span data-stu-id="ef03b-240">Probably the best know is [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) which is currently used in [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) and we'll cover in some detail in this guide but there's also the option to use [NSwag](https://github.com/RSuter/NSwag), which can generate Typescript and C\# API clients, as well as C\# controllers, from a Swagger or OpenAPI specification and even by scanning the .dll that contains the controllers, using [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="ef03b-241">Jak automatizovat generování metadat API Swagger pomocí balíčku Swashbuckle NuGet</span><span class="sxs-lookup"><span data-stu-id="ef03b-241">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="ef03b-242">Generování metadat Swagger ručně (v souboru JSON nebo YAML) může být zdlouhavá práce.</span><span class="sxs-lookup"><span data-stu-id="ef03b-242">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="ef03b-243">Můžete však automatizovat zjišťování rozhraní API ASP.NET služby webového rozhraní API pomocí [balíčku Swashbuckle NuGet](https://aka.ms/swashbuckledotnetcore) pro dynamickou generování metadat rozhraní API Swagger.</span><span class="sxs-lookup"><span data-stu-id="ef03b-243">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](https://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="ef03b-244">Swashbuckle automaticky generuje metadata Swagger pro vaše projekty webového rozhraní API ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ef03b-244">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="ef03b-245">Podporuje ASP.NET core web API projekty a tradiční ASP.NET webové rozhraní API a jakékoli jiné varianty, jako je například Azure API App, Azure Mobile App, Azure Service Fabric mikroslužeb na základě ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="ef03b-245">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="ef03b-246">Podporuje také prosté webové rozhraní API nasazené v kontejnerech, jako v pro referenční aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ef03b-246">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="ef03b-247">Swashbuckle kombinuje průzkumníka rozhraní API a Swagger nebo [swagger-ui](https://github.com/swagger-api/swagger-ui) a poskytuje bohaté prostředí pro zjišťování a dokumentaci pro vaše spotřebitele rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ef03b-247">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="ef03b-248">Kromě svého motoru generátoru metadat Swagger obsahuje Swashbuckle také vestavěnou verzi swagger-ui, která bude automaticky sloužit až po instalaci Swashbuckle.</span><span class="sxs-lookup"><span data-stu-id="ef03b-248">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="ef03b-249">To znamená, že můžete doplnit rozhraní API o příjemné zjišťování uI pomoci vývojářům používat vaše rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ef03b-249">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="ef03b-250">Vyžaduje velmi malé množství kódu a údržby, protože je automaticky generována, což vám umožní soustředit se na vytváření rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ef03b-250">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="ef03b-251">Výsledek pro průzkumníka rozhraní API vypadá jako obrázek 6-8.</span><span class="sxs-lookup"><span data-stu-id="ef03b-251">The result for the API Explorer looks like Figure 6-8.</span></span>

![Snímek obrazovky s Průzkumníkem rozhraní Api Swagger zobrazujícím rozhraní API eShopOContainers.](./media/data-driven-crud-microservice/swagger-metadata-eshoponcontainers-catalog-microservice.png)

<span data-ttu-id="ef03b-253">**Obrázek 6-8**.</span><span class="sxs-lookup"><span data-stu-id="ef03b-253">**Figure 6-8**.</span></span> <span data-ttu-id="ef03b-254">Swashbuckle API Explorer založený na metadatech Swagger – mikroslužba katalogu eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="ef03b-254">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="ef03b-255">Swashbuckle generované Swagger Rozhraní API dokumentace obsahuje všechny publikované akce.</span><span class="sxs-lookup"><span data-stu-id="ef03b-255">The Swashbuckle generated Swagger UI API documentation includes all published actions.</span></span> <span data-ttu-id="ef03b-256">Průzkumník rozhraní API zde není nejdůležitější věc.</span><span class="sxs-lookup"><span data-stu-id="ef03b-256">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="ef03b-257">Jakmile budete mít webové rozhraní API, které lze popsat sám sebe v metadatech Swagger, vaše rozhraní API lze bez problémů použít z nástrojů založených na Swagger, včetně generátorů kódu proxy klienta třídy proxy, které mohou cílit na mnoho platforem.</span><span class="sxs-lookup"><span data-stu-id="ef03b-257">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="ef03b-258">Například, jak již bylo zmíněno, [AutoRest](https://github.com/Azure/AutoRest) automaticky generuje třídy klienta .NET.</span><span class="sxs-lookup"><span data-stu-id="ef03b-258">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="ef03b-259">Ale další nástroje, jako [je swagger-codegen](https://github.com/swagger-api/swagger-codegen) jsou také k dispozici, které umožňují generování kódu klientských knihoven rozhraní API, server zástupné procedury a dokumentace automaticky.</span><span class="sxs-lookup"><span data-stu-id="ef03b-259">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="ef03b-260">V současné době swashbuckle se skládá z pěti interních balíčků NuGet pod metabalíčkem s vysokou úrovní [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) pro ASP.NET aplikace Core.</span><span class="sxs-lookup"><span data-stu-id="ef03b-260">Currently, Swashbuckle consists of five internal NuGet packages under the high-level meta- package [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) for ASP.NET Core applications.</span></span>

<span data-ttu-id="ef03b-261">Po instalaci těchto balíčků NuGet v projektu webového rozhraní API je třeba nakonfigurovat Swagger ve třídě Startup, jako v následujícím **zjednodušeném** kódu:</span><span class="sxs-lookup"><span data-stu-id="ef03b-261">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following **simplified** code:</span></span>

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

<span data-ttu-id="ef03b-262">Jakmile to uděláte, můžete spustit aplikaci a procházet následující koncové body Swagger JSON a UI pomocí adres URL, jako jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="ef03b-262">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```console
  http://<your-root-url>/swagger/v1/swagger.json

  http://<your-root-url>/swagger/
```

<span data-ttu-id="ef03b-263">Dříve jste viděli generované ui vytvořené Swashbuckle `http://<your-root-url>/swagger`pro ADRESU URL, jako je .</span><span class="sxs-lookup"><span data-stu-id="ef03b-263">You previously saw the generated UI created by Swashbuckle for a URL like `http://<your-root-url>/swagger`.</span></span> <span data-ttu-id="ef03b-264">Na obrázku 6-9 můžete také vidět, jak můžete otestovat libovolnou metodu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ef03b-264">In Figure 6-9 you can also see how you can test any API method.</span></span>

![Snímek obrazovky s uzlou rozhraní Swagger zobrazující dostupné testovací nástroje](./media/data-driven-crud-microservice/swashbuckle-ui-testing.png)

<span data-ttu-id="ef03b-266">**Obrázek 6-9**.</span><span class="sxs-lookup"><span data-stu-id="ef03b-266">**Figure 6-9**.</span></span> <span data-ttu-id="ef03b-267">Uživatelské rozhraní Swashbuckle otestování metody rozhraní API katalogu/položek</span><span class="sxs-lookup"><span data-stu-id="ef03b-267">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="ef03b-268">Podrobnosti rozhraní API Swagger u> zobrazuje ukázku odpovědi a lze použít ke spuštění skutečné rozhraní API, což je skvělé pro zjišťování vývojáře.</span><span class="sxs-lookup"><span data-stu-id="ef03b-268">The Swagger UI API detail shows a sample of the response and can be used to execute the real API, which is great for developer discovery.</span></span> <span data-ttu-id="ef03b-269">Obrázek 6-10 ukazuje Swagger JSON metadata generovaná z eShopOnContainers mikroslužby (což je to, co nástroje používají pod) při žádosti pomocí `http://<your-root-url>/swagger/v1/swagger.json` [Postman](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="ef03b-269">Figure 6-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request `http://<your-root-url>/swagger/v1/swagger.json` using [Postman](https://www.getpostman.com/).</span></span>

![Snímek obrazovky s ukázkovým pošťákovým uzemňovacím rozhraním zobrazujícím metadata Swagger JSON](./media/data-driven-crud-microservice/swagger-json-metadata.png)

<span data-ttu-id="ef03b-271">**Obrázek 6-10**.</span><span class="sxs-lookup"><span data-stu-id="ef03b-271">**Figure 6-10**.</span></span> <span data-ttu-id="ef03b-272">Metadata Swagger JSON</span><span class="sxs-lookup"><span data-stu-id="ef03b-272">Swagger JSON metadata</span></span>

<span data-ttu-id="ef03b-273">Je to tak jednoduché.</span><span class="sxs-lookup"><span data-stu-id="ef03b-273">It is that simple.</span></span> <span data-ttu-id="ef03b-274">A protože je automaticky generována, metadata Swagger se zvýší, když přidáte další funkce do rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="ef03b-274">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="ef03b-275">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="ef03b-275">Additional resources</span></span>

- <span data-ttu-id="ef03b-276">**stránky nápovědy webového rozhraní API ASP.NET pomocí swaggeru** </span><span class="sxs-lookup"><span data-stu-id="ef03b-276">**ASP.NET Web API Help Pages using Swagger** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger](/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- <span data-ttu-id="ef03b-277">**Začínáme s Swashbuckle a ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="ef03b-277">**Get started with Swashbuckle and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle](/aspnet/core/tutorials/getting-started-with-swashbuckle)

- <span data-ttu-id="ef03b-278">**Začínáme s NSwag a ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="ef03b-278">**Get started with NSwag and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag](/aspnet/core/tutorials/getting-started-with-nswag)

> [!div class="step-by-step"]
> <span data-ttu-id="ef03b-279">[Předchozí](microservice-application-design.md)
> [další](multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="ef03b-279">[Previous](microservice-application-design.md)
[Next](multi-container-applications-docker-compose.md)</span></span>
