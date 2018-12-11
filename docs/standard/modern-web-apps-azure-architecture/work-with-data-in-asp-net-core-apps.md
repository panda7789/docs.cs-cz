---
title: Práce s daty v aplikace v ASP.NET Core
description: Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure | Práce s daty v aplikacích ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 06/28/2018
ms.openlocfilehash: efadf3a0d216197b05d6cd4cfe94ee3eb24bb18e
ms.sourcegitcommit: ccd8c36b0d74d99291d41aceb14cf98d74dc9d2b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53147171"
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="15f1d-103">Práce s daty v aplikacích ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="15f1d-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="15f1d-104">"Dat je cenný věc a bude trvat déle než systémy sami."</span><span class="sxs-lookup"><span data-stu-id="15f1d-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>
>
> <span data-ttu-id="15f1d-105">TIM Berners-Lee</span><span class="sxs-lookup"><span data-stu-id="15f1d-105">Tim Berners-Lee</span></span>

<span data-ttu-id="15f1d-106">Přístup k datům je důležitou součástí téměř všechny softwarové aplikace.</span><span class="sxs-lookup"><span data-stu-id="15f1d-106">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="15f1d-107">ASP.NET Core podporuje širokou škálu možnosti přístupu k datům, včetně Entity Framework Core (a také Entity Framework 6) a může fungovat s jakékoli rozhraní .NET framework data access.</span><span class="sxs-lookup"><span data-stu-id="15f1d-107">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="15f1d-108">Volba, které přístup k datům framework použít závisí na potřebách vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="15f1d-108">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="15f1d-109">Poskytuje abstrakci tyto možnosti z projektů ApplicationCore a uživatelského rozhraní a zapouzdření podrobností o implementaci v infrastruktuře, pomáhá vytvářet volně propojených, možností intenzivního testování softwaru.</span><span class="sxs-lookup"><span data-stu-id="15f1d-109">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="15f1d-110">Entity Framework Core (pro relační databáze)</span><span class="sxs-lookup"><span data-stu-id="15f1d-110">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="15f1d-111">Pokud píšete nové aplikace ASP.NET Core, kterou je potřeba práci s relačními daty, Entity Framework Core (jádro EF) je doporučený postup pro vaši aplikaci pro přístup k jeho datům.</span><span class="sxs-lookup"><span data-stu-id="15f1d-111">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="15f1d-112">EF Core je objektově relační Mapovač (O/RM), který umožňuje vývojářům .NET k uchování objektů do a z datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="15f1d-112">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="15f1d-113">To eliminuje potřebu většinu kód přístupu k datům, které obvykle byste museli vývojáři napsat.</span><span class="sxs-lookup"><span data-stu-id="15f1d-113">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="15f1d-114">Jako je ASP.NET Core EF Core přepsali jsme od základů podporuje modulární multiplatformní aplikace.</span><span class="sxs-lookup"><span data-stu-id="15f1d-114">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="15f1d-115">Přidat do vaší aplikace jako balíček NuGet, jeho konfiguraci v při spuštění a žádosti pomocí vkládání závislostí, bez ohledu na to budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="15f1d-115">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="15f1d-116">EF Core pomocí databáze SQL serveru, spusťte následující příkaz rozhraní příkazového řádku dotnet:</span><span class="sxs-lookup"><span data-stu-id="15f1d-116">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

<span data-ttu-id="15f1d-117">příkaz DotNet add package Microsoft.EntityFrameworkCore.SqlServer</span><span class="sxs-lookup"><span data-stu-id="15f1d-117">dotnet add package Microsoft.EntityFrameworkCore.SqlServer</span></span>

<span data-ttu-id="15f1d-118">Přidání podpory pro zdroj dat InMemory, pro účely testování:</span><span class="sxs-lookup"><span data-stu-id="15f1d-118">To add support for an InMemory data source, for testing:</span></span>

<span data-ttu-id="15f1d-119">příkaz DotNet add package Microsoft.EntityFrameworkCore.InMemory</span><span class="sxs-lookup"><span data-stu-id="15f1d-119">dotnet add package Microsoft.EntityFrameworkCore.InMemory</span></span>

### <a name="the-dbcontext"></a><span data-ttu-id="15f1d-120">Uvolněn objekt DbContext</span><span class="sxs-lookup"><span data-stu-id="15f1d-120">The DbContext</span></span>

<span data-ttu-id="15f1d-121">Pro práci s EF Core, je třeba podtřída <xref:Microsoft.EntityFrameworkCore.DbContext>.</span><span class="sxs-lookup"><span data-stu-id="15f1d-121">To work with EF Core, you need a subclass of <xref:Microsoft.EntityFrameworkCore.DbContext>.</span></span> <span data-ttu-id="15f1d-122">Tato třída obsahuje vlastnosti představující kolekce entit, které vaše aplikace bude fungovat s.</span><span class="sxs-lookup"><span data-stu-id="15f1d-122">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="15f1d-123">Ukázka eShopOnWeb zahrnuje CatalogContext s kolekcí položek, značky a typy:</span><span class="sxs-lookup"><span data-stu-id="15f1d-123">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

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

<span data-ttu-id="15f1d-124">Vaše DbContext musí mít konstruktor, který přijímá DbContextOptions a předat tento argument pro konstruktor základní třídy DbContext.</span><span class="sxs-lookup"><span data-stu-id="15f1d-124">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="15f1d-125">Poznámka: Pokud máte pouze jeden DbContext v aplikaci, můžete předat instanci DbContextOptions, ale pokud máte více než jeden je nutné použít obecný DbContextOptions<T> typ, předejte typ DbContext jako na generický parametr.</span><span class="sxs-lookup"><span data-stu-id="15f1d-125">Note that if you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="15f1d-126">Konfigurace EF Core</span><span class="sxs-lookup"><span data-stu-id="15f1d-126">Configuring EF Core</span></span>

