---
title: "Práce s daty v aplikacích ASP.NET Core"
description: "Architektury moderních webových aplikací pomocí ASP.NET Core a Azure | Práce s daty v asp"
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 648e0a4cdd388cf4a322f0fc049d5dcfca53d54b
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="5c123-103">Práce s daty v aplikacích ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5c123-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="5c123-104">"Data drahocenný jedinou a bude trvat déle, než systémy sami."</span><span class="sxs-lookup"><span data-stu-id="5c123-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>

<span data-ttu-id="5c123-105">Tim Berners-Lee</span><span class="sxs-lookup"><span data-stu-id="5c123-105">Tim Berners-Lee</span></span>

## <a name="summary"></a><span data-ttu-id="5c123-106">Souhrn</span><span class="sxs-lookup"><span data-stu-id="5c123-106">Summary</span></span>

<span data-ttu-id="5c123-107">Přístup k datům je důležitou součástí téměř jakoukoli softwarová aplikace.</span><span class="sxs-lookup"><span data-stu-id="5c123-107">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="5c123-108">ASP.NET Core podporuje celou řadu možností přístupu data, včetně Entity Framework Core (a také Entity Framework 6) a mohou pracovat s žádné rozhraní .NET framework data access.</span><span class="sxs-lookup"><span data-stu-id="5c123-108">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="5c123-109">Výběr z nich přístup k datům framework použít závisí na potřebám aplikace.</span><span class="sxs-lookup"><span data-stu-id="5c123-109">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="5c123-110">Poskytuje abstrakci tyto volby z projektů ApplicationCore a uživatelského rozhraní a zapouzdření podrobnosti implementace v infrastruktuře, pomáhá vytvářet volně párované, možností intenzivního testování softwaru.</span><span class="sxs-lookup"><span data-stu-id="5c123-110">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="5c123-111">Entity Framework Core (pro relační databáze)</span><span class="sxs-lookup"><span data-stu-id="5c123-111">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="5c123-112">Pokud píšete novou aplikaci ASP.NET Core, která musí pracovat s relačních dat, základní Entity Framework (EF jader) je doporučeným způsobem pro vaši aplikaci pro přístup k jeho data.</span><span class="sxs-lookup"><span data-stu-id="5c123-112">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="5c123-113">Základní EF je objekt relační mapper (O/RM), která umožňuje zachovat objekty do a ze zdroje dat vývojáři v rozhraní .NET.</span><span class="sxs-lookup"><span data-stu-id="5c123-113">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="5c123-114">Eliminuje potřebu většinu kódu přístup dat, které vývojáři obvykle potřebovat k zápisu.</span><span class="sxs-lookup"><span data-stu-id="5c123-114">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="5c123-115">Jako ASP.NET Core jsou přepsána EF základní od základu podporuje modulární multiplatformní aplikace.</span><span class="sxs-lookup"><span data-stu-id="5c123-115">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="5c123-116">Přidat do vaší aplikace jako balíčku NuGet, jeho konfiguraci v spuštění a žádostí pomocí vkládání závislostí, bez ohledu na to potřebujete.</span><span class="sxs-lookup"><span data-stu-id="5c123-116">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="5c123-117">Použití jádra EF s databázi systému SQL Server, spusťte následující příkaz dotnet rozhraní příkazového řádku:</span><span class="sxs-lookup"><span data-stu-id="5c123-117">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

<span data-ttu-id="5c123-118">Přidejte balíček Microsoft.EntityFrameworkCore.SqlServer DotNet.</span><span class="sxs-lookup"><span data-stu-id="5c123-118">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span></span>

<span data-ttu-id="5c123-119">Chcete-li přidat podporu pro zdroj dat InMemory pro testování:</span><span class="sxs-lookup"><span data-stu-id="5c123-119">To add support for an InMemory data source, for testing:</span></span>

<span data-ttu-id="5c123-120">Přidejte balíček Microsoft.EntityFrameworkCore.InMemory DotNet.</span><span class="sxs-lookup"><span data-stu-id="5c123-120">dotnet add package Microsoft.EntityFrameworkCore.InMemory</span></span>

### <a name="the-dbcontext"></a><span data-ttu-id="5c123-121">DbContext</span><span class="sxs-lookup"><span data-stu-id="5c123-121">The DbContext</span></span>

<span data-ttu-id="5c123-122">Chcete-li pracovat s EF jádra, je třeba podtřídou třídy DbContext.</span><span class="sxs-lookup"><span data-stu-id="5c123-122">To work with EF Core, you need a subclass of DbContext.</span></span> <span data-ttu-id="5c123-123">Tato třída obsahuje vlastnosti představující kolekce entit, které vaše aplikace bude fungovat s.</span><span class="sxs-lookup"><span data-stu-id="5c123-123">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="5c123-124">Ukázka eShopOnWeb zahrnuje CatalogContext s kolekcí pro položky, značky a typy:</span><span class="sxs-lookup"><span data-stu-id="5c123-124">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

```csharp
public class CatalogContext : DbContext
{
    public CatalogContext(DbContextOptions<CatalogContext> options) : base(options)
    {

    }

    public DbSet<CatalogItem> CatalogItems { get; set; }

    public DbSet<CatalogBrand> CatalogBrands { get; set; }

    public DbSet<CatalogType> CatalogTypes { get; set; }
}
```

<span data-ttu-id="5c123-125">Vaše DbContext musí mít konstruktor, který přijímá DbContextOptions a předat tento argument základní konstruktor DbContext.</span><span class="sxs-lookup"><span data-stu-id="5c123-125">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="5c123-126">Všimněte si, že pokud máte pouze jeden DbContext v aplikaci, můžete předat instanci DbContextOptions, ale pokud máte více než jeden musíte použít obecné DbContextOptions<T> předávání v vašeho typu DbContext jako obecný parametr typu.</span><span class="sxs-lookup"><span data-stu-id="5c123-126">Note that if you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="5c123-127">Konfigurace EF jádra</span><span class="sxs-lookup"><span data-stu-id="5c123-127">Configuring EF Core</span></span>

