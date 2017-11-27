---
title: "Vytvoření jednoduchého mikroslužbu CRUD řízené daty"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Vytvoření jednoduchého mikroslužbu CRUD řízené daty"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: b814d344f2c78e7cf57f9e2896cf1d6b52db38d9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="creating-a-simple-data-driven-crud-microservice"></a><span data-ttu-id="dec5d-104">Vytvoření jednoduchého mikroslužbu CRUD řízené daty</span><span class="sxs-lookup"><span data-stu-id="dec5d-104">Creating a simple data-driven CRUD microservice</span></span>

<span data-ttu-id="dec5d-105">Tato část obsahuje přehled, jak vytvořit jednoduchou mikroslužbu, který provádí vytváření, čtení, aktualizace a operace odstranění (CRUD) ve zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="dec5d-105">This section outlines how to create a simple microservice that performs create, read, update, and delete (CRUD) operations on a data source.</span></span>

## <a name="designing-a-simple-crud-microservice"></a><span data-ttu-id="dec5d-106">Navrhování jednoduché mikroslužbu CRUD</span><span class="sxs-lookup"><span data-stu-id="dec5d-106">Designing a simple CRUD microservice</span></span>

<span data-ttu-id="dec5d-107">Z návrhu hlediska je velmi jednoduchý tento typ kontejnerizované mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="dec5d-107">From a design point of view, this type of containerized microservice is very simple.</span></span> <span data-ttu-id="dec5d-108">Možná je jednoduchá problém vyřešit, nebo možná implementace je pouze testování konceptu.</span><span class="sxs-lookup"><span data-stu-id="dec5d-108">Perhaps the problem to solve is simple, or perhaps the implementation is only a proof of concept.</span></span>

![](./media/image4.png)

<span data-ttu-id="dec5d-109">**Obrázek 8-4**.</span><span class="sxs-lookup"><span data-stu-id="dec5d-109">**Figure 8-4**.</span></span> <span data-ttu-id="dec5d-110">Interní návrhu pro jednoduché mikroslužeb CRUD</span><span class="sxs-lookup"><span data-stu-id="dec5d-110">Internal design for simple CRUD microservices</span></span>

<span data-ttu-id="dec5d-111">Příkladem tento druh jednoduché datové jednotky služby je mikroslužbu katalogu v eShopOnContainers ukázkové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dec5d-111">An example of this kind of simple data-drive service is the catalog microservice from the eShopOnContainers sample application.</span></span> <span data-ttu-id="dec5d-112">Tento typ služby implementuje všechny její funkce v jedné projekt webového rozhraní API ASP.NET Core, který obsahuje třídy pro svůj model dat, jeho obchodní logiky a jeho data přístupový kód.</span><span class="sxs-lookup"><span data-stu-id="dec5d-112">This type of service implements all its functionality in a single ASP.NET Core Web API project that includes classes for its data model, its business logic, and its data access code.</span></span> <span data-ttu-id="dec5d-113">Také ukládá související data v databázi spuštěna v systému SQL Server (jako jiný kontejner pro účely vývoje/testování), ale mohou být také všechny regulární hostitele systému SQL Server, jak ukazuje obrázek 8-5.</span><span class="sxs-lookup"><span data-stu-id="dec5d-113">It also stores its related data in a database running in SQL Server (as another container for dev/test purposes), but could also be any regular SQL Server host, as shown in Figure 8-5.</span></span>

![](./media/image5.png)

<span data-ttu-id="dec5d-114">**Obrázek 8-5**.</span><span class="sxs-lookup"><span data-stu-id="dec5d-114">**Figure 8-5**.</span></span> <span data-ttu-id="dec5d-115">Jednoduché mikroslužbu data řízené/CRUD návrhu</span><span class="sxs-lookup"><span data-stu-id="dec5d-115">Simple data-driven/CRUD microservice design</span></span>

