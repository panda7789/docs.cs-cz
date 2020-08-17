---
title: Vytvoření jednoduché mikroslužby CRUD řízené daty
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Pochopení vytvoření jednoduché mikroslužby CRUD (založené na datech) v rámci kontextu aplikace mikroslužeb.
ms.date: 08/14/2020
ms.openlocfilehash: 4d475ba42cb0f86b57b2467549635556cab1136d
ms.sourcegitcommit: 0100be20fcf23f61dab672deced70059ed71bb2e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/17/2020
ms.locfileid: "88267955"
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="b5a10-103">Vytvoření jednoduché mikroslužby CRUD řízené daty</span><span class="sxs-lookup"><span data-stu-id="b5a10-103">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="b5a10-104">Tato část popisuje, jak vytvořit jednoduchou mikroslužbu, která provádí operace vytvoření, čtení, aktualizace a odstranění (CRUD) ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="b5a10-104">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="b5a10-105">Návrh jednoduché mikroslužby CRUD</span><span class="sxs-lookup"><span data-stu-id="b5a10-105">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="b5a10-106">Z hlediska návrhu je tento typ kontejnerové mikroslužby velmi jednoduchý.</span><span class="sxs-lookup"><span data-stu-id="b5a10-106">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="b5a10-107">Je možné, že problém, který se má vyřešit, je jednoduchý nebo možná implementace je pouze důkaz konceptu.</span><span class="sxs-lookup"><span data-stu-id="b5a10-107">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![Diagram znázorňující jednoduchý vzor návrhu mikroslužeb CRUD](./media/data-driven-crud-microservice/internal-design-simple-crud-microservices.png)

<span data-ttu-id="b5a10-109">**Obrázek 6-4**.</span><span class="sxs-lookup"><span data-stu-id="b5a10-109">**Figure 6-4**.</span></span> <span data-ttu-id="b5a10-110">Interní návrh jednoduchých mikroslužeb CRUD</span><span class="sxs-lookup"><span data-stu-id="b5a10-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="b5a10-111">Příkladem tohoto druhu jednoduchých datových jednotek je služba cloudová služba z ukázkové aplikace eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="b5a10-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="b5a10-112">Tento typ služby implementuje všechny funkce v jednom ASP.NET Core projektu webového rozhraní API, který obsahuje třídy pro svůj datový model, jeho obchodní logiku a kód pro přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="b5a10-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="b5a10-113">Ukládá také data v databázi běžící v SQL Server (jako jiný kontejner pro účely vývoje a testování), ale může to být také jakýkoli pravidelný SQL Server Hostitel, jak je znázorněno na obrázku 6-5.</span><span class="sxs-lookup"><span data-stu-id="b5a10-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 6-5.</span></span>

![Diagram znázorňující datově řízený kontejner mikroslužeb nebo CRUD.](./media/data-driven-crud-microservice/simple-data-driven-crud-microservice.png)