<span data-ttu-id="15f1d-127">V aplikaci ASP.NET Core obvykle nakonfigurujete EF Core ve své metodě ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="15f1d-127">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="15f1d-128">EF Core používá DbContextOptionsBuilder, která podporuje několik užitečných rozšiřující metody pro usnadnit jeho konfiguraci.</span><span class="sxs-lookup"><span data-stu-id="15f1d-128">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="15f1d-129">Pokud chcete nakonfigurovat CatalogContext pro použití jiné databáze systému SQL Server pomocí připojovacího řetězce definované v konfiguraci, by přidejte následující kód k ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="15f1d-129">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="15f1d-130">Použití databáze v paměti:</span><span class="sxs-lookup"><span data-stu-id="15f1d-130">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="15f1d-131">Po EF Core vytvořili podřízený typ DbContext, nainstalované a nakonfigurované v ConfigureServices, jste připraveni používat EF Core.</span><span class="sxs-lookup"><span data-stu-id="15f1d-131">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="15f1d-132">Můžete požádat o instanci typu DbContext v jakékoli služby, která potřebuje a začít pracovat s trvalou entit pomocí LINQ, jako by byly jednoduše v kolekci.</span><span class="sxs-lookup"><span data-stu-id="15f1d-132">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="15f1d-133">EF Core funguje překlad výrazech LINQ na dotazy SQL pro ukládání a načítání dat.</span><span class="sxs-lookup"><span data-stu-id="15f1d-133">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="15f1d-134">Můžete zobrazit dotazy EF Core provádí konfigurací protokolovací nástroj a zajištění jeho úroveň je nastavené aspoň informace, jak ukazuje obrázek 8-1.</span><span class="sxs-lookup"><span data-stu-id="15f1d-134">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![](./media/image8-1.png)

<span data-ttu-id="15f1d-135">Obrázek 8-1 protokolování EF Core dotazy do konzoly</span><span class="sxs-lookup"><span data-stu-id="15f1d-135">Figure 8-1 Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="15f1d-136">Načítání a ukládání dat</span><span class="sxs-lookup"><span data-stu-id="15f1d-136">Fetching and storing Data</span></span>

<span data-ttu-id="15f1d-137">K načtení dat z EF Core, přístup k příslušné vlastnosti a zprostředkovatel LINQ slouží pro filtrování výsledků.</span><span class="sxs-lookup"><span data-stu-id="15f1d-137">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="15f1d-138">LINQ můžete také použít k provedení projekce, transformaci výsledku z jednoho typu na jiný.</span><span class="sxs-lookup"><span data-stu-id="15f1d-138">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="15f1d-139">V následujícím příkladu by načíst CatalogBrands, seřazené podle názvu, filtrovat podle jejich vlastnosti Enabled a plánovaných na typ SelectListItem:</span><span class="sxs-lookup"><span data-stu-id="15f1d-139">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="15f1d-140">Je důležité v příkladu výše a přidejte volání do ToListAsync, aby bylo možné okamžitě spustit dotaz.</span><span class="sxs-lookup"><span data-stu-id="15f1d-140">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="15f1d-141">V opačném případě bude příkaz Přiřadit položku IQueryable<SelectListItem> k brandItems, který nebude provedeno, dokud je ve výčtu.</span><span class="sxs-lookup"><span data-stu-id="15f1d-141">Otherwise, the statement will assign an IQueryable<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="15f1d-142">Existují výhody a nevýhody vrací typ IQueryable výsledky z metod.</span><span class="sxs-lookup"><span data-stu-id="15f1d-142">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="15f1d-143">Umožňuje dotazu, které EF Core vytvoří dále upravit, ale můžete také za následek chyby, které se vztahuje pouze na za běhu, pokud operace jsou přidány do dotazu, který nelze přeložit EF Core.</span><span class="sxs-lookup"><span data-stu-id="15f1d-143">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="15f1d-144">Obecně je bezpečnější pro předání nějaké filtry do metody provádí přístup k datům a vrátit zpět kolekce v paměti (například seznamu<T>) jako výsledek.</span><span class="sxs-lookup"><span data-stu-id="15f1d-144">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List<T>) as the result.</span></span>

<span data-ttu-id="15f1d-145">EF Core sleduje změny u entit, který načte z trvalého úložiště.</span><span class="sxs-lookup"><span data-stu-id="15f1d-145">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="15f1d-146">Pokud chcete uložit změny do sledované entity, stačí zavolat metodu SaveChanges objekt dbcontext, ujistěte se, že se že jedná o stejnou instanci DbContext, který byl použit pro načtení entity.</span><span class="sxs-lookup"><span data-stu-id="15f1d-146">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="15f1d-147">Přidávání a odebírání entity se provádí přímo na odpovídající vlastnosti DbSet, znovu s volání SaveChanges pro spuštění databázových příkazů.</span><span class="sxs-lookup"><span data-stu-id="15f1d-147">Adding and removing entities is directly done on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="15f1d-148">Následující příklad ukazuje přidání, aktualizace nebo odebrání entity z trvalého úložiště.</span><span class="sxs-lookup"><span data-stu-id="15f1d-148">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

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

<span data-ttu-id="15f1d-149">EF Core podporuje obě synchronní a asynchronní metody pro načítání a ukládání.</span><span class="sxs-lookup"><span data-stu-id="15f1d-149">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="15f1d-150">Ve webových aplikacích doporučuje se použití vzoru async/await s asynchronními metodami, tak, aby při čekání na dokončení operací přístupu k data nejsou blokované vlákna webového serveru.</span><span class="sxs-lookup"><span data-stu-id="15f1d-150">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="15f1d-151">Načítání souvisejících dat</span><span class="sxs-lookup"><span data-stu-id="15f1d-151">Fetching related data</span></span>

<span data-ttu-id="15f1d-152">Když EF Core načte entity, naplní všechny vlastnosti, které jsou uloženy přímo s dané entitě v databázi.</span><span class="sxs-lookup"><span data-stu-id="15f1d-152">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="15f1d-153">Navigační vlastnosti, jako je například seznam souvisejících entit nejsou naplněny a může mít nastavenou na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="15f1d-153">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="15f1d-154">Tím se zajistí, že EF Core není načítání více dat, než je potřeba, což je obzvláště důležité pro webové aplikace, které musí rychle zpracovávají požadavky a vracet odpovědi efektivním způsobem.</span><span class="sxs-lookup"><span data-stu-id="15f1d-154">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="15f1d-155">Zahrnout vztahy s entitu s využitím _předběžné načítání_, určete vlastnost pomocí metody rozšíření zahrnout u dotazu, jak je znázorněno:</span><span class="sxs-lookup"><span data-stu-id="15f1d-155">To include relationships with an entity using _eager loading_, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="15f1d-156">Může obsahovat více vztahů a může také obsahovat dílčí vztahy pomocí ThenInclude.</span><span class="sxs-lookup"><span data-stu-id="15f1d-156">You can include multiple relationships, and you can also include sub-relationships using ThenInclude.</span></span> <span data-ttu-id="15f1d-157">EF Core se spustit jeden dotaz pro načtení výslednou sadu entit.</span><span class="sxs-lookup"><span data-stu-id="15f1d-157">EF Core will execute a single query to retrieve the resulting set of entities.</span></span>

