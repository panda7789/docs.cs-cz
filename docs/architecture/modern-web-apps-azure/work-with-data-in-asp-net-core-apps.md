---
title: Práce s daty v ASP.NET základních aplikacích
description: Architekt moderní webové aplikace s ASP.NET core a Azure | Práce s daty v aplikacích ASP.NET Core
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: b706332b28aec669a841f510046aa7b185be1373
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80987839"
---
# <a name="working-with-data-in-aspnet-core-apps"></a><span data-ttu-id="61f98-103">Práce s daty v základních aplikacích ASP.NET</span><span class="sxs-lookup"><span data-stu-id="61f98-103">Working with Data in ASP.NET Core Apps</span></span>

> <span data-ttu-id="61f98-104">"Data jsou vzácná věc a vydrží déle než samotné systémy."</span><span class="sxs-lookup"><span data-stu-id="61f98-104">"Data is a precious thing and will last longer than the systems themselves."</span></span>
>
> <span data-ttu-id="61f98-105">Tim Berners-Lee</span><span class="sxs-lookup"><span data-stu-id="61f98-105">Tim Berners-Lee</span></span>

<span data-ttu-id="61f98-106">Přístup k datům je důležitou součástí téměř každé softwarové aplikace.</span><span class="sxs-lookup"><span data-stu-id="61f98-106">Data access is an important part of almost any software application.</span></span> <span data-ttu-id="61f98-107">ASP.NET Core podporuje celou řadu možností přístupu k datům, včetně entity framework core (a entity Framework 6 také) a může pracovat s libovolným rozhraním pro přístup k datům .NET.</span><span class="sxs-lookup"><span data-stu-id="61f98-107">ASP.NET Core supports a variety of data access options, including Entity Framework Core (and Entity Framework 6 as well), and can work with any .NET data access framework.</span></span> <span data-ttu-id="61f98-108">Volba, které rozhraní pro přístup k datům použít, závisí na potřebách aplikace.</span><span class="sxs-lookup"><span data-stu-id="61f98-108">The choice of which data access framework to use depends on the application's needs.</span></span> <span data-ttu-id="61f98-109">Abstrakce těchto možností z projektů ApplicationCore a UI a zapouzdření podrobností implementace v infrastruktuře pomáhá vytvářet volně vázaný, testovatelný software.</span><span class="sxs-lookup"><span data-stu-id="61f98-109">Abstracting these choices from the ApplicationCore and UI projects, and encapsulating implementation details in Infrastructure, helps to produce loosely coupled, testable software.</span></span>

## <a name="entity-framework-core-for-relational-databases"></a><span data-ttu-id="61f98-110">Core rámce entity (pro relační databáze)</span><span class="sxs-lookup"><span data-stu-id="61f98-110">Entity Framework Core (for relational databases)</span></span>

<span data-ttu-id="61f98-111">Pokud píšete novou ASP.NET základní aplikace, která potřebuje pracovat s relačními daty, pak entity framework core (EF Core) je doporučený způsob, jak pro vaši aplikaci přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="61f98-111">If you're writing a new ASP.NET Core application that needs to work with relational data, then Entity Framework Core (EF Core) is the recommended way for your application to access its data.</span></span> <span data-ttu-id="61f98-112">EF Core je objektrelační mapovač (O/RM), který umožňuje vývojářům rozhraní .NET uchovávat objekty do a ze zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="61f98-112">EF Core is an object-relational mapper (O/RM) that enables .NET developers to persist objects to and from a data source.</span></span> <span data-ttu-id="61f98-113">Eliminuje potřebu pro většinu vývojáři kódu přístupu k datům by obvykle nutné psát.</span><span class="sxs-lookup"><span data-stu-id="61f98-113">It eliminates the need for most of the data access code developers would typically need to write.</span></span> <span data-ttu-id="61f98-114">Stejně jako ASP.NET Core, EF Core byl přepsán od základu pro podporu modulárních aplikací pro více platforem.</span><span class="sxs-lookup"><span data-stu-id="61f98-114">Like ASP.NET Core, EF Core has been rewritten from the ground up to support modular cross-platform applications.</span></span> <span data-ttu-id="61f98-115">Přidáte ji do aplikace jako balíček NuGet, nakonfigurujte jej při spuštění a požádejte o něj prostřednictvím vkládání závislostí, kdekoli ji potřebujete.</span><span class="sxs-lookup"><span data-stu-id="61f98-115">You add it to your application as a NuGet package, configure it in Startup, and request it through dependency injection wherever you need it.</span></span>

<span data-ttu-id="61f98-116">Chcete-li použít ef core s databází serveru SQL Server, spusťte následující příkaz dotnet CLI:</span><span class="sxs-lookup"><span data-stu-id="61f98-116">To use EF Core with a SQL Server database, run the following dotnet CLI command:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.SqlServer
```

<span data-ttu-id="61f98-117">Chcete-li přidat podporu pro zdroj dat InMemory, pro testování:</span><span class="sxs-lookup"><span data-stu-id="61f98-117">To add support for an InMemory data source, for testing:</span></span>

```dotnetcli
dotnet add package Microsoft.EntityFrameworkCore.InMemory
```

### <a name="the-dbcontext"></a><span data-ttu-id="61f98-118">Kontextu db</span><span class="sxs-lookup"><span data-stu-id="61f98-118">The DbContext</span></span>

<span data-ttu-id="61f98-119">Chcete-li pracovat s EF Core, <xref:Microsoft.EntityFrameworkCore.DbContext>potřebujete podtřídu .</span><span class="sxs-lookup"><span data-stu-id="61f98-119">To work with EF Core, you need a subclass of <xref:Microsoft.EntityFrameworkCore.DbContext>.</span></span> <span data-ttu-id="61f98-120">Tato třída obsahuje vlastnosti představující kolekce entit, se kterými bude aplikace pracovat.</span><span class="sxs-lookup"><span data-stu-id="61f98-120">This class holds properties representing collections of the entities your application will work with.</span></span> <span data-ttu-id="61f98-121">Ukázka eShopOnWeb obsahuje Kontext katalogu s kolekcemi pro položky, značky a typy:</span><span class="sxs-lookup"><span data-stu-id="61f98-121">The eShopOnWeb sample includes a CatalogContext with collections for items, brands, and types:</span></span>

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

<span data-ttu-id="61f98-122">DbContext musí mít konstruktor, který přijímá DbContextOptions a předat tento argument základní dbContext konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="61f98-122">Your DbContext must have a constructor that accepts DbContextOptions and pass this argument to the base DbContext constructor.</span></span> <span data-ttu-id="61f98-123">Pokud máte pouze jeden DbContext ve vaší aplikaci, můžete předat instanci DbContextOptions, ale pokud\<máte více než jeden, musíte použít obecný DbContextOptions T> typu, předávání typu DbContext jako obecný parametr.</span><span class="sxs-lookup"><span data-stu-id="61f98-123">If you have only one DbContext in your application, you can pass an instance of DbContextOptions, but if you have more than one you must use the generic DbContextOptions\<T> type, passing in your DbContext type as the generic parameter.</span></span>

### <a name="configuring-ef-core"></a><span data-ttu-id="61f98-124">Konfigurace jádra EF</span><span class="sxs-lookup"><span data-stu-id="61f98-124">Configuring EF Core</span></span>

<span data-ttu-id="61f98-125">Ve vaší aplikaci ASP.NET Core obvykle nakonfigurujete EF Core v metodě ConfigureServices.</span><span class="sxs-lookup"><span data-stu-id="61f98-125">In your ASP.NET Core application, you'll typically configure EF Core in your ConfigureServices method.</span></span> <span data-ttu-id="61f98-126">EF Core používá DbContextOptionsBuilder, který podporuje několik užitečných metod rozšíření pro zjednodušení jeho konfigurace.</span><span class="sxs-lookup"><span data-stu-id="61f98-126">EF Core uses a DbContextOptionsBuilder, which supports several helpful extension methods to streamline its configuration.</span></span> <span data-ttu-id="61f98-127">Chcete-li nakonfigurovat CatalogContext pro použití databáze serveru SQL Server s připojovacím řetězcem definovaným v konfiguraci, přidejte do služby ConfigureServices následující kód:</span><span class="sxs-lookup"><span data-stu-id="61f98-127">To configure CatalogContext to use a SQL Server database with a connection string defined in Configuration, you would add the following code to ConfigureServices:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options => options.UseSqlServer (Configuration.GetConnectionString("DefaultConnection")));
```

<span data-ttu-id="61f98-128">Použití databáze v paměti:</span><span class="sxs-lookup"><span data-stu-id="61f98-128">To use the in-memory database:</span></span>

```csharp
services.AddDbContext<CatalogContext>(options =>
    options.UseInMemoryDatabase());
```

<span data-ttu-id="61f98-129">Po instalaci EF Core, vytvořil dbcontext podřízený typ a nakonfiguroval jej v ConfigureServices, jste připraveni k použití EF Core.</span><span class="sxs-lookup"><span data-stu-id="61f98-129">Once you have installed EF Core, created a DbContext child type, and configured it in ConfigureServices, you are ready to use EF Core.</span></span> <span data-ttu-id="61f98-130">Můžete požádat o instanci typu DbContext v libovolné službě, která ji potřebuje, a začít pracovat s trvalými entitami pomocí LINQ, jako by byly jednoduše v kolekci.</span><span class="sxs-lookup"><span data-stu-id="61f98-130">You can request an instance of your DbContext type in any service that needs it, and start working with your persisted entities using LINQ as if they were simply in a collection.</span></span> <span data-ttu-id="61f98-131">EF Core provádí překlad výrazů LINQ do dotazů SQL pro uložení a načtení dat.</span><span class="sxs-lookup"><span data-stu-id="61f98-131">EF Core does the work of translating your LINQ expressions into SQL queries to store and retrieve your data.</span></span>

<span data-ttu-id="61f98-132">Můžete vidět dotazy EF Core je spuštěn a konfigurace protokolování a zajištění jeho úroveň je nastavena alespoň informace, jak je znázorněno na obrázku 8-1.</span><span class="sxs-lookup"><span data-stu-id="61f98-132">You can see the queries EF Core is executing by configuring a logger and ensuring its level is set to at least Information, as shown in Figure 8-1.</span></span>