<span data-ttu-id="b5a10-115">**Obrázek 6-5**.</span><span class="sxs-lookup"><span data-stu-id="b5a10-115">**Figure 6-5**.</span></span> <span data-ttu-id="b5a10-116">Jednoduchý návrh mikroslužeb založený na datech/CRUD</span><span class="sxs-lookup"><span data-stu-id="b5a10-116">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="b5a10-117">Předchozí diagram znázorňuje mikroslužbu logického katalogu, která obsahuje svou databázi katalogu, která může být nebo ne ve stejném hostiteli Docker.</span><span class="sxs-lookup"><span data-stu-id="b5a10-117">The previous diagram shows the logical Catalog microservice, that includes its Catalog database, which can be or not in the same Docker host.</span></span> <span data-ttu-id="b5a10-118">Databáze ve stejném hostiteli Docker může být vhodná pro vývoj, ale ne pro produkční prostředí.</span><span class="sxs-lookup"><span data-stu-id="b5a10-118">Having the database in the same Docker host might be good for development, but not for production.</span></span> <span data-ttu-id="b5a10-119">Při vývoji tohoto typu služby potřebujete jenom [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) a rozhraní API pro přístup k datům nebo ORM, jako je [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span><span class="sxs-lookup"><span data-stu-id="b5a10-119">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="b5a10-120">Metadata [Swagger](https://swagger.io/) můžete také automaticky vygenerovat prostřednictvím [swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) a zadat popis toho, co vaše služba nabízí, jak je vysvětleno v další části.</span><span class="sxs-lookup"><span data-stu-id="b5a10-120">You could also generate [Swagger](https://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="b5a10-121">Všimněte si, že provoz databázového serveru, jako je SQL Server v kontejneru Docker, je skvělý pro vývojová prostředí, protože můžete mít všechny závislosti v provozu, aniž byste museli zřídit databázi v cloudu nebo místně.</span><span class="sxs-lookup"><span data-stu-id="b5a10-121">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="b5a10-122">To je velmi užitečné při spouštění integračních testů.</span><span class="sxs-lookup"><span data-stu-id="b5a10-122">This is very convenient when running integration tests.</span></span> <span data-ttu-id="b5a10-123">V produkčních prostředích se ale nedoporučuje používat databázový server v kontejneru, protože pro tento přístup obvykle nezískáte vysokou dostupnost.</span><span class="sxs-lookup"><span data-stu-id="b5a10-123">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="b5a10-124">V produkčním prostředí v Azure se doporučuje používat službu Azure SQL DB nebo jakoukoli jinou databázovou technologii, která může poskytovat vysokou dostupnost a vysokou škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="b5a10-124">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="b5a10-125">Například pro NoSQL přístup můžete zvolit CosmosDB.</span><span class="sxs-lookup"><span data-stu-id="b5a10-125">For example, for a NoSQL approach, you might choose CosmosDB.</span></span>

<span data-ttu-id="b5a10-126">Nakonec můžete úpravou souborů metadat souboru Dockerfile a Docker-Compose. yml nakonfigurovat, jak se vytvoří obrázek tohoto kontejneru – jakou základní image bude používat, a také nastavení návrhu, jako jsou interní a externí názvy a porty TCP.</span><span class="sxs-lookup"><span data-stu-id="b5a10-126">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span>

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="b5a10-127">Implementace jednoduché mikroslužby CRUD pomocí ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="b5a10-127">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="b5a10-128">Chcete-li implementovat jednoduchou mikroslužbu CRUD pomocí .NET Core a sady Visual Studio, Začněte vytvořením jednoduchého projektu ASP.NET Core webového rozhraní API (běžícího na rozhraní .NET Core, který je možné spustit na hostiteli Docker Linux), jak je znázorněno na obrázku 6-6.</span><span class="sxs-lookup"><span data-stu-id="b5a10-128">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 6-6.</span></span>

![Snímek obrazovky s vizuálním studia se zobrazením nastavení projektu.](./media/data-driven-crud-microservice/create-asp-net-core-web-api-project.png)

<span data-ttu-id="b5a10-130">**Obrázek 6-6**.</span><span class="sxs-lookup"><span data-stu-id="b5a10-130">**Figure 6-6**.</span></span> <span data-ttu-id="b5a10-131">Vytvoření projektu webového rozhraní API ASP.NET Core v aplikaci Visual Studio 2019</span><span class="sxs-lookup"><span data-stu-id="b5a10-131">Creating an ASP.NET Core Web API project in Visual Studio 2019</span></span>

<span data-ttu-id="b5a10-132">Pokud chcete vytvořit ASP.NET Core projekt webového rozhraní API, vyberte nejdřív ASP.NET Core webovou aplikaci a pak vyberte typ rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b5a10-132">To create an ASP.NET Core Web API Project, first select an ASP.NET Core Web Application and then select the API type.</span></span> <span data-ttu-id="b5a10-133">Po vytvoření projektu můžete své řadiče MVC implementovat stejně jako v jakémkoli jiném projektu webového rozhraní API, a to pomocí rozhraní Entity Framework API nebo jiného rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b5a10-133">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="b5a10-134">V novém projektu webového rozhraní API vidíte, že jediná závislost, kterou máte v této mikroslužbě, je ASP.NET Core sama.</span><span class="sxs-lookup"><span data-stu-id="b5a10-134">In a new Web API project, you can see that the only dependency you have in that microservice is on ASP.NET Core itself.</span></span> <span data-ttu-id="b5a10-135">Interně v rámci závislosti *Microsoft. AspNetCore. All* odkazuje na Entity Framework a spoustu dalších balíčků NuGet pro .NET Core, jak je znázorněno na obrázku 6-7.</span><span class="sxs-lookup"><span data-stu-id="b5a10-135">Internally, within the *Microsoft.AspNetCore.All* dependency, it is referencing Entity Framework and many other .NET Core NuGet packages, as shown in Figure 6-7.</span></span>

![Snímek obrazovky sady Visual Studio zobrazující závislosti NuGet Catalog. API](./media/data-driven-crud-microservice/simple-crud-web-api-microservice-dependencies.png)

<span data-ttu-id="b5a10-137">**Obrázek 6-7**.</span><span class="sxs-lookup"><span data-stu-id="b5a10-137">**Figure 6-7**.</span></span> <span data-ttu-id="b5a10-138">Závislosti v jednoduché mikroslužbě webového rozhraní API CRUD</span><span class="sxs-lookup"><span data-stu-id="b5a10-138">Dependencies in a simple CRUD Web API microservice</span></span>

<span data-ttu-id="b5a10-139">Projekt rozhraní API obsahuje odkazy na balíček NuGet Microsoft. AspNetCore. app, který obsahuje odkazy na všechny podstatné balíčky.</span><span class="sxs-lookup"><span data-stu-id="b5a10-139">The API project includes references to Microsoft.AspNetCore.App NuGet package, that includes references to all essential packages.</span></span> <span data-ttu-id="b5a10-140">Může to zahrnovat i některé další balíčky.</span><span class="sxs-lookup"><span data-stu-id="b5a10-140">It could include some other packages as well.</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="b5a10-141">Implementace služeb webového rozhraní API CRUD pomocí Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="b5a10-141">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="b5a10-142">Jádro Entity Framework (EF) je odlehčená, rozšiřitelná a více platforem oblíbené technologie Entity Framework data pro přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="b5a10-142">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="b5a10-143">EF Core je objektově-relační Mapovač (ORM), který umožňuje vývojářům rozhraní .NET pracovat s databází pomocí objektů .NET.</span><span class="sxs-lookup"><span data-stu-id="b5a10-143">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="b5a10-144">Mikroslužba katalogu používá EF a poskytovatele SQL Server, protože jeho databáze je spuštěná v kontejneru s SQL Server pro Image Docker pro Linux.</span><span class="sxs-lookup"><span data-stu-id="b5a10-144">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="b5a10-145">Databázi ale můžete nasadit do libovolného SQL Server, jako je Windows v místním prostředí nebo Azure SQL DB.</span><span class="sxs-lookup"><span data-stu-id="b5a10-145">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="b5a10-146">Jedinou věcí, kterou byste mohli změnit, je připojovací řetězec v mikroslužbě ASP.NET webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b5a10-146">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="the-data-model"></a><span data-ttu-id="b5a10-147">Datový model</span><span class="sxs-lookup"><span data-stu-id="b5a10-147">The data model</span></span>

<span data-ttu-id="b5a10-148">Pomocí EF Core se přístup k datům provádí pomocí modelu.</span><span class="sxs-lookup"><span data-stu-id="b5a10-148">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="b5a10-149">Model se skládá z tříd entit (doménového modelu) a odvozeného kontextu (DbContext), který představuje relaci s databází, a umožňuje dotazování a ukládání dat.</span><span class="sxs-lookup"><span data-stu-id="b5a10-149">A model is made up of (domain model) entity classes and a derived context (DbContext) that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="b5a10-150">Můžete vygenerovat model z existující databáze, ručně nastavovat model tak, aby odpovídal vaší databázi, nebo pomocí metody migrace EF vytvořit databázi z modelu pomocí přístupu k prvnímu kódu (který usnadňuje vývoj databáze ve chvíli, kdy se model mění v průběhu času).</span><span class="sxs-lookup"><span data-stu-id="b5a10-150">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations technique to create a database from your model, using the code-first approach (that makes it easy to evolve the database as your model changes over time).</span></span> <span data-ttu-id="b5a10-151">Pro mikroslužbu katalogu byl použit poslední přístup.</span><span class="sxs-lookup"><span data-stu-id="b5a10-151">For the catalog microservice, the last approach has been used.</span></span> <span data-ttu-id="b5a10-152">Příklad třídy entity CatalogItem lze vidět v následujícím příkladu kódu, což je jednoduchá Třída entity Object typu CLR ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)).</span><span class="sxs-lookup"><span data-stu-id="b5a10-152">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

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

