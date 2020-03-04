---
title: Práce s daty v aplikacích ASP.NET Core
description: Architekt moderních webových aplikací pomocí ASP.NET Core a Azure | Práce s daty v aplikacích ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 5a38ca94b6df676858e7cb058272e450aaf1572e
ms.sourcegitcommit: 43d10ef65f0f1fd6c3b515e363bde11a3fcd8d6d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/03/2020
ms.locfileid: "78241036"
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="4a9b3-103">Práce s daty v aplikacích ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a9b3-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="4a9b3-104">"Data jsou úžasné a budou naposledy delší než systémy samotné."</span><span class="sxs-lookup"><span data-stu-id="4a9b3-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>
>
> <span data-ttu-id="4a9b3-105">Tim Berners-Novák</span><span class="sxs-lookup"><span data-stu-id="4a9b3-105">Tim Berners-Lee</span></span>

<span data-ttu-id="4a9b3-106">Přístup k datům je důležitou součástí téměř libovolné softwarové aplikace.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-106">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="4a9b3-107">ASP.NET Core podporuje celou řadu možností přístupu k datům, včetně Entity Framework Core (a také Entity Framework 6), a může fungovat s libovolným rozhraním .NET Data Access Framework.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-107">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="4a9b3-108">Volba rozhraní pro přístup k datům, která se má použít, závisí na potřebách aplikace.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-108">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="4a9b3-109">Díky abstrakci těchto voleb z projektů ApplicationCore a uživatelských rozhraní a zapouzdřování podrobností o implementaci v infrastruktuře vám pomůže vydávat volně spojený testovatelné software.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-109">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="4a9b3-110">Entity Framework Core (pro relační databáze)</span><span class="sxs-lookup"><span data-stu-id="4a9b3-110">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="4a9b3-111">Pokud vytváříte novou ASP.NET Core aplikaci, která potřebuje pracovat s relačními daty, je doporučeným způsobem, jak vaše aplikace přistupuje k datům, je Entity Framework Core (EF Core).</span><span class="sxs-lookup"><span data-stu-id="4a9b3-111">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="4a9b3-112">EF Core je objektově-relační Mapovač (O/RM), který umožňuje vývojářům v rozhraní .NET zachovat objekty do a ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-112">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="4a9b3-113">Eliminuje nutnost, že většina vývojářů kódu pro přístup k datům obvykle vyžaduje zápis.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-113">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="4a9b3-114">Podobně jako u ASP.NET Core se EF Core od základu přepsala pro podporu modulárních aplikací pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-114">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="4a9b3-115">Přidáte ho do vaší aplikace jako balíček NuGet, nakonfigurujete ho při spuštění a vyžádáte ho přes vkládání závislostí všude, kde ho potřebujete.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-115">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="4a9b3-116">Pokud chcete použít EF Core s databází SQL Server, spusťte následující příkaz dotnet CLI:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-116">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

<span data-ttu-id="4a9b3-117">Přidání podpory pro zdroj dat pro nedostatek paměti pro testování:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-117">To add support for an InMemory data source, for testing:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

### <a name="the-dbcontext"></a><span data-ttu-id="4a9b3-118">DbContext</span><span class="sxs-lookup"><span data-stu-id="4a9b3-118">The DbContext</span></span>

<span data-ttu-id="4a9b3-119">Chcete-li pracovat s EF Core, potřebujete podtřídu <xref:Microsoft.EntityFrameworkCore.DbContext>.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-119">To work with EF Core, you need a subclass of <xref:Microsoft.EntityFrameworkCore.DbContext>.</span></span> <span data-ttu-id="4a9b3-120">Tato třída uchovává vlastnosti představující kolekce entit, se kterými bude aplikace pracovat.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-120">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="4a9b3-121">Ukázka eShopOnWeb zahrnuje CatalogContext s kolekcemi pro položky, značky a typy:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-121">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

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

<span data-ttu-id="4a9b3-122">Vaše DbContext musí mít konstruktor, který přijímá DbContextOptions a předávat tento argument základnímu konstruktoru DbContext.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-122">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="4a9b3-123">Máte-li ve své aplikaci pouze jeden DbContext, můžete předat instanci DbContextOptions, ale pokud máte více než jeden, musíte použít > typu Generic DbContextOptions\<T a předat jako obecný parametr typ DbContext.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-123">If you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions\<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="4a9b3-124">Konfigurace EF Core</span><span class="sxs-lookup"><span data-stu-id="4a9b3-124">Configuring EF Core</span></span>

<span data-ttu-id="4a9b3-125">Ve vaší aplikaci ASP.NET Core obvykle ve své metodě ConfigureServices nakonfigurujete EF Core.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-125">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="4a9b3-126">EF Core používá DbContextOptionsBuilder, který podporuje několik užitečných metod rozšíření pro zjednodušení konfigurace.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-126">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="4a9b3-127">Chcete-li nakonfigurovat CatalogContext pro použití databáze SQL Server s připojovacím řetězcem definovaným v konfiguraci, přidejte do ConfigureServices následující kód:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-127">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="4a9b3-128">Použití databáze v paměti:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-128">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="4a9b3-129">Jakmile nainstalujete EF Core, vytvoříte podřízený typ DbContext a nakonfigurujete ho v ConfigureServices, jste připraveni použít EF Core.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-129">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="4a9b3-130">Můžete požádat o instanci DbContext typu v jakékoli službě, která ji potřebuje, a začít pracovat s trvalými entitami pomocí LINQ, jako kdyby byly jednoduše v kolekci.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-130">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="4a9b3-131">EF Core provádí překlad výrazů LINQ do dotazů SQL a ukládá a načítá vaše data.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-131">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="4a9b3-132">Můžete zobrazit dotazy EF Core spouštíte konfigurací protokolovacího nástroje a zajištěním jeho úrovně na alespoň informace, jak je znázorněno na obrázku 8-1.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-132">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![Protokolování dotazů EF Core do konzoly](./media/image8-1.png)

<span data-ttu-id="4a9b3-134">**Obrázek 8-1**.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-134">**Figure 8-1**.</span></span> <span data-ttu-id="4a9b3-135">Protokolování dotazů EF Core do konzoly</span><span class="sxs-lookup"><span data-stu-id="4a9b3-135">Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="4a9b3-136">Načítají se a ukládají se data.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-136">Fetching and storing Data</span></span>