<span data-ttu-id="5c123-128">V aplikaci ASP.NET Core obvykle nakonfigurujete EF základní ve své metodě ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="5c123-128">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="5c123-129">Základní EF používá DbContextOptionsBuilder, která podporuje několik užitečné rozšiřující metody pro zjednodušit konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="5c123-129">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="5c123-130">Pokud chcete nakonfigurovat CatalogContext používat databázi systému SQL Server s připojovacím řetězcem definované v konfiguraci, by přidejte následující kód do ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="5c123-130">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="5c123-131">Chcete použít databázi v paměti:</span><span class="sxs-lookup"><span data-stu-id="5c123-131">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="5c123-132">Po instalaci základní EF, vytvořili podřízené typ DbContext a nakonfigurovat v ConfigureServices, budete chtít použít EF jádra.</span><span class="sxs-lookup"><span data-stu-id="5c123-132">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="5c123-133">Můžete požádat o instanci typu DbContext v jakoukoli službu, která jej potřebuje a začít pracovat s trvalou pomocí LINQ, jako kdyby byly jednoduše v kolekci entit.</span><span class="sxs-lookup"><span data-stu-id="5c123-133">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="5c123-134">Základní EF funguje překladu vaší LINQ – výrazy do dotazů SQL pro ukládání a načítání vaše data.</span><span class="sxs-lookup"><span data-stu-id="5c123-134">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="5c123-135">Můžete zobrazit dotazy EF základní provádí konfiguraci protokoly a zajištění jeho úroveň je nastavena alespoň na informace, jak ukazuje obrázek 8-1.</span><span class="sxs-lookup"><span data-stu-id="5c123-135">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![](./media/image8-1.png)

<span data-ttu-id="5c123-136">Obrázek 8-1 protokolování EF základní dotazy do konzoly nástroje</span><span class="sxs-lookup"><span data-stu-id="5c123-136">Figure 8-1 Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="5c123-137">Načítání a ukládání dat</span><span class="sxs-lookup"><span data-stu-id="5c123-137">Fetching and Storing Data</span></span>

<span data-ttu-id="5c123-138">K načtení dat z EF jádra, přístup k příslušné vlastnosti a pomocí LINQ filtrovat výsledek.</span><span class="sxs-lookup"><span data-stu-id="5c123-138">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="5c123-139">LINQ můžete použít také k provedení projekce, transformace jeden typ výsledku.</span><span class="sxs-lookup"><span data-stu-id="5c123-139">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="5c123-140">V následujícím příkladu by načíst CatalogBrands, seřazené podle názvu, filtrovaná podle jejich vlastnost povoleno a promítnuta na typ SelectListItem:</span><span class="sxs-lookup"><span data-stu-id="5c123-140">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="5c123-141">Je důležité v předchozím příkladu a přidejte volání do ToListAsync okamžitě provádění dotazu.</span><span class="sxs-lookup"><span data-stu-id="5c123-141">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="5c123-142">Příkaz, jinak hodnota přiřadí položku IQueryable<SelectListItem> k brandItems, který nebude provedeno, dokud je ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="5c123-142">Otherwise, the statement will assign an IQueryable<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="5c123-143">Existují výhody a nevýhody vrací IQueryable výsledky z metod.</span><span class="sxs-lookup"><span data-stu-id="5c123-143">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="5c123-144">Umožňuje na dotaz, který EF základní vytvoří další upravovat, ale může taky vést chyb vzniklých pouze za běhu, pokud operace jsou přidány do dotazu, který nemůže překládat EF jádra.</span><span class="sxs-lookup"><span data-stu-id="5c123-144">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="5c123-145">Obecně je bezpečnější k předání všechny filtry do metoda provádí přístup k datům a vraťte se zpět kolekci v paměti (například seznam<T>) jako výsledek.</span><span class="sxs-lookup"><span data-stu-id="5c123-145">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List<T>) as the result.</span></span>

<span data-ttu-id="5c123-146">Základní EF sleduje změny u entit, který je načte z trvalost.</span><span class="sxs-lookup"><span data-stu-id="5c123-146">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="5c123-147">Pokud chcete uložit změny do sledované entity, stačí zavolat metodu SaveChanges pro dbcontext, ujistěte se, že je stejné instanci DbContext, která byla použita k načtení entity.</span><span class="sxs-lookup"><span data-stu-id="5c123-147">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="5c123-148">Přidávání a odebírání entity je přímo na příslušnou vlastnost DbSet, znovu s volání SaveChanges příkazy databáze.</span><span class="sxs-lookup"><span data-stu-id="5c123-148">Adding and removing entities is directly on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="5c123-149">Následující příklad ukazuje, přidání, aktualizace a odstranění entity z trvalost.</span><span class="sxs-lookup"><span data-stu-id="5c123-149">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

```csharp
// create
var newBrand = new CatalogBrand() { Brand = "Acme" };
_context.Add(newBrand);
await _context.SaveChangesAsync();

// read and update
var existingBrand = _context.CatalogBrands.Find(1);
existingBrand.Brand = "Updated Brand";
await _context.SaveChangesAsync();

// read and delete (alternate Find syntax)
var brandToDelete = _context.Find<CatalogBrand>(2);
_context.CatalogBrands.Remove(brandToDelete);
await _context.SaveChangesAsync();
```

<span data-ttu-id="5c123-150">Jádro EF podporuje i synchronní a asynchronní metody pro načítání a ukládání.</span><span class="sxs-lookup"><span data-stu-id="5c123-150">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="5c123-151">V webových aplikací se doporučuje použití vzoru async/await s asynchronní metody, tak, aby webový server vláken nejsou blokované při čekání na dokončení operací přístupu pro data.</span><span class="sxs-lookup"><span data-stu-id="5c123-151">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="5c123-152">Načítají se související Data</span><span class="sxs-lookup"><span data-stu-id="5c123-152">Fetching Related Data</span></span>

<span data-ttu-id="5c123-153">Když EF základní načte entity, naplní všechny vlastnosti, které jsou uloženy přímo s dané entity v databázi.</span><span class="sxs-lookup"><span data-stu-id="5c123-153">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="5c123-154">Navigační vlastnosti, jako je například seznam entit v relaci, nejsou naplněny a může mít jejich nastavená na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="5c123-154">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="5c123-155">Tím se zajistí, že EF jádra není načítání více dat, než je potřeba, který je obzvláště důležité pro webové aplikace, které musí rychle zpracovávat požadavky a odpovědi vrátit účinným způsobem.</span><span class="sxs-lookup"><span data-stu-id="5c123-155">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="5c123-156">Zahrnout relace se entitu s využitím *přes načítání*, určete vlastnost použití metody rozšíření zahrnout v dotazu, jak je znázorněno:</span><span class="sxs-lookup"><span data-stu-id="5c123-156">To include relationships with an entity using *eager loading*, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="5c123-157">Může obsahovat více vztahů, a může zahrnovat i dílčí relace pomocí ThenInclude.</span><span class="sxs-lookup"><span data-stu-id="5c123-157">You can include multiple relationships, and you can also include sub-relationships using ThenInclude.</span></span> <span data-ttu-id="5c123-158">Základní EF provede jeden dotaz pro načtení výslednou sadu entit.</span><span class="sxs-lookup"><span data-stu-id="5c123-158">EF Core will execute a single query to retrieve the resulting set of entities.</span></span>