<span data-ttu-id="b5a10-153">Budete také potřebovat DbContext, který představuje relaci s databází.</span><span class="sxs-lookup"><span data-stu-id="b5a10-153">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="b5a10-154">Pro mikroslužbu katalogu je třída CatalogContext odvozená od základní třídy DbContext, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b5a10-154">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

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

<span data-ttu-id="b5a10-155">Můžete mít další `DbContext` implementace.</span><span class="sxs-lookup"><span data-stu-id="b5a10-155">You can have additional `DbContext` implementations.</span></span> <span data-ttu-id="b5a10-156">Například v ukázkovém katalogu. mikroslužba rozhraní API má druhý název, kde se `DbContext` při `CatalogContextSeed` prvním pokusu o přístup k databázi automaticky naplní ukázková data.</span><span class="sxs-lookup"><span data-stu-id="b5a10-156">For example, in the sample Catalog.API microservice, there's a second `DbContext` named `CatalogContextSeed` where it automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="b5a10-157">Tato metoda je užitečná pro ukázková data a také pro scénáře automatizovaného testování.</span><span class="sxs-lookup"><span data-stu-id="b5a10-157">This method is useful for demo data and for automated testing scenarios, as well.</span></span>

<span data-ttu-id="b5a10-158">V nástroji `DbContext` použijete `OnModelCreating` metodu k přizpůsobení mapování entit objektu/databáze a dalších [bodů rozšiřitelnosti EF](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span><span class="sxs-lookup"><span data-stu-id="b5a10-158">Within the `DbContext`, you use the `OnModelCreating` method to customize object/database entity mappings and other [EF extensibility points](https://devblogs.microsoft.com/dotnet/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="b5a10-159">Dotazování dat z řadičů webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b5a10-159">Querying data from Web API controllers</span></span>

<span data-ttu-id="b5a10-160">Instance tříd vaší entity se obvykle načítají z databáze pomocí jazyka LINQ (Language Integrated Query), jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b5a10-160">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

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

##### <a name="saving-data"></a><span data-ttu-id="b5a10-161">Ukládání dat</span><span class="sxs-lookup"><span data-stu-id="b5a10-161">Saving data</span></span>

<span data-ttu-id="b5a10-162">Data se vytvářejí, odstraňují a upravují v databázi s použitím instancí tříd vaší entity.</span><span class="sxs-lookup"><span data-stu-id="b5a10-162">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="b5a10-163">Do vašich řadičů webového rozhraní API můžete přidat kód, například následující pevně zakódovaný příklad (data v tomto případě).</span><span class="sxs-lookup"><span data-stu-id="b5a10-163">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
                                     Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="b5a10-164">Vkládání závislostí v ASP.NET Core a v řadičích webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b5a10-164">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="b5a10-165">V ASP.NET Core můžete použít vkládání závislostí (DI) z pole.</span><span class="sxs-lookup"><span data-stu-id="b5a10-165">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="b5a10-166">Nemusíte nastavovat kontejner IoC (inverze) třetí strany, ale pokud chcete, můžete svůj preferovaný kontejner IoC připojit do infrastruktury ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b5a10-166">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="b5a10-167">V takovém případě to znamená, že můžete přímo vložit požadované DBContext EF nebo další úložiště prostřednictvím konstruktoru kontroleru.</span><span class="sxs-lookup"><span data-stu-id="b5a10-167">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span>

<span data-ttu-id="b5a10-168">Ve `CatalogController` třídě zmíněné výše `CatalogContext` je typ (který dědí z `DbContext` ) vložený spolu s jinými požadovanými objekty v `CatalogController()` konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="b5a10-168">In the `CatalogController` class mentioned earlier, `CatalogContext` (which inherits from `DbContext`) type is injected along with the other required objects in the `CatalogController()` constructor.</span></span>

<span data-ttu-id="b5a10-169">Důležitou konfigurací, která se nastavuje v projektu webového rozhraní API, je registrace třídy DbContext do kontejneru IoC služby.</span><span class="sxs-lookup"><span data-stu-id="b5a10-169">An important configuration to set up in the Web API project is the DbContext class registration into the service's IoC container.</span></span> <span data-ttu-id="b5a10-170">To se obvykle provádí ve `Startup` třídě voláním `services.AddDbContext<CatalogContext>()` metody uvnitř `ConfigureServices()` metody, jak je znázorněno v následujícím **zjednodušeném** příkladu:</span><span class="sxs-lookup"><span data-stu-id="b5a10-170">You typically do so in the `Startup` class by calling the `services.AddDbContext<CatalogContext>()` method inside the `ConfigureServices()` method, as shown in the following **simplified** example:</span></span>

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

### <a name="additional-resources"></a><span data-ttu-id="b5a10-171">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="b5a10-171">Additional resources</span></span>

- <span data-ttu-id="b5a10-172">**Dotazování na data** </span><span class="sxs-lookup"><span data-stu-id="b5a10-172">**Querying Data** </span></span>\
  [https://docs.microsoft.com/ef/core/querying/index](/ef/core/querying/index)

- <span data-ttu-id="b5a10-173">**Ukládání dat** </span><span class="sxs-lookup"><span data-stu-id="b5a10-173">**Saving Data** </span></span>\
  [https://docs.microsoft.com/ef/core/saving/index](/ef/core/saving/index)

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="b5a10-174">Připojovací řetězec databáze a proměnné prostředí používané kontejnery Docker</span><span class="sxs-lookup"><span data-stu-id="b5a10-174">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="b5a10-175">Můžete použít nastavení ASP.NET Core a do settings.jssouboru přidat vlastnost ConnectionString, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="b5a10-175">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

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

<span data-ttu-id="b5a10-176">settings.jsv souboru může mít výchozí hodnoty pro vlastnost ConnectionString nebo pro jakoukoliv jinou vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b5a10-176">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="b5a10-177">Tyto vlastnosti však budou přepsány hodnotami proměnných prostředí, které zadáte v souboru Docker-Compose. override. yml při použití Docker.</span><span class="sxs-lookup"><span data-stu-id="b5a10-177">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file, when using Docker.</span></span>

<span data-ttu-id="b5a10-178">Z vašich souborů Docker-Compose. yml nebo Docker-Compose. yml můžete inicializovat tyto proměnné prostředí tak, aby je Docker nastavil jako proměnné prostředí operačního systému, jak je znázorněno v následujícím souboru Docker-Compose. override. yml (připojovací řetězec a další řádky se v tomto příkladu zabalí, ale nebalí se do vašeho vlastního souboru).</span><span class="sxs-lookup"><span data-stu-id="b5a10-178">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

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

<span data-ttu-id="b5a10-179">Soubory Docker-Compose. yml na úrovni řešení nejsou pružnější než konfigurační soubory na úrovni projektu nebo mikroslužby, ale také bezpečnější, pokud přepíšete proměnné prostředí deklarované v souborech Docker-skládání s hodnotami nastavenými z vašich nástrojů pro nasazení, jako například Azure DevOps Services z úloh nasazení Docker.</span><span class="sxs-lookup"><span data-stu-id="b5a10-179">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure if you override the environment variables declared at the docker-compose files with values set from your deployment tools, like from Azure DevOps Services Docker deployment tasks.</span></span>

<span data-ttu-id="b5a10-180">Nakonec můžete získat tuto hodnotu z kódu pomocí konfigurace \[ "ConnectionString" \] , jak je znázorněno v metodě ConfigureServices v předchozím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="b5a10-180">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="b5a10-181">V produkčních prostředích však můžete chtít prozkoumat další způsoby ukládání tajných kódů, jako jsou připojovací řetězce.</span><span class="sxs-lookup"><span data-stu-id="b5a10-181">However, for production environments, you might want to explore additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="b5a10-182">Skvělý způsob správy tajných klíčů aplikací používá [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span><span class="sxs-lookup"><span data-stu-id="b5a10-182">An excellent way to manage application secrets is using [Azure Key Vault](https://azure.microsoft.com/services/key-vault/).</span></span>

<span data-ttu-id="b5a10-183">Azure Key Vault pomáhá ukládat a chránit kryptografické klíče a tajné klíče používané vašimi cloudových aplikacemi a službami.</span><span class="sxs-lookup"><span data-stu-id="b5a10-183">Azure Key Vault helps to store and safeguard cryptographic keys and secrets used by your cloud applications and services.</span></span> <span data-ttu-id="b5a10-184">Tajný kód je cokoli, co chcete zachovat striktní řízení, jako jsou klíče rozhraní API, připojovací řetězce, hesla atd. a striktní řízení zahrnuje protokolování použití, nastavení vypršení platnosti, Správa přístupu, *mimo jiné*.</span><span class="sxs-lookup"><span data-stu-id="b5a10-184">A secret is anything you want to keep strict control of, like API keys, connection strings, passwords, etc. and strict control includes usage logging, setting expiration, managing access, *among others*.</span></span>

<span data-ttu-id="b5a10-185">Azure Key Vault umožňuje velmi detailní úroveň řízení používání tajných klíčů aplikací, aniž by bylo nutné, aby ji znali kdokoli.</span><span class="sxs-lookup"><span data-stu-id="b5a10-185">Azure Key Vault allows a very detailed control level of the application secrets usage without the need to let anyone know them.</span></span> <span data-ttu-id="b5a10-186">Tajné kódy je dokonce možné otočit za účelem zvýšení zabezpečení, aniž by došlo k narušení vývoje nebo provozu.</span><span class="sxs-lookup"><span data-stu-id="b5a10-186">The secrets can even be rotated for enhanced security without disrupting development or operations.</span></span>

<span data-ttu-id="b5a10-187">Aplikace musí být zaregistrované ve službě Active Directory organizace, aby mohli používat Key Vault.</span><span class="sxs-lookup"><span data-stu-id="b5a10-187">Applications have to be registered in the organization's Active Directory, so they can use the Key Vault.</span></span>

<span data-ttu-id="b5a10-188">Další podrobnosti najdete v *dokumentaci k konceptům Key Vault* .</span><span class="sxs-lookup"><span data-stu-id="b5a10-188">You can check the *Key Vault Concepts documentation* for more details.</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="b5a10-189">Implementace správy verzí ve webových rozhraních API ASP.NET</span><span class="sxs-lookup"><span data-stu-id="b5a10-189">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="b5a10-190">V rámci změny obchodních požadavků se můžou přidat nové kolekce prostředků, můžou se změnit vztahy mezi prostředky a struktura dat v prostředcích se může změnit.</span><span class="sxs-lookup"><span data-stu-id="b5a10-190">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="b5a10-191">Aktualizace webového rozhraní API tak, aby zpracovávala nové požadavky, je poměrně přímočarý proces, ale je potřeba vzít v úvahu účinky, které tyto změny budou mít na klientských aplikacích, které spotřebovávají webové rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b5a10-191">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="b5a10-192">I když vývojář, který navrhuje a implementuje webové rozhraní API, má plnou kontrolu nad tímto rozhraním API, vývojář nemá stejnou úroveň kontroly nad klientskými aplikacemi, které můžou být sestavené pomocí vzdáleného provozování organizací třetích stran.</span><span class="sxs-lookup"><span data-stu-id="b5a10-192">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third-party organizations operating remotely.</span></span>

<span data-ttu-id="b5a10-193">Správa verzí umožňuje webovému rozhraní API označovat funkce a prostředky, které zveřejňuje.</span><span class="sxs-lookup"><span data-stu-id="b5a10-193">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="b5a10-194">Klientská aplikace pak může odeslat požadavky na konkrétní verzi funkce nebo prostředku.</span><span class="sxs-lookup"><span data-stu-id="b5a10-194">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="b5a10-195">Existuje několik přístupů k implementaci správy verzí:</span><span class="sxs-lookup"><span data-stu-id="b5a10-195">There are several approaches to implement versioning:</span></span>

- <span data-ttu-id="b5a10-196">Správa verzí pomocí identifikátoru URI</span><span class="sxs-lookup"><span data-stu-id="b5a10-196">URI versioning</span></span>

- <span data-ttu-id="b5a10-197">Správa verzí pomocí řetězce dotazu</span><span class="sxs-lookup"><span data-stu-id="b5a10-197">Query string versioning</span></span>

- <span data-ttu-id="b5a10-198">Správa verzí pomocí hlavičky</span><span class="sxs-lookup"><span data-stu-id="b5a10-198">Header versioning</span></span>

<span data-ttu-id="b5a10-199">Způsob implementace řetězce dotazu a verze identifikátoru URI je nejjednodušší.</span><span class="sxs-lookup"><span data-stu-id="b5a10-199">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="b5a10-200">Správa verzí hlaviček je dobrým přístupem.</span><span class="sxs-lookup"><span data-stu-id="b5a10-200">Header versioning is a good approach.</span></span> <span data-ttu-id="b5a10-201">Nicméně verze hlaviček není tak explicitní a přímá jako verze identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="b5a10-201">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="b5a10-202">Vzhledem k tomu, že správa verzí adres URL je nejjednodušší a nejpřesnější, používá ukázková aplikace eShopOnContainers správu verzí pomocí identifikátoru URI.</span><span class="sxs-lookup"><span data-stu-id="b5a10-202">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="b5a10-203">S verzí identifikátoru URI, jako v ukázkové aplikaci eShopOnContainers, pokaždé, když upravíte webové rozhraní API nebo změníte schéma prostředků, přidáte číslo verze k identifikátoru URI pro každý prostředek.</span><span class="sxs-lookup"><span data-stu-id="b5a10-203">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="b5a10-204">Existující identifikátory URI by měly nadále fungovat jako dřív a vracet prostředky, které odpovídají schématu odpovídajícímu požadované verzi.</span><span class="sxs-lookup"><span data-stu-id="b5a10-204">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="b5a10-205">Jak je znázorněno v následujícím příkladu kódu, verze lze nastavit pomocí atributu směrování v rámci kontroleru webového rozhraní API, který v tomto případě provede explicitní verzi v identifikátoru URI (V1).</span><span class="sxs-lookup"><span data-stu-id="b5a10-205">As shown in the following code example, the version can be set by using the Route attribute in the Web API controller, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="b5a10-206">Tento mechanismus správy verzí je jednoduchý a závisí na serveru, který požadavek směruje na příslušný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="b5a10-206">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="b5a10-207">Pro výkonnější správu verzí a nejlepší způsob používání REST je však vhodné použít médium a implementovat [HATEOAS (hypertextový odkaz jako modul stavu aplikace)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span><span class="sxs-lookup"><span data-stu-id="b5a10-207">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#use-hateoas-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b5a10-208">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="b5a10-208">Additional resources</span></span>

- <span data-ttu-id="b5a10-209">**Scott Hanselman Jednodušší ASP.NET Core RESTful webového rozhraní API pro správu** </span><span class="sxs-lookup"><span data-stu-id="b5a10-209">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy** </span></span>\
  <https://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx>

- <span data-ttu-id="b5a10-210">**Správa verzí webového rozhraní API RESTful** </span><span class="sxs-lookup"><span data-stu-id="b5a10-210">**Versioning a RESTful web API** </span></span>\
  <https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api>

- <span data-ttu-id="b5a10-211">**Roy pole. Správa verzí, multimédií a REST** </span><span class="sxs-lookup"><span data-stu-id="b5a10-211">**Roy Fielding. Versioning, Hypermedia, and REST** </span></span>\
  <https://www.infoq.com/articles/roy-fielding-on-versioning>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="b5a10-212">Generování metadat popisu Swagger z ASP.NET Core webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="b5a10-212">Generating Swagger description metadata from your ASP.NET Core Web API</span></span>

<span data-ttu-id="b5a10-213">[Swagger](https://swagger.io/) je běžně používaná platforma open source, kterou poskytuje velký ekosystém nástrojů, který vám pomůže navrhovat, sestavovat, zdokumentovat a spotřebovávat rozhraní RESTful API.</span><span class="sxs-lookup"><span data-stu-id="b5a10-213">[Swagger](https://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="b5a10-214">Stane se standardem pro doménu metadat popisu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b5a10-214">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="b5a10-215">Měli byste zahrnout metadata popisu Swagger s jakýmkoli typem mikroslužeb, buď mikroslužby řízené daty, nebo pokročilejší mikroslužby založené na doméně (jak je vysvětleno v následující části).</span><span class="sxs-lookup"><span data-stu-id="b5a10-215">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in the following section).</span></span>

<span data-ttu-id="b5a10-216">Srdcem Swagger je specifikace Swagger, což je metadata popisu rozhraní API v souboru JSON nebo YAML.</span><span class="sxs-lookup"><span data-stu-id="b5a10-216">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="b5a10-217">Specifikace vytvoří pro vaše rozhraní API kontrakt RESTful, který podrobně popisuje všechny jeho prostředky a operace v uživatelsky čitelném formátu pro snadné vývoj, zjišťování a integraci.</span><span class="sxs-lookup"><span data-stu-id="b5a10-217">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="b5a10-218">Specifikace je základem pro specifikaci OpenAPI (OAS) a je vyvíjena v otevřené, transparentní a spolupracovní komunitě pro standardizaci způsobu, jakým jsou definována rozhraní RESTful.</span><span class="sxs-lookup"><span data-stu-id="b5a10-218">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="b5a10-219">Specifikace definuje strukturu, jak může být služba zjištěná a jak se její schopnosti považují.</span><span class="sxs-lookup"><span data-stu-id="b5a10-219">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="b5a10-220">Další informace, včetně webového editoru a příkladů specifikací Swagger od společností, jako je Spotify, Uber, časová rezerva a Microsoft, najdete v webu Swagger ( <https://swagger.io> ).</span><span class="sxs-lookup"><span data-stu-id="b5a10-220">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<https://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="b5a10-221">Proč používat Swagger?</span><span class="sxs-lookup"><span data-stu-id="b5a10-221">Why use Swagger?</span></span>

<span data-ttu-id="b5a10-222">Hlavními důvody pro vygenerování metadat Swagger pro vaše rozhraní API jsou následující.</span><span class="sxs-lookup"><span data-stu-id="b5a10-222">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="b5a10-223">**Schopnost dalších produktů automaticky využívat a integrovat vaše rozhraní API**.</span><span class="sxs-lookup"><span data-stu-id="b5a10-223">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="b5a10-224">Spousta produktů a [komerčních nástrojů](https://swagger.io/commercial-tools/) a mnoho [knihoven a platforem](https://swagger.io/open-source-integrations/) podporují Swagger.</span><span class="sxs-lookup"><span data-stu-id="b5a10-224">Dozens of products and [commercial tools](https://swagger.io/commercial-tools/) and many [libraries and frameworks](https://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="b5a10-225">Microsoft má produkty vysoké úrovně a nástroje, které mohou automaticky využívat rozhraní API založená na Swagger, například následující:</span><span class="sxs-lookup"><span data-stu-id="b5a10-225">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

- <span data-ttu-id="b5a10-226">[AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="b5a10-226">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="b5a10-227">Můžete automaticky vygenerovat klientské třídy .NET pro volání Swagger.</span><span class="sxs-lookup"><span data-stu-id="b5a10-227">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="b5a10-228">Tento nástroj lze použít z CLI a také se integruje se sadou Visual Studio pro snadné použití prostřednictvím grafického uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="b5a10-228">This tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

- <span data-ttu-id="b5a10-229">[Microsoft Flow](https://flow.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="b5a10-229">[Microsoft Flow](https://flow.microsoft.com/).</span></span> <span data-ttu-id="b5a10-230">[Své rozhraní API můžete automaticky používat a integrovat](https://flow.microsoft.com/blog/integrating-custom-api/) do Microsoft Flowho pracovního postupu na nejvyšší úrovni, aniž by se vyžadovaly žádné znalosti programování.</span><span class="sxs-lookup"><span data-stu-id="b5a10-230">You can automatically [use and integrate your API](https://flow.microsoft.com/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

- <span data-ttu-id="b5a10-231">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span><span class="sxs-lookup"><span data-stu-id="b5a10-231">[Microsoft PowerApps](https://powerapps.microsoft.com/).</span></span> <span data-ttu-id="b5a10-232">Své rozhraní API můžete automaticky využít z [PowerAppsch mobilních aplikací](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) vytvořených pomocí [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), aniž by se vyžadovaly žádné znalosti programování.</span><span class="sxs-lookup"><span data-stu-id="b5a10-232">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/build-powerapps/), with no programming skills required.</span></span>

- <span data-ttu-id="b5a10-233">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="b5a10-233">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="b5a10-234">[Své rozhraní API můžete automaticky používat a integrovat do aplikace Azure App Service Logic](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), bez nutnosti programování.</span><span class="sxs-lookup"><span data-stu-id="b5a10-234">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="b5a10-235">**Schopnost automaticky generovat dokumentaci k rozhraní API**.</span><span class="sxs-lookup"><span data-stu-id="b5a10-235">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="b5a10-236">Když vytváříte rozsáhlá rozhraní API RESTful, jako jsou komplexní aplikace založené na mikroslužbách, je potřeba zvládnout mnoho koncových bodů s různými datovými modely použitými v datových vytíženích žádosti a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="b5a10-236">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="b5a10-237">V případě, že máte správnou dokumentaci a máte plnou dokumentaci k rozhraní API, je klíč pro úspěch vašeho rozhraní API a jejich přijetí vývojáři.</span><span class="sxs-lookup"><span data-stu-id="b5a10-237">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="b5a10-238">Metadata Swagger je to, co Microsoft Flow, PowerApps a Azure Logic Apps využívají k pochopení, jak používat rozhraní API a připojení k nim.</span><span class="sxs-lookup"><span data-stu-id="b5a10-238">Swagger's metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

<span data-ttu-id="b5a10-239">K dispozici je několik možností pro automatizaci generování metadat Swagger pro aplikace ASP.NET Core REST API, ve formě stránek s podporou funkčního rozhraní API na základě *uživatelského rozhraní Swagger*.</span><span class="sxs-lookup"><span data-stu-id="b5a10-239">There are several options to automate Swagger metadata generation for ASP.NET Core REST API applications, in the form of functional API help pages, based on *swagger-ui*.</span></span>

<span data-ttu-id="b5a10-240">Je pravděpodobné, že nejlepší je [swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) , který se aktuálně používá v [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) , a v tomto průvodci se podrobněji podíváme, ale je k dispozici také možnost použít [NSwag](https://github.com/RSuter/NSwag), která může generovat klienty TypeScript a C API a také \# řadiče jazyka c \# , ze sady Swagger nebo specifikace openapi, a to i kontrolou knihovny DLL, která obsahuje řadiče, pomocí [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span><span class="sxs-lookup"><span data-stu-id="b5a10-240">Probably the best know is [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) which is currently used in [eShopOnContainers](https://github.com/dotnet-architecture/eShopOnContainers) and we'll cover in some detail in this guide but there's also the option to use [NSwag](https://github.com/RSuter/NSwag), which can generate Typescript and C\# API clients, as well as C\# controllers, from a Swagger or OpenAPI specification and even by scanning the .dll that contains the controllers, using [NSwagStudio](https://github.com/RSuter/NSwag/wiki/NSwagStudio).</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="b5a10-241">Automatizace generování metadat Swagger API pomocí balíčku NuGet swashbuckle</span><span class="sxs-lookup"><span data-stu-id="b5a10-241">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="b5a10-242">Ruční generování metadat Swagger (v souboru JSON nebo YAML) může být zdlouhavá práce.</span><span class="sxs-lookup"><span data-stu-id="b5a10-242">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="b5a10-243">Rozpoznávání rozhraní API služeb webového rozhraní API ASP.NET ale můžete automatizovat pomocí [balíčku NuGet swashbuckle](https://aka.ms/swashbuckledotnetcore) a dynamicky generovat metadata rozhraní Swagger API.</span><span class="sxs-lookup"><span data-stu-id="b5a10-243">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](https://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="b5a10-244">Swashbuckle automaticky generuje metadata Swagger pro vaše projekty webového rozhraní API pro ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b5a10-244">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="b5a10-245">Podporuje ASP.NET Core projekty webového rozhraní API a tradiční webové rozhraní API ASP.NET a jakékoli jiné charaktery, jako je například aplikace API Azure, mobilní aplikace Azure, Azure Service Fabric mikroslužby založené na ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="b5a10-245">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="b5a10-246">Podporuje také jednoduché webové rozhraní API nasazené na kontejnerech, jako v případě referenční aplikace.</span><span class="sxs-lookup"><span data-stu-id="b5a10-246">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="b5a10-247">Swashbuckle kombinuje rozhraní API Explorer a Swagger nebo [Swagger – uživatelské rozhraní](https://github.com/swagger-api/swagger-ui) pro poskytování bohatých funkcí zjišťování a dokumentace pro vaše příjemce rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b5a10-247">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="b5a10-248">Kromě svého modulu generátoru metadat Swagger swashbuckle obsahuje také vloženou verzi Swagger – uživatelské rozhraní, které bude automaticky fungovat po instalaci swashbuckle.</span><span class="sxs-lookup"><span data-stu-id="b5a10-248">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="b5a10-249">To znamená, že můžete své rozhraní API doplnit o uživatelské rozhraní s dobrým zjišťováním, které vývojářům umožní používat vaše rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b5a10-249">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="b5a10-250">Vyžaduje velmi malý objem kódu a údržby, protože se vygeneruje automaticky, takže se můžete soustředit na vytváření rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b5a10-250">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="b5a10-251">Výsledek pro Průzkumník rozhraní API vypadá jako obrázek 6-8.</span><span class="sxs-lookup"><span data-stu-id="b5a10-251">The result for the API Explorer looks like Figure 6-8.</span></span>

![Snímek obrazovky s rozhraním API Swagger, které zobrazuje rozhraní eShopOContainers API](./media/data-driven-crud-microservice/swagger-metadata-eshoponcontainers-catalog-microservice.png)

<span data-ttu-id="b5a10-253">**Obrázek 6-8**.</span><span class="sxs-lookup"><span data-stu-id="b5a10-253">**Figure 6-8**.</span></span> <span data-ttu-id="b5a10-254">Swashbuckle Explorer API na základě metadat Swagger – mikroslužba eShopOnContainers Catalog</span><span class="sxs-lookup"><span data-stu-id="b5a10-254">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="b5a10-255">Dokumentace k rozhraní API uživatelského rozhraní Swagger vygenerované swashbuckle zahrnuje všechny publikované akce.</span><span class="sxs-lookup"><span data-stu-id="b5a10-255">The Swashbuckle generated Swagger UI API documentation includes all published actions.</span></span> <span data-ttu-id="b5a10-256">Průzkumník rozhraní API není tady nejdůležitější.</span><span class="sxs-lookup"><span data-stu-id="b5a10-256">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="b5a10-257">Po použití webového rozhraní API, které se může považovat za sebe sama v metadatech Swagger, se dá rozhraní API bez problémů používat v nástrojích založených na Swagger, včetně generátorů kódu třídy proxy serveru klienta, které můžou cílit na mnoho platforem.</span><span class="sxs-lookup"><span data-stu-id="b5a10-257">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="b5a10-258">Například jak je uvedeno, automatické [REST](https://github.com/Azure/AutoRest) automaticky vygeneruje klientské třídy .NET.</span><span class="sxs-lookup"><span data-stu-id="b5a10-258">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="b5a10-259">Ale k dispozici jsou i další nástroje, jako je [Swagger-CodeGen](https://github.com/swagger-api/swagger-codegen) , což umožňuje automatické generování kódu klientských knihoven API, zástupných procedur serveru a dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="b5a10-259">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="b5a10-260">V současné době se swashbuckle skládá z pěti interních balíčků NuGet v rámci vysoké úrovně Metapackage [swashbuckle. AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) pro aplikace ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b5a10-260">Currently, Swashbuckle consists of five internal NuGet packages under the high-level metapackage [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore) for ASP.NET Core applications.</span></span>

<span data-ttu-id="b5a10-261">Po instalaci těchto balíčků NuGet do projektu webového rozhraní API je potřeba nakonfigurovat Swagger ve třídě Startup, jako v následujícím **zjednodušeném** kódu:</span><span class="sxs-lookup"><span data-stu-id="b5a10-261">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following **simplified** code:</span></span>

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

<span data-ttu-id="b5a10-262">Až to uděláte, můžete aplikaci spustit a procházet následujícími koncovými body JSON a UI pomocí adres URL, jako jsou tyto:</span><span class="sxs-lookup"><span data-stu-id="b5a10-262">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```console
  http://<your-root-url>/swagger/v1/swagger.json

  http://<your-root-url>/swagger/
```

<span data-ttu-id="b5a10-263">Dříve jste viděli vygenerované uživatelské rozhraní vytvořené nástrojem swashbuckle pro adresu URL `http://<your-root-url>/swagger` , jako je.</span><span class="sxs-lookup"><span data-stu-id="b5a10-263">You previously saw the generated UI created by Swashbuckle for a URL like `http://<your-root-url>/swagger`.</span></span> <span data-ttu-id="b5a10-264">Na obrázku 6-9 můžete také zjistit, jak můžete testovat jakoukoli metodu rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="b5a10-264">In Figure 6-9 you can also see how you can test any API method.</span></span>

![Snímek obrazovky uživatelského rozhraní Swagger zobrazující dostupné testovací nástroje](./media/data-driven-crud-microservice/swashbuckle-ui-testing.png)

<span data-ttu-id="b5a10-266">**Obrázek 6-9**.</span><span class="sxs-lookup"><span data-stu-id="b5a10-266">**Figure 6-9**.</span></span> <span data-ttu-id="b5a10-267">Testování uživatelského rozhraní swashbuckle – metoda rozhraní API katalogu/položek</span><span class="sxs-lookup"><span data-stu-id="b5a10-267">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="b5a10-268">Podrobnosti o rozhraní API uživatelského rozhraní Swagger zobrazuje ukázku odpovědi a dá se použít ke spuštění reálného rozhraní API, které je skvělé pro vyhledávání pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="b5a10-268">The Swagger UI API detail shows a sample of the response and can be used to execute the real API, which is great for developer discovery.</span></span> <span data-ttu-id="b5a10-269">Obrázek 6-10 ukazuje metadata JSON Swagger vygenerovaná z mikroslužby eShopOnContainers (což je to, co používají nástroje), když požadujete `http://<your-root-url>/swagger/v1/swagger.json` použití [metody post](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="b5a10-269">Figure 6-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request `http://<your-root-url>/swagger/v1/swagger.json` using [Postman](https://www.getpostman.com/).</span></span>

![Snímek obrazovky s ukázkovým uživatelským rozhraním, které zobrazuje metadata JSON pro Swagger](./media/data-driven-crud-microservice/swagger-json-metadata.png)

<span data-ttu-id="b5a10-271">**Obrázek 6-10**.</span><span class="sxs-lookup"><span data-stu-id="b5a10-271">**Figure 6-10**.</span></span> <span data-ttu-id="b5a10-272">Metadata JSON pro Swagger</span><span class="sxs-lookup"><span data-stu-id="b5a10-272">Swagger JSON metadata</span></span>

<span data-ttu-id="b5a10-273">To je jednoduché.</span><span class="sxs-lookup"><span data-stu-id="b5a10-273">It is that simple.</span></span> <span data-ttu-id="b5a10-274">A vzhledem k tomu, že se automaticky generuje, metadata Swagger se po přidání dalších funkcí do rozhraní API zvětší.</span><span class="sxs-lookup"><span data-stu-id="b5a10-274">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="b5a10-275">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="b5a10-275">Additional resources</span></span>

- <span data-ttu-id="b5a10-276">**Stránky pomoci webového rozhraní API ASP.NET pomocí Swagger** </span><span class="sxs-lookup"><span data-stu-id="b5a10-276">**ASP.NET Web API Help Pages using Swagger** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger](/aspnet/core/tutorials/web-api-help-pages-using-swagger)

- <span data-ttu-id="b5a10-277">**Začínáme s swashbuckle a ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="b5a10-277">**Get started with Swashbuckle and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-swashbuckle](/aspnet/core/tutorials/getting-started-with-swashbuckle)

- <span data-ttu-id="b5a10-278">**Začínáme s NSwag a ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="b5a10-278">**Get started with NSwag and ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/tutorials/getting-started-with-nswag](/aspnet/core/tutorials/getting-started-with-nswag)

> [!div class="step-by-step"]
> <span data-ttu-id="b5a10-279">[Předchozí](microservice-application-design.md) 
>  [Další](multi-container-applications-docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="b5a10-279">[Previous](microservice-application-design.md)
[Next](multi-container-applications-docker-compose.md)</span></span>