<span data-ttu-id="4a9b3-137">Chcete-li načíst data z EF Core, přistupujete k příslušné vlastnosti a pomocí LINQ můžete filtrovat výsledek.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-137">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="4a9b3-138">Můžete také použít LINQ k provedení projekce a transformovat výsledek z jednoho typu na jiný.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-138">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="4a9b3-139">Následující příklad by načetl CatalogBrands seřazený podle názvu, vyfiltroval podle jejich povolených vlastností a propnul na SelectListItem typ:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-139">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="4a9b3-140">Ve výše uvedeném příkladu je důležité přidat volání do ToListAsync, aby se dotaz spustil okamžitě.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-140">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="4a9b3-141">V opačném případě příkaz přiřadí rozhraní IQueryable\<SelectListItem > k brandItems, které nebude provedeno, dokud není vyhodnocena.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-141">Otherwise, the statement will assign an IQueryable\<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="4a9b3-142">Existují specialisté a nevýhody vrácení výsledků IQueryable z metod.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-142">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="4a9b3-143">Umožňuje, aby byl dotaz EF Core dále upravován, ale může také vést k chybám, ke kterým dochází pouze za běhu, pokud jsou do dotazu přidány operace, které EF Core nelze přeložit.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-143">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="4a9b3-144">Obecně je bezpečnější předat jakékoli filtry do metody, která provádí přístup k datům, a vrátit zpět kolekci v paměti (například seznam\<T >) jako výsledek.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-144">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List\<T>) as the result.</span></span>

<span data-ttu-id="4a9b3-145">EF Core sleduje změny entit, které načítá z Persistence.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-145">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="4a9b3-146">Chcete-li uložit změny ve sledované entitě, stačí zavolat metodu SaveChanges na DbContext, čímž se zajistí, že se jedná o stejnou instanci DbContext, která byla použita k načtení entity.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-146">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="4a9b3-147">Přidávání a odebírání entit je přímo provedeno na příslušné vlastnosti Negenerickými a volání metody SaveChanges ke spuštění databázových příkazů.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-147">Adding and removing entities is directly done on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="4a9b3-148">Následující příklad ukazuje přidávání, aktualizování a odebírání entit z Persistence.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-148">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

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

<span data-ttu-id="4a9b3-149">EF Core podporuje synchronní i asynchronní metody pro načítání a ukládání.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-149">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="4a9b3-150">Ve webových aplikacích se doporučuje použít vzor Async/await s asynchronními metodami, aby se vlákna webového serveru neblokovala při čekání na dokončení operací přístupu k datům.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-150">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="4a9b3-151">Načítají se související data.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-151">Fetching related data</span></span>

<span data-ttu-id="4a9b3-152">Když EF Core načítá entity, naplní všechny vlastnosti, které jsou uloženy přímo s touto entitou v databázi.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-152">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="4a9b3-153">Navigační vlastnosti, jako jsou například seznamy souvisejících entit, nejsou naplněny a mohou mít hodnotu nastavenou na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-153">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="4a9b3-154">Tím se zajistí, že EF Core nenačítá víc dat, než je potřeba, což je zvláště důležité pro webové aplikace, které musí rychle zpracovávat požadavky a vracet odpovědi účinným způsobem.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-154">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="4a9b3-155">Chcete-li zahrnout relace s entitou pomocí _Eager načítání_, zadejte vlastnost pomocí metody include Extension na dotaz, jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-155">To include relationships with an entity using _eager loading_, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="4a9b3-156">Můžete zahrnout více relací a můžete také zahrnout podrelace pomocí ThenInclude.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-156">You can include multiple relationships, and you can also include subrelationships using ThenInclude.</span></span> <span data-ttu-id="4a9b3-157">EF Core spustí jeden dotaz, který načte výslednou sadu entit.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-157">EF Core will execute a single query to retrieve the resulting set of entities.</span></span> <span data-ttu-id="4a9b3-158">Alternativně můžete zahrnout navigační vlastnosti navigačních vlastností předáním ".". -řetězec oddělený řetězcem metody rozšíření `.Include()`, například:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-158">Alternately you can include navigation properties of navigation properties by passing a '.'-separated string to the `.Include()` extension method, like so:</span></span>

```csharp
    .Include(“Items.Products”)
```

<span data-ttu-id="4a9b3-159">Kromě zapouzdření logiky filtrování může specifikace určit tvar dat, která mají být vrácena, včetně vlastností, které mají být naplněny.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-159">In addition to encapsulating filtering logic, a specification can specify the shape of the data to be returned, including which properties to populate.</span></span> <span data-ttu-id="4a9b3-160">Ukázka eShopOnWeb obsahuje několik specifikací, které ukazují, jak zapouzdřit Eager načítání informací v rámci specifikace.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-160">The eShopOnWeb sample includes several specifications that demonstrate encapsulating eager loading information within the specification.</span></span> <span data-ttu-id="4a9b3-161">To, jak se specifikace používá jako součást dotazu, vidíte tady:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-161">You can see how the specification is used as part of a query here:</span></span>

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

<span data-ttu-id="4a9b3-162">Další možností načítání souvisejících dat je použití _explicitního načítání_.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-162">Another option for loading related data is to use _explicit loading_.</span></span> <span data-ttu-id="4a9b3-163">Explicitní načítání umožňuje načíst další data do entity, která již byla načtena.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-163">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="4a9b3-164">Vzhledem k tomu, že se jedná o samostatný požadavek na databázi, není doporučeno používat webové aplikace, což by mělo minimalizovat počet přenosů databáze odeslaných na požadavek.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-164">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="4a9b3-165">_Opožděné načítání_ je funkce, která automaticky načte související data, která jsou odkazována aplikací.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-165">_Lazy loading_ is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="4a9b3-166">EF Core přidaná podpora pro opožděné načítání ve verzi 2,1.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-166">EF Core has added support for lazy loading in version 2.1.</span></span> <span data-ttu-id="4a9b3-167">Opožděné načítání není ve výchozím nastavení povolené a vyžaduje instalaci `Microsoft.EntityFrameworkCore.Proxies`.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-167">Lazy loading is not enabled by default and requires installing the `Microsoft.EntityFrameworkCore.Proxies`.</span></span> <span data-ttu-id="4a9b3-168">Stejně jako u explicitního načítání by se obvykle mělo pro webové aplikace zakázat opožděné načítání, protože jeho použití bude mít za následek další databázové dotazy v rámci každé webové žádosti.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-168">As with explicit loading, lazy loading should typically be disabled for web applications, since its use will result in additional database queries being made within each web request.</span></span> <span data-ttu-id="4a9b3-169">Režijní náklady spojené s opožděným načtením se bohužel často neúčtují v době vývoje, pokud je latence malá a často jsou datové sady používané pro testování malé.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-169">Unfortunately, the overhead incurred by lazy loading often goes unnoticed at development time, when latency is small and often the data sets used for testing are small.</span></span> <span data-ttu-id="4a9b3-170">Nicméně v produkčním prostředí s více uživateli, více daty a větší latencí můžou další požadavky databáze často způsobit špatný výkon webových aplikací, které využívají opožděné načítání.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-170">However, in production, with more users, more data, and more latency, the additional database requests can often result in poor performance for web applications that make heavy use of lazy loading.</span></span>

