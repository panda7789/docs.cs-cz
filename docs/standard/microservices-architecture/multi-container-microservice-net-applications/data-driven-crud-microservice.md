---
title: Vytvoření jednoduché mikroslužby CRUD řízené daty
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Principy vytváření jednoduchých CRUD (řízené daty) mikroslužeb v rámci kontextu aplikace mikroslužeb.
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 10/02/2018
ms.openlocfilehash: c6316717f78dffb672afdf79e919fd1bd7874b52
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53149566"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="8b5aa-103">Vytvoření jednoduché mikroslužby CRUD řízené daty</span><span class="sxs-lookup"><span data-stu-id="8b5aa-103">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="8b5aa-104">Tento oddíl, který ukazuje jak vytvořit jednoduchou mikroslužeb, která provádí vytvořit, číst, aktualizace a odstranění (CRUD) operací na zdroj dat.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-104">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="8b5aa-105">Navrhování jednoduché mikroslužby CRUD</span><span class="sxs-lookup"><span data-stu-id="8b5aa-105">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="8b5aa-106">Tento typ kontejnerizované mikroslužby z návrhu hlediska, je velmi jednoduché.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-106">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="8b5aa-107">Možná je jednoduchý problém vyřešit, nebo možná implementace je pouze testování konceptu.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-107">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![Jednoduché mikroslužby CRUD je vzorek vnitřního návrhu.](./media/image4.png)

<span data-ttu-id="8b5aa-109">**Obrázek 6 – 4**.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-109">**Figure 6-4**.</span></span> <span data-ttu-id="8b5aa-110">Interní návrhu pro jednoduché mikroslužby CRUD</span><span class="sxs-lookup"><span data-stu-id="8b5aa-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="8b5aa-111">Příkladem tohoto druhu služby Jednoduché datové jednotky je mikroslužeb katalogu v aplikaci eShopOnContainers ukázkové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="8b5aa-112">Tento typ služby implementuje všechny jeho funkce v jednom projektu webového rozhraní API ASP.NET Core, který obsahuje třídy pro její datový model, jeho obchodní logiky a jeho kód přístupu k datům.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="8b5aa-113">Je také ukládá související data v databázi spuštěna v systému SQL Server (jako jiný kontejner pro účely vývoje a testování), ale mohou být také jakýmkoli regulární systému SQL Server hostitelem, jak je znázorněno v obrázek 6 – 5.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 6-5.</span></span>

![Logické mikroslužeb katalogu obsahuje databázi katalogu, která může být nebo není ve stejném Docker hostovat.](./media/image5.png)