<span data-ttu-id="15f1d-158">Další možností pro načítání souvisejících dat je použití _explicitní načtení_.</span><span class="sxs-lookup"><span data-stu-id="15f1d-158">Another option for loading related data is to use _explicit loading_.</span></span> <span data-ttu-id="15f1d-159">Explicitní načtení umožňuje načtení dalších dat do entity, která již byla načtena.</span><span class="sxs-lookup"><span data-stu-id="15f1d-159">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="15f1d-160">Protože to vyžaduje samostatnou žádost do databáze, se nedoporučuje pro webové aplikace, které byste minimalizovat počet databáze má zpáteční převod vytvářejí pro jednotlivé žádosti.</span><span class="sxs-lookup"><span data-stu-id="15f1d-160">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="15f1d-161">_Opožděné načtení_ je funkce, která automaticky načte související data, jak se odkazuje aplikaci.</span><span class="sxs-lookup"><span data-stu-id="15f1d-161">_Lazy loading_ is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="15f1d-162">EF Core má přidanou podporu pro opožděné načtení ve verzi 2.1.</span><span class="sxs-lookup"><span data-stu-id="15f1d-162">EF Core has added support for lazy loading in version 2.1.</span></span> <span data-ttu-id="15f1d-163">Opožděné načtení není ve výchozím nastavení povolené a vyžaduje instalaci `Microsoft.EntityFrameworkCore.Proxies`.</span><span class="sxs-lookup"><span data-stu-id="15f1d-163">Lazy loading is not enabled by default and requires installing the `Microsoft.EntityFrameworkCore.Proxies`.</span></span> <span data-ttu-id="15f1d-164">Stejně jako u explicitní načtení opožděné načtení obvykle je třeba zakázat pro webové aplikace, protože její použití způsobí další databázových dotazů prováděných v rámci každého webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="15f1d-164">As with explicit loading, lazy loading should typically be disabled for web applications, since its use will result in additional database queries being made within each web request.</span></span> <span data-ttu-id="15f1d-165">Režie vzniklé opožděné načtení často přejde bohužel bez povšimnutí při vývoji, kdy latence je malý a často jsou malé datové sady, používá se pro testování.</span><span class="sxs-lookup"><span data-stu-id="15f1d-165">Unfortunately, the overhead incurred by lazy loading often goes unnoticed at development time, when latency is small and often the data sets used for testing are small.</span></span> <span data-ttu-id="15f1d-166">Ale v produkčním prostředí s více uživateli, víc dat a další latence požadavky další databáze můžete často za následek nízký výkon pro webové aplikace, které se hojně používají opožděné načtení.</span><span class="sxs-lookup"><span data-stu-id="15f1d-166">However, in production, with more users, more data, and more latency, the additional database requests can often result in poor performance for web applications that make heavy use of lazy loading.</span></span>