<span data-ttu-id="5c123-159">Další možností pro načítání související data se má používat *explicitní načítání*.</span><span class="sxs-lookup"><span data-stu-id="5c123-159">Another option for loading related data is to use *explicit loading*.</span></span> <span data-ttu-id="5c123-160">Explicitní načítání umožňuje načíst další data do entity, která již byla načtena.</span><span class="sxs-lookup"><span data-stu-id="5c123-160">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="5c123-161">Vzhledem k tomu, že to zahrnuje samostatné žádosti do databáze, se nedoporučuje pro webové aplikace, které by měl minimalizovat počet databáze odezev provedené na základě požadavku.</span><span class="sxs-lookup"><span data-stu-id="5c123-161">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="5c123-162">*Opožděného načítání* je funkce, která automaticky načte související data, protože odkazuje na aplikaci.</span><span class="sxs-lookup"><span data-stu-id="5c123-162">*Lazy loading* is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="5c123-163">Není aktuálně podporována EF jádra, ale jako s explicitní načítání je obvykle třeba zakázat pro webové aplikace.</span><span class="sxs-lookup"><span data-stu-id="5c123-163">It's not currently supported by EF Core, but as with explicit loading it should typically be disabled for web applications.</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="5c123-164">Odolné připojení</span><span class="sxs-lookup"><span data-stu-id="5c123-164">Resilient Connections</span></span>