[<span data-ttu-id="4a9b3-171">Vyhnout se entitám opožděného načítání ve webových aplikacích</span><span class="sxs-lookup"><span data-stu-id="4a9b3-171">Avoid Lazy Loading Entities in Web Applications</span></span>](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a><span data-ttu-id="4a9b3-172">Zapouzdření dat</span><span class="sxs-lookup"><span data-stu-id="4a9b3-172">Encapsulating data</span></span>

<span data-ttu-id="4a9b3-173">EF Core podporuje několik funkcí, které umožní vašemu modelu správně zapouzdřit svůj stav.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-173">EF Core supports several features that allow your model to properly encapsulate its state.</span></span> <span data-ttu-id="4a9b3-174">Běžným problémem v doménových modelech je to, že zveřejňují vlastnosti navigace v kolekci jako veřejně přístupné typy seznamů.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-174">A common problem in domain models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="4a9b3-175">To umožňuje všem spolupracovníkům manipulovat s obsahem těchto typů kolekcí, což může obejít důležité obchodní pravidla související s kolekcí, což může opustit objekt v neplatném stavu.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-175">This allows any collaborator to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="4a9b3-176">Řešením je vystavit přístup jen pro čtení k souvisejícím kolekcím a explicitně poskytnout metody definující způsoby, kterými je můžou klienti manipulovat, jako v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-176">The solution to this is to expose read-only access to related collections, and explicitly provide methods defining ways in which clients can manipulate them, as in this example:</span></span>

```csharp
public class Basket : BaseEntity
{
    public string BuyerId { get; set; }
    private readonly List<BasketItem> _items = new List<BasketItem>();
    public IReadOnlyCollection<BasketItem> Items => _items.AsReadOnly();

    public void AddItem(int catalogItemId, decimal unitPrice, int quantity = 1)
    {
        if (!Items.Any(i => i.CatalogItemId == catalogItemId))
        {
            _items.Add(new BasketItem()
            {
                CatalogItemId = catalogItemId,
                Quantity = quantity,
                UnitPrice = unitPrice
            });
            return;
        }
        var existingItem = Items.FirstOrDefault(i => i.CatalogItemId == catalogItemId);
        existingItem.Quantity += quantity;
    }
}
```

<span data-ttu-id="4a9b3-177">Tento typ entity nevystavuje vlastnost Public `List` nebo `ICollection`, ale místo toho zpřístupňuje typ `IReadOnlyCollection`, který zabalí základní typ seznamu.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-177">This entity type doesn’t expose a public `List` or `ICollection` property, but instead exposes an `IReadOnlyCollection` type that wraps the underlying List type.</span></span> <span data-ttu-id="4a9b3-178">Při použití tohoto modelu můžete určit, že se má Entity Framework Core použít pole pro zálohování, například:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-178">When using this pattern, you can indicate to Entity Framework Core to use the backing field like so:</span></span>

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

<span data-ttu-id="4a9b3-179">Dalším způsobem, jak můžete zlepšit model domény, je použití objektů hodnot pro typy, které postrádají identitu a jsou rozlišeny jenom jejich vlastnostmi.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-179">Another way in which you can improve your domain model is through the use of value objects for types that lack identity and are only distinguished by their properties.</span></span> <span data-ttu-id="4a9b3-180">Použití takových typů jako vlastností vašich entit může pomoci udržet logiku specifickou pro objekt hodnoty, kde patří, a může zabránit duplicitní logice mezi několika entitami, které používají stejný pojem.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-180">Using such types as properties of your entities can help keep logic specific to the value object where it belongs, and can avoid duplicate logic between multiple entities that use the same concept.</span></span> <span data-ttu-id="4a9b3-181">V Entity Framework Core můžete zachovat objekty hodnot ve stejné tabulce jako jejich vlastnící entita nakonfigurováním typu jako vlastněné entity, například takto:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-181">In Entity Framework Core, you can persist value objects in the same table as their owning entity by configuring the type as an owned entity, like so:</span></span>

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

<span data-ttu-id="4a9b3-182">V tomto příkladu je vlastnost `ShipToAddress` typu `Address`.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-182">In this example, the `ShipToAddress` property is of type `Address`.</span></span> <span data-ttu-id="4a9b3-183">`Address` je objekt hodnoty s několika vlastnostmi, například `Street` a `City`.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-183">`Address` is a value object with several properties such as `Street` and `City`.</span></span> <span data-ttu-id="4a9b3-184">EF Core mapuje objekt `Order` na jeho tabulku s jedním sloupcem na `Address` vlastnost, přičemž prefixuje název každého sloupce s názvem vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-184">EF Core maps the `Order` object to its table with one column per `Address` property, prefixing each column name with the name of the property.</span></span> <span data-ttu-id="4a9b3-185">V tomto příkladu by tabulka `Order` zahrnovala sloupce jako `ShipToAddress_Street` a `ShipToAddress_City`.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-185">In this example, the `Order` table would include columns such as `ShipToAddress_Street` and `ShipToAddress_City`.</span></span> <span data-ttu-id="4a9b3-186">V případě potřeby je také možné uložit vlastněné typy v samostatných tabulkách.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-186">It's also possible to store owned types in separate tables, if desired.</span></span>

<span data-ttu-id="4a9b3-187">Přečtěte si další informace o podpoře vlastněných [entit v EF Core](/ef/core/modeling/owned-entities).</span><span class="sxs-lookup"><span data-stu-id="4a9b3-187">Learn more about owned [entity support in EF Core](/ef/core/modeling/owned-entities).</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="4a9b3-188">Odolná připojení</span><span class="sxs-lookup"><span data-stu-id="4a9b3-188">Resilient connections</span></span>

<span data-ttu-id="4a9b3-189">Externí prostředky, jako jsou databáze SQL, mohou být občas nedostupné.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-189">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="4a9b3-190">V případech dočasné nedostupnosti mohou aplikace použít logiku opakování, aby nedošlo k vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-190">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="4a9b3-191">Tato technika se běžně označuje jako _odolnost připojení_.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-191">This technique is commonly referred to as _connection resiliency_.</span></span> <span data-ttu-id="4a9b3-192">Můžete implementovat [vlastní opakování pomocí exponenciální omezení rychlosti](https://docs.microsoft.com/azure/architecture/patterns/retry) techniky tím, že zkusíte opakovat pokus s exponenciálním zvýšením čekací doby, dokud nedosáhnete maximálního počtu opakování.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-192">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to retry with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="4a9b3-193">Tato technika zahrnuje skutečnost, že prostředky cloudu můžou být občas nedostupné po krátkou dobu, což vede k selhání některých požadavků.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-193">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="4a9b3-194">Pro Azure SQL DB už Entity Framework Core k dispozici odolnost interního připojení k databázi a logiku opakování.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-194">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="4a9b3-195">Pro každé připojení DbContext ale musíte povolit strategii spouštění Entity Framework, pokud chcete mít odolná EF Core připojení.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-195">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="4a9b3-196">Například následující kód na úrovni připojení EF Core umožňuje odolné připojení SQL, které se opakuje, pokud se připojení nepovede.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-196">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="4a9b3-197">Strategie provádění a explicitní transakce pomocí BeginTransaction a více DbContexts</span><span class="sxs-lookup"><span data-stu-id="4a9b3-197">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="4a9b3-198">Když jsou v EF Core připojení povolené opakované pokusy, každá operace, kterou provádíte pomocí EF Core, se stal svou vlastní opakovanou operací.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-198">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retryable operation.</span></span> <span data-ttu-id="4a9b3-199">Každý dotaz a každé volání metody SaveChanges se bude opakovat jako jednotka, pokud dojde k přechodnému selhání.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-199">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="4a9b3-200">Nicméně pokud váš kód inicializuje transakci pomocí BeginTransaction, definujete vlastní skupinu operací, které je třeba považovat za jednotku. vše uvnitř transakce se musí vrátit zpátky, pokud dojde k selhání.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-200">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit; everything inside the transaction has to be rolled back if a failure occurs.</span></span> <span data-ttu-id="4a9b3-201">Pokud se pokusíte provést tuto transakci při použití strategie provádění EF (opakování zásad) a zahrnete do něj několik DbContexts, zobrazí se výjimka podobná následující.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-201">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="4a9b3-202">System. InvalidOperationException: nakonfigurovaná strategie provádění SqlServerRetryingExecutionStrategy nepodporuje transakce iniciované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-202">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="4a9b3-203">K provedení všech operací v transakci jako opakované jednotky použijte strategii spuštění vrácenou funkcí DbContext. Database. CreateExecutionStrategy ().</span><span class="sxs-lookup"><span data-stu-id="4a9b3-203">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retryable unit.</span></span>

<span data-ttu-id="4a9b3-204">Řešením je ruční vyvolání strategie provádění EF s delegátem, který představuje všechno, co je třeba provést.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-204">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="4a9b3-205">Pokud dojde k přechodnému selhání, strategie provádění znovu vyvolá delegáta.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-205">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="4a9b3-206">Následující kód ukazuje, jak implementovat tento přístup:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-206">The following code shows how to implement this approach:</span></span>

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

<span data-ttu-id="4a9b3-207">První DbContext je \_catalogContext a druhá DbContext je v objektu \_integrationEventLogService.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-207">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="4a9b3-208">Nakonec se akce potvrzení provede více DbContexts a použije se strategie provádění EF.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-208">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="4a9b3-209">Odkazy – Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="4a9b3-209">References – Entity Framework Core</span></span>
>
> - <span data-ttu-id="4a9b3-210">**EF Core Docs**
>   <https://docs.microsoft.com/ef/></span><span class="sxs-lookup"><span data-stu-id="4a9b3-210">**EF Core Docs**
<https://docs.microsoft.com/ef/></span></span>
> - <span data-ttu-id="4a9b3-211">**EF Core: související
>   dat** <https://docs.microsoft.com/ef/core/querying/related-data></span><span class="sxs-lookup"><span data-stu-id="4a9b3-211">**EF Core: Related Data**
<https://docs.microsoft.com/ef/core/querying/related-data></span></span>
> - <span data-ttu-id="4a9b3-212">**Vyhněte se entitám opožděného načítání v aplikacích ASPNET**
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span><span class="sxs-lookup"><span data-stu-id="4a9b3-212">**Avoid Lazy Loading Entities in ASPNET Applications**
<https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span></span>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="4a9b3-213">EF Core nebo mikroorm?</span><span class="sxs-lookup"><span data-stu-id="4a9b3-213">EF Core or micro-ORM?</span></span>

<span data-ttu-id="4a9b3-214">I když je EF Core skvělou volbou pro správu trvalosti a většina z nich zapouzdřuje podrobnosti databáze od vývojářů aplikací, není jedinou volbou.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-214">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it isn't the only choice.</span></span> <span data-ttu-id="4a9b3-215">Další oblíbenou alternativou Open Source je [dapperem](https://github.com/StackExchange/Dapper), což se říká mikroorm.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-215">Another popular open-source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="4a9b3-216">Mikroorm je odlehčený a méně plnohodnotný nástroj pro mapování objektů na datové struktury.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-216">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="4a9b3-217">V případě Dapperem se záměr jejich návrhu zaměřuje na výkon, místo úplného zapouzdření základních dotazů, které používá k načtení a aktualizaci dat.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-217">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="4a9b3-218">Vzhledem k tomu, že se nejedná o abstraktní SQL z vývojářů, Dapperem je "blíže k metalu" a vývojářům umožňuje psát přesné dotazy, které chtějí použít pro danou operaci přístupu k datům.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-218">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="4a9b3-219">EF Core má dvě důležité funkce, které nabízí oddělení IT od Dapperem, ale také přidávají k jeho režijnímu výkonu.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-219">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="4a9b3-220">První je převod z výrazů LINQ do jazyka SQL.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-220">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="4a9b3-221">Tyto překlady jsou ukládány do mezipaměti, ale i tak, aby při prvním spuštění bylo režie.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-221">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="4a9b3-222">Druhým je sledování změn u entit (aby bylo možné vygenerovat efektivní příkazy aktualizace).</span><span class="sxs-lookup"><span data-stu-id="4a9b3-222">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="4a9b3-223">Toto chování je možné vypnout pro konkrétní dotazy pomocí rozšíření AsNotTracking.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-223">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="4a9b3-224">EF Core také generuje dotazy SQL, které jsou obvykle velice efektivní a v jakémkoliv případě zcela přijatelné z hlediska výkonu, ale pokud potřebujete lepší kontrolu nad přesným dotazem, který se má provést, můžete předat vlastní SQL (nebo spustit uloženou proceduru) pomocí EF. Jádro.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-224">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="4a9b3-225">V takovém případě Dapperem stále vykonává EF Core, ale jenom mírně.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-225">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="4a9b3-226">Julie Lerman prezentuje údaje o výkonu v jeho 2016 článku na webu MSDN [dapperem, Entity Framework a hybridních aplikacích](https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps).</span><span class="sxs-lookup"><span data-stu-id="4a9b3-226">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps).</span></span> <span data-ttu-id="4a9b3-227">Další data srovnávacích testů výkonu pro celou řadu metod přístupu k datům najdete na [webu dapperem](https://github.com/StackExchange/Dapper).</span><span class="sxs-lookup"><span data-stu-id="4a9b3-227">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="4a9b3-228">Chcete-li zjistit, jak se syntaxe Dapperem liší od EF Core, zvažte tyto dvě verze stejné metody pro načtení seznamu položek:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-228">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

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

<span data-ttu-id="4a9b3-229">Pokud potřebujete vytvořit složitější grafy objektů pomocí Dapperem, je potřeba napsat přidružené dotazy sami (na rozdíl od přidání zahrnutí jako při EF Core).</span><span class="sxs-lookup"><span data-stu-id="4a9b3-229">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="4a9b3-230">To je podporováno prostřednictvím nejrůznějších syntaxí, včetně funkce s názvem vícenásobné mapování, které umožňuje mapovat jednotlivé řádky na více mapovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-230">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="4a9b3-231">Například vzhledem k tomu, že daný příspěvek třídy se vlastníkem vlastnosti typu uživatel, vrátí následující SQL všechna potřebná data:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-231">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="4a9b3-232">Každý vrácený řádek obsahuje data uživatelů i post.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-232">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="4a9b3-233">Vzhledem k tomu, že data uživatelů by měla být připojena k post data prostřednictvím její vlastnosti Owner, je použita následující funkce:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-233">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="4a9b3-234">Úplný výpis kódu, který vrátí kolekci příspěvků s vlastností Owner naplněnou s přidruženými uživatelskými daty, by byl:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-234">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="4a9b3-235">Vzhledem k tomu, že nabízí méně zapouzdření, Dapperem vyžaduje, aby si vývojáři dozvěděli více o tom, jak jsou jejich data uložená, jak je efektivně dotazovat, a zapsali další kód pro jeho načtení.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-235">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="4a9b3-236">Při změně modelu místo pouhého vytvoření nové migrace (jiné funkce EF Core) a aktualizace informací o mapování na jednom místě v DbContext musí být všechny ovlivněné dotazy aktualizované.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-236">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="4a9b3-237">Tyto dotazy nemají žádné záruky v době kompilace, takže můžou v reakci na změny modelu nebo databáze přerušit za běhu. díky tomu je obtížné detekovat chyby rychleji.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-237">These queries have no compile-time guarantees, so they may break at run time in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="4a9b3-238">V systému Exchange pro tyto kompromisy nabízí Dapperem extrémně vysoký výkon.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-238">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="4a9b3-239">Pro většinu aplikací a pro většinu částí téměř všech aplikací nabízí EF Core přijatelný výkon.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-239">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="4a9b3-240">Proto se přínosy pro produktivitu vývojářů můžou snížit na výkon.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-240">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="4a9b3-241">V případě dotazů, které mohou využívat ukládání do mezipaměti, může být samotný dotaz proveden pouze v malém procentu času, což vede k poměrně malým rozdílům ve výkonu dotazů moot.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-241">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="4a9b3-242">SQL nebo NoSQL</span><span class="sxs-lookup"><span data-stu-id="4a9b3-242">SQL or NoSQL</span></span>

<span data-ttu-id="4a9b3-243">Tradičně jsou relační databáze, jako je SQL Server, na webu Marketplace pro trvalé úložiště dat, ale nejedná se o jediné dostupné řešení.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-243">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="4a9b3-244">Databáze NoSQL, jako je [MongoDB](https://www.mongodb.com/what-is-mongodb) , nabízejí odlišný přístup k ukládání objektů.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-244">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="4a9b3-245">Místo mapování objektů na tabulky a řádky je další možností serializace celého grafu objektů a uložení výsledku.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-245">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="4a9b3-246">Nejnižšími výhodami tohoto přístupu je jednoduchost a výkon.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-246">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="4a9b3-247">Je jednodušší uložit jeden serializovaný objekt s klíčem, než aby bylo možné objekt rozložit na mnoho tabulek se vztahy a aktualizacemi a řádky, které se mohly změnit od posledního načtení objektu z databáze.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-247">It's simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="4a9b3-248">Podobně načítání a deserializace jednoho objektu z úložiště založeného na klíčích je obvykle mnohem rychlejší a jednodušší než složitá spojení nebo více databázových dotazů, které jsou nutné k úplnému vytvoření stejného objektu z relační databáze.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-248">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="4a9b3-249">Chybějící zámky nebo transakce nebo pevné schéma také zpřístupňuje NoSQL databází snadněji škálování napříč mnoha počítači a podporují velmi velké datové sady.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-249">The lack of locks or transactions or a fixed schema also makes NoSQL databases amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="4a9b3-250">Na druhé straně databáze NoSQL (jak jsou obvykle volány) mají své nevýhody.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-250">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="4a9b3-251">Relační databáze používají normalizaci k vymáhání konzistence a vyhnout se duplikaci dat.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-251">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="4a9b3-252">Tím se zmenší celková velikost databáze a zajistí, že aktualizace sdílených dat budou k dispozici okamžitě v rámci databáze.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-252">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="4a9b3-253">V relační databázi může tabulka adres odkazovat na tabulku zemí podle ID, takže pokud se změnil název země nebo oblasti, budou se záznamy adres těžit z této aktualizace, aniž by bylo nutné je aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-253">In a relational database, an Address table might reference a Country table by ID, such that if the name of a country/region were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="4a9b3-254">V databázi NoSQL se ale adresa a přidružená země můžou serializovat jako součást mnoha uložených objektů.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-254">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="4a9b3-255">Aktualizace názvu země nebo oblasti by vyžadovala aktualizaci všech takových objektů, nikoli jednoho řádku.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-255">An update to a country/region name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="4a9b3-256">Relační databáze mohou také zajistit relační integritu vynucením pravidel, jako jsou cizí klíče.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-256">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="4a9b3-257">Databáze NoSQL obvykle nenabízejí taková omezení pro svá data.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-257">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="4a9b3-258">Jiné databáze složitosti NoSQL musí řešit správu verzí.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-258">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="4a9b3-259">Když se změní vlastnosti objektu, nemusí být možné deserializovat z minulých verzí, které byly uloženy.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-259">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="4a9b3-260">Proto musí být všechny existující objekty, které mají serializovanou (předchozí) verzi objektu, aktualizovány tak, aby odpovídaly novému schématu.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-260">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="4a9b3-261">Nejedná se o koncepční rozdíl od relační databáze, kde změny schématu někdy vyžadují skripty aktualizace nebo aktualizace mapování.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-261">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="4a9b3-262">Počet položek, které je třeba upravit, je však často mnohem větší v přístupu NoSQL, protože existuje více duplicit dat.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-262">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="4a9b3-263">Je možné, že databáze NoSQL ukládá více verzí objektů, ale některé pevné relační databáze schémat obvykle nepodporují.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-263">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="4a9b3-264">Nicméně v tomto případě bude kód vaší aplikace muset brát v úvahu existenci předchozích verzí objektů a přidává další složitost.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-264">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="4a9b3-265">Databáze NoSQL obvykle vynutily [kyselinu](https://en.wikipedia.org/wiki/ACID), což znamená, že výhody výkonu i škálovatelnosti oproti relačním databázím.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-265">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="4a9b3-266">Jsou vhodné pro extrémně velké datové sady a objekty, které nejsou vhodné pro úložiště v normalizovaných strukturách tabulek.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-266">They're well suited to extremely large datasets and objects that are not well suited to storage in normalized table structures.</span></span> <span data-ttu-id="4a9b3-267">Neexistuje žádný důvod, proč jediná aplikace nemůže využívat relační i NoSQL databáze, a to s využitím každého z nich, kde se nejlépe hodí.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-267">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-cosmos-db"></a><span data-ttu-id="4a9b3-268">Databáze Azure Cosmos</span><span class="sxs-lookup"><span data-stu-id="4a9b3-268">Azure Cosmos DB</span></span>

<span data-ttu-id="4a9b3-269">Azure Cosmos DB je plně spravovaná databázová služba NoSQL, která nabízí cloudové úložiště dat bez schématu.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-269">Azure Cosmos DB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="4a9b3-270">Azure Cosmos DB je postavená na zajištění rychlého a předvídatelného výkonu, vysoké dostupnosti, elastického škálování a globální distribuce.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-270">Azure Cosmos DB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="4a9b3-271">I když se jedná o databázi NoSQL, můžou vývojáři používat pro data JSON bohatou a známou schopnost dotazů SQL.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-271">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="4a9b3-272">Všechny prostředky v Azure Cosmos DB jsou uloženy jako dokumenty JSON.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-272">All resources in Azure Cosmos DB are stored as JSON documents.</span></span> <span data-ttu-id="4a9b3-273">Prostředky se spravují jako _položky_, což jsou dokumenty obsahující metadata a _kanály_, které jsou kolekcemi položek.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-273">Resources are managed as _items_, which are documents containing metadata, and _feeds_, which are collections of items.</span></span> <span data-ttu-id="4a9b3-274">Obrázek 8-2 ukazuje vztah mezi různými prostředky Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-274">Figure 8-2 shows the relationship between different Azure Cosmos DB resources.</span></span>

![Hierarchický vztah mezi prostředky v Azure Cosmos DB databáze JSON NoSQL](./media/image8-2.png)

<span data-ttu-id="4a9b3-276">**Obrázek 8-2.**</span><span class="sxs-lookup"><span data-stu-id="4a9b3-276">**Figure 8-2.**</span></span> <span data-ttu-id="4a9b3-277">Azure Cosmos DB organizace prostředků.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-277">Azure Cosmos DB resource organization.</span></span>

<span data-ttu-id="4a9b3-278">Dotazovací jazyk Azure Cosmos DB je jednoduché, ale výkonné rozhraní pro dotazování dokumentů JSON.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-278">The Azure Cosmos DB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="4a9b3-279">Tento jazyk podporuje podmnožinu gramatiky ANSI SQL a přidává těsnou integraci s javascriptovými objekty, poli, vytvářením objektů a voláním funkcí.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-279">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="4a9b3-280">**Odkazy – Azure Cosmos DB**</span><span class="sxs-lookup"><span data-stu-id="4a9b3-280">**References – Azure Cosmos DB**</span></span>

- <span data-ttu-id="4a9b3-281">Azure Cosmos DB Úvod <https://docs.microsoft.com/azure/cosmos-db/introduction></span><span class="sxs-lookup"><span data-stu-id="4a9b3-281">Azure Cosmos DB Introduction <https://docs.microsoft.com/azure/cosmos-db/introduction></span></span>

## <a name="other-persistence-options"></a><span data-ttu-id="4a9b3-282">Další možnosti trvalosti</span><span class="sxs-lookup"><span data-stu-id="4a9b3-282">Other persistence options</span></span>

<span data-ttu-id="4a9b3-283">Kromě možností relačního a NoSQL úložiště mohou aplikace ASP.NET Core používat Azure Storage k ukládání nejrůznějších formátů dat a souborů v cloudovém škálovatelném způsobem.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-283">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="4a9b3-284">Azure Storage je široce škálovatelná, takže můžete začít ukládat malé objemy dat a škálovat je tak, aby se ukládaly stovky nebo terabajty, pokud je vaše aplikace vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-284">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="4a9b3-285">Azure Storage podporuje čtyři druhy dat:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-285">Azure Storage supports four kinds of data:</span></span>

- <span data-ttu-id="4a9b3-286">Blob Storage nestrukturovaných textových nebo binárních úložišť, označovaných také jako úložiště objektů.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-286">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

- <span data-ttu-id="4a9b3-287">Table Storage strukturovaných datových sad, které jsou přístupné prostřednictvím klíčů řádků.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-287">Table Storage for structured datasets, accessible via row keys.</span></span>

- <span data-ttu-id="4a9b3-288">Queue Storage pro spolehlivé zasílání zpráv na základě fronty.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-288">Queue Storage for reliable queue-based messaging.</span></span>

- <span data-ttu-id="4a9b3-289">File Storage pro přístup ke sdíleným souborům mezi virtuálními počítači Azure a místními aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-289">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="4a9b3-290">**Odkazy – Azure Storage**</span><span class="sxs-lookup"><span data-stu-id="4a9b3-290">**References – Azure Storage**</span></span>

- <span data-ttu-id="4a9b3-291">Azure Storage Úvod <https://docs.microsoft.com/azure/storage/storage-introduction></span><span class="sxs-lookup"><span data-stu-id="4a9b3-291">Azure Storage Introduction <https://docs.microsoft.com/azure/storage/storage-introduction></span></span>

## <a name="caching"></a><span data-ttu-id="4a9b3-292">Ukládání do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="4a9b3-292">Caching</span></span>

<span data-ttu-id="4a9b3-293">V případě webových aplikací by měly být jednotlivé webové žádosti dokončeny v nejkratší možné době.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-293">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="4a9b3-294">Toho můžete dosáhnout tak, že omezíte počet externích volání, které server musí provést, aby se žádost dokončila.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-294">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="4a9b3-295">Ukládání do mezipaměti zahrnuje ukládání kopie dat na server (nebo jiné úložiště dat, které je snazší dotazovat se na zdroj dat).</span><span class="sxs-lookup"><span data-stu-id="4a9b3-295">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="4a9b3-296">Webové aplikace a zejména tradiční webové aplikace bez ověřování hesla potřebují pro každý požadavek sestavit celé uživatelské rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-296">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="4a9b3-297">To často znamená, že mnoho stejných databázových dotazů opakovaně vychází z jednoho požadavku uživatele na další.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-297">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="4a9b3-298">Ve většině případů se tato data mění zřídka, proto existuje málo důvodů, jak ji z databáze trvale vyžádat.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-298">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="4a9b3-299">ASP.NET Core podporuje ukládání odpovědí do mezipaměti, pro ukládání celých stránek do mezipaměti a ukládání dat do mezipaměti, které podporuje podrobnější chování ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-299">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="4a9b3-300">Při implementaci ukládání do mezipaměti je důležité mít na paměti oddělení obav.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-300">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="4a9b3-301">Vyhněte se implementaci logiky ukládání do mezipaměti v logice přístupu k datům nebo v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-301">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="4a9b3-302">Místo toho zapouzdřujte ukládání do mezipaměti ve vlastních třídách a pomocí konfigurace spravujte jeho chování.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-302">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="4a9b3-303">Postupuje podle otevřených/uzavřených a jednoduchých zodpovědností a usnadňuje vám správu způsobu ukládání do mezipaměti ve vaší aplikaci během rozšiřování.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-303">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="4a9b3-304">Ukládání odpovědí do mezipaměti ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="4a9b3-304">ASP.NET Core response caching</span></span>

<span data-ttu-id="4a9b3-305">ASP.NET Core podporuje dvě úrovně ukládání odpovědí do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-305">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="4a9b3-306">První úroveň neukládá do mezipaměti cokoli na serveru, ale přidává hlavičky HTTP, které instruují klienty a proxy servery k ukládání odpovědí do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-306">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="4a9b3-307">To je implementováno přidáním atributu ResponseCache na jednotlivé řadiče nebo akce:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-307">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
[ResponseCache(Duration = 60)]
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";
    return View();
}
```

<span data-ttu-id="4a9b3-308">V předchozím příkladu bude k odpovědi přidáno následující záhlaví, které dává klientům pokyn, aby výsledky do mezipaměti po dobu až 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-308">The previous example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.</span></span>

<span data-ttu-id="4a9b3-309">Cache-Control: Public, Max-Age = 60</span><span class="sxs-lookup"><span data-stu-id="4a9b3-309">Cache-Control: public,max-age=60</span></span>

<span data-ttu-id="4a9b3-310">Aby bylo možné do aplikace přidat ukládání do mezipaměti na straně serveru, musíte odkazovat na balíček NuGet Microsoft. AspNetCore. ResponseCaching a pak přidat middleware pro ukládání odpovědí do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-310">In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware.</span></span> <span data-ttu-id="4a9b3-311">Tento middleware je nakonfigurovaný jak v ConfigureServices, tak v konfiguraci při spuštění:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-311">This middleware is configured in both ConfigureServices and Configure in Startup:</span></span>

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

<span data-ttu-id="4a9b3-312">Middleware pro ukládání odpovědí do mezipaměti bude automaticky ukládat odpovědi na základě sady podmínek, které můžete přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-312">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="4a9b3-313">Ve výchozím nastavení se do mezipaměti ukládají pouze odpovědi 200 (OK) požadované prostřednictvím metody GET nebo HEAD.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-313">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="4a9b3-314">Kromě toho musí mít požadavky odpověď s hlavičkou Cache-Control: Public header a nesmí obsahovat hlavičky pro Authorization nebo Set-cookie.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-314">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="4a9b3-315">Podívejte se na [úplný seznam podmínek ukládání do mezipaměti, které používá middleware pro ukládání odpovědí do mezipaměti](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span><span class="sxs-lookup"><span data-stu-id="4a9b3-315">See a [complete list of the caching conditions used by the response caching middleware](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="4a9b3-316">Ukládání dat do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="4a9b3-316">Data caching</span></span>

<span data-ttu-id="4a9b3-317">Místo (nebo kromě) ukládání úplných webových odpovědí do mezipaměti můžete ukládat výsledky jednotlivých dotazů na data.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-317">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="4a9b3-318">V takovém případě můžete použít v ukládání do mezipaměti na webovém serveru nebo použít [distribuovanou mezipaměť](/aspnet/core/performance/caching/distributed).</span><span class="sxs-lookup"><span data-stu-id="4a9b3-318">For this, you can use in memory caching on the web server, or use [a distributed cache](/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="4a9b3-319">V této části se dozvíte, jak implementovat v mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-319">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="4a9b3-320">Přidáte podporu pro ukládání do mezipaměti (nebo distribuované) do mezipaměti v ConfigureServices:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-320">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="4a9b3-321">Nezapomeňte přidat také balíček NuGet Microsoft. Extensions. Caching. Memory.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-321">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="4a9b3-322">Po přidání služby si vyžádáte IMemoryCache prostřednictvím injektáže závislosti, kdykoli budete potřebovat přístup do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-322">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="4a9b3-323">V tomto příkladu používá CachedCatalogService vzor návrhu proxy (nebo dekoratér) tím, že poskytuje alternativní implementaci ICatalogService, která řídí přístup k základní implementaci CatalogService (nebo k tomu přidává chování).</span><span class="sxs-lookup"><span data-stu-id="4a9b3-323">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

```csharp
public class CachedCatalogService : ICatalogService
{
    private readonly IMemoryCache _cache;
    private readonly CatalogService _catalogService;
    private static readonly string _brandsKey = "brands";
    private static readonly string _typesKey = "types";
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
        string cacheKey = $"items-{pageIndex}-{itemsPage}-{brandID}-{typeId}";
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

<span data-ttu-id="4a9b3-324">Chcete-li nakonfigurovat aplikaci tak, aby používala verzi služby uloženou v mezipaměti, ale stále umožňuje službě získat v jejím konstruktoru instanci CatalogService, kterou potřebuje, přidejte do ConfigureServices následující:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-324">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="4a9b3-325">V takovém případě se databáze volá do načtení dat katalogu pouze jednou za minutu, nikoli u všech požadavků.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-325">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="4a9b3-326">V závislosti na provozu na lokalitu to může mít výrazný vliv na počet dotazů provedených v databázi a na průměrnou dobu načítání stránky pro domovskou stránku, která v současné době závisí na všech třech dotazech vystavených touto službou.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-326">Depending on the traffic to the site, this can have a significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="4a9b3-327">K problému, který nastane při implementaci ukládání do mezipaměti, je _zastaralá data_ – to znamená, že data, která se změnila ve zdroji, ale zastaralá verze, zůstanou v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-327">An issue that arises when caching is implemented is _stale data_ – that is, data that has changed at the source but an out-of-date version remains in the cache.</span></span> <span data-ttu-id="4a9b3-328">Jednoduchým způsobem, jak tento problém zmírnit, je použití malých mezipamětí, protože u zaneprázdněné aplikace je k rozšíření dat délky v mezipaměti omezená další výhoda.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-328">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="4a9b3-329">Představte si například stránku, která vytváří jeden databázový dotaz a je požadována desetkrát za sekundu.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-329">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="4a9b3-330">Pokud se tato stránka ukládá do mezipaměti po dobu jedné minuty, bude se počet dotazů databáze za minutu odpustit z 600 na 1, což snižuje 99,8%.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-330">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="4a9b3-331">Pokud místo toho jste udělali dobu trvání mezipaměti, celkové snížení by bylo 99,997%, ale teď je pravděpodobnost výrazně větší i potenciální stáří zastaralých dat.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-331">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="4a9b3-332">Další možností je proaktivně odebrat položky mezipaměti, když jsou data, která obsahují, aktualizována.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-332">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="4a9b3-333">Jednotlivé položky lze odebrat, pokud je její klíč znám:</span><span class="sxs-lookup"><span data-stu-id="4a9b3-333">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="4a9b3-334">Pokud vaše aplikace zpřístupňuje funkce pro aktualizaci záznamů, které ukládá do mezipaměti, můžete odebrat odpovídající položky mezipaměti v kódu, který provádí aktualizace.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-334">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="4a9b3-335">V některých případech se může jednat o mnoho různých položek závislých na konkrétní sadě dat.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-335">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="4a9b3-336">V takovém případě může být užitečné vytvořit závislosti mezi položkami mezipaměti pomocí CancellationChangeToken.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-336">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="4a9b3-337">S CancellationChangeToken můžete vypršet platnost několika záznamů v mezipaměti tím, že token zrušíte.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-337">With a CancellationChangeToken, you can expire multiple cache entries at once by canceling the token.</span></span>

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

<span data-ttu-id="4a9b3-338">Ukládání do mezipaměti může výrazně zlepšit výkon webových stránek, které opakovaně vyžádají stejné hodnoty z databáze.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-338">Caching can dramatically improve the performance of web pages that repeatedly request the same values from the database.</span></span> <span data-ttu-id="4a9b3-339">Nezapomeňte změřit přístup k datům a výkon stránky před použitím ukládání do mezipaměti a použít ukládání do mezipaměti jenom v případě, že je potřeba zlepšení.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-339">Be sure to measure data access and page performance before applying caching, and only apply caching where you see a need for improvement.</span></span> <span data-ttu-id="4a9b3-340">Ukládání do mezipaměti spotřebovává prostředky paměti webového serveru a zvyšuje složitost aplikace, takže je důležité, abyste s touto technikou nemuseli předčasně optimalizovat.</span><span class="sxs-lookup"><span data-stu-id="4a9b3-340">Caching consumes web server memory resources and increases the complexity of the application, so it’s important you don’t prematurely optimize using this technique.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="4a9b3-341">[Předchozí](develop-asp-net-core-mvc-apps.md)
>[Další](test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="4a9b3-341">[Previous](develop-asp-net-core-mvc-apps.md)
[Next](test-asp-net-core-mvc-apps.md)</span></span>