![Protokolování dotazů EF Core do konzoly](./media/image8-1.png)

<span data-ttu-id="61f98-134">**Obrázek 8-1**.</span><span class="sxs-lookup"><span data-stu-id="61f98-134">**Figure 8-1**.</span></span> <span data-ttu-id="61f98-135">Protokolování dotazů EF Core do konzoly</span><span class="sxs-lookup"><span data-stu-id="61f98-135">Logging EF Core queries to the console</span></span>

### <a name="fetching-and-storing-data"></a><span data-ttu-id="61f98-136">Načítání a ukládání dat</span><span class="sxs-lookup"><span data-stu-id="61f98-136">Fetching and storing Data</span></span>

<span data-ttu-id="61f98-137">Chcete-li načíst data z EF Core, přístup k příslušné vlastnosti a pomocí LINQ filtrovat výsledek.</span><span class="sxs-lookup"><span data-stu-id="61f98-137">To retrieve data from EF Core, you access the appropriate property and use LINQ to filter the result.</span></span> <span data-ttu-id="61f98-138">Můžete také použít LINQ k provedení projekce, transformovat výsledek z jednoho typu do druhého.</span><span class="sxs-lookup"><span data-stu-id="61f98-138">You can also use LINQ to perform projection, transforming the result from one type to another.</span></span> <span data-ttu-id="61f98-139">Následující příklad by načetl CatalogBrands, seřazené podle názvu, filtrované podle jejich Vlastnost IPoa a promítnuté do typu SelectListItem:</span><span class="sxs-lookup"><span data-stu-id="61f98-139">The following example would retrieve CatalogBrands, ordered by name, filtered by their Enabled property, and projected onto a SelectListItem type:</span></span>

```csharp
var brandItems = await _context.CatalogBrands
    .Where(b => b.Enabled)
    .OrderBy(b => b.Name)
    .Select(b => new SelectListItem {
        Value = b.Id, Text = b.Name })
    .ToListAsync();
```

<span data-ttu-id="61f98-140">Ve výše uvedeném příkladu je důležité přidat volání toListAsync, aby bylo možné okamžitě spustit dotaz.</span><span class="sxs-lookup"><span data-stu-id="61f98-140">It's important in the above example to add the call to ToListAsync in order to execute the query immediately.</span></span> <span data-ttu-id="61f98-141">V opačném případě příkaz přiřadí\<IQueryable SelectListItem> brandItems, které nebudou provedeny, dokud nebude uveden výčet.</span><span class="sxs-lookup"><span data-stu-id="61f98-141">Otherwise, the statement will assign an IQueryable\<SelectListItem> to brandItems, which will not be executed until it is enumerated.</span></span> <span data-ttu-id="61f98-142">Existují klady a zápory k vrácení IQueryable výsledky z metod.</span><span class="sxs-lookup"><span data-stu-id="61f98-142">There are pros and cons to returning IQueryable results from methods.</span></span> <span data-ttu-id="61f98-143">Umožňuje dotaz EF Core bude konstrukce dále upravit, ale může také způsobit chyby, které dochází pouze za běhu, pokud operace jsou přidány do dotazu, který EF Core nelze přeložit.</span><span class="sxs-lookup"><span data-stu-id="61f98-143">It allows the query EF Core will construct to be further modified, but can also result in errors that only occur at runtime, if operations are added to the query that EF Core cannot translate.</span></span> <span data-ttu-id="61f98-144">Obecně je bezpečnější předat všechny filtry do metody provádějící přístup k datům a vrátit\<zpět kolekci v paměti (například Seznam T>) jako výsledek.</span><span class="sxs-lookup"><span data-stu-id="61f98-144">It's generally safer to pass any filters into the method performing the data access, and return back an in-memory collection (for example, List\<T>) as the result.</span></span>

<span data-ttu-id="61f98-145">EF Core sleduje změny na entity, které načte z trvalosti.</span><span class="sxs-lookup"><span data-stu-id="61f98-145">EF Core tracks changes on entities it fetches from persistence.</span></span> <span data-ttu-id="61f98-146">Chcete-li uložit změny sledované entity, stačí zavolat SaveChanges metoda na DbContext, ujistěte se, že je to stejné DbContext instance, která byla použita k načtení entity.</span><span class="sxs-lookup"><span data-stu-id="61f98-146">To save changes to a tracked entity, you just call the SaveChanges method on the DbContext, making sure it's the same DbContext instance that was used to fetch the entity.</span></span> <span data-ttu-id="61f98-147">Přidání a odebrání entit se provádí přímo na příslušné DbSet vlastnost, opět s voláním SaveChanges ke spuštění příkazů databáze.</span><span class="sxs-lookup"><span data-stu-id="61f98-147">Adding and removing entities is directly done on the appropriate DbSet property, again with a call to SaveChanges to execute the database commands.</span></span> <span data-ttu-id="61f98-148">Následující příklad ukazuje přidání, aktualizaci a odebrání entit z trvalosti.</span><span class="sxs-lookup"><span data-stu-id="61f98-148">The following example demonstrates adding, updating, and removing entities from persistence.</span></span>

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

<span data-ttu-id="61f98-149">EF Core podporuje synchronní i asynchronní metody pro načítání a ukládání.</span><span class="sxs-lookup"><span data-stu-id="61f98-149">EF Core supports both synchronous and async methods for fetching and saving.</span></span> <span data-ttu-id="61f98-150">Ve webových aplikacích se doporučuje použít vzor async/await s asynchronními metodami, aby vlákna webového serveru nebyla blokována při čekání na dokončení operací přístupu k datům.</span><span class="sxs-lookup"><span data-stu-id="61f98-150">In web applications, it's recommended to use the async/await pattern with the async methods, so that web server threads are not blocked while waiting for data access operations to complete.</span></span>

### <a name="fetching-related-data"></a><span data-ttu-id="61f98-151">Načítání souvisejících dat</span><span class="sxs-lookup"><span data-stu-id="61f98-151">Fetching related data</span></span>

<span data-ttu-id="61f98-152">Když EF Core načte entity, naplní všechny vlastnosti, které jsou uloženy přímo s tuto entitu v databázi.</span><span class="sxs-lookup"><span data-stu-id="61f98-152">When EF Core retrieves entities, it populates all of the properties that are stored directly with that entity in the database.</span></span> <span data-ttu-id="61f98-153">Navigační vlastnosti, jako jsou seznamy souvisejících entit, nejsou naplněny a mohou mít jejich hodnotu nastavenou na hodnotu null.</span><span class="sxs-lookup"><span data-stu-id="61f98-153">Navigation properties, such as lists of related entities, are not populated and may have their value set to null.</span></span> <span data-ttu-id="61f98-154">Tím je zajištěno, že EF Core nenačítá více dat, než je potřeba, což je obzvláště důležité pro webové aplikace, které musí rychle zpracovat požadavky a vrátit odpovědi efektivním způsobem.</span><span class="sxs-lookup"><span data-stu-id="61f98-154">This ensures EF Core is not fetching more data than is needed, which is especially important for web applications, which must quickly process requests and return responses in an efficient manner.</span></span> <span data-ttu-id="61f98-155">Chcete-li zahrnout vztahy s entitou pomocí _eager loading_, zadejte vlastnost pomocí metody Include extension v dotazu, jak je znázorněno:</span><span class="sxs-lookup"><span data-stu-id="61f98-155">To include relationships with an entity using _eager loading_, you specify the property using the Include extension method on the query, as shown:</span></span>

```csharp
// .Include requires using Microsoft.EntityFrameworkCore
var brandsWithItems = await _context.CatalogBrands
    .Include(b => b.Items)
    .ToListAsync();
```

<span data-ttu-id="61f98-156">Můžete zahrnout více relací a můžete také zahrnout podvztahy pomocí ThenInclude.</span><span class="sxs-lookup"><span data-stu-id="61f98-156">You can include multiple relationships, and you can also include subrelationships using ThenInclude.</span></span> <span data-ttu-id="61f98-157">EF Core spustí jeden dotaz k načtení výsledné sady entit.</span><span class="sxs-lookup"><span data-stu-id="61f98-157">EF Core will execute a single query to retrieve the resulting set of entities.</span></span> <span data-ttu-id="61f98-158">Alternativně můžete zahrnout navigační vlastnosti navigačnívlastnosti předáním '.. -oddělený řetězec `.Include()` k metodě rozšíření, například takto:</span><span class="sxs-lookup"><span data-stu-id="61f98-158">Alternately you can include navigation properties of navigation properties by passing a '.'-separated string to the `.Include()` extension method, like so:</span></span>

```csharp
    .Include("Items.Products")
```

<span data-ttu-id="61f98-159">Kromě logiky zapouzdření filtrování může specifikace určit tvar dat, která mají být vrácena, včetně vlastností, které mají být naplněny.</span><span class="sxs-lookup"><span data-stu-id="61f98-159">In addition to encapsulating filtering logic, a specification can specify the shape of the data to be returned, including which properties to populate.</span></span> <span data-ttu-id="61f98-160">Ukázka eShopOnWeb obsahuje několik specifikací, které demonstrují zapouzdření dychtivých informací o načítání v rámci specifikace.</span><span class="sxs-lookup"><span data-stu-id="61f98-160">The eShopOnWeb sample includes several specifications that demonstrate encapsulating eager loading information within the specification.</span></span> <span data-ttu-id="61f98-161">Můžete vidět, jak se specifikace používá jako součást dotazu zde:</span><span class="sxs-lookup"><span data-stu-id="61f98-161">You can see how the specification is used as part of a query here:</span></span>

```csharp
// Includes all expression-based includes
query = specification.Includes.Aggregate(query,
            (current, include) => current.Include(include));

// Include any string-based include statements
query = specification.IncludeStrings.Aggregate(query,
            (current, include) => current.Include(include));
```