<span data-ttu-id="5c123-165">Příležitostně externím prostředkům, jako jsou databáze SQL pravděpodobně není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="5c123-165">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="5c123-166">V případě dočasné nedostupnosti aplikace, můžete použít logika opakovaných pokusů předejdete vyvolání k výjimce.</span><span class="sxs-lookup"><span data-stu-id="5c123-166">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="5c123-167">Tento postup se obvykle označuje jako *odolnost připojení*.</span><span class="sxs-lookup"><span data-stu-id="5c123-167">This technique is commonly referred to as *connection resiliency*.</span></span> <span data-ttu-id="5c123-168">Můžete implementovat vaše [vlastní znova s exponenciálního omezení rychlosti](https://docs.microsoft.com/azure/architecture/patterns/retry) technika pokusem o rety s exponenciálně roste doba čekání, až maximální počet opakování byl dosažen.</span><span class="sxs-lookup"><span data-stu-id="5c123-168">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to rety with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="5c123-169">Tento postup zahrnuje fakt, že cloudové prostředky občas je pravděpodobně není k dispozici na krátkou dobu, což vede k selhání některých požadavků.</span><span class="sxs-lookup"><span data-stu-id="5c123-169">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="5c123-170">Pro databáze SQL Azure Entity Framework Core již poskytuje interní databáze připojení odolnost proti chybám a zkuste to znovu logiku.</span><span class="sxs-lookup"><span data-stu-id="5c123-170">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="5c123-171">Ale musíte povolit strategii provádění Entity Framework pro každé připojení DbContext, pokud chcete mít odolné EF základní připojení.</span><span class="sxs-lookup"><span data-stu-id="5c123-171">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="5c123-172">Například následující kód na úrovni připojení EF základní umožňuje odolné připojení SQL, které jsou opakovat, pokud se nepovede připojit.</span><span class="sxs-lookup"><span data-stu-id="5c123-172">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

```csharp
// Startup.cs from any ASP.NET Core Web API
public class Startup
{
    public IServiceProvider ConfigureServices(IServiceCollection services)
    {
        //...
        services.AddDbContext<OrderingContext>(options =>
        {
            options.UseSqlServer(Configuration["ConnectionString"],
            sqlServerOptionsAction: sqlOptions =>
        {
            sqlOptions.EnableRetryOnFailure(
            maxRetryCount: 5,
            maxRetryDelay: TimeSpan.FromSeconds(30), 
            errorNumbersToAdd: null); 
        });
    });
}
//...
```

  #### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="5c123-173">Strategie provádění a pomocí zahájení transakce a více DbContexts explicitních transakcí</span><span class="sxs-lookup"><span data-stu-id="5c123-173">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span> 
  
  <span data-ttu-id="5c123-174">Když opakování jsou povolena v připojení EF jádra, stane jednotlivých operací, které můžete provádět pomocí EF základní vlastní dá se zkusit znovu operaci.</span><span class="sxs-lookup"><span data-stu-id="5c123-174">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="5c123-175">Každý dotaz a každé volání SaveChanges bude zopakován jako jednotku, pokud dojde k přechodné chybě.</span><span class="sxs-lookup"><span data-stu-id="5c123-175">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>
  
  <span data-ttu-id="5c123-176">Ale pokud kódu inicializuje transakci pomocí zahájení transakce, definujete vlastní skupiny operací, které musí být považovány za jednotku – všechno uvnitř transakce se vrátila zpět v případě, že dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="5c123-176">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="5c123-177">Pokud se pokusíte provést tuto transakci, při použití EF strategii provádění (zásady opakování) a zahrnují několik SaveChanges z více DbContexts v něm uvidíte výjimku podobně jako tento.</span><span class="sxs-lookup"><span data-stu-id="5c123-177">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="5c123-178">System.InvalidOperationException: V nakonfigurované strategii provádění 'SqlServerRetryingExecutionStrategy' nepodporuje transakce inicializované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="5c123-178">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="5c123-179">Použijte strategii provádění vrácený 'DbContext.Database.CreateExecutionStrategy()' provádět všechny operace v rámci transakce jako nevyřeší jednotku.</span><span class="sxs-lookup"><span data-stu-id="5c123-179">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="5c123-180">Řešení je ručně vyvolání strategie provádění EF s představující všechno delegáta, který je třeba provést.</span><span class="sxs-lookup"><span data-stu-id="5c123-180">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="5c123-181">Pokud dojde k přechodné chybě, bude strategii provádění znovu vyvolání delegáta.</span><span class="sxs-lookup"><span data-stu-id="5c123-181">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="5c123-182">Následující kód ukazuje, jak implementovat tohoto přístupu:</span><span class="sxs-lookup"><span data-stu-id="5c123-182">The following code shows how to implement this approach:</span></span>

```csharp
// Use of an EF Core resiliency strategy when using multiple DbContexts
// within an explicit transaction
// See:
// https://docs.microsoft.com/ef/core/miscellaneous/connection-resiliency
var strategy = _catalogContext.Database.CreateExecutionStrategy(); 
await strategy.ExecuteAsync(async () =>
{
    // Achieving atomicity between original Catalog database operation and the
    // IntegrationEventLog thanks to a local transaction
    using (var transaction = _catalogContext.Database.BeginTransaction())
    {
        _catalogContext.CatalogItems.Update(catalogItem);
        await _catalogContext.SaveChangesAsync();
        
        // Save to EventLog only if product price changed
        if (raiseProductPriceChangedEvent)
        await _integrationEventLogService.SaveEventAsync(priceChangedEvent);
        transaction.Commit();
    }
});
```

<span data-ttu-id="5c123-183">Je první DbContext \_catalogContext a druhý je DbContext v rámci \_integrationEventLogService objektu.</span><span class="sxs-lookup"><span data-stu-id="5c123-183">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="5c123-184">Nakonec potvrzení akce bude provedena více DbContexts a pomocí strategii provádění EF.</span><span class="sxs-lookup"><span data-stu-id="5c123-184">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="5c123-185">Odkazy – základní Entity Framework</span><span class="sxs-lookup"><span data-stu-id="5c123-185">References – Entity Framework Core</span></span>
> - <span data-ttu-id="5c123-186">**EF základní dokumentace**</span><span class="sxs-lookup"><span data-stu-id="5c123-186">**EF Core Docs**</span></span>  
> <span data-ttu-id="5c123-187"><https://docs.microsoft.com/ef/></span><span class="sxs-lookup"><span data-stu-id="5c123-187"><https://docs.microsoft.com/ef/></span></span>
> - <span data-ttu-id="5c123-188">**EF jádra: Související Data**</span><span class="sxs-lookup"><span data-stu-id="5c123-188">**EF Core: Related Data**</span></span>  
> <span data-ttu-id="5c123-189"><https://docs.microsoft.com/ef/core/querying/related-data></span><span class="sxs-lookup"><span data-stu-id="5c123-189"><https://docs.microsoft.com/ef/core/querying/related-data></span></span>
> - <span data-ttu-id="5c123-190">**Vyhněte se opožděného načítání entity v aplikacích ASPNET**</span><span class="sxs-lookup"><span data-stu-id="5c123-190">**Avoid Lazy Loading Entities in ASPNET Applications**</span></span>  
> <span data-ttu-id="5c123-191"><http://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span><span class="sxs-lookup"><span data-stu-id="5c123-191"><http://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span></span>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="5c123-192">Základní EF nebo micro ORM?</span><span class="sxs-lookup"><span data-stu-id="5c123-192">EF Core or micro-ORM?</span></span>

<span data-ttu-id="5c123-193">Při EF základní je je služba skvělou volbou pro správu trvalosti a ve většině případů zapouzdří podrobnosti databáze z vývojáři aplikace, není pouze volbu.</span><span class="sxs-lookup"><span data-stu-id="5c123-193">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it is not the only choice.</span></span> <span data-ttu-id="5c123-194">Další alternativou populární open source je [Dapper](https://github.com/StackExchange/Dapper), takzvané micro ORM.</span><span class="sxs-lookup"><span data-stu-id="5c123-194">Another popular open source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="5c123-195">Micro-ORM je lightweight, méně plnohodnotný nástroj pro mapování objektů na datové struktury.</span><span class="sxs-lookup"><span data-stu-id="5c123-195">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="5c123-196">V případě Dapper návrh cíle soustředit na výkon, nikoli plně zapouzdřením základní dotazy používá načíst a aktualizovat data.</span><span class="sxs-lookup"><span data-stu-id="5c123-196">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="5c123-197">Vzhledem k tomu, že ji nebude abstraktní SQL od vývojáře, Dapper "blíže počítač" a umožňuje vývojářům zápisu přesný operace přístupu k dotazy, které chtějí používat pro daná data.</span><span class="sxs-lookup"><span data-stu-id="5c123-197">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="5c123-198">Základní EF má dvě důležité funkce poskytuje které oddělení od Dapper, ale také přidat do jeho nároky na výkon.</span><span class="sxs-lookup"><span data-stu-id="5c123-198">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="5c123-199">První je překlad z LINQ – výrazy do SQL.</span><span class="sxs-lookup"><span data-stu-id="5c123-199">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="5c123-200">Tyto překlady jsou uložené v mezipaměti, ale i tak je zatížení při provádění je poprvé.</span><span class="sxs-lookup"><span data-stu-id="5c123-200">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="5c123-201">Druhá je sledování změn na entity (tak, aby příkazy efektivní aktualizace může být generována).</span><span class="sxs-lookup"><span data-stu-id="5c123-201">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="5c123-202">Toto chování může být vypnuto pro konkrétní dotazy pomocí AsNotTracking rozšíření.</span><span class="sxs-lookup"><span data-stu-id="5c123-202">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="5c123-203">Základní EF vytvoří také dotazy SQL, které obvykle jsou velmi efektivně a v každém případě zcela přijatelné z hlediska výkonu, ale pokud je třeba přesně řídit provedení přesné dotazu, abyste mohli předávat vlastní SQL (nebo provedení uložené procedury) pomocí EF Příliš základní.</span><span class="sxs-lookup"><span data-stu-id="5c123-203">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="5c123-204">V takovém případě Dapper stále překonává výkonem EF jádra, ale pouze mírně.</span><span class="sxs-lookup"><span data-stu-id="5c123-204">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="5c123-205">Uvede Julie Lerman některé údaje o výkonu v její může článku na webu MSDN 2016 [Dapper Entity Framework a hybridní aplikace](https://msdn.microsoft.com/magazine/mt703432.aspx).</span><span class="sxs-lookup"><span data-stu-id="5c123-205">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://msdn.microsoft.com/magazine/mt703432.aspx).</span></span> <span data-ttu-id="5c123-206">Další srovnávací test data o výkonu pro celou řadu metod přístupu dat můžete najít na [webu Dapper](https://github.com/StackExchange/Dapper).</span><span class="sxs-lookup"><span data-stu-id="5c123-206">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="5c123-207">Pokud chcete zobrazit, jak se liší od EF základní syntaxe Dapper, vezměte v úvahu tyto dvě verze stejné metodu pro načtení seznamu položek:</span><span class="sxs-lookup"><span data-stu-id="5c123-207">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

```csharp
// EF Core
private readonly CatalogContext _context;
public async Task<IEnumerable<CatalogType>> GetCatalogTypes()
{
    return await _context.CatalogTypes.ToListAsync();
}

// Dapper
private readonly SqlConnection _conn;
public async Task<IEnumerable<CatalogType>> GetCatalogTypesWithDapper()
{
    return await _conn.QueryAsync<CatalogType>("SELECT * FROM CatalogType");
}
```

<span data-ttu-id="5c123-208">Pokud potřebujete k vytváření složitějších objekt grafy s Dapper, budete muset zápisu přidružené dotazy (na rozdíl od přidání zahrnutí, stejně jako v základní EF).</span><span class="sxs-lookup"><span data-stu-id="5c123-208">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="5c123-209">Tato možnost je podporována prostřednictvím řady různých syntaxe, včetně funkci více mapování, která umožňuje mapování jednotlivých řádků na více objektů namapované.</span><span class="sxs-lookup"><span data-stu-id="5c123-209">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="5c123-210">Například danou třídu Post s vlastností vlastníka typu uživatele, následující příkaz SQL vrátí všechna potřebná data:</span><span class="sxs-lookup"><span data-stu-id="5c123-210">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join \#Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="5c123-211">Každý vrácený řádek obsahuje data uživatele a Post.</span><span class="sxs-lookup"><span data-stu-id="5c123-211">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="5c123-212">Vzhledem k tomu, že data uživatele by měl být připojen následná data přes vlastnost jeho vlastníka, se používá následující funkce:</span><span class="sxs-lookup"><span data-stu-id="5c123-212">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="5c123-213">Výpis úplného kódu mají vracet kolekci příspěvcích s jejich vlastnost Owner naplněný daty uživatele by byl:</span><span class="sxs-lookup"><span data-stu-id="5c123-213">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="5c123-214">Protože nabízí menší zapouzdření, Dapper vyžaduje vývojáři vědět více o tom, jak mají uložená data, jak efektivní dotazování a napsat další kód se jej načíst.</span><span class="sxs-lookup"><span data-stu-id="5c123-214">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="5c123-215">Když se změní model, místo jednoduše vytváření nové migrace (jiné EF základní funkce), a aktualizovat informace o mapování na jednom místě v konstruktoru DbContext každý dotaz, který je ovlivněno musí aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="5c123-215">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="5c123-216">Tyto dotazy mají není kompilace čas záruky, takže se může zalomit za běhu v reakci na změny do modelu nebo databáze, což chyby obtížné rychle zjistit.</span><span class="sxs-lookup"><span data-stu-id="5c123-216">These queries have not compile time guarantees, so they may break at runtime in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="5c123-217">Za těchto kompromisy Dapper nabízí velmi vysoký výkon.</span><span class="sxs-lookup"><span data-stu-id="5c123-217">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="5c123-218">Pro většinu aplikací a většina částí téměř všechny aplikace nabízí základní EF přijatelný výkon.</span><span class="sxs-lookup"><span data-stu-id="5c123-218">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="5c123-219">Proto se jeho výhody produktivitu vývojářů pravděpodobně převáží nad jeho nároky na výkon.</span><span class="sxs-lookup"><span data-stu-id="5c123-219">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="5c123-220">Pro dotazy, které můžete využít ukládání do mezipaměti, skutečný dotaz může spustit pouze malá velikost procento doby, což poměrně malý dotaz moot rozdíly výkonu.</span><span class="sxs-lookup"><span data-stu-id="5c123-220">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="5c123-221">SQL nebo NoSQL</span><span class="sxs-lookup"><span data-stu-id="5c123-221">SQL or NoSQL</span></span>

<span data-ttu-id="5c123-222">Obvyklým relační databáze jako SQL Server mají potřebná hlavně marketplace pro úložiště dat, ale nejsou k dispozici pouze řešení.</span><span class="sxs-lookup"><span data-stu-id="5c123-222">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="5c123-223">Databáze NoSQL, jako [MongoDB](https://www.mongodb.com/what-is-mongodb) nabízejí jiný přístup k ukládání objektů.</span><span class="sxs-lookup"><span data-stu-id="5c123-223">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="5c123-224">Další možností je místo mapování objektů na tabulky a řádky, serializaci celý objekt grafu a uložit výsledek.</span><span class="sxs-lookup"><span data-stu-id="5c123-224">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="5c123-225">Výhody tohoto přístupu alespoň na začátku jsou jednoduchost a výkonu.</span><span class="sxs-lookup"><span data-stu-id="5c123-225">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="5c123-226">Je určitě jednodušší pro uložení jedné serializovaný objekt s klíčem, než se rozložit na mnoho tabulky se vztahy objektu a aktualizací a řádky, které může se změnily od posledního objekt načíst z databáze.</span><span class="sxs-lookup"><span data-stu-id="5c123-226">It's certainly simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="5c123-227">Podobně načítání a deserializaci jeden objekt z úložiště na základě klíčů je obvykle mnohem rychlejší a snadnější než komplexní spojení nebo více dotazů databáze, které jsou potřeba plně tvoří stejný objekt z relační databáze.</span><span class="sxs-lookup"><span data-stu-id="5c123-227">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="5c123-228">Nedostatek zámky nebo transakce nebo pevného schématu také díky databáze NoSQL velmi přenášejí škálování mezi mnoho počítačů, podpora velmi rozsáhlých datových sad.</span><span class="sxs-lookup"><span data-stu-id="5c123-228">The lack of locks or transactions or a fixed schema also makes NoSQL databases very amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="5c123-229">Na druhé straně databáze NoSQL (jako jsou obvykle nazývá) mít svoje nevýhody.</span><span class="sxs-lookup"><span data-stu-id="5c123-229">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="5c123-230">Relační databáze pomocí normalizaci zajistit konzistenci a zamezit tak duplicitních dat.</span><span class="sxs-lookup"><span data-stu-id="5c123-230">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="5c123-231">To snižuje celkové velikosti databáze a zajistí, že aktualizace sdílených dat jsou k dispozici okamžitě celé databáze.</span><span class="sxs-lookup"><span data-stu-id="5c123-231">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="5c123-232">V relační databázi může tabulky adres referenční tabulku země podle ID, tak, že pokud se změnily název země, záznamy adres by využívat aktualizace bez sami nutnosti ho aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="5c123-232">In a relational database, an Address table might reference a Country table by ID, such that if a country's name were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="5c123-233">Ale v databázi NoSQL, adresa a její přidružené země může serializovat v rámci uložené objektů.</span><span class="sxs-lookup"><span data-stu-id="5c123-233">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="5c123-234">Aktualizace název země by vyžadovaly všechny tyto objekty k aktualizaci, místo jednoho řádku.</span><span class="sxs-lookup"><span data-stu-id="5c123-234">An update to a country name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="5c123-235">Relační databáze můžete také zajistit relační integritu vynucením pravidla, jako jsou cizí klíče.</span><span class="sxs-lookup"><span data-stu-id="5c123-235">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="5c123-236">Databáze NoSQL obvykle nenabízejí takové omezení na svá data.</span><span class="sxs-lookup"><span data-stu-id="5c123-236">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="5c123-237">Další složitost NoSQL databáze musí řešit je správa verzí.</span><span class="sxs-lookup"><span data-stu-id="5c123-237">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="5c123-238">Při změně vlastnosti objektu, nemusí být možné deserializovat od minulých verzí, které jste uložili.</span><span class="sxs-lookup"><span data-stu-id="5c123-238">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="5c123-239">Proto musí být aktualizovány všechny existující objekty, které mají serializovaných (předchozí) verze objektu, tak, aby odpovídala nové schématem.</span><span class="sxs-lookup"><span data-stu-id="5c123-239">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="5c123-240">Toto není koncepčně liší od relační databázi, kde je někdy změní schéma vyžadují skriptů pro aktualizaci nebo mapování aktualizace.</span><span class="sxs-lookup"><span data-stu-id="5c123-240">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="5c123-241">Počet položek, které se musí upravit, je však často mnohem větší v přístupu NoSQL, protože existuje více duplicitních dat.</span><span class="sxs-lookup"><span data-stu-id="5c123-241">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="5c123-242">Je možné v databáze NoSQL uložit více verzí objektů, něco pevného schématu relačních databází obvykle nepodporují.</span><span class="sxs-lookup"><span data-stu-id="5c123-242">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="5c123-243">Ale v tomto případě kód aplikace potřeba účet existenci předchozích verzích objektů a přidávání dalších složitost.</span><span class="sxs-lookup"><span data-stu-id="5c123-243">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="5c123-244">Databáze NoSQL obvykle Nevynucovat [kyseliny](http://en.wikipedia.org/wiki/ACID), což znamená, že mají výkon a škálovatelnost výhody nad relačních databází.</span><span class="sxs-lookup"><span data-stu-id="5c123-244">NoSQL databases typically do not enforce [ACID](http://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="5c123-245">Jsou vhodné řešení pro velmi rozsáhlých datových sad a objektů, které nejsou vhodné řešení pro úložiště v struktury normalizovaný tabulky.</span><span class="sxs-lookup"><span data-stu-id="5c123-245">They're well-suited to extremely large datasets and objects that are not well-suited to storage in normalized table structures.</span></span> <span data-ttu-id="5c123-246">Neexistuje žádný důvod, proč jednu aplikaci nelze využít výhod obě relační a vhodné databáze NoSQL, každý pomocí, kde je nejvhodnější.</span><span class="sxs-lookup"><span data-stu-id="5c123-246">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-documentdb"></a><span data-ttu-id="5c123-247">Azure DocumentDB</span><span class="sxs-lookup"><span data-stu-id="5c123-247">Azure DocumentDB</span></span>

<span data-ttu-id="5c123-248">Azure DocumentDB je plně spravovaná služba databáze NoSQL, která nabízí úložiště založené na cloudu data bez schémat.</span><span class="sxs-lookup"><span data-stu-id="5c123-248">Azure DocumentDB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="5c123-249">DocumentDB je vytvořené pro vysoký a předvídatelný výkon, vysokou dostupnost, elastické škálování a globální distribuční.</span><span class="sxs-lookup"><span data-stu-id="5c123-249">DocumentDB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="5c123-250">Přestože jsou databáze NoSQL, vývojáři mohou použít bohatý a známých možnosti dotazů SQL na JSON data.</span><span class="sxs-lookup"><span data-stu-id="5c123-250">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="5c123-251">Všechny prostředky v DocumentDB jsou ukládány jako dokumenty JSON.</span><span class="sxs-lookup"><span data-stu-id="5c123-251">All resources in DocumentDB are stored as JSON documents.</span></span> <span data-ttu-id="5c123-252">Prostředky se spravují jako *položky*, které jsou dokumenty obsahující metadata, a *kanály*, které jsou kolekce položek.</span><span class="sxs-lookup"><span data-stu-id="5c123-252">Resources are managed as *items*, which are documents containing metadata, and *feeds*, which are collections of items.</span></span> <span data-ttu-id="5c123-253">Obrázek 8-2 ukazuje vztah mezi různými prostředky DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="5c123-253">Figure 8-2 shows the relationship between different DocumentDB resources.</span></span>


![Hierarchický vztah mezi prostředky v DocumentDB, databázi NoSQL JSON](./media/image8-2.png)

<span data-ttu-id="5c123-255">**Obrázek 8-2.**</span><span class="sxs-lookup"><span data-stu-id="5c123-255">**Figure 8-2.**</span></span> <span data-ttu-id="5c123-256">DocumentDB prostředků organizace.</span><span class="sxs-lookup"><span data-stu-id="5c123-256">DocumentDB resource organization.</span></span>

<span data-ttu-id="5c123-257">Dotazovací jazyk DocumentDB je jednoduché, ale výkonné rozhraní pro dotazování dokumentů JSON.</span><span class="sxs-lookup"><span data-stu-id="5c123-257">The DocumentDB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="5c123-258">Jazyk podporuje podmnožinu gramatiky ANSI SQL a přidává těsnou integraci objekt jazyka JavaScript, pole, vytvářením objektů a volání funkce.</span><span class="sxs-lookup"><span data-stu-id="5c123-258">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="5c123-259">**Odkazy – DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="5c123-259">**References – DocumentDB**</span></span>

-   <span data-ttu-id="5c123-260">DocumentDB Introduction\\</span><span class="sxs-lookup"><span data-stu-id="5c123-260">DocumentDB Introduction\\</span></span>
    <span data-ttu-id="5c123-261"><https://docs.microsoft.com/azure/documentdb/documentdb-introduction></span><span class="sxs-lookup"><span data-stu-id="5c123-261"><https://docs.microsoft.com/azure/documentdb/documentdb-introduction></span></span>

## <a name="other-persistence-options"></a><span data-ttu-id="5c123-262">Další možnosti trvalost</span><span class="sxs-lookup"><span data-stu-id="5c123-262">Other Persistence Options</span></span>

<span data-ttu-id="5c123-263">Také na relační a možnosti úložiště typu NoSQL aplikace ASP.NET Core slouží k uložení různých formátů data a soubory způsobem Cloudová, škálovatelná Azure Storage.</span><span class="sxs-lookup"><span data-stu-id="5c123-263">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="5c123-264">Azure Storage je nesmírně škálovatelná služba, abyste mohli začít se ukládání malé množství dat a škálování až ukládání stovkami nebo terabajtů, pokud vaše aplikace vyžaduje, aby ho.</span><span class="sxs-lookup"><span data-stu-id="5c123-264">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="5c123-265">Úložiště Azure podporuje čtyři typy dat:</span><span class="sxs-lookup"><span data-stu-id="5c123-265">Azure Storage supports four kinds of data:</span></span>

-   <span data-ttu-id="5c123-266">Pro nestrukturovaná text nebo binární úložiště, které jsou také označovány jako úložiště objektů úložiště objektů BLOB.</span><span class="sxs-lookup"><span data-stu-id="5c123-266">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

-   <span data-ttu-id="5c123-267">Úložiště Table pro strukturované datové sady, přístupné přes řádek klíče.</span><span class="sxs-lookup"><span data-stu-id="5c123-267">Table Storage for structured datasets, accessible via row keys.</span></span>

-   <span data-ttu-id="5c123-268">Fronty úložiště pro zasílání zpráv spolehlivého na základě fronty.</span><span class="sxs-lookup"><span data-stu-id="5c123-268">Queue Storage for reliable queue-based messaging.</span></span>

-   <span data-ttu-id="5c123-269">Úložiště souborů pro přístup ke sdílenému souboru mezi virtuálními počítači Azure a místními aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="5c123-269">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="5c123-270">**Odkazy – úložiště Azure**</span><span class="sxs-lookup"><span data-stu-id="5c123-270">**References – Azure Storage**</span></span>

-   <span data-ttu-id="5c123-271">Introduction\ úložiště Azure</span><span class="sxs-lookup"><span data-stu-id="5c123-271">Azure Storage Introduction\\</span></span>
    <span data-ttu-id="5c123-272"><https://docs.microsoft.com/azure/storage/storage-introduction></span><span class="sxs-lookup"><span data-stu-id="5c123-272"><https://docs.microsoft.com/azure/storage/storage-introduction></span></span>

## <a name="caching"></a><span data-ttu-id="5c123-273">Caching</span><span class="sxs-lookup"><span data-stu-id="5c123-273">Caching</span></span>

<span data-ttu-id="5c123-274">Ve webových aplikacích každý webový požadavek by se měly dokončit v možná nejkratší době.</span><span class="sxs-lookup"><span data-stu-id="5c123-274">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="5c123-275">Jedním ze způsobů jak toho docílit je omezit počet externí volání, které server musíte provést žádost dokončit.</span><span class="sxs-lookup"><span data-stu-id="5c123-275">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="5c123-276">Ukládání do mezipaměti zahrnuje ukládání kopii dat na serveru (nebo jiného úložiště dat, který je více než zdroj dat snadno dotaz).</span><span class="sxs-lookup"><span data-stu-id="5c123-276">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="5c123-277">Webové aplikace a hlavně-zabezpečené ověřování HESLA tradiční webových aplikací, potřebujete k vytvoření celé uživatelské rozhraní s každou žádostí.</span><span class="sxs-lookup"><span data-stu-id="5c123-277">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="5c123-278">To často zahrnuje, vytvoření řadu stejné databázové dotazy opakovaně z jednoho uživatele požadavku na další.</span><span class="sxs-lookup"><span data-stu-id="5c123-278">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="5c123-279">Ve většině případů tato data změní zřídka, takže je málo důvod neustále požádat o z databáze.</span><span class="sxs-lookup"><span data-stu-id="5c123-279">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="5c123-280">ASP.NET Core podporuje ukládání odpovědí do mezipaměti, pro ukládání do mezipaměti celé stránky a ukládání do mezipaměti dat, která podporuje podrobnější chování ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="5c123-280">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="5c123-281">Při implementaci ukládání do mezipaměti, je důležité mít na paměti oddělené oblasti zájmu.</span><span class="sxs-lookup"><span data-stu-id="5c123-281">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="5c123-282">Vyhněte se implementace logiky ukládaní do mezipaměti v logika data přístup, nebo v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="5c123-282">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="5c123-283">Místo toho zapouzdření ukládání do mezipaměti v jeho vlastní třídy a konfiguraci použít ke správě své chování.</span><span class="sxs-lookup"><span data-stu-id="5c123-283">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="5c123-284">To odpovídá otevřete/uzavřeno a jeden odpovědnost zásady a bude jednodušší pro správu, jak používat ukládání do mezipaměti v aplikaci jako roste.</span><span class="sxs-lookup"><span data-stu-id="5c123-284">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="5c123-285">Ukládání odpovědí do mezipaměti ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="5c123-285">ASP.NET Core Response Caching</span></span>

<span data-ttu-id="5c123-286">Jádro ASP.NET podporuje dvě úrovně ukládání odpovědí do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="5c123-286">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="5c123-287">První úroveň neukládá do mezipaměti nic na serveru, ale přidá hlavičky HTTP, které dáte pokyn, klienty a proxy servery do mezipaměti odpovědi.</span><span class="sxs-lookup"><span data-stu-id="5c123-287">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="5c123-288">Tato možnost je implementovaná přidáním atribut ResponseCache pro jednotlivé řadiče nebo akce:</span><span class="sxs-lookup"><span data-stu-id="5c123-288">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }
    
    ViewData["Message"] = "Your contact page.";
    return View();
}

The above example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.

Cache-Control: public,max-age=60

In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware. This middleware is configured in both ConfigureServices and Configure in Startup:

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddResponseCaching();
}