[<span data-ttu-id="15f1d-167">Vyhněte se opožděné načtení entit ve webových aplikacích</span><span class="sxs-lookup"><span data-stu-id="15f1d-167">Avoid Lazy Loading Entities in Web Applications</span></span>](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="resilient-connections"></a><span data-ttu-id="15f1d-168">Odolnost připojení</span><span class="sxs-lookup"><span data-stu-id="15f1d-168">Resilient connections</span></span>

<span data-ttu-id="15f1d-169">Externí prostředky, jako jsou databáze SQL může být čas od času není k dispozici.</span><span class="sxs-lookup"><span data-stu-id="15f1d-169">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="15f1d-170">V případech dočasné nedostupnosti aplikací můžete logiku opakování vyhnuli vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="15f1d-170">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="15f1d-171">Tato technika se obvykle označuje jako _odolnost připojení_.</span><span class="sxs-lookup"><span data-stu-id="15f1d-171">This technique is commonly referred to as _connection resiliency_.</span></span> <span data-ttu-id="15f1d-172">Můžete implementovat vaše [vlastní opakování pomocí exponenciálního omezení rychlosti](https://docs.microsoft.com/azure/architecture/patterns/retry) techniku pokusem o opakování s exponenciálně rostoucím času čekání, dokud nedosáhne maximální počet opakování.</span><span class="sxs-lookup"><span data-stu-id="15f1d-172">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to retry with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="15f1d-173">Tento postup poskytuje výkonný fakt, že cloudové prostředky přerušovaně pravděpodobně není k dispozici pro krátkou dobu, což vede k selhání některé požadavky.</span><span class="sxs-lookup"><span data-stu-id="15f1d-173">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="15f1d-174">Pro službu Azure SQL DB Entity Framework Core již poskytuje interní databáze připojení odolnost proti chybám a zkuste to znovu logiku.</span><span class="sxs-lookup"><span data-stu-id="15f1d-174">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="15f1d-175">Ale je potřeba povolit strategie provádění Entity Framework pro každé připojení kontext databáze. Pokud chcete mít odolnost připojení EF Core.</span><span class="sxs-lookup"><span data-stu-id="15f1d-175">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="15f1d-176">Například následující kód na úrovni připojení EF Core umožňuje odolnost připojení SQL, které se zopakují, pokud se nepovede.</span><span class="sxs-lookup"><span data-stu-id="15f1d-176">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="15f1d-177">Strategie provádění a explicitní transakce pomocí BeginTransaction a více DbContexts</span><span class="sxs-lookup"><span data-stu-id="15f1d-177">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="15f1d-178">Pokud opakované pokusy jsou povolené v EF Core připojení, bude každé operace, které můžete provádět pomocí EF Core vyvolaly provozu.</span><span class="sxs-lookup"><span data-stu-id="15f1d-178">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retriable operation.</span></span> <span data-ttu-id="15f1d-179">Každý dotaz a každé volání SaveChanges bude zopakován jako celek, pokud dojde k přechodnému selhání.</span><span class="sxs-lookup"><span data-stu-id="15f1d-179">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="15f1d-180">Ale pokud váš kód zahájí transakci pomocí BeginTransaction, definujete vlastní skupinu operací, které je potřeba za jednotku považuje – všechno, co je uvnitř transakce se vrátila zpět, pokud dojde k chybě.</span><span class="sxs-lookup"><span data-stu-id="15f1d-180">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit—everything inside the transaction has be rolled back if a failure occurs.</span></span> <span data-ttu-id="15f1d-181">Pokud se pokusíte spustit transakci, při použití strategie provádění EF (zásady opakování) a v ní zahrnete několik SaveChanges z více DbContexts uvidíte výjimku vypadat asi takto.</span><span class="sxs-lookup"><span data-stu-id="15f1d-181">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="15f1d-182">System.InvalidOperationException: Strategie provádění nakonfigurované "SqlServerRetryingExecutionStrategy" nepodporuje transakce iniciované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="15f1d-182">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="15f1d-183">Použití strategie provádění vrácený "DbContext.Database.CreateExecutionStrategy()" provádět všechny operace v transakci jako vyvolaly jednotky.</span><span class="sxs-lookup"><span data-stu-id="15f1d-183">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retriable unit.</span></span>

<span data-ttu-id="15f1d-184">Řešením je vyvolat strategie provádění EF s všechno, co představuje delegáta, který je nutné spustit ručně.</span><span class="sxs-lookup"><span data-stu-id="15f1d-184">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="15f1d-185">Pokud dojde k přechodnému selhání, strategie provádění znovu vyvolá delegáta.</span><span class="sxs-lookup"><span data-stu-id="15f1d-185">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="15f1d-186">Následující kód ukazuje implementaci tohoto přístupu:</span><span class="sxs-lookup"><span data-stu-id="15f1d-186">The following code shows how to implement this approach:</span></span>

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

<span data-ttu-id="15f1d-187">Je první objekt DbContext \_catalogContext a druhý je DbContext v rámci \_integrationEventLogService objektu.</span><span class="sxs-lookup"><span data-stu-id="15f1d-187">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="15f1d-188">Nakonec potvrzení bude akce provedena více DbContexts a použitím strategie provádění EF.</span><span class="sxs-lookup"><span data-stu-id="15f1d-188">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="15f1d-189">Odkazy – Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="15f1d-189">References – Entity Framework Core</span></span>
>
> - <span data-ttu-id="15f1d-190">**EF Core dokumentace**</span><span class="sxs-lookup"><span data-stu-id="15f1d-190">**EF Core Docs**</span></span>  
>   <https://docs.microsoft.com/ef/>
> - <span data-ttu-id="15f1d-191">**EF Core: Související Data**</span><span class="sxs-lookup"><span data-stu-id="15f1d-191">**EF Core: Related Data**</span></span>  
>   <https://docs.microsoft.com/ef/core/querying/related-data>
> - <span data-ttu-id="15f1d-192">**Vyhněte se opožděné načtení entit v aplikacích ASPNET**</span><span class="sxs-lookup"><span data-stu-id="15f1d-192">**Avoid Lazy Loading Entities in ASPNET Applications**</span></span>  
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="15f1d-193">EF Core nebo micro ORM?</span><span class="sxs-lookup"><span data-stu-id="15f1d-193">EF Core or micro-ORM?</span></span>

<span data-ttu-id="15f1d-194">EF Core je skvělou volbou pro správu trvalosti a ve většině případů zapouzdřuje databáze informace od vývojářů aplikací, není pouze podle výběru.</span><span class="sxs-lookup"><span data-stu-id="15f1d-194">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it is not the only choice.</span></span> <span data-ttu-id="15f1d-195">Další oblíbené open source alternativou je [Dapperem](https://github.com/StackExchange/Dapper), takzvané ORM micro.</span><span class="sxs-lookup"><span data-stu-id="15f1d-195">Another popular open source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="15f1d-196">Micro-ORM představuje jednoduché, méně plně funkční nástroj pro mapování objektů na datové struktury.</span><span class="sxs-lookup"><span data-stu-id="15f1d-196">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="15f1d-197">V případě Dapperem jeho návrhu, které cíle soustředit na výkon, nikoli plně zapouzdření základní dotazy používá k načtení a aktualizovat data.</span><span class="sxs-lookup"><span data-stu-id="15f1d-197">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="15f1d-198">Vzhledem k tomu, že SQL ji není abstraktní od vývojáře, Dapperem "nejblíže až na úroveň hardwaru" a umožňuje vývojářům psát přesné dotazy, které chtějí používat pro daný datový přístup k operaci.</span><span class="sxs-lookup"><span data-stu-id="15f1d-198">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="15f1d-199">EF Core má dvě důležité funkce poskytuje které oddělení od Dapperem, ale také přidat do své nároky na výkon.</span><span class="sxs-lookup"><span data-stu-id="15f1d-199">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="15f1d-200">První je překlad z výrazů LINQ do SQL.</span><span class="sxs-lookup"><span data-stu-id="15f1d-200">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="15f1d-201">Tyto převody jsou uložené v mezipaměti, ale i tak je režie při prvním spuštění.</span><span class="sxs-lookup"><span data-stu-id="15f1d-201">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="15f1d-202">Druhým je sledování změn u entit (tak, aby je možné generovat příkazy efektivní aktualizace).</span><span class="sxs-lookup"><span data-stu-id="15f1d-202">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="15f1d-203">Toto chování vypnete pro určité dotazy s použitím rozšíření AsNotTracking.</span><span class="sxs-lookup"><span data-stu-id="15f1d-203">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="15f1d-204">EF Core také vygeneruje dotazy SQL, které jsou obvykle velmi efektivní a v každém případě nemusíte zajistit dokonalou přijatelné z hlediska výkonu, ale pokud potřebujete jemné kontrolu nad přesné provedení dotazu, můžete předat vlastní SQL (nebo provedení uložené procedury) pomocí EF Příliš jádro.</span><span class="sxs-lookup"><span data-stu-id="15f1d-204">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="15f1d-205">V takovém případě Dapper stále lepší výkon než EF Core, ale jen mírně.</span><span class="sxs-lookup"><span data-stu-id="15f1d-205">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="15f1d-206">Některá data o výkonu v její může článku na webu MSDN 2016 uvede Julie Lerman [Dapperem, Entity Framework a také hybridní aplikace](https://msdn.microsoft.com/magazine/mt703432.aspx).</span><span class="sxs-lookup"><span data-stu-id="15f1d-206">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://msdn.microsoft.com/magazine/mt703432.aspx).</span></span> <span data-ttu-id="15f1d-207">Dalších srovnávací test dat o výkonu pro celou řadu metod datového přístupu můžete najít na [Dapper lokality](https://github.com/StackExchange/Dapper).</span><span class="sxs-lookup"><span data-stu-id="15f1d-207">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="15f1d-208">Chcete-li zjistit, jak se liší od EF Core syntaxe Dapperem, zvažte tyto dvě verze stejné metody pro načtení seznamu položek:</span><span class="sxs-lookup"><span data-stu-id="15f1d-208">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

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

<span data-ttu-id="15f1d-209">Pokud budete muset vytvářet složitější grafů objektů s Dapperem, musíte napsat přidružené dotazy (na rozdíl od přidání do vloženého, stejně jako v EF Core).</span><span class="sxs-lookup"><span data-stu-id="15f1d-209">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="15f1d-210">To je podporováno prostřednictvím různých syntaxí, včetně funkci s více mapování, která umožňuje mapovat na více objektů pro mapovanou jednotlivých řádků.</span><span class="sxs-lookup"><span data-stu-id="15f1d-210">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="15f1d-211">Například vzhledem třídu příspěvek s vlastností vlastník typu uživatele následující příkaz SQL by vrátit všechna nezbytná data:</span><span class="sxs-lookup"><span data-stu-id="15f1d-211">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="15f1d-212">Každý vrácený řádek obsahuje data uživatelů a příspěvku.</span><span class="sxs-lookup"><span data-stu-id="15f1d-212">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="15f1d-213">Protože data uživatele by měl být připojen následných dat prostřednictvím vlastnosti jeho vlastníka, se používá následující funkce:</span><span class="sxs-lookup"><span data-stu-id="15f1d-213">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="15f1d-214">Výpis úplného kódu budou vráceny kolekci příspěvků s jejich vlastnost Owner naplněný daty přidruženého uživatele by byl:</span><span class="sxs-lookup"><span data-stu-id="15f1d-214">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="15f1d-215">Vzhledem k tomu, že nabízí méně zapouzdření, vyžaduje Dapperem vývojáři dozvědět víc o tom, jak jejich data uložená, jak efektivní dotazování a napsat další kód, který jej načíst.</span><span class="sxs-lookup"><span data-stu-id="15f1d-215">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="15f1d-216">Když se změní model, místo jednoduše vytvářet novou migraci (Další EF Core funkcí) a/nebo aktualizace informací o mapování na jednom místě v DbContext, musí aktualizovat každý dotaz, který má vliv.</span><span class="sxs-lookup"><span data-stu-id="15f1d-216">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="15f1d-217">Tyto dotazy obsahovat není záruky čas kompilace, tak se může přerušit za běhu v reakci na změny modelu nebo databáze, provádění obtížnější rychle detekovat chyby.</span><span class="sxs-lookup"><span data-stu-id="15f1d-217">These queries have not compile time guarantees, so they may break at runtime in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="15f1d-218">Výměnou za tyto nevýhody Dapperem nabízí velmi rychlý výkon.</span><span class="sxs-lookup"><span data-stu-id="15f1d-218">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="15f1d-219">Pro většinu aplikací a většina součástí téměř všechny aplikace nabízí EF Core přijatelný výkon.</span><span class="sxs-lookup"><span data-stu-id="15f1d-219">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="15f1d-220">Díky tomu se budou pravděpodobně nároky na výkon převažují nad jeho výhody produktivity pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="15f1d-220">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="15f1d-221">Pro dotazy, které mohou těžit z ukládání do mezipaměti, samotný dotaz může spustit pouze velmi malé procento doby provádění poměrně málo početnému dotazování výkonu moot rozdíly.</span><span class="sxs-lookup"><span data-stu-id="15f1d-221">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="15f1d-222">SQL a NoSQL</span><span class="sxs-lookup"><span data-stu-id="15f1d-222">SQL or NoSQL</span></span>

<span data-ttu-id="15f1d-223">Tradičně relačních databází, jako je SQL Server mají ovládnutí úložiště trvalých dat na webu marketplace, ale nejsou k dispozici jenom řešení.</span><span class="sxs-lookup"><span data-stu-id="15f1d-223">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="15f1d-224">Databáze NoSQL, jako jsou [MongoDB](https://www.mongodb.com/what-is-mongodb) nabízejí jiný přístup k ukládání objektů.</span><span class="sxs-lookup"><span data-stu-id="15f1d-224">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="15f1d-225">Další možností je místo mapování objektů do tabulek a řádků, serializaci celý objekt grafu a uložit výsledek.</span><span class="sxs-lookup"><span data-stu-id="15f1d-225">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="15f1d-226">Výhody tohoto přístupu alespoň ze začátku jsou jednoduchost a výkonu.</span><span class="sxs-lookup"><span data-stu-id="15f1d-226">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="15f1d-227">Je určitě jednodušší pro uložení jedné serializované objekt s klíčem, než se rozloží na mnoho tabulky se vztahy objektu a aktualizací a řádky, které se možná změnily od posledního objekt načtených z databáze.</span><span class="sxs-lookup"><span data-stu-id="15f1d-227">It's certainly simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="15f1d-228">Podobně načítání a deserializaci jednoho objektu z úložiště na základě klíčů je obvykle mnohem jednodušší a rychlejší než komplexním spojením nebo více databázových dotazů vyžaduje plně sestavení na stejný objekt z relační databáze.</span><span class="sxs-lookup"><span data-stu-id="15f1d-228">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="15f1d-229">Nedostatek uzamčení nebo transakce nebo pevné schéma také díky databáze NoSQL velmi vydávání kompaktních škálování napříč velký počet počítačů, podpora velmi velkých datových sad.</span><span class="sxs-lookup"><span data-stu-id="15f1d-229">The lack of locks or transactions or a fixed schema also makes NoSQL databases very amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="15f1d-230">Na druhé straně databáze NoSQL (obvykle se nazývá) mít svoje nevýhody.</span><span class="sxs-lookup"><span data-stu-id="15f1d-230">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="15f1d-231">Relační databáze pomocí normalizace vynutit konzistenci a aby nedošlo k duplikaci data.</span><span class="sxs-lookup"><span data-stu-id="15f1d-231">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="15f1d-232">Tím se sníží celkové velikosti databáze a zajistí, že jsou k dispozici okamžitě celé databáze aktualizace ke sdíleným datům.</span><span class="sxs-lookup"><span data-stu-id="15f1d-232">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="15f1d-233">V relační databázi tabulku adres může odkazovat země tabulku podle ID, tak, že pokud byla změněna název v zemi, záznamy adres je výhodná aktualizace bez musejí být aktualizována.</span><span class="sxs-lookup"><span data-stu-id="15f1d-233">In a relational database, an Address table might reference a Country table by ID, such that if a country's name were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="15f1d-234">Ale v databázi NoSQL, adresa a její přidružené země může serializovat jako součást velký počet uložených objektů.</span><span class="sxs-lookup"><span data-stu-id="15f1d-234">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="15f1d-235">Aktualizace názvu země by vyžadovaly všechny tyto objekty mají být aktualizovány, místo jednoho řádku.</span><span class="sxs-lookup"><span data-stu-id="15f1d-235">An update to a country name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="15f1d-236">Relační databáze, můžete také zajistit relační integritu tím, že vynucuje pravidla, jako jsou cizí klíče.</span><span class="sxs-lookup"><span data-stu-id="15f1d-236">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="15f1d-237">Databáze NoSQL není taková omezení na svá data obvykle nabízejí.</span><span class="sxs-lookup"><span data-stu-id="15f1d-237">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="15f1d-238">Další složitost NoSQL databáze musí čelit je správa verzí.</span><span class="sxs-lookup"><span data-stu-id="15f1d-238">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="15f1d-239">Při změně vlastnosti objektu, nemusí být možné deserializovat rozdíl od minulých verzí, které byly uloženy.</span><span class="sxs-lookup"><span data-stu-id="15f1d-239">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="15f1d-240">Díky tomu se musí aktualizovat všechny existující objekty, které mají serializovaná (předchozí) verzi objektu tak, aby odpovídal na jeho nové schéma.</span><span class="sxs-lookup"><span data-stu-id="15f1d-240">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="15f1d-241">Toto není koncepčně liší od relační databáze, kde je někdy změní schéma vyžadují skripty pro aktualizaci nebo mapování aktualizace.</span><span class="sxs-lookup"><span data-stu-id="15f1d-241">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="15f1d-242">Počet položek, které musí být upraveny je však často mnohem větší přístupu NoSQL, protože existuje více duplicitních dat.</span><span class="sxs-lookup"><span data-stu-id="15f1d-242">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="15f1d-243">Je možné v databázích NoSQL pro ukládání více verzí objektů, něco pevné schéma relačních databází obvykle nepodporují.</span><span class="sxs-lookup"><span data-stu-id="15f1d-243">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="15f1d-244">Ale v tomto případě kódu aplikace potřebovat pro existenci předchozích verzích objekty, přidáte další složitosti.</span><span class="sxs-lookup"><span data-stu-id="15f1d-244">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="15f1d-245">Databáze NoSQL obvykle Nevynucovat [kyseliny](https://en.wikipedia.org/wiki/ACID), což znamená, že mají výhody výkonu a škálovatelnosti nad relačních databází.</span><span class="sxs-lookup"><span data-stu-id="15f1d-245">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="15f1d-246">Jsou to skvěle se hodí k velmi velkých datových sad a objektů, které nejsou vhodné řešení pro úložiště ve strukturách normalizované tabulky.</span><span class="sxs-lookup"><span data-stu-id="15f1d-246">They're well-suited to extremely large datasets and objects that are not well-suited to storage in normalized table structures.</span></span> <span data-ttu-id="15f1d-247">Neexistuje žádný důvod, proč si jednu aplikaci nemůžete využít výhod obou relační a vhodné databáze NoSQL, pomocí všech, kde je nejvhodnější.</span><span class="sxs-lookup"><span data-stu-id="15f1d-247">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-documentdb"></a><span data-ttu-id="15f1d-248">Azure DocumentDB</span><span class="sxs-lookup"><span data-stu-id="15f1d-248">Azure DocumentDB</span></span>

<span data-ttu-id="15f1d-249">Azure DocumentDB je plně spravovaná služba databáze NoSQL, která nabízí úložiště založené na cloudu data bez schémat.</span><span class="sxs-lookup"><span data-stu-id="15f1d-249">Azure DocumentDB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="15f1d-250">DocumentDB je vytvořená pro vysoký a předvídatelný výkon, vysokou dostupnost, elastické škálování a globální distribuci.</span><span class="sxs-lookup"><span data-stu-id="15f1d-250">DocumentDB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="15f1d-251">Přestože jsou databáze NoSQL, vývojáři mohou pomocí bohaté a známé schopnosti příkazů jazyka SQL pro JSON data.</span><span class="sxs-lookup"><span data-stu-id="15f1d-251">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="15f1d-252">Všechny prostředky v DocumentDB se ukládají jako dokumenty JSON.</span><span class="sxs-lookup"><span data-stu-id="15f1d-252">All resources in DocumentDB are stored as JSON documents.</span></span> <span data-ttu-id="15f1d-253">Prostředky se spravují jako _položky_, které jsou dokumenty obsahující metadata, a _informační kanály_, což jsou kolekce položek.</span><span class="sxs-lookup"><span data-stu-id="15f1d-253">Resources are managed as _items_, which are documents containing metadata, and _feeds_, which are collections of items.</span></span> <span data-ttu-id="15f1d-254">Obrázek 8-2 je znázorněný vztah mezi různé prostředky DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="15f1d-254">Figure 8-2 shows the relationship between different DocumentDB resources.</span></span>

![Hierarchický vztah mezi prostředky v DocumentDB, databázi NoSQL JSON](./media/image8-2.png)

<span data-ttu-id="15f1d-256">**Obrázek 8-2.**</span><span class="sxs-lookup"><span data-stu-id="15f1d-256">**Figure 8-2.**</span></span> <span data-ttu-id="15f1d-257">Organizaci poskytující prostředky DocumentDB.</span><span class="sxs-lookup"><span data-stu-id="15f1d-257">DocumentDB resource organization.</span></span>

<span data-ttu-id="15f1d-258">Dotazovací jazyk DocumentDB je jednoduché, ale výkonné rozhraní pro dotazování dokumentů JSON.</span><span class="sxs-lookup"><span data-stu-id="15f1d-258">The DocumentDB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="15f1d-259">Jazyk podporuje podmnožinu gramatiky ANSI SQL a přidává těsnou integraci s objektu jazyka JavaScript, pole, konstrukce objektu a volání funkce.</span><span class="sxs-lookup"><span data-stu-id="15f1d-259">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="15f1d-260">**Odkazy – DocumentDB**</span><span class="sxs-lookup"><span data-stu-id="15f1d-260">**References – DocumentDB**</span></span>

- <span data-ttu-id="15f1d-261">Úvod k DocumentDB</span><span class="sxs-lookup"><span data-stu-id="15f1d-261">DocumentDB Introduction</span></span>  
  <https://docs.microsoft.com/azure/documentdb/documentdb-introduction>

## <a name="other-persistence-options"></a><span data-ttu-id="15f1d-262">Další možnosti trvalosti</span><span class="sxs-lookup"><span data-stu-id="15f1d-262">Other persistence options</span></span>

<span data-ttu-id="15f1d-263">Také do relační a možnosti úložiště NoSQL můžete použít aplikace ASP.NET Core služby Azure Storage k ukládání širokou škálu formátů data a soubory v podobě Cloudová, škálovatelná.</span><span class="sxs-lookup"><span data-stu-id="15f1d-263">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="15f1d-264">Azure Storage je široce škálovatelné, takže můžete začít ukládat malá množství dat a škálování až na ukládání stovky nebo dokonce terabajtů, pokud ho vaše aplikace vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="15f1d-264">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="15f1d-265">Azure Storage podporuje čtyři typy dat:</span><span class="sxs-lookup"><span data-stu-id="15f1d-265">Azure Storage supports four kinds of data:</span></span>

- <span data-ttu-id="15f1d-266">Úložiště objektů blob pro ukládání nestrukturovaných textových nebo binárních úložiště také označuje jako úložiště objektů.</span><span class="sxs-lookup"><span data-stu-id="15f1d-266">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

- <span data-ttu-id="15f1d-267">Table Storage pro strukturovaných datových sad, přístupné přes klíče řádku.</span><span class="sxs-lookup"><span data-stu-id="15f1d-267">Table Storage for structured datasets, accessible via row keys.</span></span>

- <span data-ttu-id="15f1d-268">Queue Storage pro spolehlivé na základě fronty zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="15f1d-268">Queue Storage for reliable queue-based messaging.</span></span>

- <span data-ttu-id="15f1d-269">Úložiště souborů pro přístup ke sdílenému souboru mezi virtuální počítače Azure a místními aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="15f1d-269">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="15f1d-270">**Odkazy – Azure Storage**</span><span class="sxs-lookup"><span data-stu-id="15f1d-270">**References – Azure Storage**</span></span>

- <span data-ttu-id="15f1d-271">Představení služby Azure Storage</span><span class="sxs-lookup"><span data-stu-id="15f1d-271">Azure Storage Introduction</span></span>  
  <https://docs.microsoft.com/azure/storage/storage-introduction>

## <a name="caching"></a><span data-ttu-id="15f1d-272">Ukládání do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="15f1d-272">Caching</span></span>

<span data-ttu-id="15f1d-273">Ve webových aplikacích každý webový požadavek by měl dokončit v nejkratší možné době.</span><span class="sxs-lookup"><span data-stu-id="15f1d-273">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="15f1d-274">Jedním ze způsobů, jak tohoto dosáhnout je omezit počet externích volání, které server musí provést k dokončení požadavku.</span><span class="sxs-lookup"><span data-stu-id="15f1d-274">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="15f1d-275">Ukládání do mezipaměti zahrnuje ukládání kopie dat na serveru (nebo jiné datové úložiště, který je více než zdroj dat snadno dotazovat).</span><span class="sxs-lookup"><span data-stu-id="15f1d-275">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="15f1d-276">Webové aplikace a hlavně-jednostránková aplikace tradiční webových aplikací, je potřeba sestavit celé uživatelské rozhraní při každé žádosti.</span><span class="sxs-lookup"><span data-stu-id="15f1d-276">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="15f1d-277">To často zahrnuje provádění mnoha stejné databázové dotazy opakovaně z požadavku na jednoho uživatele na další.</span><span class="sxs-lookup"><span data-stu-id="15f1d-277">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="15f1d-278">Ve většině případů tato data mění jen zřídka, tedy malou důvod, proč neustále žádosti z databáze.</span><span class="sxs-lookup"><span data-stu-id="15f1d-278">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="15f1d-279">ASP.NET Core podporuje ukládání odpovědí do mezipaměti, pro ukládání do mezipaměti celé stránky a ukládání dat do mezipaměti, která podporuje podrobnější chování ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="15f1d-279">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="15f1d-280">Při implementaci ukládání do mezipaměti, je důležité udržovat v úvahu oddělení oblastí zájmu.</span><span class="sxs-lookup"><span data-stu-id="15f1d-280">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="15f1d-281">Vyhněte se implementaci logiky ukládaní do mezipaměti v logikou přístupu dat nebo v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="15f1d-281">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="15f1d-282">Místo toho zapouzdření ukládání do mezipaměti v jeho vlastní třídy a použití konfigurace k spravovat své chování.</span><span class="sxs-lookup"><span data-stu-id="15f1d-282">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="15f1d-283">Následuje Open/uzavřeno a principy jednotnou zodpovědnost a usnadní správu, jak používat ukládání do mezipaměti ve vaší aplikaci, jak rostou.</span><span class="sxs-lookup"><span data-stu-id="15f1d-283">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="15f1d-284">Ukládání odpovědí do mezipaměti ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="15f1d-284">ASP.NET Core response caching</span></span>

<span data-ttu-id="15f1d-285">ASP.NET Core podporuje dvě úrovně ukládání odpovědí do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="15f1d-285">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="15f1d-286">První úroveň neukládá do mezipaměti nic na serveru, ale přidá hlavičky HTTP, které dáte pokyn, aby klienti a servery proxy do mezipaměti odpovědi.</span><span class="sxs-lookup"><span data-stu-id="15f1d-286">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="15f1d-287">Tato možnost je implementovaná tak, že přidáte atribut ResponseCache individuální řadiče nebo provádět akce:</span><span class="sxs-lookup"><span data-stu-id="15f1d-287">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
    [ResponseCache(Duration = 60)]
    public IActionResult Contact()
    { }

    ViewData["Message"] = "Your contact page.";
    return View();
}
```

<span data-ttu-id="15f1d-288">V předchozím příkladu bude výsledkem následující záhlaví se přidá do odpovědi, že klienti pro ukládání do mezipaměti výsledek až 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="15f1d-288">The previous example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.</span></span>

<span data-ttu-id="15f1d-289">Cache-Control: veřejný, max-age = 60</span><span class="sxs-lookup"><span data-stu-id="15f1d-289">Cache-Control: public,max-age=60</span></span>

<span data-ttu-id="15f1d-290">Chcete-li přidat ukládání v mezipaměti na straně serveru k aplikaci, musíte odkázat na balíček Microsoft.AspNetCore.ResponseCaching NuGet a pak přidat ukládání odpovědí do mezipaměti middlewaru.</span><span class="sxs-lookup"><span data-stu-id="15f1d-290">In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware.</span></span> <span data-ttu-id="15f1d-291">Tento middleware je nakonfigurovaný v ConfigureServices a konfigurovat v po spuštění:</span><span class="sxs-lookup"><span data-stu-id="15f1d-291">This middleware is configured in both ConfigureServices and Configure in Startup:</span></span>

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

<span data-ttu-id="15f1d-292">Middleware pro ukládání do mezipaměti odpovědi bude automaticky ukládat do mezipaměti odpovědi na základě sady podmínek, které si můžete přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="15f1d-292">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="15f1d-293">Ve výchozím nastavení jsou uložené v mezipaměti jenom 200 (OK) odpovědi požadovaný prostřednictvím metody GET a HEAD.</span><span class="sxs-lookup"><span data-stu-id="15f1d-293">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="15f1d-294">Kromě toho požadavky musí mít odpovědí s Cache-Control: veřejné záhlaví a nesmí obsahovat záhlaví pro povolení nebo Set-Cookie.</span><span class="sxs-lookup"><span data-stu-id="15f1d-294">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="15f1d-295">Najdete v článku [úplný seznam ukládání do mezipaměti podmínky používané odpovědi ukládání do mezipaměti middleware](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span><span class="sxs-lookup"><span data-stu-id="15f1d-295">See a [complete list of the caching conditions used by the response caching middleware](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="15f1d-296">Ukládání dat do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="15f1d-296">Data caching</span></span>

<span data-ttu-id="15f1d-297">Místo (nebo kromě) ukládání do mezipaměti odpovědi na úplné webu, můžete ukládat do mezipaměti výsledky jednotlivých datových dotazů.</span><span class="sxs-lookup"><span data-stu-id="15f1d-297">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="15f1d-298">V takovém případě můžete použít v paměti, ukládání do mezipaměti na webovém serveru, nebo použijte [distribuované mezipaměti](/aspnet/core/performance/caching/distributed).</span><span class="sxs-lookup"><span data-stu-id="15f1d-298">For this, you can use in memory caching on the web server, or use [a distributed cache](/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="15f1d-299">Tato část popisuje, jak implementovat v ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="15f1d-299">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="15f1d-300">Přidání podpory pro paměti (nebo distribuované) ukládání do mezipaměti v ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="15f1d-300">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="15f1d-301">Je potřeba přidat balíček Microsoft.Extensions.Caching.Memory NuGet.</span><span class="sxs-lookup"><span data-stu-id="15f1d-301">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="15f1d-302">Po přidání služby, můžete požádat o IMemoryCache pomocí vkládání závislostí bez ohledu na to budete potřebovat pro přístup do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="15f1d-302">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="15f1d-303">V tomto příkladu je CachedCatalogService pomocí vzoru návrhu proxy serveru (nebo Dekoratér), tím, že poskytuje alternativní implementace ICatalogService, který určuje přístup do (nebo přidá chování) se základní implementací CatalogService.</span><span class="sxs-lookup"><span data-stu-id="15f1d-303">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

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

<span data-ttu-id="15f1d-304">Konfigurace aplikace pro použití verze uložené v mezipaměti služby, ale stále povolit službu pro získání instance CatalogService musí ve svých konstruktorech, přidáte následující v ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="15f1d-304">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="15f1d-305">Díky tomu na místě volání databáze načíst data katalogu se provést pouze jednou za minutu, ne u každého požadavku.</span><span class="sxs-lookup"><span data-stu-id="15f1d-305">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="15f1d-306">V závislosti na provoz do lokality to může mít velmi velký vliv na počet dotazů provedené v databázi a čas načítání stránky průměrné pro domovskou stránku, která aktuálně závisí na všech třech umístěních dotazů, které jsou vystavené touto službou.</span><span class="sxs-lookup"><span data-stu-id="15f1d-306">Depending on the traffic to the site, this can have a very significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="15f1d-307">Potíže, které mohou nastat, pokud se implementuje ukládání do mezipaměti je _zastaralých dat_ – to znamená, že data, která se změnila na zdroji, ale aktuální verze zůstává v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="15f1d-307">An issue that arises when caching is implemented is _stale data_ – that is, data that has changed at the source but an out of date version remains in the cache.</span></span> <span data-ttu-id="15f1d-308">Použít malé mezipaměti doby trvání, protože zaneprázdněný aplikace je omezené výhody k prodloužení, které data uložená v mezipaměti je jednoduchý způsob, jak tento problém zmírnit.</span><span class="sxs-lookup"><span data-stu-id="15f1d-308">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="15f1d-309">Představte si třeba stránku, která se zadá dotaz izolované databáze, a vyžaduje 10krát za sekundu.</span><span class="sxs-lookup"><span data-stu-id="15f1d-309">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="15f1d-310">Pokud tato stránka je uložené v mezipaměti pro jednominutovým, způsobí počet provedených za minutu z 600 vyřazení na hodnotu 1, snížení 99,8 % databázové dotazy.</span><span class="sxs-lookup"><span data-stu-id="15f1d-310">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="15f1d-311">Pokud místo toho dobu uložení do mezipaměti byly provedeny jednu hodinu, snížení celkové by 99.997 %, ale nyní pravděpodobnost a potenciální stáří zastaralých dat jsou obě výrazné zvýšení.</span><span class="sxs-lookup"><span data-stu-id="15f1d-311">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="15f1d-312">Další možností je aktivně odebrat položky mezipaměti, když dojde k aktualizaci dat, která obsahují.</span><span class="sxs-lookup"><span data-stu-id="15f1d-312">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="15f1d-313">Všechny jednotlivé položky lze odebrat, pokud je jeho klíč je známý:</span><span class="sxs-lookup"><span data-stu-id="15f1d-313">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="15f1d-314">Pokud vaše aplikace zpřístupňuje funkce pro aktualizaci položky, které se ukládá do mezipaměti, můžete odebrat odpovídající položky v mezipaměti v kódu, který provádí aktualizace.</span><span class="sxs-lookup"><span data-stu-id="15f1d-314">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="15f1d-315">V některých případech může být mnoho různých položek, které závisí na konkrétní sady dat.</span><span class="sxs-lookup"><span data-stu-id="15f1d-315">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="15f1d-316">V takovém případě může být užitečné vytvořit závislosti mezi položky mezipaměti s využitím CancellationChangeToken.</span><span class="sxs-lookup"><span data-stu-id="15f1d-316">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="15f1d-317">S CancellationChangeToken můžete ukončit platnost více položek mezipaměti najednou zrušením tokenu.</span><span class="sxs-lookup"><span data-stu-id="15f1d-317">With a CancellationChangeToken, you can expire multiple cache entries at once by cancelling the token.</span></span>

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

<span data-ttu-id="15f1d-318">Ukládání do mezipaměti může výrazně zlepšit výkon webových stránek, které opakovaně požádat o stejné hodnoty z databáze.</span><span class="sxs-lookup"><span data-stu-id="15f1d-318">Caching can dramatically improve the performance of web pages that repeatedly request the same values from the database.</span></span> <span data-ttu-id="15f1d-319">Je nutné měřit výkon přístupu a stránky dat před použitím ukládání do mezipaměti a ukládání do mezipaměti použít pouze pokud vznikne taková potřeba pro zlepšení.</span><span class="sxs-lookup"><span data-stu-id="15f1d-319">Be sure to measure data access and page performance before applying caching, and only apply caching where you see a need for improvement.</span></span> <span data-ttu-id="15f1d-320">Ukládání do mezipaměti používá webové prostředky systémové paměti a zvyšují složitost aplikace, takže je důležité, že jste neoptimalizovat předčasně tímto způsobem.</span><span class="sxs-lookup"><span data-stu-id="15f1d-320">Caching consumes web server memory resources and increases the complexity of the application, so it’s important you don’t prematurely optimize using this technique.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="15f1d-321">[Předchozí](develop-asp-net-core-mvc-apps.md)
>[další](test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="15f1d-321">[Previous](develop-asp-net-core-mvc-apps.md)
[Next](test-asp-net-core-mvc-apps.md)</span></span>