<span data-ttu-id="61f98-162">Další možností pro načítání souvisejících dat je použití _explicitního načítání_.</span><span class="sxs-lookup"><span data-stu-id="61f98-162">Another option for loading related data is to use _explicit loading_.</span></span> <span data-ttu-id="61f98-163">Explicitní načítání umožňuje načíst další data do entity, která již byla načtena.</span><span class="sxs-lookup"><span data-stu-id="61f98-163">Explicit loading allows you to load additional data into an entity that has already been retrieved.</span></span> <span data-ttu-id="61f98-164">Vzhledem k tomu, že se jedná o samostatný požadavek do databáze, není doporučeno pro webové aplikace, což by mělo minimalizovat počet databázových zpátečních cest provedených na požadavek.</span><span class="sxs-lookup"><span data-stu-id="61f98-164">Since this involves a separate request to the database, it's not recommended for web applications, which should minimize the number of database round trips made per request.</span></span>

<span data-ttu-id="61f98-165">_Opožděné načtení_ je funkce, která automaticky načte související data, jak je odkazováno aplikací.</span><span class="sxs-lookup"><span data-stu-id="61f98-165">_Lazy loading_ is a feature that automatically loads related data as it is referenced by the application.</span></span> <span data-ttu-id="61f98-166">EF Core přidal podporu pro opožděné načítání ve verzi 2.1.</span><span class="sxs-lookup"><span data-stu-id="61f98-166">EF Core has added support for lazy loading in version 2.1.</span></span> <span data-ttu-id="61f98-167">Opožděné načtení není ve výchozím `Microsoft.EntityFrameworkCore.Proxies`nastavení povoleno a vyžaduje instalaci rozhraní .</span><span class="sxs-lookup"><span data-stu-id="61f98-167">Lazy loading is not enabled by default and requires installing the `Microsoft.EntityFrameworkCore.Proxies`.</span></span> <span data-ttu-id="61f98-168">Stejně jako u explicitní načítání opožděné načítání by měla být obvykle zakázána pro webové aplikace, protože jeho použití bude mít za následek další databázové dotazy v rámci každého webového požadavku.</span><span class="sxs-lookup"><span data-stu-id="61f98-168">As with explicit loading, lazy loading should typically be disabled for web applications, since its use will result in additional database queries being made within each web request.</span></span> <span data-ttu-id="61f98-169">Bohužel režie vzniklé opožděné načítání často bez povšimnutí v době vývoje, kdy latence je malý a často datové sady používané pro testování jsou malé.</span><span class="sxs-lookup"><span data-stu-id="61f98-169">Unfortunately, the overhead incurred by lazy loading often goes unnoticed at development time, when latency is small and often the data sets used for testing are small.</span></span> <span data-ttu-id="61f98-170">V produkčním prostředí s více uživateli, více dat a více latence, další požadavky na databázi může často vést ke snížení výkonu pro webové aplikace, které využívají náročné načítání.</span><span class="sxs-lookup"><span data-stu-id="61f98-170">However, in production, with more users, more data, and more latency, the additional database requests can often result in poor performance for web applications that make heavy use of lazy loading.</span></span>

[<span data-ttu-id="61f98-171">Vyhněte se opožděné načítání entit ve webových aplikacích</span><span class="sxs-lookup"><span data-stu-id="61f98-171">Avoid Lazy Loading Entities in Web Applications</span></span>](https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications)

### <a name="encapsulating-data"></a><span data-ttu-id="61f98-172">Zapouzdření dat</span><span class="sxs-lookup"><span data-stu-id="61f98-172">Encapsulating data</span></span>

<span data-ttu-id="61f98-173">EF Core podporuje několik funkcí, které umožňují modelu správně zapouzdřit jeho stav.</span><span class="sxs-lookup"><span data-stu-id="61f98-173">EF Core supports several features that allow your model to properly encapsulate its state.</span></span> <span data-ttu-id="61f98-174">Běžným problémem v modelech domény je, že zveřejňují navigační vlastnosti kolekce jako veřejně přístupné typy seznamů.</span><span class="sxs-lookup"><span data-stu-id="61f98-174">A common problem in domain models is that they expose collection navigation properties as publicly accessible list types.</span></span> <span data-ttu-id="61f98-175">To umožňuje všechny spolupracovníky manipulovat s obsahem těchto typů kolekce, které mohou obejít důležitá obchodní pravidla související s kolekcí, případně ponechat objekt v neplatném stavu.</span><span class="sxs-lookup"><span data-stu-id="61f98-175">This allows any collaborator to manipulate the contents of these collection types, which may bypass important business rules related to the collection, possibly leaving the object in an invalid state.</span></span> <span data-ttu-id="61f98-176">Řešením je vystavit přístup jen pro čtení k související kolekce a explicitně poskytnout metody definující způsoby, ve kterém klienti mohou manipulovat s nimi, jako v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="61f98-176">The solution to this is to expose read-only access to related collections, and explicitly provide methods defining ways in which clients can manipulate them, as in this example:</span></span>

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

<span data-ttu-id="61f98-177">Tento typ entity nezveřejňuje `List` veřejné `ICollection` nebo vlastnosti, `IReadOnlyCollection` ale místo toho zveřejňuje typ, který obtéká základní typ seznamu.</span><span class="sxs-lookup"><span data-stu-id="61f98-177">This entity type doesn't expose a public `List` or `ICollection` property, but instead exposes an `IReadOnlyCollection` type that wraps the underlying List type.</span></span> <span data-ttu-id="61f98-178">Při použití tohoto vzoru můžete na jádro entity frameworku určit, že se má použít záložní pole takto:</span><span class="sxs-lookup"><span data-stu-id="61f98-178">When using this pattern, you can indicate to Entity Framework Core to use the backing field like so:</span></span>

```csharp
private void ConfigureBasket(EntityTypeBuilder<Basket> builder)
{
    var navigation = builder.Metadata.FindNavigation(nameof(Basket.Items));

    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
}
```

<span data-ttu-id="61f98-179">Dalším způsobem, ve kterém můžete zlepšit model domény je pomocí hodnotových objektů pro typy, které postrádají identitu a jsou rozlišeny pouze jejich vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="61f98-179">Another way in which you can improve your domain model is through the use of value objects for types that lack identity and are only distinguished by their properties.</span></span> <span data-ttu-id="61f98-180">Použití takových typů, jako jsou vlastnosti entit, může pomoci zachovat logiku specifickou pro objekt hodnoty, kam patří, a vyhnout se duplicitní logice mezi více entitami, které používají stejný koncept.</span><span class="sxs-lookup"><span data-stu-id="61f98-180">Using such types as properties of your entities can help keep logic specific to the value object where it belongs, and can avoid duplicate logic between multiple entities that use the same concept.</span></span> <span data-ttu-id="61f98-181">V jádru entity frameworku můžete zachovat hodnotové objekty ve stejné tabulce jako jejich vlastnící entitu konfigurací typu jako vlastněné entity, například takto:</span><span class="sxs-lookup"><span data-stu-id="61f98-181">In Entity Framework Core, you can persist value objects in the same table as their owning entity by configuring the type as an owned entity, like so:</span></span>

```csharp
private void ConfigureOrder(EntityTypeBuilder<Order> builder)
{
    builder.OwnsOne(o => o.ShipToAddress);
}
```

<span data-ttu-id="61f98-182">V tomto příkladu `ShipToAddress` je `Address`vlastnost typu .</span><span class="sxs-lookup"><span data-stu-id="61f98-182">In this example, the `ShipToAddress` property is of type `Address`.</span></span> <span data-ttu-id="61f98-183">`Address`je objekt s několika vlastnostmi, například `Street` a `City`.</span><span class="sxs-lookup"><span data-stu-id="61f98-183">`Address` is a value object with several properties such as `Street` and `City`.</span></span> <span data-ttu-id="61f98-184">EF Core `Order` mapuje objekt na jeho `Address` tabulku s jedním sloupcem na vlastnost, předponou každý název sloupce s názvem vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="61f98-184">EF Core maps the `Order` object to its table with one column per `Address` property, prefixing each column name with the name of the property.</span></span> <span data-ttu-id="61f98-185">V tomto příkladu by tabulka `Order` `ShipToAddress_Street` obsahovala sloupce, jako jsou a `ShipToAddress_City`.</span><span class="sxs-lookup"><span data-stu-id="61f98-185">In this example, the `Order` table would include columns such as `ShipToAddress_Street` and `ShipToAddress_City`.</span></span> <span data-ttu-id="61f98-186">Je také možné v případě potřeby ukládat vlastněné typy v samostatných tabulkách.</span><span class="sxs-lookup"><span data-stu-id="61f98-186">It's also possible to store owned types in separate tables, if desired.</span></span>

<span data-ttu-id="61f98-187">Další informace o [podpoře vlastněných entit v EF Core](/ef/core/modeling/owned-entities).</span><span class="sxs-lookup"><span data-stu-id="61f98-187">Learn more about owned [entity support in EF Core](/ef/core/modeling/owned-entities).</span></span>

### <a name="resilient-connections"></a><span data-ttu-id="61f98-188">Odolná připojení</span><span class="sxs-lookup"><span data-stu-id="61f98-188">Resilient connections</span></span>