public void Configure(IApplicationBuilder app)
{
    app.UseResponseCaching();
}
```

<span data-ttu-id="5c123-289">Middleware ukládání do mezipaměti odpovědi bude automaticky ukládat do mezipaměti odpovědi na základě sady podmínek, které můžete přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="5c123-289">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="5c123-290">Ve výchozím nastavení jsou do mezipaměti pouze 200 (OK) odpovědí požadovaný prostřednictvím metody GET nebo HEAD.</span><span class="sxs-lookup"><span data-stu-id="5c123-290">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="5c123-291">Kromě toho požadavky musí mít odpověď se Cache-Control: veřejné záhlaví a nesmí obsahovat záhlaví pro autorizaci nebo Set-Cookie.</span><span class="sxs-lookup"><span data-stu-id="5c123-291">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="5c123-292">V tématu [úplný seznam ukládání do mezipaměti podmínky používané odpovědi ukládání do mezipaměti middleware](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).</span><span class="sxs-lookup"><span data-stu-id="5c123-292">See a [complete list of the caching conditions used by the response caching middleware](https://docs.microsoft.com/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="5c123-293">Ukládání dat</span><span class="sxs-lookup"><span data-stu-id="5c123-293">Data Caching</span></span>

<span data-ttu-id="5c123-294">Místo (nebo kromě) ukládání do mezipaměti úplné webové odezvy, mezipaměti můžete ukládat výsledky jednotlivých dat dotazů.</span><span class="sxs-lookup"><span data-stu-id="5c123-294">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="5c123-295">V takovém případě můžete použít v ukládání do mezipaměti na webovém serveru nebo pomocí [distribuované mezipaměti](https://docs.microsoft.com/aspnet/core/performance/caching/distributed).</span><span class="sxs-lookup"><span data-stu-id="5c123-295">For this, you can use in memory caching on the web server, or use [a distributed cache](https://docs.microsoft.com/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="5c123-296">Tato část popisuje, jak implementovat v ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="5c123-296">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="5c123-297">Přidání podpory pro paměti (nebo distribuované) ukládání do mezipaměti v ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="5c123-297">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="5c123-298">Je nutné přidat balíček Microsoft.Extensions.Caching.Memory NuGet.</span><span class="sxs-lookup"><span data-stu-id="5c123-298">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="5c123-299">Jakmile přidáte službu, můžete požádat o IMemoryCache pomocí vkládání závislostí vždy, když potřebujete pro přístup do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="5c123-299">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="5c123-300">V tomto příkladu je CachedCatalogService pomocí vzoru návrhu Proxy (nebo Dekoratéra), tím, že poskytuje alternativní implementace ICatalogService, která řídí přístup k (nebo ho přidá chování) základní implementaci CatalogService.</span><span class="sxs-lookup"><span data-stu-id="5c123-300">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
    private static readonly string _itemsKeyTemplate = "items-{0}-{1}-{2}-{3}";
    private static readonly TimeSpan _defaultCacheDuration = TimeSpan.FromSeconds(30);
    public CachedCatalogService(IMemoryCache cache,
    CatalogService catalogService)
    {
        _cache = cache;
        _catalogService = catalogService;
    }
    
    public async Task<IEnumerable<SelectListItem>> GetBrands()
    {
        return await _cache.GetOrCreateAsync(_brandsKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetBrands();
        });
    }
    
    public async Task<Catalog> GetCatalogItems(int pageIndex, int itemsPage, int? brandID, int? typeId)
    {
        string cacheKey = String.Format(_itemsKeyTemplate, pageIndex, itemsPage, brandID, typeId);
        return await _cache.GetOrCreateAsync(cacheKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetCatalogItems(pageIndex, itemsPage, brandID, typeId);
        });
    }
    
    public async Task<IEnumerable<SelectListItem>> GetTypes()
    {
        return await _cache.GetOrCreateAsync(_typesKey, async entry =>
        {
            entry.SlidingExpiration = _defaultCacheDuration;
            return await _catalogService.GetTypes();
        });
    }
}
```