<span data-ttu-id="dec5d-116">Při vývoji tento druh služby, je třeba pouze [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) a rozhraní API pro přístup k datům nebo ORM jako [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span><span class="sxs-lookup"><span data-stu-id="dec5d-116">When you are developing this kind of service, you only need [ASP.NET Core](https://docs.microsoft.com/aspnet/core/) and a data-access API or ORM like [Entity Framework Core](https://docs.microsoft.com/ef/core/index).</span></span> <span data-ttu-id="dec5d-117">Může také generovat [Swagger](http://swagger.io/) metadata automaticky přes [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) zajistit popis co nabízí služby, jak je popsáno v následující části.</span><span class="sxs-lookup"><span data-stu-id="dec5d-117">You could also generate [Swagger](http://swagger.io/) metadata automatically through [Swashbuckle](https://github.com/domaindrivendev/Swashbuckle.AspNetCore) to provide a description of what your service offers, as explained in the next section.</span></span>

<span data-ttu-id="dec5d-118">Všimněte si, že spuštění databázový server, jako je SQL Server v rámci kontejner Docker je skvělá pro vývojové prostředí, protože všechny závislosti může mít a bez nutnosti zřídit databázi v cloudu nebo místně.</span><span class="sxs-lookup"><span data-stu-id="dec5d-118">Note that running a database server like SQL Server within a Docker container is great for development environments, because you can have all your dependencies up and running without needing to provision a database in the cloud or on-premises.</span></span> <span data-ttu-id="dec5d-119">To je velmi praktické, když spouštění integrace testů.</span><span class="sxs-lookup"><span data-stu-id="dec5d-119">This is very convenient when running integration tests.</span></span> <span data-ttu-id="dec5d-120">Ale pro provozní prostředí, serverem databáze v kontejneru nedoporučuje, protože se obvykle nezobrazí vysoká dostupnost s Tento přístup.</span><span class="sxs-lookup"><span data-stu-id="dec5d-120">However, for production environments, running a database server in a container is not recommended, because you usually do not get high availability with that approach.</span></span> <span data-ttu-id="dec5d-121">Pro produkční prostředí v Azure se doporučuje používat databázi SQL Azure nebo jakékoli jiné databáze technologie, která můžete zajistit vysokou dostupnost a škálovatelnost vysoké.</span><span class="sxs-lookup"><span data-stu-id="dec5d-121">For a production environment in Azure, it is recommended that you use Azure SQL DB or any other database technology that can provide high availability and high scalability.</span></span> <span data-ttu-id="dec5d-122">Například pro přístup NoSQL, můžete zvolit DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="dec5d-122">For example, for a NoSQL approach, you might choose DocumentDB.</span></span>

<span data-ttu-id="dec5d-123">Nakonec úpravy souborů metadat soubor Docker a docker-compose.yml, můžete konfigurovat vytváření bitové kopie tohoto kontejneru, jaký základní image budou používat plus návrh nastavení, jako například vnitřní a vnější názvy a porty TCP.</span><span class="sxs-lookup"><span data-stu-id="dec5d-123">Finally, by editing the Dockerfile and docker-compose.yml metadata files, you can configure how the image of this container will be created—what base image it will use, plus design settings such as internal and external names and TCP ports.</span></span> 

## <a name="implementing-a-simple-crud-microservice-with-aspnet-core"></a><span data-ttu-id="dec5d-124">Implementace jednoduchého mikroslužbu CRUD pomocí ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="dec5d-124">Implementing a simple CRUD microservice with ASP.NET Core</span></span>

<span data-ttu-id="dec5d-125">Chcete-li implementovat jednoduché mikroslužbu CRUD pomocí .NET Core a Visual Studio, začněte vytvořením jednoduchého projektu webového rozhraní API ASP.NET Core (spuštěna na .NET Core, můžete spustit na hostiteli systému Linux Docker), jako obrázku 8-6.</span><span class="sxs-lookup"><span data-stu-id="dec5d-125">To implement a simple CRUD microservice using .NET Core and Visual Studio, you start by creating a simple ASP.NET Core Web API project (running on .NET Core so it can run on a Linux Docker host), as shown in Figure 8-6.</span></span>

  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------
  <span data-ttu-id="dec5d-126">![](./media/image6.png)   ![](./media/image7.png)</span><span class="sxs-lookup"><span data-stu-id="dec5d-126">![](./media/image6.png)   ![](./media/image7.png)</span></span>
  ------------------------------------------------------------------------------------- -------------------------------------------------------------------------------------

<span data-ttu-id="dec5d-127">**Obrázek 8-6**.</span><span class="sxs-lookup"><span data-stu-id="dec5d-127">**Figure 8-6**.</span></span> <span data-ttu-id="dec5d-128">Vytvoření projektu webového rozhraní API ASP.NET Core v sadě Visual Studio</span><span class="sxs-lookup"><span data-stu-id="dec5d-128">Creating an ASP.NET Core Web API project in Visual Studio</span></span>

<span data-ttu-id="dec5d-129">Po vytvoření projektu, můžete implementovat vaše řadiče MVC, stejně jako v jiných projekt webového rozhraní API pomocí rozhraní Entity Framework API nebo dalších rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="dec5d-129">After creating the project, you can implement your MVC controllers as you would in any other Web API project, using the Entity Framework API or other API.</span></span> <span data-ttu-id="dec5d-130">V projektu eShopOnContainers.Catalog.API uvidíte, že hlavní závislosti pro tento mikroslužby jsou právě ASP.NET Core sám sebe, rozhraní Entity Framework a Swashbuckle, jak je znázorněno na obrázku 8-7.</span><span class="sxs-lookup"><span data-stu-id="dec5d-130">In the eShopOnContainers.Catalog.API project, you can see that the main dependencies for that microservice are just ASP.NET Core itself, Entity Framework, and Swashbuckle, as shown in Figure 8-7.</span></span>

![](./media/image8.PNG)

<span data-ttu-id="dec5d-131">**Obrázek 8-7**.</span><span class="sxs-lookup"><span data-stu-id="dec5d-131">**Figure 8-7**.</span></span> <span data-ttu-id="dec5d-132">Závislosti v jednoduché mikroslužbu CRUD webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="dec5d-132">Dependencies in a simple CRUD Web API microservice</span></span>

### <a name="implementing-crud-web-api-services-with-entity-framework-core"></a><span data-ttu-id="dec5d-133">Implementace služby CRUD webového rozhraní API základní Entity Framework</span><span class="sxs-lookup"><span data-stu-id="dec5d-133">Implementing CRUD Web API services with Entity Framework Core</span></span>

<span data-ttu-id="dec5d-134">Základní Entity Framework (EF) je lightweight rozšiřitelný, a přístup technologie a platformy verzi oblíbených datům Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="dec5d-134">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="dec5d-135">Základní EF je objekt relační mapper (ORM), která umožňuje vývojářům rozhraní .NET pro práci s objekty .NET pomocí databáze.</span><span class="sxs-lookup"><span data-stu-id="dec5d-135">EF Core is an object-relational mapper (ORM) that enables .NET developers to work with a database using .NET objects.</span></span>

<span data-ttu-id="dec5d-136">Mikroslužbu katalogu používá EF a zprostředkovatele SQL Server, protože jeho databáze se spouští v kontejneru se systémem SQL Server pro Linux Docker bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="dec5d-136">The catalog microservice uses EF and the SQL Server provider because its database is running in a container with the SQL Server for Linux Docker image.</span></span> <span data-ttu-id="dec5d-137">Databáze však může být nasazený do všech ostatních SQL serverech, jako je Windows na pracovišti nebo v databázi SQL Azure.</span><span class="sxs-lookup"><span data-stu-id="dec5d-137">However, the database could be deployed into any SQL Server, such as Windows on-premises or Azure SQL DB.</span></span> <span data-ttu-id="dec5d-138">Jediné, co by se musela změnit je připojovací řetězec v rozhraní ASP.NET Web API mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="dec5d-138">The only thing you would need to change is the connection string in the ASP.NET Web API microservice.</span></span>

#### <a name="add-entity-framework-core-to-your-dependencies"></a><span data-ttu-id="dec5d-139">Přidání Entity Framework Core do vaší závislosti</span><span class="sxs-lookup"><span data-stu-id="dec5d-139">Add Entity Framework Core to your dependencies</span></span>

<span data-ttu-id="dec5d-140">Můžete nainstalovat balíček NuGet pro zprostředkovatele databáze, které chcete použít, v tomto případě SQL Server, z v prostředí Visual Studio IDE nebo s konzolou NuGet.</span><span class="sxs-lookup"><span data-stu-id="dec5d-140">You can install the NuGet package for the database provider you want to use, in this case SQL Server, from within the Visual Studio IDE or with the NuGet console.</span></span> <span data-ttu-id="dec5d-141">Použijte následující příkaz:</span><span class="sxs-lookup"><span data-stu-id="dec5d-141">Use the following command:</span></span>

```
  Install-Package Microsoft.EntityFrameworkCore.SqlServer
```

#### <a name="the-data-model"></a><span data-ttu-id="dec5d-142">Datový model</span><span class="sxs-lookup"><span data-stu-id="dec5d-142">The data model</span></span>

<span data-ttu-id="dec5d-143">Základní EF provádí se přístup k datům pomocí modelu.</span><span class="sxs-lookup"><span data-stu-id="dec5d-143">With EF Core, data access is performed by using a model.</span></span> <span data-ttu-id="dec5d-144">Model se skládá z tříd entit a odvozené kontext, který představuje relaci s databází, což umožňuje dotazování a uložit data.</span><span class="sxs-lookup"><span data-stu-id="dec5d-144">A model is made up of entity classes and a derived context that represents a session with the database, allowing you to query and save data.</span></span> <span data-ttu-id="dec5d-145">Můžete generovat model z existující databáze, ručně code model tak, aby odpovídaly vaší databáze nebo použijte EF migrace vytvořit databázi z modelu (a momentální ho jako váš model změny v čase).</span><span class="sxs-lookup"><span data-stu-id="dec5d-145">You can generate a model from an existing database, manually code a model to match your database, or use EF migrations to create a database from your model (and evolve it as your model changes over time).</span></span> <span data-ttu-id="dec5d-146">Mikroslužbu katalogu používáme poslední přístup.</span><span class="sxs-lookup"><span data-stu-id="dec5d-146">For the catalog microservice we are using the last approach.</span></span> <span data-ttu-id="dec5d-147">Vidíte příklad třídy entity CatalogItem v následujícím příkladu kódu, který je jednoduchý prostý původní objekt CLR ([objektů POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) třídy entita.</span><span class="sxs-lookup"><span data-stu-id="dec5d-147">You can see an example of the CatalogItem entity class in the following code example, which is a simple Plain Old CLR Object ([POCO](https://en.wikipedia.org/wiki/Plain_Old_CLR_Object)) entity class.</span></span>

```csharp
public class CatalogItem
{
    public int Id { get; set; }
    public string Name { get; set; }
    public string Description { get; set; }
    public decimal Price { get; set; }
    public string PictureUri { get; set; }
    public int CatalogTypeId { get; set; }
    public CatalogType CatalogType { get; set; }
    public int CatalogBrandId { get; set; }
    public CatalogBrand CatalogBrand { get; set; }
    public CatalogItem() { }
}
```

<span data-ttu-id="dec5d-148">Budete také potřebovat DbContext, který představuje relaci s databází.</span><span class="sxs-lookup"><span data-stu-id="dec5d-148">You also need a DbContext that represents a session with the database.</span></span> <span data-ttu-id="dec5d-149">Pro katalog mikroslužbu, CatalogContext třída je odvozena ze základní třídy DbContext, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="dec5d-149">For the catalog microservice, the CatalogContext class derives from the DbContext base class, as shown in the following example:</span></span>

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

<span data-ttu-id="dec5d-150">Můžete mít další kód v implementaci DbContext.</span><span class="sxs-lookup"><span data-stu-id="dec5d-150">You can have additional code in the DbContext implementation.</span></span> <span data-ttu-id="dec5d-151">Například v ukázkové aplikaci máme metody OnModelCreating ve třídě CatalogContext, která automaticky naplní ukázkových dat při prvním pokusu o přístup k databázi.</span><span class="sxs-lookup"><span data-stu-id="dec5d-151">For example, in the sample application, we have an OnModelCreating method in the CatalogContext class that automatically populates the sample data the first time it tries to access the database.</span></span> <span data-ttu-id="dec5d-152">Tato metoda je užitečná pro ukázková data.</span><span class="sxs-lookup"><span data-stu-id="dec5d-152">This method is useful for demo data.</span></span> <span data-ttu-id="dec5d-153">Metody OnModelCreating můžete také použít k přizpůsobení objektu a databáze entity mapování s mnoha dalších [body rozšiřitelnosti EF](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span><span class="sxs-lookup"><span data-stu-id="dec5d-153">You can also use the OnModelCreating method to customize object/database entity mappings with many other [EF extensibility points](https://blogs.msdn.microsoft.com/dotnet/2016/09/29/implementing-seeding-custom-conventions-and-interceptors-in-ef-core-1-0/).</span></span>

<span data-ttu-id="dec5d-154">Zobrazí se další podrobnosti o OnModelCreating v [implementace vrstvě infrastruktury trvalost Entity Framework základní](#implementing_infrastructure_persistence) dále v této příručce.</span><span class="sxs-lookup"><span data-stu-id="dec5d-154">You can see further details about OnModelCreating in the [Implementing the infrastructure-persistence layer with Entity Framework Core](#implementing_infrastructure_persistence) section later in this book.</span></span>

##### <a name="querying-data-from-web-api-controllers"></a><span data-ttu-id="dec5d-155">Dotazování na data z řadičů webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="dec5d-155">Querying data from Web API controllers</span></span>

<span data-ttu-id="dec5d-156">Instance třídy entity jsou obvykle načteny z databáze pomocí jazyka integrovaného dotazu (LINQ), jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="dec5d-156">Instances of your entity classes are typically retrieved from the database using Language Integrated Query (LINQ), as shown in the following example:</span></span>

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
        _catalogIntegrationEventService = catalogIntegrationEventService ??
           throw new ArgumentNullException(nameof(catalogIntegrationEventService));
        _settings = settings.Value;
        ((DbContext)context).ChangeTracker.QueryTrackingBehavior = QueryTrackingBehavior.NoTracking;
    }

    // GET api/v1/[controller]/items[?pageSize=3&pageIndex=10]
    [HttpGet]
    [Route("[action]")]
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

##### <a name="saving-data"></a><span data-ttu-id="dec5d-157">Ukládání dat</span><span class="sxs-lookup"><span data-stu-id="dec5d-157">Saving data</span></span>

<span data-ttu-id="dec5d-158">Data je vytvořit, odstranit a upravit v databázi pomocí instance třídy entity.</span><span class="sxs-lookup"><span data-stu-id="dec5d-158">Data is created, deleted, and modified in the database using instances of your entity classes.</span></span> <span data-ttu-id="dec5d-159">Můžete přidat kód jako následující pevně příklad (imitovaná data v tomto případě) k vašim řadičům webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="dec5d-159">You could add code like the following hard-coded example (mock data, in this case) to your Web API controllers.</span></span>

```csharp
var catalogItem = new CatalogItem() {CatalogTypeId=2, CatalogBrandId=2,
   Name="Roslyn T-Shirt", Price = 12};
_context.Catalog.Add(catalogItem);
_context.SaveChanges();
```

##### <a name="dependency-injection-in-aspnet-core-and-web-api-controllers"></a><span data-ttu-id="dec5d-160">Vkládání závislostí v řadiče ASP.NET Core a webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="dec5d-160">Dependency Injection in ASP.NET Core and Web API controllers</span></span>

<span data-ttu-id="dec5d-161">V ASP.NET Core můžete ihned vkládání závislostí (DI).</span><span class="sxs-lookup"><span data-stu-id="dec5d-161">In ASP.NET Core you can use Dependency Injection (DI) out of the box.</span></span> <span data-ttu-id="dec5d-162">Není potřeba nastavit kontejner inverzi řízení (IoC) třetí strany, i když je možné připojit vaše upřednostňované kontejner IoC ASP.NET základní infrastruktury Chcete-li.</span><span class="sxs-lookup"><span data-stu-id="dec5d-162">You do not need to set up a third-party Inversion of Control (IoC) container, although you can plug your preferred IoC container into the ASP.NET Core infrastructure if you want.</span></span> <span data-ttu-id="dec5d-163">V takovém případě znamená, že můžete přímo vložit požadované DBContext EF nebo další úložiště pomocí konstruktoru řadiče.</span><span class="sxs-lookup"><span data-stu-id="dec5d-163">In this case, it means that you can directly inject the required EF DBContext or additional repositories through the controller constructor.</span></span> <span data-ttu-id="dec5d-164">V příkladu výše třídy CatalogController jsme jsou vložení objekt typu CatalogContext plus pomocí konstruktoru CatalogController jiné objekty.</span><span class="sxs-lookup"><span data-stu-id="dec5d-164">In the example above of the CatalogController class, we are injecting an object of CatalogContext type plus other objects through the CatalogController constructor.</span></span>

<span data-ttu-id="dec5d-165">Důležité konfigurační nastavení v projektu webového rozhraní API je registrace třídy DbContext do kontejneru služby IoC.</span><span class="sxs-lookup"><span data-stu-id="dec5d-165">An important configuration to set up in the Web API project is the DbContext class registration into the service’s IoC container.</span></span> <span data-ttu-id="dec5d-166">Obvykle uděláte ve třídě spuštění voláním služby. Metoda AddDbContext uvnitř metody ConfigureServices, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="dec5d-166">You typically do so in the Startup class by calling the services.AddDbContext method inside the ConfigureServices method, as shown in the following example:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
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

### <a name="additional-resources"></a><span data-ttu-id="dec5d-167">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="dec5d-167">Additional resources</span></span>

-   <span data-ttu-id="dec5d-168">**Dotazování na Data**
    [*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span><span class="sxs-lookup"><span data-stu-id="dec5d-168">**Querying Data**
[*https://docs.microsoft.com/ef/core/querying/index*](https://docs.microsoft.com/ef/core/querying/index)</span></span>

-   <span data-ttu-id="dec5d-169">**Ukládání dat**
    [*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span><span class="sxs-lookup"><span data-stu-id="dec5d-169">**Saving Data**
[*https://docs.microsoft.com/ef/core/saving/index*](https://docs.microsoft.com/ef/core/saving/index)</span></span>

## <a name="the-db-connection-string-and-environment-variables-used-by-docker-containers"></a><span data-ttu-id="dec5d-170">DB připojovací řetězec a prostředí proměnné používané Docker kontejnery</span><span class="sxs-lookup"><span data-stu-id="dec5d-170">The DB connection string and environment variables used by Docker containers</span></span>

<span data-ttu-id="dec5d-171">Můžete použít nastavení ASP.NET Core a přidejte vlastnost ConnectionString do souboru settings.json, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="dec5d-171">You can use the ASP.NET Core settings and add a ConnectionString property to your settings.json file as shown in the following example:</span></span>

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

<span data-ttu-id="dec5d-172">Soubor settings.json může mít výchozí hodnoty pro vlastnost ConnectionString nebo pro žádné jiné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="dec5d-172">The settings.json file can have default values for the ConnectionString property or for any other property.</span></span> <span data-ttu-id="dec5d-173">Tyto vlastnosti však bude možné přepsat hodnoty proměnné prostředí, které zadáte v soubor docker-compose.override.yml.</span><span class="sxs-lookup"><span data-stu-id="dec5d-173">However, those properties will be overridden by the values of environment variables that you specify in the docker-compose.override.yml file.</span></span>

<span data-ttu-id="dec5d-174">Z docker-compose.yml nebo docker compose.override.yml souborů můžete inicializovat těchto proměnných prostředí tak, že Docker bude nastavit je jako proměnné prostředí operačního systému pro vás, jak je znázorněno v následující soubor docker-compose.override.yml (připojení řetězec a další řádky zalomení v tomto příkladu, ale nebude zabalit do vlastního souboru).</span><span class="sxs-lookup"><span data-stu-id="dec5d-174">From your docker-compose.yml or docker-compose.override.yml files, you can initialize those environment variables so that Docker will set them up as OS environment variables for you, as shown in the following docker-compose.override.yml file (the connection string and other lines wrap in this example, but it would not wrap in your own file).</span></span>

```yml
# docker-compose.override.yml

#
catalog.api:
  environment:
    - ConnectionString=Server=sql.data;Database=Microsoft.eShopOnContainers.Services.CatalogDb;User Id=sa;Password=Pass@word
    - ExternalCatalogBaseUrl=http://10.0.75.1:5101
    #- ExternalCatalogBaseUrl=http://dockerhoststaging.westus.cloudapp.azure.com:5101
  
  ports:
    - "5101:5101"
```

<span data-ttu-id="dec5d-175">Soubory docker-compose.yml na úrovni řešení nejsou jenom flexibilnější než konfigurační soubory na úrovni projektu nebo mikroslužbu, ale také bezpečnější.</span><span class="sxs-lookup"><span data-stu-id="dec5d-175">The docker-compose.yml files at the solution level are not only more flexible than configuration files at the project or microservice level, but also more secure.</span></span> <span data-ttu-id="dec5d-176">Vezměte v úvahu, že imagí Dockeru, které vytvoříte za mikroslužbu neobsahují docker-compose.yml soubory jenom binární soubory a soubory konfigurace pro každý mikroslužbu, včetně soubor Docker.</span><span class="sxs-lookup"><span data-stu-id="dec5d-176">Consider that the Docker images that you build per microservice do not contain the docker-compose.yml files, only binary files and configuration files for each microservice, including the Dockerfile.</span></span> <span data-ttu-id="dec5d-177">Ale soubor docker-compose.yml není nasazena spolu s aplikace; používá se pouze v době nasazení.</span><span class="sxs-lookup"><span data-stu-id="dec5d-177">But the docker-compose.yml file is not deployed along with your application; it is used only at deployment time.</span></span> <span data-ttu-id="dec5d-178">Umístění hodnot proměnných prostředí v těchto souborech docker-compose.yml (i bez šifrování hodnoty) je proto bezpečnější než uvedení tyto hodnoty regulární .NET konfigurační soubory, které jsou nasazeny pomocí kódu.</span><span class="sxs-lookup"><span data-stu-id="dec5d-178">Therefore, placing environment variables values in those docker-compose.yml files (even without encrypting the values) is more secure than placing those values in regular .NET configuration files that are deployed with your code.</span></span>

<span data-ttu-id="dec5d-179">Nakonec můžete získat tuto hodnotu z vašeho kódu pomocí konfigurace\["ConnectionString"\], jak je znázorněno v metodě ConfigureServices v předchozí příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="dec5d-179">Finally, you can get that value from your code by using Configuration\["ConnectionString"\], as shown in the ConfigureServices method in an earlier code example.</span></span>

<span data-ttu-id="dec5d-180">Ale pro provozní prostředí, můžete chtít další způsoby explorer na tom, jak ukládat tajné klíče jako připojovací řetězce.</span><span class="sxs-lookup"><span data-stu-id="dec5d-180">However, for production environments, you might want to explorer additional ways on how to store secrets like the connection strings.</span></span> <span data-ttu-id="dec5d-181">Obvykle, bude spravovat zvolené orchestrator, jako jsou aplikace [Docker Swarm správu tajné klíče](https://docs.docker.com/engine/swarm/secrets/).</span><span class="sxs-lookup"><span data-stu-id="dec5d-181">Usually that will be managed by your chosen orchestrator, like you can do with [Docker Swarm secrets management](https://docs.docker.com/engine/swarm/secrets/).</span></span>

### <a name="implementing-versioning-in-aspnet-web-apis"></a><span data-ttu-id="dec5d-182">Implementace správy verzí v rozhraní ASP.NET Web API</span><span class="sxs-lookup"><span data-stu-id="dec5d-182">Implementing versioning in ASP.NET Web APIs</span></span>

<span data-ttu-id="dec5d-183">Mění obchodní požadavky, mohou být přidány nové kolekce prostředků, vztahy mezi prostředky mohou změnit a může být změněna strukturu dat v prostředky.</span><span class="sxs-lookup"><span data-stu-id="dec5d-183">As business requirements change, new collections of resources may be added, the relationships between resources might change, and the structure of the data in resources might be amended.</span></span> <span data-ttu-id="dec5d-184">Aktualizace webového rozhraní API pro zpracování nových požadavků je poměrně jednoduchý proces, ale musíte zvážit důsledky, které tyto změny budou mít na klientské aplikace využívají webové rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="dec5d-184">Updating a Web API to handle new requirements is a relatively straightforward process, but you must consider the effects that such changes will have on client applications consuming the Web API.</span></span> <span data-ttu-id="dec5d-185">I když vývojáři navrhování a implementace rozhraní Web API má plnou kontrolu nad toto rozhraní API, vývojář nemá stejnou úrovní kontrolu nad klientských aplikací, které může být vytvořené třetí strany organizace operační vzdáleně.</span><span class="sxs-lookup"><span data-stu-id="dec5d-185">Although the developer designing and implementing a Web API has full control over that API, the developer does not have the same degree of control over client applications that might be built by third party organizations operating remotely.</span></span>

<span data-ttu-id="dec5d-186">Správa verzí umožňuje webového rozhraní API označíte, funkce a prostředky, které vystavuje.</span><span class="sxs-lookup"><span data-stu-id="dec5d-186">Versioning enables a Web API to indicate the features and resources that it exposes.</span></span> <span data-ttu-id="dec5d-187">Klientská aplikace pak mohou odesílat požadavky na konkrétní verzi funkce nebo prostředků.</span><span class="sxs-lookup"><span data-stu-id="dec5d-187">A client application can then submit requests to a specific version of a feature or resource.</span></span> <span data-ttu-id="dec5d-188">Existuje několik přístupů k implementaci správy verzí:</span><span class="sxs-lookup"><span data-stu-id="dec5d-188">There are several approaches to implement versioning:</span></span>

-   <span data-ttu-id="dec5d-189">Identifikátor URI Správa verzí</span><span class="sxs-lookup"><span data-stu-id="dec5d-189">URI versioning</span></span>

-   <span data-ttu-id="dec5d-190">Správa verzí řetězec dotazu</span><span class="sxs-lookup"><span data-stu-id="dec5d-190">Query string versioning</span></span>

-   <span data-ttu-id="dec5d-191">Správa verzí hlavičky</span><span class="sxs-lookup"><span data-stu-id="dec5d-191">Header versioning</span></span>

<span data-ttu-id="dec5d-192">Řetězec dotazu a správa verzí URI jsou nejjednodušší k implementaci.</span><span class="sxs-lookup"><span data-stu-id="dec5d-192">Query string and URI versioning are the simplest to implement.</span></span> <span data-ttu-id="dec5d-193">Správa verzí hlavičky je dobré přístup.</span><span class="sxs-lookup"><span data-stu-id="dec5d-193">Header versioning is a good approach.</span></span> <span data-ttu-id="dec5d-194">Ale záhlaví verze není jako explicitní a jednoduché jako správa verzí identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="dec5d-194">However, header versioning not as explicit and straightforward as URI versioning.</span></span> <span data-ttu-id="dec5d-195">Protože správa verzí adresa URL je nejjednodušší a většina explicitní, eShopOnContainers ukázková aplikace používá Správa verzí identifikátor URI.</span><span class="sxs-lookup"><span data-stu-id="dec5d-195">Because URL versioning is the simplest and most explicit, the eShopOnContainers sample application uses URI versioning.</span></span>

<span data-ttu-id="dec5d-196">Správa verzí URI jako eShopOnContainers ukázkovou aplikaci pokaždé, když upravíte webového rozhraní API nebo změnit schéma prostředky, přidejte číslo verze identifikátor URI pro každého prostředku.</span><span class="sxs-lookup"><span data-stu-id="dec5d-196">With URI versioning, as in the eShopOnContainers sample application, each time you modify the Web API or change the schema of resources, you add a version number to the URI for each resource.</span></span> <span data-ttu-id="dec5d-197">Existující identifikátory URI by měly být nadále fungovat jako dříve, vrácení prostředky, které odpovídají schématu, která odpovídá na požadovanou verzi.</span><span class="sxs-lookup"><span data-stu-id="dec5d-197">Existing URIs should continue to operate as before, returning resources that conform to the schema that matches the requested version.</span></span>

<span data-ttu-id="dec5d-198">Jak ukazuje následující příklad kódu, může být verze nastavená pomocí atributů směrování v rozhraní Web API, která vytváří verze explicitní v identifikátoru URI (v tomto případě v1).</span><span class="sxs-lookup"><span data-stu-id="dec5d-198">As shown in the following code example, the version can be set by using the Route attribute in the Web API, which makes the version explicit in the URI (v1 in this case).</span></span>

```csharp
[Route("api/v1/[controller]")]
public class CatalogController : ControllerBase
{
    // Implementation ...
```

<span data-ttu-id="dec5d-199">Tento mechanismus správy verzí je jednoduchý a závisí na serveru pro směrování požadavku na příslušný koncový bod.</span><span class="sxs-lookup"><span data-stu-id="dec5d-199">This versioning mechanism is simple and depends on the server routing the request to the appropriate endpoint.</span></span> <span data-ttu-id="dec5d-200">Ale pro sofistikovanější Správa verzí a nejlepší metody při používání REST, doporučujeme použít hypermédií a implementovat [HATEOAS (Hypertext jako stav modulu aplikace)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span><span class="sxs-lookup"><span data-stu-id="dec5d-200">However, for a more sophisticated versioning and the best method when using REST, you should use hypermedia and implement [HATEOAS (Hypertext as the Engine of Application State)](https://docs.microsoft.com/azure/architecture/best-practices/api-design#using-the-hateoas-approach-to-enable-navigation-to-related-resources).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="dec5d-201">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="dec5d-201">Additional resources</span></span>

-   <span data-ttu-id="dec5d-202">**Scott Hanselman. Správa verzí základní RESTful webového rozhraní API ASP.NET, umožněno**
    [*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span><span class="sxs-lookup"><span data-stu-id="dec5d-202">**Scott Hanselman. ASP.NET Core RESTful Web API versioning made easy**
[*http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx*](http://www.hanselman.com/blog/ASPNETCoreRESTfulWebAPIVersioningMadeEasy.aspx)</span></span>

-   <span data-ttu-id="dec5d-203">**Správa verzí RESTful webového rozhraní API**</span><span class="sxs-lookup"><span data-stu-id="dec5d-203">**Versioning a RESTful web API**</span></span>

    [<span data-ttu-id="dec5d-204">*https://docs.microsoft.com/Azure/Architecture/Best-Practices/API-Design#Versioning-a-RESTful-web-API*</span><span class="sxs-lookup"><span data-stu-id="dec5d-204">*https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api*</span></span>](https://docs.microsoft.com/azure/architecture/best-practices/api-design#versioning-a-restful-web-api)

-   <span data-ttu-id="dec5d-205">**Royi Fielding. Správa verzí, hypermédií a REST**
    [*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span><span class="sxs-lookup"><span data-stu-id="dec5d-205">**Roy Fielding. Versioning, Hypermedia, and REST**
[*https://www.infoq.com/articles/roy-fielding-on-versioning*](https://www.infoq.com/articles/roy-fielding-on-versioning)</span></span>

## <a name="generating-swagger-description-metadata-from-your-aspnet-core-web-api"></a><span data-ttu-id="dec5d-206">Generování metadat Swagger popis z ASP.NET rozhraní Web API Core</span><span class="sxs-lookup"><span data-stu-id="dec5d-206">Generating Swagger description metadata from your ASP.NET Core Web API</span></span> 

<span data-ttu-id="dec5d-207">[Swagger](http://swagger.io/) je běžně používané s otevřeným zdrojem framework zajišťoval velké ekosystém nástroje, které vám pomůžou návrhu, sestavení, dokumentu a používat vaše rozhraní RESTful API.</span><span class="sxs-lookup"><span data-stu-id="dec5d-207">[Swagger](http://swagger.io/) is a commonly used open source framework backed by a large ecosystem of tools that helps you design, build, document, and consume your RESTful APIs.</span></span> <span data-ttu-id="dec5d-208">Se stává stále standard pro doménu popis metadat rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="dec5d-208">It is becoming the standard for the APIs description metadata domain.</span></span> <span data-ttu-id="dec5d-209">By měly obsahovat metadata Swagger popis s jakýmkoli mikroslužbu řízené daty mikroslužeb nebo pokročilejší řízené domény mikroslužeb (jak je popsáno v následující části).</span><span class="sxs-lookup"><span data-stu-id="dec5d-209">You should include Swagger description metadata with any kind of microservice, either data-driven microservices or more advanced domain-driven microservices (as explained in following section).</span></span>

<span data-ttu-id="dec5d-210">Srdcem Swagger je specifikace Swagger, což je popis metadat rozhraní API v souboru YAML nebo JSON.</span><span class="sxs-lookup"><span data-stu-id="dec5d-210">The heart of Swagger is the Swagger specification, which is API description metadata in a JSON or YAML file.</span></span> <span data-ttu-id="dec5d-211">Specifikace vytvoří RESTful kontrakt pro vaše rozhraní API s podrobnostmi o všech prostředků a operace v obou lidské a machine readable formátu pro snadný vývoj, zjišťování a integrace.</span><span class="sxs-lookup"><span data-stu-id="dec5d-211">The specification creates the RESTful contract for your API, detailing all its resources and operations in both a human- and machine-readable format for easy development, discovery, and integration.</span></span>

<span data-ttu-id="dec5d-212">Specifikace je základem z specifikace OpenAPI (OAS) a je vyvinuta v komunitě otevřené, transparentní a spolupráce pro standardizaci způsob, jakým jsou definovány rozhraní RESTful.</span><span class="sxs-lookup"><span data-stu-id="dec5d-212">The specification is the basis of the OpenAPI Specification (OAS) and is developed in an open, transparent, and collaborative community to standardize the way RESTful interfaces are defined.</span></span>

<span data-ttu-id="dec5d-213">Specifikace definuje strukturu pro jak může být zjištěn služby a jak se jeho funkce rozumí.</span><span class="sxs-lookup"><span data-stu-id="dec5d-213">The specification defines the structure for how a service can be discovered and how its capabilities understood.</span></span> <span data-ttu-id="dec5d-214">Další informace, včetně editoru webové a příklady specifikace Swagger společností jako Spotify, Uber, Slack a společnosti Microsoft, najdete v části webu Swagger (<http://swagger.io>).</span><span class="sxs-lookup"><span data-stu-id="dec5d-214">For more information, including a web editor and examples of Swagger specifications from companies like Spotify, Uber, Slack, and Microsoft, see the Swagger site (<http://swagger.io>).</span></span>

### <a name="why-use-swagger"></a><span data-ttu-id="dec5d-215">Proč používat Swagger?</span><span class="sxs-lookup"><span data-stu-id="dec5d-215">Why use Swagger?</span></span>

<span data-ttu-id="dec5d-216">Hlavních důvodů pro generování metadat Swagger pro vaše rozhraní API jsou uvedeny níže.</span><span class="sxs-lookup"><span data-stu-id="dec5d-216">The main reasons to generate Swagger metadata for your APIs are the following.</span></span>

<span data-ttu-id="dec5d-217">**Možnost pro ostatní produkty automaticky využívat a integrovat vaše rozhraní API**.</span><span class="sxs-lookup"><span data-stu-id="dec5d-217">**Ability for other products to automatically consume and integrate your APIs**.</span></span> <span data-ttu-id="dec5d-218">Desítek produktů a [komerční nástroje](http://swagger.io/commercial-tools/) a mnoho [knihoven a architektur](http://swagger.io/open-source-integrations/) podporu Swagger.</span><span class="sxs-lookup"><span data-stu-id="dec5d-218">Dozens of products and [commercial tools](http://swagger.io/commercial-tools/) and many [libraries and frameworks](http://swagger.io/open-source-integrations/) support Swagger.</span></span> <span data-ttu-id="dec5d-219">Microsoft má vysoké úrovně produktů a nástroje, které mohou automaticky používat rozhraní API na základě Swagger, například následující:</span><span class="sxs-lookup"><span data-stu-id="dec5d-219">Microsoft has high-level products and tools that can automatically consume Swagger-based APIs, such as the following:</span></span>

-   <span data-ttu-id="dec5d-220">[AutoRest](https://github.com/Azure/AutoRest).</span><span class="sxs-lookup"><span data-stu-id="dec5d-220">[AutoRest](https://github.com/Azure/AutoRest).</span></span> <span data-ttu-id="dec5d-221">Může automaticky vygenerovat třídy klienta rozhraní .NET pro volání Swagger.</span><span class="sxs-lookup"><span data-stu-id="dec5d-221">You can automatically generate .NET client classes for calling Swagger.</span></span> <span data-ttu-id="dec5d-222">To</span><span class="sxs-lookup"><span data-stu-id="dec5d-222">This</span></span>

-   <span data-ttu-id="dec5d-223">Nástroj můžete použít z rozhraní příkazového řádku a je integrován se sadou Visual Studio pro snadné použití prostřednictvím grafického uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dec5d-223">tool can be used from the CLI and it also integrates with Visual Studio for easy use through the GUI.</span></span>

-   <span data-ttu-id="dec5d-224">[Tok Microsoft](https://flow.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="dec5d-224">[Microsoft Flow](https://flow.microsoft.com/en-us/).</span></span> <span data-ttu-id="dec5d-225">Můžete automaticky [používat a integrovat vaše rozhraní API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) do vysoké úrovně pracovního postupu Microsoft Flow, programování bez znalosti vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="dec5d-225">You can automatically [use and integrate your API](https://flow.microsoft.com/en-us/blog/integrating-custom-api/) into a high-level Microsoft Flow workflow, with no programming skills required.</span></span>

-   <span data-ttu-id="dec5d-226">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span><span class="sxs-lookup"><span data-stu-id="dec5d-226">[Microsoft PowerApps](https://powerapps.microsoft.com/en-us/).</span></span> <span data-ttu-id="dec5d-227">Můžete automaticky využívat vaše rozhraní API z [mobilních aplikací PowerApps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) vytvořené s [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), s žádné znalostí programování vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="dec5d-227">You can automatically consume your API from [PowerApps mobile apps](https://powerapps.microsoft.com/en-us/blog/register-and-use-custom-apis-in-powerapps/) built with [PowerApps Studio](https://powerapps.microsoft.com/en-us/guided-learning/learning-powerapps-parts/), with no programming skills required.</span></span>

-   <span data-ttu-id="dec5d-228">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span><span class="sxs-lookup"><span data-stu-id="dec5d-228">[Azure App Service Logic Apps](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-what-are-logic-apps).</span></span> <span data-ttu-id="dec5d-229">Můžete automaticky [používat a integrovat do aplikace logiky Azure App Service vaše rozhraní API](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), s žádné znalostí programování vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="dec5d-229">You can automatically [use and integrate your API into an Azure App Service Logic App](https://docs.microsoft.com/azure/app-service-logic/app-service-logic-custom-hosted-api), with no programming skills required.</span></span>

<span data-ttu-id="dec5d-230">**Umožňuje automaticky generovat dokumentaci k rozhraní API**.</span><span class="sxs-lookup"><span data-stu-id="dec5d-230">**Ability to automatically generate API documentation**.</span></span> <span data-ttu-id="dec5d-231">Při vytváření rozsáhlých rozhraní RESTful API, jako je například komplexní aplikace na základě mikroslužbu, je třeba zpracovat velký počet koncových bodů s různými datovými modely použité v datové části žádosti a odpovědi.</span><span class="sxs-lookup"><span data-stu-id="dec5d-231">When you create large-scale RESTful APIs, such as complex microservice-based applications, you need to handle many endpoints with different data models used in the request and response payloads.</span></span> <span data-ttu-id="dec5d-232">S správné dokumentaci a s plnou explorer rozhraní API, jak získat s Swagger, se klíč pro úspěch vašeho rozhraní API a přijetí vývojáři.</span><span class="sxs-lookup"><span data-stu-id="dec5d-232">Having proper documentation and having a solid API explorer, as you get with Swagger, is key for the success of your API and adoption by developers.</span></span>

<span data-ttu-id="dec5d-233">Metadata swagger společnosti je Microsoft Flow, PowerApps a Azure Logic Apps pomocí pochopit, jak používat rozhraní API a připojit se k nim.</span><span class="sxs-lookup"><span data-stu-id="dec5d-233">Swagger’s metadata is what Microsoft Flow, PowerApps, and Azure Logic Apps use to understand how to use APIs and connect to them.</span></span>

### <a name="how-to-automate-api-swagger-metadata-generation-with-the-swashbuckle-nuget-package"></a><span data-ttu-id="dec5d-234">Jak automatizovat generování metadat Swagger rozhraní API pomocí balíčku Swashbuckle NuGet</span><span class="sxs-lookup"><span data-stu-id="dec5d-234">How to automate API Swagger metadata generation with the Swashbuckle NuGet package</span></span>

<span data-ttu-id="dec5d-235">Generování metadat Swagger ručně (v souboru YAML nebo JSON) může být pracné.</span><span class="sxs-lookup"><span data-stu-id="dec5d-235">Generating Swagger metadata manually (in a JSON or YAML file) can be tedious work.</span></span> <span data-ttu-id="dec5d-236">Však můžete automatizovat zjišťování rozhraní API ASP.NET Web API služeb pomocí [balíčku Swashbuckle NuGet](http://aka.ms/swashbuckledotnetcore) dynamicky generovat metadata Swagger rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="dec5d-236">However, you can automate API discovery of ASP.NET Web API services by using the [Swashbuckle NuGet package](http://aka.ms/swashbuckledotnetcore) to dynamically generate Swagger API metadata.</span></span>

<span data-ttu-id="dec5d-237">Swashbuckle automaticky vytvoří metadata Swagger pro projekty ASP.NET Web API.</span><span class="sxs-lookup"><span data-stu-id="dec5d-237">Swashbuckle automatically generates Swagger metadata for your ASP.NET Web API projects.</span></span> <span data-ttu-id="dec5d-238">Podporuje projekty webového rozhraní API ASP.NET Core a tradiční rozhraní ASP.NET Web API a dalších příchuť, jako je například aplikace API Azure, mobilní aplikace Azure, Azure Service Fabric mikroslužeb založené na technologii ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="dec5d-238">It supports ASP.NET Core Web API projects and the traditional ASP.NET Web API and any other flavor, such as Azure API App, Azure Mobile App, Azure Service Fabric microservices based on ASP.NET.</span></span> <span data-ttu-id="dec5d-239">Také podporuje prostý webového rozhraní API nasazené na kontejnery, jako v pro odkaz na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="dec5d-239">It also supports plain Web API deployed on containers, as in for the reference application.</span></span>

<span data-ttu-id="dec5d-240">Swashbuckle kombinuje Explorer rozhraní API a Swagger nebo [uživatelského rozhraní swagger](https://github.com/swagger-api/swagger-ui) zajistit bohaté zjišťování a dokumentace prostředí pro uživatele rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="dec5d-240">Swashbuckle combines API Explorer and Swagger or [swagger-ui](https://github.com/swagger-api/swagger-ui) to provide a rich discovery and documentation experience for your API consumers.</span></span> <span data-ttu-id="dec5d-241">Kromě jeho motoru generátor metadata Swagger Swashbuckle také obsahuje vložené verzi swagger – uživatelské rozhraní, které se bude automaticky sloužit až po instalaci Swashbuckle.</span><span class="sxs-lookup"><span data-stu-id="dec5d-241">In addition to its Swagger metadata generator engine, Swashbuckle also contains an embedded version of swagger-ui, which it will automatically serve up once Swashbuckle is installed.</span></span>

<span data-ttu-id="dec5d-242">To znamená, že můžete doplnit rozhraní API pomocí dobrý zjišťování uživatelského rozhraní, což vývojářům používat vaše rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="dec5d-242">This means you can complement your API with a nice discovery UI to help developers to use your API.</span></span> <span data-ttu-id="dec5d-243">Protože je generován automaticky, umožňuje soustředit na rozhraní API vyžaduje velmi malé množství kódu a údržby.</span><span class="sxs-lookup"><span data-stu-id="dec5d-243">It requires a very small amount of code and maintenance because it is automatically generated, allowing you to focus on building your API.</span></span> <span data-ttu-id="dec5d-244">Výsledek pro rozhraní API Průzkumníka vypadá jako obrázek 8-8.</span><span class="sxs-lookup"><span data-stu-id="dec5d-244">The result for the API Explorer looks like Figure 8-8.</span></span>

![](./media/image9.png)

<span data-ttu-id="dec5d-245">**Obrázek 8-8**.</span><span class="sxs-lookup"><span data-stu-id="dec5d-245">**Figure 8-8**.</span></span> <span data-ttu-id="dec5d-246">Swashbuckle rozhraní API Explorer na základě metadat Swagger – eShopOnContainers katalogu mikroslužbu</span><span class="sxs-lookup"><span data-stu-id="dec5d-246">Swashbuckle API Explorer based on Swagger metadata—eShopOnContainers catalog microservice</span></span>

<span data-ttu-id="dec5d-247">Průzkumník rozhraní API není zde je třeba mít.</span><span class="sxs-lookup"><span data-stu-id="dec5d-247">The API explorer is not the most important thing here.</span></span> <span data-ttu-id="dec5d-248">Jakmile máte webového rozhraní API, která může sám sebe popisují v metadatech Swagger, rozhraní API slouží bezproblémově z nástrojů rozhraní Swagger, včetně generátory kódu třídu proxy klienta, které můžete cílit na mnoha platformách.</span><span class="sxs-lookup"><span data-stu-id="dec5d-248">Once you have a Web API that can describe itself in Swagger metadata, your API can be used seamlessly from Swagger-based tools, including client proxy-class code generators that can target many platforms.</span></span> <span data-ttu-id="dec5d-249">Například jako uvedených [AutoRest](https://github.com/Azure/AutoRest) automaticky vygeneruje třídy klienta rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="dec5d-249">For example, as mentioned, [AutoRest](https://github.com/Azure/AutoRest) automatically generates .NET client classes.</span></span> <span data-ttu-id="dec5d-250">Jako další nástroje, ale [swagger codegen](https://github.com/swagger-api/swagger-codegen) jsou také k dispozici, který povolí generování kódu rozhraní API klienta knihovny, server zástupných procedur a dokumentaci automaticky.</span><span class="sxs-lookup"><span data-stu-id="dec5d-250">But additional tools like [swagger-codegen](https://github.com/swagger-api/swagger-codegen) are also available, which allow code generation of API client libraries, server stubs, and documentation automatically.</span></span>

<span data-ttu-id="dec5d-251">V současné době se skládá ze dvou balíčků NuGet Swashbuckle: Swashbuckle.SwaggerGen a Swashbuckle.SwaggerUi.</span><span class="sxs-lookup"><span data-stu-id="dec5d-251">Currently, Swashbuckle consists of two NuGet packages: Swashbuckle.SwaggerGen and Swashbuckle.SwaggerUi.</span></span> <span data-ttu-id="dec5d-252">První poskytuje funkce pro generování jeden nebo více dokumentů Swagger přímo z vaší implementace rozhraní API a umístěte je jako koncové body JSON.</span><span class="sxs-lookup"><span data-stu-id="dec5d-252">The former provides functionality to generate one or more Swagger documents directly from your API implementation and expose them as JSON endpoints.</span></span> <span data-ttu-id="dec5d-253">K tomu poskytuje embedded verzi nástroje uživatelského rozhraní swagger, která může obsluhovat vaší aplikace a používá technologii generovaného dokumenty Swagger, které se popisují vaše rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="dec5d-253">The latter provides an embedded version of the swagger-ui tool that can be served by your application and powered by the generated Swagger documents to describe your API.</span></span> <span data-ttu-id="dec5d-254">Nejnovější verze Swashbuckle zabalit však tato nastavení u Swashbuckle.AspNetCore metapackage.</span><span class="sxs-lookup"><span data-stu-id="dec5d-254">However, the latest versions of Swashbuckle wrap these with the Swashbuckle.AspNetCore metapackage.</span></span>

<span data-ttu-id="dec5d-255">Všimněte si, že pro projekty webového rozhraní API .NET Core, budete muset použít [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/1.0.0) verze 1.0.0 nebo později.</span><span class="sxs-lookup"><span data-stu-id="dec5d-255">Note that for .NET Core Web API projects, you need to use [Swashbuckle.AspNetCore](https://www.nuget.org/packages/Swashbuckle.AspNetCore/1.0.0) version 1.0.0 or later.</span></span>

<span data-ttu-id="dec5d-256">Po instalaci těchto balíčků NuGet v projektu webového rozhraní API, musíte nakonfigurovat Swagger ve třídě, spuštění, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="dec5d-256">After you have installed these NuGet packages in your Web API project, you need to configure Swagger in the Startup class, as in the following code:</span></span>

```csharp
public class Startup
{
    public IConfigurationRoot Configuration { get; }
    // Other startup code...

    public void ConfigureServices(IServiceCollection services)
    {
        // Other ConfigureServices() code...
        services.AddSwaggerGen();
        services.ConfigureSwaggerGen(options =>
        {
            options.DescribeAllEnumsAsStrings();
            options.SingleApiVersion(new Swashbuckle.Swagger.Model.Info()
            {
                Title = "eShopOnContainers - Catalog HTTP API",
                Version = "v1",
                Description = "The Catalog Microservice HTTP API",
                TermsOfService = "eShopOnContainers terms of service"
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
            .UseSwaggerUi();
    }
}
```

<span data-ttu-id="dec5d-257">Až bude vše Hotovo, můžete spustit aplikaci a procházet vytvoření následujících koncových bodů JSON pro Swagger a uživatelského rozhraní, pomocí adres URL, například tyto:</span><span class="sxs-lookup"><span data-stu-id="dec5d-257">Once this is done, you can start your application and browse the following Swagger JSON and UI endpoints using URLs like these:</span></span>

```json
  http://<your-root-url>/swagger/v1/swagger.json
  
  http://<your-root-url>/swagger/ui
```

<span data-ttu-id="dec5d-258">Dříve jste viděli vygenerované uživatelské rozhraní vytvořené Swashbuckle pro adresu URL podobnou http://&lt;vaše kořenové url &gt; /swagger/uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="dec5d-258">You previously saw the generated UI created by Swashbuckle for a URL like http://&lt;your-root-url&gt;/swagger/ui.</span></span> <span data-ttu-id="dec5d-259">Obrázek 8-9 se také zobrazí jak můžete testovat libovolné metody rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="dec5d-259">In Figure 8-9 you can also see how you can test any API method.</span></span>

![](./media/image10.png)

<span data-ttu-id="dec5d-260">**Obrázek 8-9**.</span><span class="sxs-lookup"><span data-stu-id="dec5d-260">**Figure 8-9**.</span></span> <span data-ttu-id="dec5d-261">Uživatelské rozhraní Swashbuckle testování metoda API nebo položky katalogu</span><span class="sxs-lookup"><span data-stu-id="dec5d-261">Swashbuckle UI testing the Catalog/Items API method</span></span>

<span data-ttu-id="dec5d-262">Obrázek 8-10 ukazuje metadat JSON pro Swagger vygenerovat z mikroslužbu eShopOnContainers (což je nástroje použijte pod) při žádosti o &lt;vaše kořenové url&gt;/swagger/v1/swagger.json pomocí [Postman](https://www.getpostman.com/).</span><span class="sxs-lookup"><span data-stu-id="dec5d-262">Figure 8-10 shows the Swagger JSON metadata generated from the eShopOnContainers microservice (which is what the tools use underneath) when you request &lt;your-root-url&gt;/swagger/v1/swagger.json using [Postman](https://www.getpostman.com/).</span></span>

![](./media/image11.png)

<span data-ttu-id="dec5d-263">**Obrázek 8-10**.</span><span class="sxs-lookup"><span data-stu-id="dec5d-263">**Figure 8-10**.</span></span> <span data-ttu-id="dec5d-264">Metadata JSON pro swagger</span><span class="sxs-lookup"><span data-stu-id="dec5d-264">Swagger JSON metadata</span></span>

<span data-ttu-id="dec5d-265">Je to snadné.</span><span class="sxs-lookup"><span data-stu-id="dec5d-265">It is that simple.</span></span> <span data-ttu-id="dec5d-266">A protože se automaticky vygeneroval, Swagger metadata se zvýší při přidání dalších funkcí do rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="dec5d-266">And because it is automatically generated, the Swagger metadata will grow when you add more functionality to your API.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="dec5d-267">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="dec5d-267">Additional resources</span></span>

-   <span data-ttu-id="dec5d-268">**Rozhraní ASP.NET Web API pomůže Pages pomocí Swagger**
    [*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span><span class="sxs-lookup"><span data-stu-id="dec5d-268">**ASP.NET Web API Help Pages using Swagger**
[*https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger*](https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="dec5d-269">[Předchozí] (mikroslužbu aplikace design.md) [Další] (více-container-aplikace docker-compose.md)</span><span class="sxs-lookup"><span data-stu-id="dec5d-269">[Previous] (microservice-application-design.md) [Next] (multi-container-applications-docker-compose.md)</span></span>