<span data-ttu-id="8b5aa-116">**Obrázek 6 – 5**.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-116">**Figure 6-5**.</span></span> <span data-ttu-id="8b5aa-117">Jednoduché mikroslužby data-driven/CRUD návrhu</span><span class="sxs-lookup"><span data-stu-id="8b5aa-117">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="8b5aa-118">Při vývoji tento druh službu, potřebujete jenom [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) a rozhraní API pro přístup k datům nebo ORM jako [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span><span class="sxs-lookup"><span data-stu-id="8b5aa-118">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="8b5aa-119">Může také generovat [Swagger](https://swagger.io/) metadat automaticky prostřednictvím [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) k poskytnutí popisu co nabídek služby, jak je vysvětleno v další části.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-119">You could also generate [Swagger](https://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="8b5aa-120">Všimněte si, že databázový server, jako je SQL Server v kontejneru Dockeru se skvěle hodí pro vývojová prostředí, protože všechny závislosti může mít až systémem, aniž by museli o zřízení databáze v cloudu nebo místně.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-120">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="8b5aa-121">To je velmi praktické, když s integrací testy.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-121">This is very convenient when running integration tests.</span></span> <span data-ttu-id="8b5aa-122">Však pro produkční prostředí, databázový server v kontejneru nedoporučuje se používat, protože se obvykle nezobrazí vysokou dostupnost s možnostmi tento přístup.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-122">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="8b5aa-123">Pro produkční prostředí v Azure se doporučuje použít službu Azure SQL DB nebo jiné databázové technologie, která dokáže poskytovat vysokou dostupnost a vysokou škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-123">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="8b5aa-124">Například pro NoSQL přístup, můžete zvolit služby cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-124">For example, for a NoSQL approach, you might choose CosmosDB.</span></span>

<span data-ttu-id="8b5aa-125">Nakonec pomocí úpravy souboru Docker a docker-compose.yml soubory metadat, můžete nakonfigurovat jak se vytvoří snímek tohoto kontejneru, jaké základní image budou používat plus návrh nastavení, jako je interní a externí názvy a porty TCP.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-125">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span> 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="8b5aa-126">Implementace jednoduché mikroslužby CRUD s ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8b5aa-126">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="8b5aa-127">Provádět jednoduché mikroslužby CRUD pomocí .NET Core a Visual Studio spustíte tak, že vytvoříte jednoduchý projekt webového rozhraní API ASP.NET Core (spouštění v .NET Core tak může probíhat na hostitele linuxového Dockeru), jako obrázku 6 – 6.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-127">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 6-6.</span></span>

![Vytvoření rozhraní API webového projektu ASP.NET Core, nejprve vyberte webovou aplikaci ASP.NET Core a pak vyberte typ rozhraní API.](./media/image6.png)

<span data-ttu-id="8b5aa-129">**Obrázek 6 – 6**.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-129">**Figure 6-6**.</span></span> <span data-ttu-id="8b5aa-130">Vytvoření projektu webového rozhraní API ASP.NET Core v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="8b5aa-130">Creating an ASP.NET Core Web API project in Visual Studio</span></span>

<span data-ttu-id="8b5aa-131">Po vytvoření projektu, můžete implementovat vaše řadiče MVC, stejně jako v jiných projekt webového rozhraní API pomocí rozhraní API Entity Framework nebo jiném rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-131">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="8b5aa-132">V novém projektu webového rozhraní API zobrazí se pouze závislost mít v mikroslužba je v ASP.NET Core, samotný.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-132">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="8b5aa-133">Interně, v rámci *metabalíček* závislostí, odkazuje Entity Framework a řada dalších balíčků .NET Core Nuget, jak je znázorněno v obrázek 6 až 7.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-133">Internally, within the *Microsoft.AspNetCore.All* dependency, it is referencing Entity Framework and many other .NET Core Nuget packages, as shown in Figure 6-7.</span></span>

![Projekt rozhraní API obsahuje odkazy na balíček Microsoft.AspNetCore.App NuGet, který obsahuje odkazy na všechny nezbytné balíčky.](./media/image8.png)

<span data-ttu-id="8b5aa-136">**Obrázek 6 až 7**.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-136">**Figure 6-7**.</span></span> <span data-ttu-id="8b5aa-137">Závislosti v jednoduché mikroslužby CRUD webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8b5aa-137">Dependencies in a simple CRUD Web API microservice</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="8b5aa-138">Implementace CRUD webového rozhraní API služeb s Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="8b5aa-138">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="8b5aa-139">Entity Framework (EF) Core je odlehčený, rozšiřitelné, a multiplatformní verze oblíbených dat Entity Framework přístup k technologii.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-139">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="8b5aa-140">EF Core je objektově relační Mapovač (ORM), který umožňuje vývojářům .NET pracovat s databází s použitím objektů .NET.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-140">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="8b5aa-141">Mikroslužby katalogu používá EF a zprostředkovatele SQL Server, protože jeho databáze je spuštěna v kontejneru se serverem SQL Server pro image Dockeru pro Linux.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-141">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="8b5aa-142">Databáze však může být nasazený do SQL serveru, jako je například Windows on-premises nebo databázi SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-142">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="8b5aa-143">Jediné, co je třeba změnit je připojovací řetězec webového rozhraní API ASP.NET mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-143">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="the-data-model"></a><span data-ttu-id="8b5aa-144">Datový model</span><span class="sxs-lookup"><span data-stu-id="8b5aa-144">The data model</span></span>

<span data-ttu-id="8b5aa-145">S EF Core provádí přístup k datům s použitím modelu.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-145">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="8b5aa-146">Model je tvořené tříd entit (doménový model) a odvozené kontextu (DbContext), který reprezentuje relaci s databází, umožňuje dotazování a uložit data.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-146">A model is made up of (domain model) entity classes and a derived context (DbContext) that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="8b5aa-147">Můžete generovat model z existující databáze, ručně code model tak, aby odpovídaly vaší databáze nebo migraci EF použít k vytvoření databáze z vašeho modelu pomocí přístupu code first, (, který umožňuje snadno vyvíjet databáze s modelu mění v průběhu času).</span><span class="sxs-lookup"><span data-stu-id="8b5aa-147">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model, using the code-first approach (that makes it easy to evolve the database as your model changes over time).</span></span> <span data-ttu-id="8b5aa-148">Poslední přístup se používá pro mikroslužby katalogu.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-148">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="8b5aa-149">Vidíte příklad třídy entity catalogitem je například v následujícím příkladu kódu, který je jednoduchý prostý původní objekt CLR ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) třída entity.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-149">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

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

<span data-ttu-id="8b5aa-150">Budete také potřebovat DbContext, který reprezentuje relaci s databází.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-150">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="8b5aa-151">Pro mikroslužby katalogu CatalogContext třída je odvozena ze základní třídy DbContext, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8b5aa-151">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

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

<span data-ttu-id="8b5aa-152">Můžete mít další `DbContext` implementace.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-152">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="8b5aa-153">Například v ukázkové Catalog.API mikroslužeb, je druhý `DbContext` s názvem `CatalogContextSeed` kde automaticky naplní vzorová data při prvním pokusu o přístup k databázi.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-153">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="8b5aa-154">Tato metoda je užitečná pro ukázková data a pro automatizované testování, podporuje i scénáře.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-154">This method is useful for demo data and for automated testing scenarios, as well.</span></span> 

<span data-ttu-id="8b5aa-155">V rámci `DbContext`, je použít `OnModelCreating` metodu za účelem přizpůsobení entity mapování objektů a databáze a další [bodů rozšiřitelnosti EF](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span><span class="sxs-lookup"><span data-stu-id="8b5aa-155">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings and other [EF extensibility points](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="8b5aa-156">Dotazování na data z kontrolerů rozhraní Web API</span><span class="sxs-lookup"><span data-stu-id="8b5aa-156">Querying data from Web API controllers</span></span>

<span data-ttu-id="8b5aa-157">Instance třídy entity se obvykle načítají z databáze pomocí Language Integrated Query (LINQ), jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8b5aa-157">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

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

##### <a name="saving-data"></a><span data-ttu-id="8b5aa-158">Ukládání dat</span><span class="sxs-lookup"><span data-stu-id="8b5aa-158">Saving data</span></span>

<span data-ttu-id="8b5aa-159">Data je vytvořit, odstranit a upravit v databázi pomocí instance třídy entity.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-159">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="8b5aa-160">Můžete přidat kód jako v následujícím pevně zakódované příkladu (mock data v tomto případě) k vašim řadičům webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-160">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="8b5aa-161">Injektáž závislostí do kontrolerů ASP.NET Core a webové rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8b5aa-161">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="8b5aa-162">V ASP.NET Core můžete ihned Dependency Injection (DI).</span><span class="sxs-lookup"><span data-stu-id="8b5aa-162">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="8b5aa-163">Není potřeba nastavit kontejner řízení IOC (Inversion) třetí strany, i když můžete svůj upřednostňovaný kontejner IoC pružný infrastruktury ASP.NET Core, chcete-li.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-163">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="8b5aa-164">V tomto případě znamená, že můžete přímo vložit požadovaná DBContext EF nebo další úložiště prostřednictvím konstruktoru kontroleru.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-164">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span>

<span data-ttu-id="8b5aa-165">V příkladu výše `CatalogController` třídy, jsme se vkládá objekt `CatalogContext` zadejte plus dalších objektů prostřednictvím `CatalogController()` konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-165">In the example above of the `CatalogController` class, we are injecting an object of `CatalogContext` type plus other objects through the `CatalogController()` constructor.</span></span>

<span data-ttu-id="8b5aa-166">Důležité konfigurační nastavení v projektu webového rozhraní API je registrace třídy DbContext na kontejner IoC služby.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-166">An important configuration to set up in the Web API project is the DbContext class registration into the service's IoC container.</span></span> <span data-ttu-id="8b5aa-167">To obvykle děláte, `Startup` třídy voláním `services.AddDbContext<DbContext>()` metodu `ConfigureServices()` způsob, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8b5aa-167">You typically do so in the `Startup` class by calling the `services.AddDbContext<DbContext>()` method inside the `ConfigureServices()` method, as shown in the following example:</span></span>

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

### <a name="additional-resources"></a><span data-ttu-id="8b5aa-168">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="8b5aa-168">Additional resources</span></span>

- <span data-ttu-id="8b5aa-169">**Dotazování na Data** \\</span><span class="sxs-lookup"><span data-stu-id="8b5aa-169">**Querying Data** \\</span></span>
  [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)

- <span data-ttu-id="8b5aa-170">**Ukládání dat** \\</span><span class="sxs-lookup"><span data-stu-id="8b5aa-170">**Saving Data** \\</span></span>
  [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="8b5aa-171">DB připojovací řetězec a prostředí proměnné využívaných kontejnery Dockeru</span><span class="sxs-lookup"><span data-stu-id="8b5aa-171">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="8b5aa-172">Můžete použít nastavení ASP.NET Core a přidejte vlastnost ConnectionString do souboru Settings.JSON v nástroji, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8b5aa-172">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

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

<span data-ttu-id="8b5aa-173">Výchozí hodnoty pro vlastnost ConnectionString nebo jakoukoli jinou vlastnosti můžou mít soubor Settings.JSON v nástroji.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-173">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="8b5aa-174">Tyto vlastnosti však přepíše hodnoty proměnných prostředí, které zadáte v souboru docker-compose.override.yml při použití Dockeru.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-174">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="8b5aa-175">Ze svých souborů docker-compose.yml a docker-compose.override.yml můžete inicializovat těchto proměnných prostředí tak, které Docker se nastavit je jako proměnné prostředí operačního systému pro vás, jak je znázorněno v následujícím souboru docker-compose.override.yml (připojení řetězce a další řádky zalamovat v tomto příkladu, ale nebude zabalení ve vlastním souboru).</span><span class="sxs-lookup"><span data-stu-id="8b5aa-175">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

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

<span data-ttu-id="8b5aa-176">Soubory docker-compose.yml na úrovni řešení nejsou pouze flexibilnější, než konfigurační soubory na úrovni projektu nebo mikroslužeb, ale také vyšší úroveň zabezpečení Pokud přepíšete deklarované na docker-compose soubory s hodnotami z nastavení proměnné prostředí z nasazení úloh Azure DevOps služby Docker, jako jsou nástroje pro nasazení.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-176">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from Azure DevOps Services Docker deployment tasks.</span></span> 

<span data-ttu-id="8b5aa-177">Nakonec můžete získat tuto hodnotu v kódu s použitím konfigurace\["ConnectionString"\], jak je znázorněno v metodě ConfigureServices v předchozím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-177">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="8b5aa-178">Pro produkční prostředí, můžete však prozkoumat další způsoby, jak na tom, jak ukládat tajné kódy jako jsou připojovací řetězce.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-178">However, for production environments, you might want to explore additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="8b5aa-179">Pomocí vynikající způsob, jak spravovat tajné kódy aplikace [Azure Key Vault} (https://azure.microsoft.com/services/key-vault/).</span><span class="sxs-lookup"><span data-stu-id="8b5aa-179">An excellent way to manage application secrets is using [Azure Key Vault}(https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="8b5aa-180">Služba Azure Key Vault umožňuje ukládat a ochraně kryptografických klíčů a tajných kódů používaných cloudovými aplikacemi a službami.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-180">Azure Key Vault helps to store and safeguard cryptographic keys and secrets used by your cloud applications and services.</span></span> <span data-ttu-id="8b5aa-181">Tajný kód se něco chcete zachovat striktní kontrolu nad, jako jsou klíče rozhraní API, připojovací řetězce, hesla, atd. a přísné zahrnuje využití protokolování, nastavení vypršení platnosti, Správa přístupu, <span class="underline">mimo jiné</span>.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-181">A secret is anything you want to keep strict control of, like API keys, connection strings, passwords, etc. and strict control includes usage logging, setting expiration, managing access, <span class="underline">among others</span>.</span></span>

<span data-ttu-id="8b5aa-182">Služba Azure Key Vault umožňuje velmi podrobné řízení úrovně použití tajných kódů aplikace bez nutnosti libovolný uživatel je znají.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-182">Azure Key Vault allows a very detailed control level of the application secrets usage without the need to let anyone know them.</span></span> <span data-ttu-id="8b5aa-183">Tajné klíče můžete otočit i pro zvýšení zabezpečení bez narušení běžného vývoj nebo operace.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-183">The secrets can even be rotated for enhanced security without disrupting development or operations.</span></span>

<span data-ttu-id="8b5aa-184">Aplikace mají k registraci ve službě Active Directory organizace tak, aby používaly služby Key Vault.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-184">Applications have to be registered in the organization's Active Directory, so they can use the Key Vault.</span></span>

<span data-ttu-id="8b5aa-185">Můžete zkontrolovat <span class="underline">dokumentace ke službě Key Vault koncepty</span> další podrobnosti.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-185">You can check the <span class="underline">Key Vault Concepts documentation</span> for more details.</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="8b5aa-186">Implementace správy verzí v rozhraní ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="8b5aa-186">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="8b5aa-187">Podle měnících se obchodních požadavků, mohou být přidány nové kolekce prostředků, může změnit vztahy mezi prostředky a může být změněna strukturu dat v prostředcích.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-187">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="8b5aa-188">Aktualizace webového rozhraní API pro zpracování nových požadavků je poměrně přímočarý proces, ale musíte zvážit důsledky, které tyto změny budou mít na klientské aplikace využívající webové rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-188">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="8b5aa-189">I když vývojář navrhující a implementující webové rozhraní API má plnou kontrolu nad tímto rozhraním API, vývojář nemá stejnou úroveň kontroly nad klientskými aplikacemi, které může být sestavena v třetích stran, vzdáleně působící organizace.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-189">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="8b5aa-190">Správa verzí umožňuje webovému rozhraní API k označení funkce a prostředky, které vystavuje.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-190">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="8b5aa-191">Klientská aplikace může potom odesílat požadavky na konkrétní verzi funkce nebo prostředku.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-191">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="8b5aa-192">Existuje několik přístupů k implementaci správy verzí:</span><span class="sxs-lookup"><span data-stu-id="8b5aa-192">There are several approaches to implement versioning:</span></span>

- <span data-ttu-id="8b5aa-193">Identifikátor URI správy verzí</span><span class="sxs-lookup"><span data-stu-id="8b5aa-193">URI versioning</span></span>

- <span data-ttu-id="8b5aa-194">Správa verzí pomocí řetězce dotazu</span><span class="sxs-lookup"><span data-stu-id="8b5aa-194">Query string versioning</span></span>

- <span data-ttu-id="8b5aa-195">Správa verzí pomocí hlavičky</span><span class="sxs-lookup"><span data-stu-id="8b5aa-195">Header versioning</span></span>

<span data-ttu-id="8b5aa-196">Řetězec dotazu a identifikátor URI správy verzí jsou nejjednodušší implementace.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-196">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="8b5aa-197">Správa verzí pomocí hlavičky je dobrý nápad.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-197">Header versioning is a good approach.</span></span> <span data-ttu-id="8b5aa-198">Nicméně správa verzí pomocí hlavičky, ne jako explicitní a přímočaré jako identifikátor URI správy verzí.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-198">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="8b5aa-199">Vzhledem k tomu, že adresa URL správy verzí je nejjednodušší a největší explicitní, aplikaci eShopOnContainers ukázková aplikace používá Správa verzí identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-199">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="8b5aa-200">Pomocí správy verzí identifikátor URI, stejně jako v aplikaci eShopOnContainers ukázkovou aplikaci pokaždé, když upravíte webové rozhraní API nebo změníte schéma prostředků, přidejte číslo verze do identifikátoru URI každého prostředku.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-200">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="8b5aa-201">Existující identifikátory URI by měly nadále fungovat jako předtím, vracet prostředky, které odpovídají schématu, která odpovídá na požadovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-201">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="8b5aa-202">Jak je znázorněno v následujícím příkladu kódu, může být verze nastavená pomocí atribut trasy v kontroleru webového rozhraní API, takže verze explicitní v identifikátoru URI (verze 1 v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="8b5aa-202">As shown in the following code example, the version can be set by using the Route attribute in the Web API controller, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="8b5aa-203">Tento mechanismus správy verzí je jednoduché a závisí na směrování požadavků na příslušný koncový bod serveru.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-203">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="8b5aa-204">Pro složitější správy verzí a nejlepší metody při používání REST, můžete ale by měl používejte hypermédia a implementovat [HATEOAS (Hypertext as Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span><span class="sxs-lookup"><span data-stu-id="8b5aa-204">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="8b5aa-205">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="8b5aa-205">Additional resources</span></span>

- <span data-ttu-id="8b5aa-206">**Scott Hanselman. Správa verzí RESTful webového rozhraní API ASP.NET Core snadné** \\</span><span class="sxs-lookup"><span data-stu-id="8b5aa-206">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy** \\</span></span>
  [*https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)

- <span data-ttu-id="8b5aa-207">**Správa verzí RESTful webového rozhraní API** \\</span><span class="sxs-lookup"><span data-stu-id="8b5aa-207">**Versioning a RESTful web API** \\</span></span>
  [*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

- <span data-ttu-id="8b5aa-208">**Roy Fielding. Správa verzí, Hypermédia a REST** \\</span><span class="sxs-lookup"><span data-stu-id="8b5aa-208">**Roy Fielding. Versioning, Hypermedia, and REST** \\</span></span>
  [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="8b5aa-209">Generování metadat Swagger popis z webové rozhraní API ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="8b5aa-209">Generating Swagger description metadata from your ASP.NET Core Web API</span></span> 

<span data-ttu-id="8b5aa-210">[Swagger](https://swagger.io/) je běžně používaný open source architektura zajištěná rozsáhlého ekosystému nástrojů, která vám pomůže návrhu, sestavení, dokument a využívání rozhraní RESTful API.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-210">[Swagger](https://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="8b5aa-211">To se stává standard pro doménu metadat popis rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-211">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="8b5aa-212">By měl obsahovat popis metadata Swagger s jakýmkoli mikroslužeb, mikroslužby s daty nebo pokročilejší mikroslužeb řízeného doménou (jak je popsáno v následující části).</span><span class="sxs-lookup"><span data-stu-id="8b5aa-212">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="8b5aa-213">Srdce Swaggeru je specifikace Swaggeru, což je popis metadat rozhraní API v souboru JSON nebo YAML.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-213">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="8b5aa-214">Specifikace vytvoří RESTful smlouvy pro vaše rozhraní API s podrobnostmi o všech jeho prostředků a operací v obou lidské a machine readable formátu pro snadný vývoj, zjišťování a integrace.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-214">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="8b5aa-215">Specifikace je základem z specifikaci OpenAPI (OAS) a je vyvinuta v komunitě open transparentní a spolupráci ke standardizaci způsob, jakým jsou definovány rozhraní RESTful.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-215">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="8b5aa-216">Specifikace definuje strukturu pro jak může služba zjistit a jak své možnosti srozumitelný.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-216">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="8b5aa-217">Další informace, včetně editoru webu a příklady specifikace Swagger ze společnosti, jako Spotify, Uber, Slack a Microsoft, naleznete v tématu Swagger lokality ([https://swagger.io](https://swagger.io)).</span><span class="sxs-lookup"><span data-stu-id="8b5aa-217">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site ([https://swagger.io](https://swagger.io)).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="8b5aa-218">Proč používat Swagger?</span><span class="sxs-lookup"><span data-stu-id="8b5aa-218">Why use Swagger?</span></span>

<span data-ttu-id="8b5aa-219">Hlavní důvody ke generování metadat Swagger pro rozhraní API jsou uvedeny níže.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-219">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="8b5aa-220">**Možnost pro ostatní produkty automaticky využívat a integrovat vaše rozhraní API**.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-220">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="8b5aa-221">Desítky produkty a [komerční nástroje](https://swagger.io/commercial-tools/) a mnoha [knihoven a architektur](https://swagger.io/open-source-integrations/) podporují Swagger.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-221">Dozens of products and [commercial tools](https://swagger.io/commercial-tools/) and many [libraries and frameworks](https://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="8b5aa-222">Microsoft má vysoké úrovně produkty a nástroje, které automaticky využívají rozhraní API založená na Swaggeru, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="8b5aa-222">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

- <span data-ttu-id="8b5aa-223">[AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="8b5aa-223">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="8b5aa-224">Můžete automaticky vygenerovat třídy klienta rozhraní .NET pro volání Swagger.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-224">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="8b5aa-225">Tento nástroj se dá použít rozhraní příkazového řádku a také se integruje se sadou Visual Studio pro snadné použití prostřednictvím grafického uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-225">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

- <span data-ttu-id="8b5aa-226">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="8b5aa-226">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span></span> <span data-ttu-id="8b5aa-227">Můžete automaticky [použít a integrovat vaše rozhraní API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) do vysoké úrovně pracovního postupu Microsoft Flow, bez programování dovednosti nutné.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-227">You can automatically [use and integrate your API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

- <span data-ttu-id="8b5aa-228">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="8b5aa-228">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span></span> <span data-ttu-id="8b5aa-229">Můžete automaticky využití rozhraní API z [mobilní aplikace PowerApps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) vytvořených pomocí [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), bez programování znalosti vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-229">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), with no programming skills required.</span></span>

- <span data-ttu-id="8b5aa-230">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="8b5aa-230">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="8b5aa-231">Můžete automaticky [použít a integrovat vaše rozhraní API do Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), bez programování znalosti vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-231">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="8b5aa-232">**Možnost automaticky generovat dokumentaci k rozhraní API**.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-232">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="8b5aa-233">Při vytváření rozsáhlých rozhraní RESTful API, jako je například komplexních aplikací založených na mikroslužbách, potřebujete zpracovávat mnoho koncových bodů s různými datovými modely použité v datových částí požadavků a odpovědí.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-233">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="8b5aa-234">Máte správnou dokumentaci a s plnou Průzkumník rozhraní API, budete si ve Swaggeru, je klíčem k úspěchu rozhraní API a přijetí vývojáři.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-234">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="8b5aa-235">Metadata swagger společnosti je, co Microsoft Flow, PowerApps a Azure Logic Apps můžete pochopit, jak používat rozhraní API a připojit se k nim.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-235">Swagger's metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

<span data-ttu-id="8b5aa-236">Existuje několik možností, jak automatizovat generování metadat Swagger pro aplikace ASP.NET Core REST API ve formě stránek nápovědy, funkční rozhraní API, na základě <span class="underline">uživatelského rozhraní swagger</span>.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-236">There are several options to automate Swagger metadata generation for ASP.NET Core REST API applications, in the form of functional API help pages, based on <span class="underline">swagger-ui</span>.</span></span>

<span data-ttu-id="8b5aa-237">Pravděpodobně je nejlepší know [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) který se aktuálně používá v [eShopOnCntainers](https://github.com/dotnet-architecture/eShopOnContainers) a probereme některé podrobně v tomto průvodci, ale je také možnost použít [službou NSwag](https://github.com/RSuter/NSwag), Typescript a C, které lze generovat\# klienty rozhraní API, stejně jako C\# řadiče, od specifikace Swagger nebo OpenAPI a dokonce i tím, že kontroluje .dll, který obsahuje kontrolery, pomocí [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span><span class="sxs-lookup"><span data-stu-id="8b5aa-237">Probably the best know is [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) which is currently used in [eShopOnCntainers](https://github.com/dotnet-architecture/eShopOnContainers) and we'll cover in some detail in this guide but there's also the option to use [NSwag](https://github.com/RSuter/NSwag), that can generate Typescript and C\# API clients, as well as C\# controllers, from a Swagger or OpenAPI specification and even by scanning the .dll that contains the controllers, using [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="8b5aa-238">Jak automatizovat generování metadat Swagger rozhraní API pomocí balíčku Swashbuckle NuGet</span><span class="sxs-lookup"><span data-stu-id="8b5aa-238">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="8b5aa-239">Generování metadat Swagger ručně (v souboru JSON nebo YAML) může být pracné.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-239">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="8b5aa-240">Však můžete automatizovat zjišťování rozhraní API služeb ASP.NET Web API s použitím [balíček Swashbuckle NuGet](https://aka.ms/swashbuckledotnetcore) dynamicky generovat metadata Swagger rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-240">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](https://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="8b5aa-241">Swashbuckle vygeneruje automaticky metadata Swagger pro projekty ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-241">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="8b5aa-242">Podporuje projekty webového rozhraní API ASP.NET Core a tradiční rozhraní ASP.NET Web API a další charakter, například aplikaci API Azure, Azure mobilní aplikace mikroslužeb Azure Service Fabric, které jsou založeny na technologii ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-242">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="8b5aa-243">Také podporuje prostý webového rozhraní API nasazené v kontejnerech, stejně jako v referenční aplikace.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-243">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="8b5aa-244">Swashbuckle kombinuje Průzkumník rozhraní API a Swagger nebo [uživatelského rozhraní swagger](https://github.com/swagger-api/swagger-ui) k poskytování bohatých zjišťování a dokumentaci prostředí pro vaše zákazníky.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-244">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="8b5aa-245">Kromě motor generátor metadata Swagger Swashbuckle také obsahuje vložený verzi swaggeru – uživatelské rozhraní, které se bude automaticky poskytovat po instalaci Swashbuckle.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-245">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="8b5aa-246">To znamená, že můžou doplnit rozhraní API ve službě hezké zjišťování uživatelského rozhraní, což vývojářům umožňuje používat vaše rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-246">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="8b5aa-247">Vyžaduje velmi malé množství kódu a údržby, protože to není automaticky vygenerován, tak budete moct soustředit na vytváření rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-247">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="8b5aa-248">Výsledek pro Průzkumník rozhraní API bude vypadat podobně jako obrázek 6 – 8.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-248">The result for the API Explorer looks like Figure 6-8.</span></span>

![Swashbuckle vygenerované uživatelské rozhraní Swagger API dokumentace obsahuje všechny publikované akce.](./media/image9.png)

<span data-ttu-id="8b5aa-250">**Obrázek 6 – 8**.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-250">**Figure 6-8**.</span></span> <span data-ttu-id="8b5aa-251">Průzkumník rozhraní API Swashbuckle na základě metadat Swagger – aplikaci eShopOnContainers katalogu mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="8b5aa-251">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="8b5aa-252">Průzkumník rozhraní API není nejdůležitějším rozhodnutím.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-252">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="8b5aa-253">Jakmile máte webové rozhraní API, které můžete popsat sám sebe v metadatech Swaggeru, vaše rozhraní API je možné bez problémů ze Swaggeru nástrojů, včetně generátory kódu třídu proxy klienta, které můžete cílit na spoustě platforem.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-253">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="8b5aa-254">Příklad, jak bylo zmíněno [AutoRest](https://github.com/Azure/AutoRest) automaticky vygeneruje třídy klienta rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-254">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="8b5aa-255">Další nástroje, jako je, ale [swagger codegen](https://github.com/swagger-api/swagger-codegen) jsou také k dispozici, který umožňuje generování kódu rozhraní API klientské knihovny, server zástupné procedury a dokumentaci automaticky.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-255">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="8b5aa-256">V současné době se skládá z pěti interní balíčky NuGet v rámci základní meta balíček Swashbuckle [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) pro aplikace ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-256">Currently, Swashbuckle consists of five internal NuGet packages under the high-level meta- package [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) for ASP.NET Core applications.</span></span>

<span data-ttu-id="8b5aa-257">Po instalaci těchto balíčků NuGet v projektu webového rozhraní API, musíte nakonfigurovat Swagger ve třídě spuštění, stejně jako v následujícím kódu (zjednodušená):</span><span class="sxs-lookup"><span data-stu-id="8b5aa-257">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following code (simplified):</span></span>

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

<span data-ttu-id="8b5aa-258">Až to uděláte, můžete spustit aplikaci a přejděte následující koncové body JSON pro Swagger a uživatelského rozhraní, pomocí adres URL, jako jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="8b5aa-258">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```url
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/
```

<span data-ttu-id="8b5aa-259">Dříve jste viděli vygenerované uživatelské rozhraní vytvořené Swashbuckle pro adresu URL jako třeba http://\<your kořenové url \> /swagger.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-259">You previously saw the generated UI created by Swashbuckle for a URL like http://\<your-root-url\>/swagger.</span></span> <span data-ttu-id="8b5aa-260">Obrázek 6 – 9 také uvidíte jak otestovat všechny metody rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-260">In Figure 6-9 you can also see how you can test any API method.</span></span>

![Podrobnosti uživatelské rozhraní Swagger API ukazuje ukázkové odpovědi a lze použít k provedení skutečnému rozhraní API, což je skvělé pro zjišťování pro vývojáře.](./media/image10.png)

<span data-ttu-id="8b5aa-262">**Obrázek 6. až 9**.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-262">**Figure 6-9**.</span></span> <span data-ttu-id="8b5aa-263">Uživatelské rozhraní nástroje Swashbuckle testování/položky katalogu rozhraní API – metoda</span><span class="sxs-lookup"><span data-stu-id="8b5aa-263">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="8b5aa-264">Obrázek 6-10 ukazuje metadat JSON pro Swagger generují z mikroslužeb aplikaci eShopOnContainers (což je tyto nástroje používají pod) při žádosti o \<your kořenové url\>/swagger/v1/swagger.json pomocí [Postman](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="8b5aa-264">Figure 6-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request \<your-root-url\>/swagger/v1/swagger.json using [Postman](https://www.getpostman.com/).</span></span>

![Ukázka Postman uživatelské rozhraní zobrazení metadat JSON pro Swagger](./media/image11.png)

<span data-ttu-id="8b5aa-266">**Obrázek 6-10**.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-266">**Figure 6-10**.</span></span> <span data-ttu-id="8b5aa-267">Swagger JSON metadata</span><span class="sxs-lookup"><span data-stu-id="8b5aa-267">Swagger JSON metadata</span></span>

<span data-ttu-id="8b5aa-268">Je to jednoduché.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-268">It is that simple.</span></span> <span data-ttu-id="8b5aa-269">A protože není automaticky vygenerován, Swagger metadata se zvýší, když přidáte další funkce do vašeho rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8b5aa-269">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="8b5aa-270">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="8b5aa-270">Additional resources</span></span>

- <span data-ttu-id="8b5aa-271">**ASP.NET Web API stránky nápovědy k využívající Swagger** \\</span><span class="sxs-lookup"><span data-stu-id="8b5aa-271">**ASP.NET Web API Help Pages using Swagger** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- <span data-ttu-id="8b5aa-272">**Začínáme s Swashbuckle a ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="8b5aa-272">**Get started with Swashbuckle and ASP.NET Core** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.1\&tabs=visual-studio%2Cvisual-studio-xml*](https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle?view=aspnetcore-2.1\&tabs=visual-studio%2Cvisual-studio-xml)

- <span data-ttu-id="8b5aa-273">**Začínáme se službou NSwag a ASP.NET Core** \\</span><span class="sxs-lookup"><span data-stu-id="8b5aa-273">**Get started with NSwag and ASP.NET Core** \\</span></span>
  [*https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag?view=aspnetcore-2.1\&tabs=visual-studio%2Cvisual-studio-xml*](https://docs.microsoft.com/en-us/aspnet/core/tutorials/getting-started-with-nswag?view=aspnetcore-2.1\&tabs=visual-studio%2Cvisual-studio-xml)

>[!div class="step-by-step"]
><span data-ttu-id="8b5aa-274">[Předchozí](microservice-application-design.md)
>[další](multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="8b5aa-274">[Previous](microservice-application-design.md)
[Next](multi-container-applications-docker-compose.md)</span></span>