<span data-ttu-id="61f98-189">Externí prostředky, jako jsou databáze SQL, mohou být občas nedostupné.</span><span class="sxs-lookup"><span data-stu-id="61f98-189">External resources like SQL databases may occasionally be unavailable.</span></span> <span data-ttu-id="61f98-190">V případech dočasné nedostupnosti aplikace můžete použít logiku opakování, aby se zabránilo vyvolání výjimky.</span><span class="sxs-lookup"><span data-stu-id="61f98-190">In cases of temporary unavailability, applications can use retry logic to avoid raising an exception.</span></span> <span data-ttu-id="61f98-191">Tato technika se běžně označuje jako _odolnost proti chybám připojení_.</span><span class="sxs-lookup"><span data-stu-id="61f98-191">This technique is commonly referred to as _connection resiliency_.</span></span> <span data-ttu-id="61f98-192">Můžete implementovat [vlastní opakování s exponenciální backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technika pokusem o opakování s exponenciálně zvyšuje čekací doby, dokud není dosaženo maximální počet opakování bylo dosaženo.</span><span class="sxs-lookup"><span data-stu-id="61f98-192">You can implement your [own retry with exponential backoff](https://docs.microsoft.com/azure/architecture/patterns/retry) technique by attempting to retry with an exponentially increasing wait time, until a maximum retry count has been reached.</span></span> <span data-ttu-id="61f98-193">Tato technika zahrnuje skutečnost, že cloudové prostředky může být občas k dispozici pro krátké časové období, což má za následek selhání některých požadavků.</span><span class="sxs-lookup"><span data-stu-id="61f98-193">This technique embraces the fact that cloud resources might intermittently be unavailable for short periods of time, resulting in failure of some requests.</span></span>

<span data-ttu-id="61f98-194">Pro Azure SQL DB, Entity Framework Core již poskytuje odolnost proti interní muškát připojení databáze a logiku opakování.</span><span class="sxs-lookup"><span data-stu-id="61f98-194">For Azure SQL DB, Entity Framework Core already provides internal database connection resiliency and retry logic.</span></span> <span data-ttu-id="61f98-195">Ale musíte povolit strategii provádění entity framework pro každé připojení DbContext, pokud chcete mít odolné připojení EF Core.</span><span class="sxs-lookup"><span data-stu-id="61f98-195">But you need to enable the Entity Framework execution strategy for each DbContext connection if you want to have resilient EF Core connections.</span></span>

<span data-ttu-id="61f98-196">Například následující kód na úrovni připojení EF Core umožňuje odolná připojení SQL, která jsou opakována, pokud se připojení nezdaří.</span><span class="sxs-lookup"><span data-stu-id="61f98-196">For instance, the following code at the EF Core connection level enables resilient SQL connections that are retried if the connection fails.</span></span>

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

#### <a name="execution-strategies-and-explicit-transactions-using-begintransaction-and-multiple-dbcontexts"></a><span data-ttu-id="61f98-197">Strategie provádění a explicitní transakce pomocí BeginTransaction a více DbContexts</span><span class="sxs-lookup"><span data-stu-id="61f98-197">Execution strategies and explicit transactions using BeginTransaction and multiple DbContexts</span></span>

<span data-ttu-id="61f98-198">Pokud jsou v připojeních EF Core povoleny opakované pokusy, každá operace, kterou provedete pomocí EF Core, se stane vlastní opakovatelnou operací.</span><span class="sxs-lookup"><span data-stu-id="61f98-198">When retries are enabled in EF Core connections, each operation you perform using EF Core becomes its own retryable operation.</span></span> <span data-ttu-id="61f98-199">Každý dotaz a každé volání SaveChanges bude opakován jako celek, pokud dojde k přechodné selhání.</span><span class="sxs-lookup"><span data-stu-id="61f98-199">Each query and each call to SaveChanges will be retried as a unit if a transient failure occurs.</span></span>

<span data-ttu-id="61f98-200">Pokud však váš kód iniciuje transakci pomocí BeginTransaction, definujete vlastní skupinu operací, které je třeba považovat za jednotku; vše uvnitř transakce musí být vrácena zpět, pokud dojde k selhání.</span><span class="sxs-lookup"><span data-stu-id="61f98-200">However, if your code initiates a transaction using BeginTransaction, you are defining your own group of operations that need to be treated as a unit; everything inside the transaction has to be rolled back if a failure occurs.</span></span> <span data-ttu-id="61f98-201">Zobrazí se výjimka, jako je následující, pokud se pokusíte provést tuto transakci při použití strategie provádění EF (zásady opakování) a zahrnout několik SaveChanges z více DbContexts v něm.</span><span class="sxs-lookup"><span data-stu-id="61f98-201">You will see an exception like the following if you attempt to execute that transaction when using an EF execution strategy (retry policy) and you include several SaveChanges from multiple DbContexts in it.</span></span>

<span data-ttu-id="61f98-202">System.InvalidOperationException: Nakonfigurovaná strategie spuštění SqlServerRetryingExecutionStrategy nepodporuje transakce iniciované uživatelem.</span><span class="sxs-lookup"><span data-stu-id="61f98-202">System.InvalidOperationException: The configured execution strategy 'SqlServerRetryingExecutionStrategy' does not support user initiated transactions.</span></span> <span data-ttu-id="61f98-203">Pomocí strategie provádění vrácené 'DbContext.Database.CreateExecutionStrategy()' provést všechny operace v transakci jako opakovatelné jednotky.</span><span class="sxs-lookup"><span data-stu-id="61f98-203">Use the execution strategy returned by 'DbContext.Database.CreateExecutionStrategy()' to execute all the operations in the transaction as a retryable unit.</span></span>

<span data-ttu-id="61f98-204">Řešením je ručně vyvolat strategii provádění EF s delegátem představující vše, co je třeba provést.</span><span class="sxs-lookup"><span data-stu-id="61f98-204">The solution is to manually invoke the EF execution strategy with a delegate representing everything that needs to be executed.</span></span> <span data-ttu-id="61f98-205">Pokud dojde k přechodnému selhání, strategie provádění znovu vyvolá delegáta.</span><span class="sxs-lookup"><span data-stu-id="61f98-205">If a transient failure occurs, the execution strategy will invoke the delegate again.</span></span> <span data-ttu-id="61f98-206">Následující kód ukazuje, jak implementovat tento přístup:</span><span class="sxs-lookup"><span data-stu-id="61f98-206">The following code shows how to implement this approach:</span></span>

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

<span data-ttu-id="61f98-207">První DbContext je \_catalogContext a druhý DbContext \_je v rámci integrationEventLogService objektu.</span><span class="sxs-lookup"><span data-stu-id="61f98-207">The first DbContext is the \_catalogContext and the second DbContext is within the \_integrationEventLogService object.</span></span> <span data-ttu-id="61f98-208">Nakonec potvrzení akce by být provedena více DbContexts a pomocí strategie provádění EF.</span><span class="sxs-lookup"><span data-stu-id="61f98-208">Finally, the Commit action would be performed multiple DbContexts and using an EF Execution Strategy.</span></span>

> ### <a name="references--entity-framework-core"></a><span data-ttu-id="61f98-209">Odkazy – jádro rámce entity</span><span class="sxs-lookup"><span data-stu-id="61f98-209">References – Entity Framework Core</span></span>
>
> - <span data-ttu-id="61f98-210">**Základní dokumenty EF**
>   <https://docs.microsoft.com/ef/></span><span class="sxs-lookup"><span data-stu-id="61f98-210">**EF Core Docs**
<https://docs.microsoft.com/ef/></span></span>
> - <span data-ttu-id="61f98-211">**EF Core: Související údaje**
>   <https://docs.microsoft.com/ef/core/querying/related-data></span><span class="sxs-lookup"><span data-stu-id="61f98-211">**EF Core: Related Data**
<https://docs.microsoft.com/ef/core/querying/related-data></span></span>
> - <span data-ttu-id="61f98-212">**Vyhněte se opožděným načítáním entit v aplikacích ASPNET**
>   <https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span><span class="sxs-lookup"><span data-stu-id="61f98-212">**Avoid Lazy Loading Entities in ASPNET Applications**
<https://ardalis.com/avoid-lazy-loading-entities-in-asp-net-applications></span></span>

## <a name="ef-core-or-micro-orm"></a><span data-ttu-id="61f98-213">EF Core nebo mikro-ORM?</span><span class="sxs-lookup"><span data-stu-id="61f98-213">EF Core or micro-ORM?</span></span>

<span data-ttu-id="61f98-214">Zatímco EF Core je skvělou volbou pro správu trvalosti a z větší části zapouzdřuje podrobnosti o databázi od vývojářů aplikací, není to jediná volba.</span><span class="sxs-lookup"><span data-stu-id="61f98-214">While EF Core is a great choice for managing persistence, and for the most part encapsulates database details from application developers, it isn't the only choice.</span></span> <span data-ttu-id="61f98-215">Další populární open-source alternativou je [Dapper](https://github.com/StackExchange/Dapper), takzvaný mikro-ORM.</span><span class="sxs-lookup"><span data-stu-id="61f98-215">Another popular open-source alternative is [Dapper](https://github.com/StackExchange/Dapper), a so-called micro-ORM.</span></span> <span data-ttu-id="61f98-216">Mikro-ORM je lehký, méně plnohodnotný nástroj pro mapování objektů na datové struktury.</span><span class="sxs-lookup"><span data-stu-id="61f98-216">A micro-ORM is a lightweight, less full-featured tool for mapping objects to data structures.</span></span> <span data-ttu-id="61f98-217">V případě Dapper, jeho cíle návrhu se zaměřují na výkon, spíše než plně zapouzdření základní dotazy, které používá k načtení a aktualizaci dat.</span><span class="sxs-lookup"><span data-stu-id="61f98-217">In the case of Dapper, its design goals focus on performance, rather than fully encapsulating the underlying queries it uses to retrieve and update data.</span></span> <span data-ttu-id="61f98-218">Vzhledem k tomu, že není abstraktní SQL od vývojáře, Dapper je "blíže ke kovu" a umožňuje vývojářům psát přesné dotazy, které chtějí použít pro danou operaci přístupu k datům.</span><span class="sxs-lookup"><span data-stu-id="61f98-218">Because it doesn't abstract SQL from the developer, Dapper is "closer to the metal" and lets developers write the exact queries they want to use for a given data access operation.</span></span>

<span data-ttu-id="61f98-219">EF Core má dvě významné funkce, které poskytuje, které ji oddělují od Dapper, ale také přidat k jeho výkonu režie.</span><span class="sxs-lookup"><span data-stu-id="61f98-219">EF Core has two significant features it provides which separate it from Dapper but also add to its performance overhead.</span></span> <span data-ttu-id="61f98-220">První je překlad z výrazů LINQ do SQL.</span><span class="sxs-lookup"><span data-stu-id="61f98-220">The first is translation from LINQ expressions into SQL.</span></span> <span data-ttu-id="61f98-221">Tyto překlady jsou uloženy do mezipaměti, ale i tak je režie při jejich provádění poprvé.</span><span class="sxs-lookup"><span data-stu-id="61f98-221">These translations are cached, but even so there is overhead in performing them the first time.</span></span> <span data-ttu-id="61f98-222">Druhým je sledování změn na entity (tak, aby efektivní příkazy aktualizace mohou být generovány).</span><span class="sxs-lookup"><span data-stu-id="61f98-222">The second is change tracking on entities (so that efficient update statements can be generated).</span></span> <span data-ttu-id="61f98-223">Toto chování lze vypnout pro konkrétní dotazy pomocí rozšíření AsNotTracking.</span><span class="sxs-lookup"><span data-stu-id="61f98-223">This behavior can be turned off for specific queries by using the AsNotTracking extension.</span></span> <span data-ttu-id="61f98-224">EF Core také generuje dotazy SQL, které jsou obvykle velmi efektivní a v každém případě dokonale přijatelné z hlediska výkonu, ale pokud potřebujete jemné řízení nad přesný dotaz, který má být proveden, můžete předat vlastní SQL (nebo spustit uloženou proceduru) pomocí EF Core, taky.</span><span class="sxs-lookup"><span data-stu-id="61f98-224">EF Core also generates SQL queries that usually are very efficient and in any case perfectly acceptable from a performance standpoint, but if you need fine control over the precise query to be executed, you can pass in custom SQL (or execute a stored procedure) using EF Core, too.</span></span> <span data-ttu-id="61f98-225">V tomto případě Dapper stále překonává EF Core, ale jen mírně.</span><span class="sxs-lookup"><span data-stu-id="61f98-225">In this case, Dapper still outperforms EF Core, but only slightly.</span></span> <span data-ttu-id="61f98-226">Julie Lerman představuje některé údaje o výkonu ve svém článku MSDN z května 2016 [Dapper, Entity Framework a Hybridní aplikace](https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps).</span><span class="sxs-lookup"><span data-stu-id="61f98-226">Julie Lerman presents some performance data in her May 2016 MSDN article [Dapper, Entity Framework, and Hybrid Apps](https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps).</span></span> <span data-ttu-id="61f98-227">Další srovnávací údaje o výkonnosti pro různé metody přístupu k datům lze nalézt na [webu Dapper](https://github.com/StackExchange/Dapper).</span><span class="sxs-lookup"><span data-stu-id="61f98-227">Additional performance benchmark data for a variety of data access methods can be found on [the Dapper site](https://github.com/StackExchange/Dapper).</span></span>

<span data-ttu-id="61f98-228">Chcete-li zjistit, jak se syntaxe pro Dapper liší od EF Core, zvažte tyto dvě verze stejné metody pro načítání seznamu položek:</span><span class="sxs-lookup"><span data-stu-id="61f98-228">To see how the syntax for Dapper varies from EF Core, consider these two versions of the same method for retrieving a list of items:</span></span>

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

<span data-ttu-id="61f98-229">Pokud potřebujete vytvořit složitější objektové grafy s Dapper, musíte napsat přidružené dotazy sami (na rozdíl od přidání Include jako v EF Core).</span><span class="sxs-lookup"><span data-stu-id="61f98-229">If you need to build more complex object graphs with Dapper, you need to write the associated queries yourself (as opposed to adding an Include as you would in EF Core).</span></span> <span data-ttu-id="61f98-230">To je podporováno prostřednictvím různých syntaxí, včetně funkce s názvem Vícenásobné mapování, která umožňuje mapovat jednotlivé řádky na více mapovaných objektů.</span><span class="sxs-lookup"><span data-stu-id="61f98-230">This is supported through a variety of syntaxes, including a feature called Multi Mapping that lets you map individual rows to multiple mapped objects.</span></span> <span data-ttu-id="61f98-231">Například vzhledem k tomu, třídy Post s vlastností Vlastník typu Uživatel, následující SQL vrátí všechna potřebná data:</span><span class="sxs-lookup"><span data-stu-id="61f98-231">For example, given a class Post with a property Owner of type User, the following SQL would return all of the necessary data:</span></span>

```sql
select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id
```

<span data-ttu-id="61f98-232">Každý vrácený řádek obsahuje data uživatele i příspěvku.</span><span class="sxs-lookup"><span data-stu-id="61f98-232">Each returned row includes both User and Post data.</span></span> <span data-ttu-id="61f98-233">Vzhledem k tomu, že uživatelská data by měla být připojena k datům Příspěvku prostřednictvím vlastnosti Owner, používá se následující funkce:</span><span class="sxs-lookup"><span data-stu-id="61f98-233">Since the User data should be attached to the Post data via its Owner property, the following function is used:</span></span>

```csharp
(post, user) => { post.Owner = user; return post; }
```

<span data-ttu-id="61f98-234">Úplný výpis kódu pro vrácení kolekce příspěvků s jejich owner vlastností naplněnou přidruženými uživatelskými daty by byl:</span><span class="sxs-lookup"><span data-stu-id="61f98-234">The full code listing to return a collection of posts with their Owner property populated with the associated user data would be:</span></span>

```csharp
var sql = @"select * from #Posts p
left join #Users u on u.Id = p.OwnerId
Order by p.Id";
var data = connection.Query<Post, User, Post>(sql,
(post, user) => { post.Owner = user; return post;});
```

<span data-ttu-id="61f98-235">Vzhledem k tomu, že nabízí méně zapouzdření, Dapper vyžaduje, aby vývojáři věděli více o tom, jak jsou jejich data uložena, jak je efektivně dotazovat a psát další kód pro jejich načtení.</span><span class="sxs-lookup"><span data-stu-id="61f98-235">Because it offers less encapsulation, Dapper requires developers know more about how their data is stored, how to query it efficiently, and write more code to fetch it.</span></span> <span data-ttu-id="61f98-236">Při změně modelu, namísto jednoduše vytvoření nové migrace (jiné funkce EF Core) a/nebo aktualizace informací o mapování na jednom místě v DbContext, každý dotaz, který je ovlivněn, musí být aktualizovány.</span><span class="sxs-lookup"><span data-stu-id="61f98-236">When the model changes, instead of simply creating a new migration (another EF Core feature), and/or updating mapping information in one place in a DbContext, every query that is impacted must be updated.</span></span> <span data-ttu-id="61f98-237">Tyto dotazy nemají žádné záruky kompilace, takže může přerušit za běhu v reakci na změny modelu nebo databáze, takže chyby obtížnější zjistit rychle.</span><span class="sxs-lookup"><span data-stu-id="61f98-237">These queries have no compile-time guarantees, so they may break at run time in response to changes to the model or database, making errors more difficult to detect quickly.</span></span> <span data-ttu-id="61f98-238">Výměnou za tyto kompromisy, Dapper nabízí extrémně rychlý výkon.</span><span class="sxs-lookup"><span data-stu-id="61f98-238">In exchange for these tradeoffs, Dapper offers extremely fast performance.</span></span>

<span data-ttu-id="61f98-239">Pro většinu aplikací a většinu částí téměř všech aplikací nabízí EF Core přijatelný výkon.</span><span class="sxs-lookup"><span data-stu-id="61f98-239">For most applications, and most parts of almost all applications, EF Core offers acceptable performance.</span></span> <span data-ttu-id="61f98-240">Výhody produktivity vývojářů tedy pravděpodobně převáží nad režií výkonu.</span><span class="sxs-lookup"><span data-stu-id="61f98-240">Thus, its developer productivity benefits are likely to outweigh its performance overhead.</span></span> <span data-ttu-id="61f98-241">U dotazů, které mohou těžit z ukládání do mezipaměti, skutečný dotaz může být proveden pouze malé procento času, takže relativně malé rozdíly výkonu dotazu diskutabilní.</span><span class="sxs-lookup"><span data-stu-id="61f98-241">For queries that can benefit from caching, the actual query may only be executed a tiny percentage of the time, making relatively small query performance differences moot.</span></span>

## <a name="sql-or-nosql"></a><span data-ttu-id="61f98-242">SQL nebo NoSQL</span><span class="sxs-lookup"><span data-stu-id="61f98-242">SQL or NoSQL</span></span>

<span data-ttu-id="61f98-243">Relační databáze jako SQL Server tradičně dominují trhu pro trvalé ukládání dat, ale nejsou jediným dostupným řešením.</span><span class="sxs-lookup"><span data-stu-id="61f98-243">Traditionally, relational databases like SQL Server have dominated the marketplace for persistent data storage, but they are not the only solution available.</span></span> <span data-ttu-id="61f98-244">NoSQL databáze jako [MongoDB](https://www.mongodb.com/what-is-mongodb) nabízejí jiný přístup k ukládání objektů.</span><span class="sxs-lookup"><span data-stu-id="61f98-244">NoSQL databases like [MongoDB](https://www.mongodb.com/what-is-mongodb) offer a different approach to storing objects.</span></span> <span data-ttu-id="61f98-245">Spíše než mapování objektů na tabulky a řádky, další možností je serializovat celý objekt grafu a uložit výsledek.</span><span class="sxs-lookup"><span data-stu-id="61f98-245">Rather than mapping objects to tables and rows, another option is to serialize the entire object graph, and store the result.</span></span> <span data-ttu-id="61f98-246">Výhody tohoto přístupu, alespoň zpočátku, jsou jednoduchost a výkon.</span><span class="sxs-lookup"><span data-stu-id="61f98-246">The benefits of this approach, at least initially, are simplicity and performance.</span></span> <span data-ttu-id="61f98-247">Je jednodušší uložit jeden serializovaný objekt s klíčem než rozložit objekt do mnoha tabulek s relacemi a aktualizace a řádky, které se mohly změnit od posledního načtení objektu z databáze.</span><span class="sxs-lookup"><span data-stu-id="61f98-247">It's simpler to store a single serialized object with a key than to decompose the object into many tables with relationships and update and rows that may have changed since the object was last retrieved from the database.</span></span> <span data-ttu-id="61f98-248">Podobně načítání a deserializace jednoho objektu z úložiště založeného na klíči je obvykle mnohem rychlejší a jednodušší než komplexní spojení nebo více databázových dotazů potřebných k úplnému vytvoření stejného objektu z relační databáze.</span><span class="sxs-lookup"><span data-stu-id="61f98-248">Likewise, fetching and deserializing a single object from a key-based store is typically much faster and easier than complex joins or multiple database queries required to fully compose the same object from a relational database.</span></span> <span data-ttu-id="61f98-249">Nedostatek zámků nebo transakcí nebo pevné schéma také umožňuje NoSQL databáze přístupné škálování napříč mnoha počítači, podporující velmi velké datové sady.</span><span class="sxs-lookup"><span data-stu-id="61f98-249">The lack of locks or transactions or a fixed schema also makes NoSQL databases amenable to scaling across many machines, supporting very large datasets.</span></span>

<span data-ttu-id="61f98-250">Na druhou stranu, NoSQL databáze (jak se obvykle nazývají) mají své nevýhody.</span><span class="sxs-lookup"><span data-stu-id="61f98-250">On the other hand, NoSQL databases (as they are typically called) have their drawbacks.</span></span> <span data-ttu-id="61f98-251">Relační databáze používají normalizaci k vynucení konzistence a zabránění duplikaci dat.</span><span class="sxs-lookup"><span data-stu-id="61f98-251">Relational databases use normalization to enforce consistency and avoid duplication of data.</span></span> <span data-ttu-id="61f98-252">Tím se zmenší celková velikost databáze a zajistí, že aktualizace sdílených dat jsou k dispozici okamžitě v celé databázi.</span><span class="sxs-lookup"><span data-stu-id="61f98-252">This reduces the total size of the database and ensures that updates to shared data are available immediately throughout the database.</span></span> <span data-ttu-id="61f98-253">V relační databázi může tabulka Adresa odkazovat na tabulku Země podle ID, takže pokud by byl změněn název země nebo oblasti, záznamy adres by měly prospěch z aktualizace, aniž by musely být aktualizovány.</span><span class="sxs-lookup"><span data-stu-id="61f98-253">In a relational database, an Address table might reference a Country table by ID, such that if the name of a country/region were changed, the address records would benefit from the update without themselves having to be updated.</span></span> <span data-ttu-id="61f98-254">V databázi NoSQL však může být adresa a přidružená země serializována jako součást mnoha uložených objektů.</span><span class="sxs-lookup"><span data-stu-id="61f98-254">However, in a NoSQL database, Address and its associated Country might be serialized as part of many stored objects.</span></span> <span data-ttu-id="61f98-255">Aktualizace názvu země nebo oblasti by vyžadovala, aby byly aktualizovány všechny tyto objekty, nikoli jeden řádek.</span><span class="sxs-lookup"><span data-stu-id="61f98-255">An update to a country/region name would require all such objects to be updated, rather than a single row.</span></span> <span data-ttu-id="61f98-256">Relační databáze mohou také zajistit relační integritu vynucením pravidel, jako jsou cizí klíče.</span><span class="sxs-lookup"><span data-stu-id="61f98-256">Relational databases can also ensure relational integrity by enforcing rules like foreign keys.</span></span> <span data-ttu-id="61f98-257">NoSQL databáze obvykle nenabízejí taková omezení na jejich data.</span><span class="sxs-lookup"><span data-stu-id="61f98-257">NoSQL databases typically do not offer such constraints on their data.</span></span>

<span data-ttu-id="61f98-258">Další složitost NoSQL databáze musí řešit, je správa verzí.</span><span class="sxs-lookup"><span data-stu-id="61f98-258">Another complexity NoSQL databases must deal with is versioning.</span></span> <span data-ttu-id="61f98-259">Při změně vlastností objektu nemusí být možné rekonstruovat z minulých verzí, které byly uloženy.</span><span class="sxs-lookup"><span data-stu-id="61f98-259">When an object's properties change, it may not be able to be deserialized from past versions that were stored.</span></span> <span data-ttu-id="61f98-260">Proto všechny existující objekty, které mají serializované (předchozí) verze objektu musí být aktualizovány tak, aby odpovídaly jeho nové schéma.</span><span class="sxs-lookup"><span data-stu-id="61f98-260">Thus, all existing objects that have a serialized (previous) version of the object must be updated to conform to its new schema.</span></span> <span data-ttu-id="61f98-261">To se koncepčně neliší od relační databáze, kde změny schématu někdy vyžadují aktualizace skriptů nebo aktualizace mapování.</span><span class="sxs-lookup"><span data-stu-id="61f98-261">This is not conceptually different from a relational database, where schema changes sometimes require update scripts or mapping updates.</span></span> <span data-ttu-id="61f98-262">Počet položek, které musí být změněny, je však často mnohem větší v přístupu NoSQL, protože je více duplikace dat.</span><span class="sxs-lookup"><span data-stu-id="61f98-262">However, the number of entries that must be modified is often much greater in the NoSQL approach, because there is more duplication of data.</span></span>

<span data-ttu-id="61f98-263">Je možné v nosql databázích ukládat více verzí objektů, něco pevné schéma relační databáze obvykle nepodporují.</span><span class="sxs-lookup"><span data-stu-id="61f98-263">It's possible in NoSQL databases to store multiple versions of objects, something fixed schema relational databases typically do not support.</span></span> <span data-ttu-id="61f98-264">V tomto případě však kód aplikace bude muset účet pro existenci předchozíverze objektů, přidání další složitosti.</span><span class="sxs-lookup"><span data-stu-id="61f98-264">However, in this case your application code will need to account for the existence of previous versions of objects, adding additional complexity.</span></span>

<span data-ttu-id="61f98-265">NoSQL databáze obvykle nevynucují [ACID](https://en.wikipedia.org/wiki/ACID), což znamená, že mají výhody výkonu i škálovatelnosti oproti relačním databázím.</span><span class="sxs-lookup"><span data-stu-id="61f98-265">NoSQL databases typically do not enforce [ACID](https://en.wikipedia.org/wiki/ACID), which means they have both performance and scalability benefits over relational databases.</span></span> <span data-ttu-id="61f98-266">Jsou vhodné pro extrémně velké datové sady a objekty, které nejsou vhodné pro ukládání v normalizovaných strukturách tabulek.</span><span class="sxs-lookup"><span data-stu-id="61f98-266">They're well suited to extremely large datasets and objects that are not well suited to storage in normalized table structures.</span></span> <span data-ttu-id="61f98-267">Neexistuje žádný důvod, proč jedna aplikace nemůže využít relační a NoSQL databáze, pomocí každého, kde je nejvhodnější.</span><span class="sxs-lookup"><span data-stu-id="61f98-267">There is no reason why a single application cannot take advantage of both relational and NoSQL databases, using each where it is best suited.</span></span>

## <a name="azure-cosmos-db"></a><span data-ttu-id="61f98-268">Azure Cosmos DB</span><span class="sxs-lookup"><span data-stu-id="61f98-268">Azure Cosmos DB</span></span>

<span data-ttu-id="61f98-269">Azure Cosmos DB je plně spravovaná databázová služba NoSQL, která nabízí cloudové úložiště dat bez schématu.</span><span class="sxs-lookup"><span data-stu-id="61f98-269">Azure Cosmos DB is a fully managed NoSQL database service that offers cloud-based schema-free data storage.</span></span> <span data-ttu-id="61f98-270">Azure Cosmos DB je vybudován pro rychlý a předvídatelný výkon, vysokou dostupnost, elastické škálování a globální distribuci.</span><span class="sxs-lookup"><span data-stu-id="61f98-270">Azure Cosmos DB is built for fast and predictable performance, high availability, elastic scaling, and global distribution.</span></span> <span data-ttu-id="61f98-271">Přesto, že je databáze NoSQL, mohou vývojáři používat bohaté a známé funkce DOTAZŮ SQL na datech JSON.</span><span class="sxs-lookup"><span data-stu-id="61f98-271">Despite being a NoSQL database, developers can use rich and familiar SQL query capabilities on JSON data.</span></span> <span data-ttu-id="61f98-272">Všechny prostředky v Azure Cosmos DB jsou uloženy jako dokumenty JSON.</span><span class="sxs-lookup"><span data-stu-id="61f98-272">All resources in Azure Cosmos DB are stored as JSON documents.</span></span> <span data-ttu-id="61f98-273">Prostředky jsou _spravovány_jako položky , což jsou dokumenty obsahující metadata a _informační kanály_, což jsou kolekce položek.</span><span class="sxs-lookup"><span data-stu-id="61f98-273">Resources are managed as _items_, which are documents containing metadata, and _feeds_, which are collections of items.</span></span> <span data-ttu-id="61f98-274">Obrázek 8-2 znázorňuje vztah mezi různými prostředky Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="61f98-274">Figure 8-2 shows the relationship between different Azure Cosmos DB resources.</span></span>

![Hierarchický vztah mezi prostředky v Azure Cosmos DB, databázi NoSQL JSON](./media/image8-2.png)

<span data-ttu-id="61f98-276">**Obrázek 8-2.**</span><span class="sxs-lookup"><span data-stu-id="61f98-276">**Figure 8-2.**</span></span> <span data-ttu-id="61f98-277">Organizace prostředků Azure Cosmos DB.</span><span class="sxs-lookup"><span data-stu-id="61f98-277">Azure Cosmos DB resource organization.</span></span>

<span data-ttu-id="61f98-278">Dotazovací jazyk Azure Cosmos DB je jednoduché, ale výkonné rozhraní pro dotazování dokumentů JSON.</span><span class="sxs-lookup"><span data-stu-id="61f98-278">The Azure Cosmos DB query language is a simple yet powerful interface for querying JSON documents.</span></span> <span data-ttu-id="61f98-279">Tento jazyk podporuje podmnožinu gramatiky ANSI SQL a přidává těsnou integraci s javascriptovými objekty, poli, vytvářením objektů a voláním funkcí.</span><span class="sxs-lookup"><span data-stu-id="61f98-279">The language supports a subset of ANSI SQL grammar and adds deep integration of JavaScript object, arrays, object construction, and function invocation.</span></span>

<span data-ttu-id="61f98-280">**Reference – Azure Cosmos DB**</span><span class="sxs-lookup"><span data-stu-id="61f98-280">**References – Azure Cosmos DB**</span></span>

- <span data-ttu-id="61f98-281">Úvod do Azure Cosmos DB<https://docs.microsoft.com/azure/cosmos-db/introduction></span><span class="sxs-lookup"><span data-stu-id="61f98-281">Azure Cosmos DB Introduction <https://docs.microsoft.com/azure/cosmos-db/introduction></span></span>

## <a name="other-persistence-options"></a><span data-ttu-id="61f98-282">Další možnosti trvalosti</span><span class="sxs-lookup"><span data-stu-id="61f98-282">Other persistence options</span></span>

<span data-ttu-id="61f98-283">Kromě možností relačního úložiště a úložiště NoSQL můžou aplikace ASP.NET Core používat Azure Storage k ukládání různých formátů dat a souborů cloudovým a škálovatelným způsobem.</span><span class="sxs-lookup"><span data-stu-id="61f98-283">In addition to relational and NoSQL storage options, ASP.NET Core applications can use Azure Storage to store a variety of data formats and files in a cloud-based, scalable fashion.</span></span> <span data-ttu-id="61f98-284">Azure Storage je masivně škálovatelné, takže můžete začít ukládat malá množství dat a škálovat až na ukládání stovek nebo terabajtů, pokud to vaše aplikace vyžaduje.</span><span class="sxs-lookup"><span data-stu-id="61f98-284">Azure Storage is massively scalable, so you can start out storing small amounts of data and scale up to storing hundreds or terabytes if your application requires it.</span></span> <span data-ttu-id="61f98-285">Azure Storage podporuje čtyři druhy dat:</span><span class="sxs-lookup"><span data-stu-id="61f98-285">Azure Storage supports four kinds of data:</span></span>

- <span data-ttu-id="61f98-286">Úložiště objektů blob pro nestrukturovaný text nebo binární úložiště, označované také jako úložiště objektů.</span><span class="sxs-lookup"><span data-stu-id="61f98-286">Blob Storage for unstructured text or binary storage, also referred to as object storage.</span></span>

- <span data-ttu-id="61f98-287">Úložiště tabulek pro strukturované datové sady, přístupné pomocí klíčů řádků.</span><span class="sxs-lookup"><span data-stu-id="61f98-287">Table Storage for structured datasets, accessible via row keys.</span></span>

- <span data-ttu-id="61f98-288">Úložiště fronty pro spolehlivé zasílání zpráv založené na frontách.</span><span class="sxs-lookup"><span data-stu-id="61f98-288">Queue Storage for reliable queue-based messaging.</span></span>

- <span data-ttu-id="61f98-289">Úložiště souborů pro sdílený přístup k souborům mezi virtuálními počítači Azure a místními aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="61f98-289">File Storage for shared file access between Azure virtual machines and on-premises applications.</span></span>

<span data-ttu-id="61f98-290">**Reference – Azure Storage**</span><span class="sxs-lookup"><span data-stu-id="61f98-290">**References – Azure Storage**</span></span>

- <span data-ttu-id="61f98-291">Úvod k úložišti Azure<https://docs.microsoft.com/azure/storage/storage-introduction></span><span class="sxs-lookup"><span data-stu-id="61f98-291">Azure Storage Introduction <https://docs.microsoft.com/azure/storage/storage-introduction></span></span>

## <a name="caching"></a><span data-ttu-id="61f98-292">Ukládání do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="61f98-292">Caching</span></span>

<span data-ttu-id="61f98-293">Ve webových aplikacích by měl být každý webový požadavek dokončen v co nejkratším možném čase.</span><span class="sxs-lookup"><span data-stu-id="61f98-293">In web applications, each web request should be completed in the shortest time possible.</span></span> <span data-ttu-id="61f98-294">Jedním ze způsobů, jak toho dosáhnout, je omezit počet externích volání, která musí server provést k dokončení požadavku.</span><span class="sxs-lookup"><span data-stu-id="61f98-294">One way to achieve this is to limit the number of external calls the server must make to complete the request.</span></span> <span data-ttu-id="61f98-295">Ukládání do mezipaměti zahrnuje ukládání kopie dat na server (nebo jiné úložiště dat, které je snadněji dotazován než zdroj dat).</span><span class="sxs-lookup"><span data-stu-id="61f98-295">Caching involves storing a copy of data on the server (or another data store that is more easily queried than the source of the data).</span></span> <span data-ttu-id="61f98-296">Webové aplikace, a zejména non-SPA tradiční webové aplikace, je třeba vytvořit celé uživatelské rozhraní s každým požadavkem.</span><span class="sxs-lookup"><span data-stu-id="61f98-296">Web applications, and especially non-SPA traditional web applications, need to build the entire user interface with every request.</span></span> <span data-ttu-id="61f98-297">To často zahrnuje provádění mnoho stejných databázových dotazů opakovaně z jednoho požadavku uživatele na další.</span><span class="sxs-lookup"><span data-stu-id="61f98-297">This frequently involves making many of the same database queries repeatedly from one user request to the next.</span></span> <span data-ttu-id="61f98-298">Ve většině případů se tato data mění zřídka, takže je malý důvod neustále požadovat z databáze.</span><span class="sxs-lookup"><span data-stu-id="61f98-298">In most cases, this data changes rarely, so there is little reason to constantly request it from the database.</span></span> <span data-ttu-id="61f98-299">ASP.NET Core podporuje ukládání do mezipaměti odpovědí, ukládání do mezipaměti celých stránek a ukládání dat do mezipaměti, které podporuje podrobnější chování ukládání do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="61f98-299">ASP.NET Core supports response caching, for caching entire pages, and data caching, which supports more granular caching behavior.</span></span>

<span data-ttu-id="61f98-300">Při implementaci ukládání do mezipaměti je důležité mít na paměti oddělení obav.</span><span class="sxs-lookup"><span data-stu-id="61f98-300">When implementing caching, it's important to keep in mind separation of concerns.</span></span> <span data-ttu-id="61f98-301">Vyhněte se implementaci logiky ukládání do mezipaměti v logice přístupu k datům nebo v uživatelském rozhraní.</span><span class="sxs-lookup"><span data-stu-id="61f98-301">Avoid implementing caching logic in your data access logic, or in your user interface.</span></span> <span data-ttu-id="61f98-302">Místo toho zapouzdřte ukládání do mezipaměti ve vlastních třídách a použijte konfiguraci ke správě jeho chování.</span><span class="sxs-lookup"><span data-stu-id="61f98-302">Instead, encapsulate caching in its own classes, and use configuration to manage its behavior.</span></span> <span data-ttu-id="61f98-303">To se řídí otevřenými/uzavřenými a jednotnými zásadami odpovědnosti a usnadňuje vám správu způsobu používání ukládání do mezipaměti v aplikaci podle jeho růstu.</span><span class="sxs-lookup"><span data-stu-id="61f98-303">This follows the Open/Closed and Single Responsibility principles, and will make it easier for you to manage how you use caching in your application as it grows.</span></span>

### <a name="aspnet-core-response-caching"></a><span data-ttu-id="61f98-304">ASP.NET ukládání do mezipaměti odpovědi jádra</span><span class="sxs-lookup"><span data-stu-id="61f98-304">ASP.NET Core response caching</span></span>

<span data-ttu-id="61f98-305">ASP.NET Core podporuje dvě úrovně ukládání do mezipaměti odezvy.</span><span class="sxs-lookup"><span data-stu-id="61f98-305">ASP.NET Core supports two levels of response caching.</span></span> <span data-ttu-id="61f98-306">První úroveň neukládá na server nic do mezipaměti, ale přidává hlavičky HTTP, které instruují klienty a proxy servery k ukládání odpovědí do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="61f98-306">The first level does not cache anything on the server, but adds HTTP headers that instruct clients and proxy servers to cache responses.</span></span> <span data-ttu-id="61f98-307">To je implementováno přidáním atributu ResponseCache k jednotlivým řadičům nebo akcím:</span><span class="sxs-lookup"><span data-stu-id="61f98-307">This is implemented by adding the ResponseCache attribute to individual controllers or actions:</span></span>

```csharp
[ResponseCache(Duration = 60)]
public IActionResult Contact()
{
    ViewData["Message"] = "Your contact page.";
    return View();
}
```

<span data-ttu-id="61f98-308">V předchozím příkladu bude mít za následek následující záhlaví, které jsou přidány do odpovědi, pokyn klientům do mezipaměti výsledek po dobu až 60 sekund.</span><span class="sxs-lookup"><span data-stu-id="61f98-308">The previous example will result in the following header being added to the response, instructing clients to cache the result for up to 60 seconds.</span></span>

<span data-ttu-id="61f98-309">Cache-Control: veřejná,max-age=60</span><span class="sxs-lookup"><span data-stu-id="61f98-309">Cache-Control: public,max-age=60</span></span>

<span data-ttu-id="61f98-310">Chcete-li do aplikace přidat ukládání do mezipaměti na straně serveru v paměti, musíte odkazovat na balíček NuGet služby Microsoft.AspNetCore.ResponseCaching a potom přidat middleware pro ukládání do mezipaměti odpovědi.</span><span class="sxs-lookup"><span data-stu-id="61f98-310">In order to add server-side in-memory caching to the application, you must reference the Microsoft.AspNetCore.ResponseCaching NuGet package, and then add the Response Caching middleware.</span></span> <span data-ttu-id="61f98-311">Tento middleware je konfigurován v configureservices a konfigurovat při spuštění:</span><span class="sxs-lookup"><span data-stu-id="61f98-311">This middleware is configured in both ConfigureServices and Configure in Startup:</span></span>

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

<span data-ttu-id="61f98-312">Middleware pro ukládání do mezipaměti odpovědi bude automaticky ukládány do mezipaměti na základě sady podmínek, které můžete přizpůsobit.</span><span class="sxs-lookup"><span data-stu-id="61f98-312">The Response Caching Middleware will automatically cache responses based on a set of conditions, which you can customize.</span></span> <span data-ttu-id="61f98-313">Ve výchozím nastavení pouze 200 (OK) odpovědi požadované prostřednictvím GET nebo HEAD metody jsou uloženy do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="61f98-313">By default, only 200 (OK) responses requested via GET or HEAD methods are cached.</span></span> <span data-ttu-id="61f98-314">Kromě toho musí mít požadavky odpověď s ovládacím prvkem cache: veřejné záhlaví a nesmí obsahovat záhlaví pro autorizaci nebo set-cookie.</span><span class="sxs-lookup"><span data-stu-id="61f98-314">In addition, requests must have a response with a Cache-Control: public header, and cannot include headers for Authorization or Set-Cookie.</span></span> <span data-ttu-id="61f98-315">Podívejte se na [úplný seznam podmínek ukládání do mezipaměti používaných middleware pro ukládání do mezipaměti odpovědi](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span><span class="sxs-lookup"><span data-stu-id="61f98-315">See a [complete list of the caching conditions used by the response caching middleware](/aspnet/core/performance/caching/middleware#conditions-for-caching).</span></span>

### <a name="data-caching"></a><span data-ttu-id="61f98-316">Ukládání dat do mezipaměti</span><span class="sxs-lookup"><span data-stu-id="61f98-316">Data caching</span></span>

<span data-ttu-id="61f98-317">Spíše než (nebo kromě) ukládání úplných webových odpovědí do mezipaměti můžete ukládat výsledky jednotlivých datových dotazů do mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="61f98-317">Rather than (or in addition to) caching full web responses, you can cache the results of individual data queries.</span></span> <span data-ttu-id="61f98-318">K tomu můžete použít ukládání do mezipaměti paměti na webovém serveru nebo [použít distribuovanou mezipaměť](/aspnet/core/performance/caching/distributed).</span><span class="sxs-lookup"><span data-stu-id="61f98-318">For this, you can use in memory caching on the web server, or use [a distributed cache](/aspnet/core/performance/caching/distributed).</span></span> <span data-ttu-id="61f98-319">Tato část ukáže, jak implementovat do mezipaměti paměti.</span><span class="sxs-lookup"><span data-stu-id="61f98-319">This section will demonstrate how to implement in memory caching.</span></span>

<span data-ttu-id="61f98-320">Podporu ukládání do mezipaměti paměti (nebo distribuovaného) ukládání do mezipaměti v programu ConfigureServices přidáte:</span><span class="sxs-lookup"><span data-stu-id="61f98-320">You add support for memory (or distributed) caching in ConfigureServices:</span></span>

```csharp
public void ConfigureServices(IServiceCollection services)
{
    services.AddMemoryCache();
    services.AddMvc();
}
```

<span data-ttu-id="61f98-321">Nezapomeňte také přidat balíček Microsoft.Extensions.Caching.Memory NuGet.</span><span class="sxs-lookup"><span data-stu-id="61f98-321">Be sure to add the Microsoft.Extensions.Caching.Memory NuGet package as well.</span></span>

<span data-ttu-id="61f98-322">Po přidání služby požádáte IMemoryCache prostřednictvím vkládání závislostí všude tam, kde potřebujete přístup k mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="61f98-322">Once you've added the service, you request IMemoryCache via dependency injection wherever you need to access the cache.</span></span> <span data-ttu-id="61f98-323">V tomto příkladu CachedCatalogService používá proxy (nebo decorator) návrhový vzor tím, že poskytuje alternativní implementaci ICatalogService, která řídí přístup (nebo přidá chování) základní implementace CatalogService.</span><span class="sxs-lookup"><span data-stu-id="61f98-323">In this example, the CachedCatalogService is using the Proxy (or Decorator) design pattern, by providing an alternative implementation of ICatalogService that controls access to (or adds behavior to) the underlying CatalogService implementation.</span></span>

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

<span data-ttu-id="61f98-324">Chcete-li nakonfigurovat aplikaci tak, aby používala verzi služby uloženou v mezipaměti, ale přesto povolit službě získat instanci služby CatalogService, kterou potřebuje ve svém konstruktoru, byste do služby ConfigureServices přidali následující:</span><span class="sxs-lookup"><span data-stu-id="61f98-324">To configure the application to use the cached version of the service, but still allow the service to get the instance of CatalogService it needs in its constructor, you would add the following in ConfigureServices:</span></span>

```csharp
services.AddMemoryCache();
services.AddScoped<ICatalogService, CachedCatalogService>();
services.AddScoped<CatalogService>();
```

<span data-ttu-id="61f98-325">S tímto na místě volání databáze načíst data katalogu bude provedena pouze jednou za minutu, nikoli na každém požadavku.</span><span class="sxs-lookup"><span data-stu-id="61f98-325">With this in place, the database calls to fetch the catalog data will only be made once per minute, rather than on every request.</span></span> <span data-ttu-id="61f98-326">V závislosti na provozu na webu to může mít významný vliv na počet dotazů provedených v databázi a průměrnou dobu načítání stránky pro domovskou stránku, která aktuálně závisí na všech třech dotazech vystavených touto službou.</span><span class="sxs-lookup"><span data-stu-id="61f98-326">Depending on the traffic to the site, this can have a significant impact on the number of queries made to the database, and the average page load time for the home page that currently depends on all three of the queries exposed by this service.</span></span>

<span data-ttu-id="61f98-327">Problém, který vzniká při implementaci ukládání do mezipaměti, jsou _zastaralá data_ – to znamená data, která se změnila u zdroje, ale v mezipaměti zůstává zastaralá verze.</span><span class="sxs-lookup"><span data-stu-id="61f98-327">An issue that arises when caching is implemented is _stale data_ – that is, data that has changed at the source but an out-of-date version remains in the cache.</span></span> <span data-ttu-id="61f98-328">Jednoduchý způsob, jak zmírnit tento problém je použití malé mezipaměti trvání, protože pro zaneprázdněné aplikace je omezená další výhoda rozšíření délky dat je uložena v mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="61f98-328">A simple way to mitigate this issue is to use small cache durations, since for a busy application there is limited additional benefit to extending the length data is cached.</span></span> <span data-ttu-id="61f98-329">Zvažte například stránku, která vytvoří dotaz na jednu databázi a je požadována 10krát za sekundu.</span><span class="sxs-lookup"><span data-stu-id="61f98-329">For example, consider a page that makes a single database query, and is requested 10 times per second.</span></span> <span data-ttu-id="61f98-330">Pokud je tato stránka uložena do mezipaměti po dobu jedné minuty, bude mít za následek počet dotazů databáze provedených za minutu, aby klesly z 600 na 1, což je snížení o 99,8 %.</span><span class="sxs-lookup"><span data-stu-id="61f98-330">If this page is cached for one minute, it will result in the number of database queries made per minute to drop from 600 to 1, a reduction of 99.8%.</span></span> <span data-ttu-id="61f98-331">Pokud místo toho trvání mezipaměti byly provedeny jednu hodinu, celkové snížení by bylo 99,997%, ale nyní pravděpodobnost a potenciální stáří zastaralých dat jsou oba dramaticky zvýšily.</span><span class="sxs-lookup"><span data-stu-id="61f98-331">If instead the cache duration were made one hour, the overall reduction would be 99.997%, but now the likelihood and potential age of stale data are both increased dramatically.</span></span>

<span data-ttu-id="61f98-332">Dalším přístupem je proaktivní odebrání položek mezipaměti při aktualizaci dat, která obsahují.</span><span class="sxs-lookup"><span data-stu-id="61f98-332">Another approach is to proactively remove cache entries when the data they contain is updated.</span></span> <span data-ttu-id="61f98-333">Každá jednotlivá položka může být odebrána, pokud je znám její klíč:</span><span class="sxs-lookup"><span data-stu-id="61f98-333">Any individual entry can be removed if its key is known:</span></span>

```csharp
_cache.Remove(cacheKey);
```

<span data-ttu-id="61f98-334">Pokud aplikace zveřejňuje funkce pro aktualizaci položek, které ukládá do mezipaměti, můžete odebrat odpovídající položky mezipaměti v kódu, který provádí aktualizace.</span><span class="sxs-lookup"><span data-stu-id="61f98-334">If your application exposes functionality for updating entries that it caches, you can remove the corresponding cache entries in your code that performs the updates.</span></span> <span data-ttu-id="61f98-335">Někdy může existovat mnoho různých položek, které závisí na konkrétní sadu dat.</span><span class="sxs-lookup"><span data-stu-id="61f98-335">Sometimes there may be many different entries that depend on a particular set of data.</span></span> <span data-ttu-id="61f98-336">V takovém případě může být užitečné vytvořit závislosti mezi položkami mezipaměti pomocí CancellationChangeToken.</span><span class="sxs-lookup"><span data-stu-id="61f98-336">In that case, it can be useful to create dependencies between cache entries, by using a CancellationChangeToken.</span></span> <span data-ttu-id="61f98-337">S CancellationChangeToken můžete vypršet více položek mezipaměti najednou zrušením tokenu.</span><span class="sxs-lookup"><span data-stu-id="61f98-337">With a CancellationChangeToken, you can expire multiple cache entries at once by canceling the token.</span></span>

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

<span data-ttu-id="61f98-338">Ukládání do mezipaměti může výrazně zlepšit výkon webových stránek, které opakovaně požadují stejné hodnoty z databáze.</span><span class="sxs-lookup"><span data-stu-id="61f98-338">Caching can dramatically improve the performance of web pages that repeatedly request the same values from the database.</span></span> <span data-ttu-id="61f98-339">Před použitím ukládání do mezipaměti nezapomeňte měřit přístup k datům a výkon stránky a používat ukládání do mezipaměti pouze tam, kde je potřeba zlepšení.</span><span class="sxs-lookup"><span data-stu-id="61f98-339">Be sure to measure data access and page performance before applying caching, and only apply caching where you see a need for improvement.</span></span> <span data-ttu-id="61f98-340">Ukládání do mezipaměti spotřebovává prostředky paměti webového serveru a zvyšuje složitost aplikace, takže je důležité, abyste předčasně optimalizovat pomocí této techniky.</span><span class="sxs-lookup"><span data-stu-id="61f98-340">Caching consumes web server memory resources and increases the complexity of the application, so it's important you don't prematurely optimize using this technique.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="61f98-341">[Předchozí](develop-asp-net-core-mvc-apps.md)
>[další](test-asp-net-core-mvc-apps.md)</span><span class="sxs-lookup"><span data-stu-id="61f98-341">[Previous](develop-asp-net-core-mvc-apps.md)
[Next](test-asp-net-core-mvc-apps.md)</span></span>