<span data-ttu-id="5c123-301">Chcete-li konfigurovat aplikaci používat v mezipaměti verzi služby, ale stále povolit služby pro získání instance CatalogService musí v jeho konstruktoru, by přidejte následující do ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="5c123-301">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="5c123-302">S tímto zavedené volání databáze načíst data katalogu se provádí pouze jednou za minutu, nikoli na každou žádost.</span><span class="sxs-lookup"><span data-stu-id="5c123-302">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="5c123-303">V závislosti na provoz na web to může mít velmi významný dopad na počet dotazů provedené v databázi a čas načítání stránky průměrná pro domovskou stránku, který aktuálně závisí na všechny tři dotazů vystavené touto službou.</span><span class="sxs-lookup"><span data-stu-id="5c123-303">Depending on the traffic to the site, this can have a very significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="5c123-304">Potíže, které mohou nastat, pokud se implementuje ukládání do mezipaměti je *zastaralých dat* – to znamená, data, která se změnila na zdroji, ale aktuální verze zůstává v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="5c123-304">An issue that arises when caching is implemented is *stale data* – that is, data that has changed at the source but an out of date version remains in the cache.</span></span> <span data-ttu-id="5c123-305">Jednoduchý způsob, jak zmírnit tento problém je použití malých doby trvání mezipaměti, protože pro zaneprázdněnou aplikaci je omezená další výhody rozšíření délku, kterou data se uloží do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="5c123-305">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="5c123-306">Představte si třeba stránky, který umožňuje dotazu jedné databáze, a vyžaduje 10krát za sekundu.</span><span class="sxs-lookup"><span data-stu-id="5c123-306">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="5c123-307">Pokud tato stránka se uloží do mezipaměti pro jednu minutu, bude výsledkem počet dotazů na databázi vyřadit z 600 na 1, snížení 99.8 % provedené za minutu.</span><span class="sxs-lookup"><span data-stu-id="5c123-307">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="5c123-308">Pokud místo toho doba uložení do mezipaměti byly provedeny jednu hodinu, celkové snížení by 99.997 %, ale teď pravděpodobnost a potenciální stáří zastaralá data jsou obě zvětšit výrazně.</span><span class="sxs-lookup"><span data-stu-id="5c123-308">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="5c123-309">Další možností je aktivně odebrat položky mezipaměti při aktualizaci dat, která obsahují.</span><span class="sxs-lookup"><span data-stu-id="5c123-309">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="5c123-310">Všechny jednotlivé položky lze odebrat, pokud je znám svůj klíč:</span><span class="sxs-lookup"><span data-stu-id="5c123-310">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="5c123-311">Pokud vaše aplikace poskytuje funkce pro aktualizaci položky, které se ukládá do mezipaměti, můžete odebrat odpovídající položky mezipaměti ve vašem kódu, který provádí aktualizaci.</span><span class="sxs-lookup"><span data-stu-id="5c123-311">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="5c123-312">V některých případech může být mnoho různé položky, které závisí na konkrétní sadu dat.</span><span class="sxs-lookup"><span data-stu-id="5c123-312">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="5c123-313">V takovém případě může být užitečné k vytvoření závislosti mezi položky mezipaměti pomocí CancellationChangeToken.</span><span class="sxs-lookup"><span data-stu-id="5c123-313">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="5c123-314">S CancellationChangeToken můžete najednou vyprší více položek mezipaměti pomocí tokenu zrušení.</span><span class="sxs-lookup"><span data-stu-id="5c123-314">With a CancellationChangeToken, you can expire multiple cache entries at once by cancelling the token.</span></span>

```csharp
// configure CancellationToken and add entry to cache
var cts = new CancellationTokenSource();
_cache.Set("cts", cts);
_cache.Set(cacheKey,
itemToCache,
new CancellationChangeToken(cts.Token));

// elsewhere, expire the cache by cancelling the token\
_cache.Get<CancellationTokenSource>("cts").Cancel();
```

>[!div class="step-by-step"]
<span data-ttu-id="5c123-315">[Previous] (develop-asp-net-core-mvc-apps.md) [Next] (test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="5c123-315">[Previous] (develop-asp-net-core-mvc-apps.md) [Next] (test-asp-net-core-mvc-apps.md)</span></span>
