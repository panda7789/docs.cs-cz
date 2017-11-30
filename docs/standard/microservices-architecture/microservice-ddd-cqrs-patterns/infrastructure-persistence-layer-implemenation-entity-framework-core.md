---
title: "Implementace vrstvu trvalosti infrastruktury základní Entity Framework"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace vrstvu trvalosti infrastruktury základní Entity Framework"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: 508d60d73eb7c0f0cc2cc909613cc4f8712b4aba
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="6a4ed-104">Implementace vrstvu trvalosti infrastruktury základní Entity Framework</span><span class="sxs-lookup"><span data-stu-id="6a4ed-104">Implementing the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="6a4ed-105">Při použití relačních databází, jako je například SQL Server, Oracle nebo PostgreSQL doporučený postup je implementace vrstvu trvalosti založené na Entity Framework (EF).</span><span class="sxs-lookup"><span data-stu-id="6a4ed-105">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="6a4ed-106">EF podporuje LINQ a poskytuje objektů se silným typem pro váš model, jakož i zjednodušené trvalost do vaší databáze.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-106">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="6a4ed-107">Rozhraní Entity Framework má dlouho historie v rámci rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-107">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="6a4ed-108">Pokud používáte .NET Core, byste měli použít také Entity Framework Core, který běží na systému Windows nebo Linux stejným způsobem jako .NET Core.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-108">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="6a4ed-109">Základní EF je kompletní přepisování Entity Frameworku, implementováno s mnohem menší nároky a důležitá vylepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-109">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="6a4ed-110">Úvod do Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="6a4ed-110">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="6a4ed-111">Základní Entity Framework (EF) je lightweight rozšiřitelný, a přístup technologie a platformy verzi oblíbených datům Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-111">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="6a4ed-112">Byla zavedená s .NET Core v polovině 2016.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-112">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="6a4ed-113">Vzhledem k tomu, že Úvod do základní EF je již k dispozici v dokumentaci společnosti Microsoft, tady jednoduše poskytujeme odkazy na tyto informace.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-113">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="6a4ed-114">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="6a4ed-114">Additional resources</span></span>

-   <span data-ttu-id="6a4ed-115">**Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span><span class="sxs-lookup"><span data-stu-id="6a4ed-115">**Entity Framework Core**
[*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span></span>

-   <span data-ttu-id="6a4ed-116">**Začínáme s ASP.NET Core a Entity Framework Core pomocí sady Visual Studio**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span><span class="sxs-lookup"><span data-stu-id="6a4ed-116">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio**
[*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span></span>

-   <span data-ttu-id="6a4ed-117">**Třída DbContext**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span><span class="sxs-lookup"><span data-stu-id="6a4ed-117">**DbContext Class**
[*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span></span>

-   <span data-ttu-id="6a4ed-118">**Porovnání EF základní & EF6.x**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span><span class="sxs-lookup"><span data-stu-id="6a4ed-118">**Compare EF Core & EF6.x**
[*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span></span>

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="6a4ed-119">Infrastruktury v Entity Framework Core z hlediska DDD</span><span class="sxs-lookup"><span data-stu-id="6a4ed-119">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="6a4ed-120">Z DDD hlediska, je důležitou schopností EF možnost používat domény entity objektů POCO, také známé v terminologii EF jako objektů POCO *kód – první entity*.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-120">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="6a4ed-121">Pokud používáte domény entity objektů POCO, tříd modelu domény jsou trvalost – které ignorují, následující [trvalost které](http://deviq.com/persistence-ignorance/) a [infrastruktury které](https://ayende.com/blog/3137/infrastructure-ignorance) zásady.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-121">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](http://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="6a4ed-122">Za vzory DDD by měl zapouzdřovat domény chování a pravidla v rámci třídy entity samostatně, takže ho můžete řídit výstupních podmínek, ověření a pravidel, při přístupu k jakékoli kolekce.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-122">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="6a4ed-123">Proto není vhodné v DDD umožňující veřejný přístup do kolekcí podřízených entit nebo hodnota objekty.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-123">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="6a4ed-124">Místo toho kterou chcete vystavit metody, které řídí, jak a kdy mohou být aktualizovány polí a vlastností kolekce, a jaké chování a akcí, má dojít, pokud k tomu dojde.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-124">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="6a4ed-125">V EF základní 1.1 splňovat tyto požadavky DDD může mít prostý pole v entity místo vlastnosti veřejné a privátní setter.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-125">In EF Core 1.1, to satisfy those DDD requirements you can have plain fields in your entities instead of properties with public and private setters.</span></span> <span data-ttu-id="6a4ed-126">Pokud nechcete, aby pole entity externě přístupné, můžete vytvořit pouze atribut nebo pole místo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-126">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="6a4ed-127">Je třeba použít privátní setter Pokud dáváte přednost tento čisticí přístup.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-127">There is no need to use private setters if you prefer this cleaner approach.</span></span>

<span data-ttu-id="6a4ed-128">Podobným způsobem, můžete Teď máte přístup jen pro čtení k kolekce pomocí veřejná vlastnost typu IEnumerable&lt;T&gt;, který je zálohovaný díky členem soukromé pole pro kolekci (jako seznam&lt;&gt;) ve vaší Entita, která využívá EF trvalosti.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-128">In a similar way, you can now have read-only access to collections by using a public property typed as IEnumerable&lt;T&gt;, which is backed by a private field member for the collection (like a List&lt;&gt;) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="6a4ed-129">Předchozí verze Entity Frameworku požadované vlastnosti kolekce pro podporu ICollection&lt;T&gt;, který určená, kdokoli z vývojářů pomocí třídy nadřazená entita může přidat nebo odebrat položky z kolekce jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-129">Previous versions of Entity Framework required collection properties to support ICollection&lt;T&gt;, which meant that any developer using the parent entity class could add or remove items from its property collections.</span></span> <span data-ttu-id="6a4ed-130">Tato možnost by proti doporučené vzory v DDD.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-130">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="6a4ed-131">Soukromé kolekce při vystavení objekt rozhraní IEnumerable jen pro čtení, můžete použít, jak je znázorněno v následujícím příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="6a4ed-131">You can use a private collection while exposing a read-only IEnumerable object, as shown in the following code example:</span></span>

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...
    private readonly List<OrderItem> _orderItems;

    public IEnumerable<OrderItem> OrderItems => _orderItems.AsReadOnly();

    protected Order() { }

    public Order(int buyerId, int paymentMethodId, Address address)
    {
        // Initializations ...
    }

    public void AddOrderItem(int productId, string productName,
        decimal unitPrice, decimal discount,
        string pictureUrl, int units = 1)
    {
        // Validation logic...
        var orderItem = new OrderItem(productId, productName, unitPrice, discount,
            pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

<span data-ttu-id="6a4ed-132">Všimněte si, že vlastnost OrderItems lze přistupovat pouze jen pro čtení pomocí seznamu&lt;&gt;. AsReadOnly().</span><span class="sxs-lookup"><span data-stu-id="6a4ed-132">Note that the OrderItems property can only be accessed as read-only using List&lt;&gt;.AsReadOnly().</span></span> <span data-ttu-id="6a4ed-133">Tato metoda vytvoří obálku kolem seznamu privátní jen pro čtení tak, že je soubor chráněný proti externí aktualizace.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-133">This method creates a read-only wrapper around the private list so that it is protected against external updates.</span></span> <span data-ttu-id="6a4ed-134">Je výrazně levnější než ToList způsobem, protože nemá zkopírujte všechny položky v kolekci nové; Místo toho provádí pouze jednu operaci alokační haldy pro instanci obálku.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-134">It is much cheaper than using the ToList method, because it does not have to copy all the items in a new collection; instead, it performs just one heap alloc operation for the wrapper instance.</span></span>

<span data-ttu-id="6a4ed-135">Základní EF poskytuje způsob, jak mapování modelu domény na fyzické databázi bez kontaminujících modelu domény.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-135">EF Core provides a way to map the domain model to the physical database without contaminating the domain model.</span></span> <span data-ttu-id="6a4ed-136">Je čistá .NET objektů POCO kódu, protože mapování akce je implementována ve vrstvu trvalosti.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-136">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="6a4ed-137">V této akci mapování budete muset konfigurovat mapování polí do databáze.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-137">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="6a4ed-138">V následujícím příkladu metody OnModelCreating informuje zvýrazněný EF základní přístup k vlastnosti OrderItems prostřednictvím jeho pole.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-138">In the following example of an OnModelCreating method, the highlighted code tells EF Core to access the OrderItems property through its field.</span></span>

```csharp
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    // ...
    modelBuilder.Entity<Order>(ConfigureOrder);
    // Other entities ...
}

void ConfigureOrder(EntityTypeBuilder<Order> orderConfiguration)
{
    // Other configuration ...
    var navigation = orderConfiguration.Metadata.
    FindNavigation(nameof(Order.OrderItems));
    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);
    // Other configuration ...
}
```

<span data-ttu-id="6a4ed-139">Pokud použijete pole místo vlastnosti, je entita OrderItem nastavené jako trvalé stejně, jako by se mělo seznam&lt;OrderItem&gt; vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-139">When you use fields instead of properties, the OrderItem entity is persisted just as if it had a List&lt;OrderItem&gt; property.</span></span> <span data-ttu-id="6a4ed-140">Však zveřejňuje jednoho přístupového objektu (metoda AddOrderItem) pro přidání nových položek do pořadí.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-140">However, it exposes a single accessor (the AddOrderItem method) for adding new items to the order.</span></span> <span data-ttu-id="6a4ed-141">V důsledku toho chování a data jsou svázané společně a bude konzistentní v rámci aplikace kód, který používá model domény.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-141">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implementing-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="6a4ed-142">Implementace vlastní úložiště základní Entity Framework</span><span class="sxs-lookup"><span data-stu-id="6a4ed-142">Implementing custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="6a4ed-143">Na úrovni implementace úložiště je jednoduše třídu s kódem trvalosti dat, koordinuje jednotka práce (DBContext v základní EF) při provádění aktualizací, jak je znázorněno v následující třídy:</span><span class="sxs-lookup"><span data-stu-id="6a4ed-143">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

```csharp
// using statements...
namespace Microsoft.eShopOnContainers.Services.Ordering.Infrastructure.Repositories
{
    public class BuyerRepository : IBuyerRepository
    {
        private readonly OrderingContext _context;

        public IUnitOfWork UnitOfWork
        {
            get
            {
                return _context;
            }
        }
    }

    public BuyerRepository(OrderingContext context)
    {
        if (context == null)
        {
            throw new ArgumentNullException(
                nameof(context));
        }
        _context = context;
    }

    public Buyer Add(Buyer buyer)
    {
        return _context.Buyers.Add(buyer).Entity;
    }

    public async Task<Buyer> FindAsync(string BuyerIdentityGuid)
    {
        var buyer = await _context.Buyers.Include(b => b.Payments)
            .Where(b => b.FullName == BuyerIdentityGuid)
            .SingleOrDefaultAsync();
        return buyer;
    }
}
```

<span data-ttu-id="6a4ed-144">Všimněte si, že rozhraní IBuyerRepository pochází z vrstvy modelu domény.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-144">Note that the IBuyerRepository interface comes from the domain model layer.</span></span> <span data-ttu-id="6a4ed-145">Implementace úložiště se však provádí na trvalosti a vrstvě infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-145">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="6a4ed-146">EF DbContext přicházejí konstruktoru pomocí vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-146">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="6a4ed-147">Jsou sdílena mezi několika úložiště v rámci stejného oboru požadavku HTTP, díky jeho výchozí doba života (ServiceLifetime.Scoped) v kontejneru IoC (která může také být explicitně nastaveny službou. AddDbContext&lt;&gt;).</span><span class="sxs-lookup"><span data-stu-id="6a4ed-147">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (ServiceLifetime.Scoped) in the IoC container (which can also be explicitly set with services.AddDbContext&lt;&gt;).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="6a4ed-148">Metody k implementaci v úložišti (aktualizace nebo transakce a dotazy)</span><span class="sxs-lookup"><span data-stu-id="6a4ed-148">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="6a4ed-149">V rámci každé třídy úložiště byste měli umístit trvalost metody, které aktualizuje stav entity obsažený v jeho související agregace.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-149">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="6a4ed-150">Mějte na paměti, že existuje relace 1: 1 mezi agregace a jeho souvisejících úložiště.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-150">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="6a4ed-151">Vezměte v úvahu, že objekt entity agregační kořenové může vložených podřízených entit v rámci jeho EF grafu.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-151">Take into account that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="6a4ed-152">Například kupujících může mít více způsoby platby jako souvisejících podřízených entit.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-152">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="6a4ed-153">Vzhledem k tomu, že přístup pro řazení mikroslužbu v eShopOnContainers také podle CQS/CQRS, většinu dotazů nejsou implementované v vlastní úložiště.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-153">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="6a4ed-154">Vývojáři mají možnost používat tato zařízení k vytvoření dotazů a spojení, které potřebují pro prezentační vrstvy bez omezení, způsobené agregace, vlastní úložiště na agregaci a DDD obecně.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-154">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="6a4ed-155">Většina vlastní úložiště navrhované tímto průvodcem má několik aktualizací nebo transakční metody, ale jenom metody dotazů nutná, aby se aktualizovat data.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-155">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="6a4ed-156">Například úložiště BuyerRepository implementuje metodu asynchronně vyhledá, protože aplikace je potřeba vědět, zda existuje konkrétní kupujících před vytvořením nového kupujících související s pořadí.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-156">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="6a4ed-157">Však budete implementovat metody skutečné dotazů se získat data k odeslání do prezentační vrstvy nebo klienta aplikace, jak je uvedeno v dotazech CQRS podle flexibilní dotazy pomocí Dapper.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-157">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="6a4ed-158">Použití vlastního úložiště a kdy EF DbContext přímo</span><span class="sxs-lookup"><span data-stu-id="6a4ed-158">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="6a4ed-159">Třída Entity Framework DbContext podle vzorů jednotky práce a úložiště a slouží přímo z vašeho kódu, například z řadiče ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-159">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="6a4ed-160">To znamená způsob, jakým můžete vytvořit kód nejjednodušší jako mikroslužbu katalogu CRUD v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-160">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="6a4ed-161">V případech, kde chcete nejjednodušší kód možné můžete přímo použití třídy DbContext, stejně jako celá řada vývojářů.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-161">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="6a4ed-162">Ale implementace vlastní úložiště nabízí několik výhod při implementaci složitější mikroslužeb nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-162">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="6a4ed-163">Vzory jednotky práce a úložiště jsou určeny k zapouzdření vrstvu trvalosti infrastruktury, je odpojená od aplikace a vrstvy modelu domény.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-163">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="6a4ed-164">Implementace tyto vzory usnadnit používání imitované úložišť simulaci přístup k databázi.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-164">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="6a4ed-165">Obrázek 9 až 18 se zobrazí rozdíly mezi nepoužíváte úložiště (přímo pomocí EF DbContext) a kdy úložiště, které usnadňují model těchto úložiště.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-165">In Figure 9-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![](./media/image19.png)

<span data-ttu-id="6a4ed-166">**Obrázek 9 až 18**.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-166">**Figure 9-18**.</span></span> <span data-ttu-id="6a4ed-167">Použití vlastní úložiště versus prostý DbContext</span><span class="sxs-lookup"><span data-stu-id="6a4ed-167">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="6a4ed-168">Při mocking se více alternativy.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="6a4ed-169">Může model právě úložiště nebo může model celou pracovní jednotka.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="6a4ed-170">Obvykle mocking právě úložiště je dostatek a složitost a abstraktní model celou pracovní jednotka není obvykle nutné.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="6a4ed-171">Později když se zaměříme na aplikační vrstvu, zobrazí se fungování vkládání závislostí v ASP.NET Core a jak jsou implementované při použití úložiště.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="6a4ed-172">Stručně řečeno vlastní úložiště umožňují snadněji testování kódu pomocí jednotkových testů, které nejsou vliv stav dat vrstvy.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="6a4ed-173">Pokud spustíte testy, které také přístup k databázi skutečné prostřednictvím rozhraní Entity Framework, nejsou testování částí, ale testy integrace, které jsou mnohem nižší.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="6a4ed-174">Pokud jste používali DbContext přímo, jenom možnost, kterou byste měli by mohla být spouštění testů jednotek pomocí serveru SQL v paměti s předvídatelný dat pro testování částí.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-174">If you were using DbContext directly, the only choice you would have would be to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="6a4ed-175">Nebude moci řídit mock objektů a falešných dat na úrovni úložiště stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-175">You would not be able to control mock objects and fake data in the same way at the repository level.</span></span> <span data-ttu-id="6a4ed-176">Samozřejmě může vždy otestovat řadiče MVC.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="6a4ed-177">EF DbContext a IUnitOfWork doba platnosti instance v vaší kontejner IoC</span><span class="sxs-lookup"><span data-stu-id="6a4ed-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="6a4ed-178">Objekt DbContext (zveřejněné jako objekt IUnitOfWork) může být potřeba sdílet mezi více úložiště v rámci stejného oboru požadavku HTTP.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-178">The DbContext object (exposed as an IUnitOfWork object) might need to be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="6a4ed-179">Například to platí při operaci spouštěna musí pracovat s více agregace, ani jednoduše vzhledem k tomu, že používáte více instancí úložiště.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="6a4ed-180">Je také důležité zmínit, že rozhraní IUnitOfWork je součástí domény, ne typ EF.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-180">It is also important to mention that the IUnitOfWork interface is part of the domain, not an EF type.</span></span>

<span data-ttu-id="6a4ed-181">Aby bylo možné provést, musí mít jeho služby dobu života nastavenu na ServiceLifetime.Scoped instanci objekt DbContext.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-181">In order to do that, the instance of the DbContext object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="6a4ed-182">Toto je výchozí doba života při registraci DbContext s služeb. AddDbContext ve vaší kontejner IoC z metody ConfigureServices souboru Startup.cs v projektu webového rozhraní API ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-182">This is the default lifetime when registering a DbContext with services.AddDbContext in your IoC container from the ConfigureServices method of the Startup.cs file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="6a4ed-183">Následující kód to znázorňuje.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-183">The following code illustrates this.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    // Add framework services.
    services.AddMvc(options =>
    {
        options.Filters.Add(typeof(HttpGlobalExceptionFilter));
    }).AddControllersAsServices();

    services.AddEntityFrameworkSqlServer()
    .AddDbContext<OrderingContext>(options =>
    {
        options.UseSqlServer(Configuration["ConnectionString"],
        sqlop => sqlop.MigrationsAssembly(typeof(Startup).GetTypeInfo().
        Assembly.GetName().Name));
    },
    ServiceLifetime.Scoped // Note that Scoped is the default choice
    // in AddDbContext. It is shown here only for
    // pedagogic purposes.
    );
}
```

<span data-ttu-id="6a4ed-184">Režim vytváření instancí DbContext by se neměla konfigurovat jako ServiceLifetime.Transient nebo ServiceLifetime.Singleton.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="6a4ed-185">Doba platnosti instance úložiště v vaší kontejner IoC</span><span class="sxs-lookup"><span data-stu-id="6a4ed-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="6a4ed-186">Podobným způsobem musí být v úložišti životnost obvykle nastavená jako oboru (InstancePerLifetimeScope v Autofac).</span><span class="sxs-lookup"><span data-stu-id="6a4ed-186">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="6a4ed-187">Také může být přechodná (InstancePerDependency v Autofac), ale vaše služba bude efektivnější v paměti namapoval při použití vymezená životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="6a4ed-188">Všimněte si, že pomocí singleton doba platnosti pro úložiště by mohla způsobovat můžete souběžnosti závažné problémy vaší DbContext nastavena na obor životnosti (InstancePerLifetimeScope) (výchozí doba života pro DBContext).</span><span class="sxs-lookup"><span data-stu-id="6a4ed-188">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="6a4ed-189">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="6a4ed-189">Additional resources</span></span>

-   <span data-ttu-id="6a4ed-190">**Implementace úložiště a jednotky pracovních vzorů v aplikaci ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/ Implementing-the-Repository-and-Unit-of-work-Patterns-in-an-ASP-NET-MVC-Application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span><span class="sxs-lookup"><span data-stu-id="6a4ed-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application**
[*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span></span>

-   <span data-ttu-id="6a4ed-191">**Jonathan Allen. Strategie implementace pro úložiště vzor s platformou Entity Framework, Dapper a řetězu**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span><span class="sxs-lookup"><span data-stu-id="6a4ed-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain**
[*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span></span>

-   <span data-ttu-id="6a4ed-192">**Cesaru členka Torre. Porovnávání životnosti služby kontejner IoC jádro ASP.NET s obory instance kontejner Autofac IoC**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ Comparing-ASP-NET-Core-IOC-Service-LIFE-Times-and-autofac-IOC-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="6a4ed-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="table-mapping"></a><span data-ttu-id="6a4ed-193">Mapování tabulek</span><span class="sxs-lookup"><span data-stu-id="6a4ed-193">Table mapping</span></span>

<span data-ttu-id="6a4ed-194">Mapování tabulky identifikuje data tabulky, která mají být získaných z a uložit do databáze.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="6a4ed-195">Dříve jste viděli, jak lze pomocí entity domény (například produktu nebo pořadí doména) Generovat schéma související databáze.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="6a4ed-196">EF je důrazně uspořádaná kolem koncept *konvence*.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="6a4ed-197">Konvence adresu otázky typu "Jaký název tabulky bude?"</span><span class="sxs-lookup"><span data-stu-id="6a4ed-197">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="6a4ed-198">nebo "jaké vlastnost je primární klíč?"</span><span class="sxs-lookup"><span data-stu-id="6a4ed-198">or “What property is the primary key?”</span></span> <span data-ttu-id="6a4ed-199">Konvence jsou obvykle založené na běžné názvy – například je typické pro primární klíč jako vlastnost, která končí ID.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-199">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="6a4ed-200">Podle konvence, každá entita se nastavit tak, aby mapovat do tabulky se stejným názvem jako DbSet&lt;TEntity&gt; vlastnost, která zveřejňuje se entita na odvozené kontextu.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-200">By convention, each entity will be set up to map to a table with the same name as the DbSet&lt;TEntity&gt; property that exposes the entity on the derived context.</span></span> <span data-ttu-id="6a4ed-201">Pokud žádné DbSet&lt;TEntity&gt; hodnota je zadaný pro danou entitu, se používá název třídy.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-201">If no DbSet&lt;TEntity&gt; value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="6a4ed-202">Datových poznámek versus rozhraní Fluent API</span><span class="sxs-lookup"><span data-stu-id="6a4ed-202">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="6a4ed-203">Existuje mnoho dalších konvence EF jádra a většina z nich lze změnit pomocí datových poznámek nebo rozhraní Fluent API implementována v rámci metody OnModelCreating.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-203">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="6a4ed-204">Datových poznámek musí použít na třídy modelu entity, sami, což je více obtěžující způsob, jak z hlediska DDD.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-204">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="6a4ed-205">Je to proto, že jsou kontaminujících modelu s anotacemi dat související s databázi infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-205">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="6a4ed-206">Na druhé straně rozhraní Fluent API je pohodlný způsob, jak změnit většina konvence a mapování v rámci vrstvě infrastruktury trvalosti dat, a tak entity model vyčištění a odpojeného od infrastruktury trvalost.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-206">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="6a4ed-207">Rozhraní Fluent API a metody OnModelCreating</span><span class="sxs-lookup"><span data-stu-id="6a4ed-207">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="6a4ed-208">Jak je uvedeno, aby bylo možné změnit konvence a mapování, můžete metody OnModelCreating v třídy DbContext.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-208">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span> <span data-ttu-id="6a4ed-209">Následující příklad ukazuje, jak jsme to udělat v řazení mikroslužbu v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-209">The following example shows how we do this in the ordering microservice in eShopOnContainers.</span></span>

```csharp
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
    //Other entities
    modelBuilder.Entity<OrderStatus>(ConfigureOrderStatus);
    //Other entities
}

void ConfigureOrder(EntityTypeBuilder<Order> orderConfiguration)
{
    orderConfiguration.ToTable("orders", DEFAULT_SCHEMA);
    orderConfiguration.HasKey(o => o.Id);
    orderConfiguration.Property(o => o.Id).ForSqlServerUseSequenceHiLo("orderseq", DEFAULT_SCHEMA);
    orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
    orderConfiguration.Property<string>("Street").IsRequired();
    orderConfiguration.Property<string>("State").IsRequired();
    orderConfiguration.Property<string>("City").IsRequired();
    orderConfiguration.Property<string>("ZipCode").IsRequired();
    orderConfiguration.Property<string>("Country").IsRequired();
    orderConfiguration.Property<int>("BuyerId").IsRequired();
    orderConfiguration.Property<int>("OrderStatusId").IsRequired();
    orderConfiguration.Property<int>("PaymentMethodId").IsRequired();

    var navigation =
    orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));
    // DDD Patterns comment:
    // Set as Field (new since EF 1.1) to access
    // the OrderItem collection property as a field
    navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

    orderConfiguration.HasOne(o => o.PaymentMethod)
        .WithMany()
        .HasForeignKey("PaymentMethodId")
        .OnDelete(DeleteBehavior.Restrict);
        orderConfiguration.HasOne(o => o.Buyer)
        .WithMany()
        .HasForeignKey("BuyerId");
        orderConfiguration.HasOne(o => o.OrderStatus)
        .WithMany()
        .HasForeignKey("OrderStatusId");
}
```

<span data-ttu-id="6a4ed-210">Můžete nastavit všechna rozhraní Fluent API mapování v rámci stejné metody OnModelCreating, ale doporučuje se oddílu tento kód a mít více submethods, jeden pro každou entitu, jak je znázorněno v příkladu.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-210">You could set all the Fluent API mappings within the same OnModelCreating method, but it is advisable to partition that code and have multiple submethods, one per entity, as shown in the example.</span></span> <span data-ttu-id="6a4ed-211">U modelů, zejména velké může i být vhodné mít samostatné zdrojové soubory (statické třídy) pro konfiguraci různých entity typů.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-211">For particularly large models, it can even be advisable to have separate source files (static classes) for configuring different entity types.</span></span>

<span data-ttu-id="6a4ed-212">Kód v ukázce je explicitní.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-212">The code in the example is explicit.</span></span> <span data-ttu-id="6a4ed-213">Konvence EF základní však provádění většiny to automaticky, takže skutečný kód, který by potřebujete k zápisu do dosáhnout samé by být mnohem menší.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-213">However, EF Core conventions do most of this automatically, so the actual code you would need to write to achieve the same thing would be much smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="6a4ed-214">Algoritmus HIS použití/Lo v EF jádra</span><span class="sxs-lookup"><span data-stu-id="6a4ed-214">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="6a4ed-215">Zajímavé aspekt kódu v předchozím příkladu je, že používá [HIS použití/Lo algoritmus](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/) jako strategie generování klíče.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-215">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/2014/06/23/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="6a4ed-216">Algoritmus HIS použití/Lo je užitečné, když potřebujete jedinečné klíče.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-216">The Hi/Lo algorithm is useful when you need unique keys.</span></span> <span data-ttu-id="6a4ed-217">Jako souhrn přiřadí algoritmus HIS použití-u jedinečné identifikátory řádky tabulky při není v závislosti na ukládání řádek v databázi okamžitě.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-217">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="6a4ed-218">Díky tomu můžete začít používat identifikátory hned, jak se stane s standardní sekvenční databázi ID.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-218">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="6a4ed-219">Algoritmus HIS použití/Lo popisuje mechanismus pro generování bezpečné ID na straně klienta a nikoli v databázi.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-219">The Hi/Lo algorithm describes a mechanism for generating safe IDs on the client side rather than in the database.</span></span> <span data-ttu-id="6a4ed-220">*Bezpečné* v tomto kontextu znamená bez kolizí.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-220">*Safe* in this context means without collisions.</span></span> <span data-ttu-id="6a4ed-221">Tento algoritmus je zajímavé z těchto důvodů:</span><span class="sxs-lookup"><span data-stu-id="6a4ed-221">This algorithm is interesting for these reasons:</span></span>

-   <span data-ttu-id="6a4ed-222">Nedochází k přerušení vzoru pracovní jednotky.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-222">It does not break the Unit of Work pattern.</span></span>

-   <span data-ttu-id="6a4ed-223">Nevyžaduje se, že odezev generátory pořadí způsob, jak provést v jiné systémy DBMS.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-223">It does not require round trips the way sequence generators do in other DBMSs.</span></span>

-   <span data-ttu-id="6a4ed-224">Vygeneruje lidského čitelný identifikátor, na rozdíl od techniky, které používají identifikátory GUID.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-224">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="6a4ed-225">Jádro EF podporuje [HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) ForSqlServerUseSequenceHiLo metodou, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-225">EF Core supports [HiLo](http://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the ForSqlServerUseSequenceHiLo method, as shown in the preceding example.</span></span>

### <a name="mapping-fields-instead-of-properties"></a><span data-ttu-id="6a4ed-226">Mapování polí místo vlastnosti</span><span class="sxs-lookup"><span data-stu-id="6a4ed-226">Mapping fields instead of properties</span></span>

<span data-ttu-id="6a4ed-227">S funkcí 1.1 EF jádra, která se mapuje na pole sloupců je možné nechcete použít jakékoli vlastnosti ve třídě entity a jenom pro mapování sloupce z tabulky na pole.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-227">With the feature of EF Core 1.1 that maps columns to fields, it is possible to not use any properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="6a4ed-228">Běžně používá pro který by privátní pole pro všechny vnitřní stav, která nemusí být subjekty mimo entity.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-228">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="6a4ed-229">EF 1.1 podporuje mapováním pole bez související vlastnosti na sloupec v databázi.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-229">EF 1.1 supports a way to map a field without a related property to a column in the database.</span></span> <span data-ttu-id="6a4ed-230">To provedete pomocí jednoho pole nebo také pomocí kolekcí, jako je seznam&lt; &gt; pole.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-230">You can do this with single fields or also with collections, like a List&lt;&gt; field.</span></span> <span data-ttu-id="6a4ed-231">Tento bod jsem už zmínili dřív když jsme se bavili modelování třídy modelu domény, ale zde se zobrazí, jak se provádí mapování s konfigurací PropertyAccessMode.Field zvýrazněných v předchozí kód.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-231">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the PropertyAccessMode.Field configuration highlighted in the previous code.</span></span>

### <a name="using-shadow-properties-in-value-objects-for-hidden-ids-at-the-infrastructure-level"></a><span data-ttu-id="6a4ed-232">Používání stínové vlastností v objektech hodnota skrytá ID na úrovni infrastruktury</span><span class="sxs-lookup"><span data-stu-id="6a4ed-232">Using shadow properties in value objects for hidden IDs at the infrastructure level</span></span>

<span data-ttu-id="6a4ed-233">Vlastnosti stínové v základní EF jsou vlastnosti, které nejsou k dispozici do třídy modelu entity.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-233">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="6a4ed-234">Hodnoty a stavy tyto vlastnosti jsou zachována výhradně v [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) třídy na úrovni infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-234">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

<span data-ttu-id="6a4ed-235">Z DDD hlediska jsou vlastnosti stínové pohodlný způsob, jak implementovat objekty hodnota skrytím ID jako primární klíč stínové vlastnost.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-235">From a DDD point of view, shadow properties are a convenient way to implement value objects by hiding the ID as a shadow property primary key.</span></span> <span data-ttu-id="6a4ed-236">To je důležité, protože objekt hodnoty by neměl mít identity (alespoň, můžete by neměl mít ID ve vrstvě modelu domény při shaping hodnota objektů).</span><span class="sxs-lookup"><span data-stu-id="6a4ed-236">This is important, because a value object should not have identity (at least, you should not have the ID in the domain model layer when shaping value objects).</span></span> <span data-ttu-id="6a4ed-237">Zde bod nemá, od aktuální verze EF základní EF základní způsob, jak implementovat objekty hodnotu jako [komplexní typy](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx), jak je možné v EF 6.x.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-237">The point here is that as of the current version of EF Core, EF Core does not have a way to implement value objects as [complex types](https://msdn.microsoft.com/library/jj680147(v=vs.113).aspx), as is possible in EF 6.x.</span></span> <span data-ttu-id="6a4ed-238">To je důvod, proč potřebujete aktuálně implementovat objekt hodnoty jako entity s skrytá ID (primární klíč) nastavit jako vlastnost stínové.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-238">That is why you currently need to implement a value object as an entity with a hidden ID (primary key) set as a shadow property.</span></span>

<span data-ttu-id="6a4ed-239">Jak vidíte v [objekt hodnoty adres](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs) v eShopOnContainers, v modelu adresu nevidíte ID:</span><span class="sxs-lookup"><span data-stu-id="6a4ed-239">As you can see in the [Address value object](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Domain/AggregatesModel/OrderAggregate/Address.cs) in eShopOnContainers, in the Address model you do not see an ID:</span></span>

```csharp
public class Address : ValueObject
{
    public String Street { get; private set; }
    public String City { get; private set; }
    public String State { get; private set; }
    public String Country { get; private set; }
    public String ZipCode { get; private set; }
    //Constructor initializing, etc
}
```

<span data-ttu-id="6a4ed-240">Ale v pozadí, je potřeba zadat ID tak, aby základní EF je možné zachovat tato data v tabulkách databáze.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-240">But under the covers, we need to provide an ID so that EF Core is able to persist this data in the database tables.</span></span> <span data-ttu-id="6a4ed-241">Provedeme to v metodě ConfigureAddress [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) třídy na úrovni infrastruktury, proto jsme není znečištění směrovány správu modelu domény s EF infrastruktury kódem.</span><span class="sxs-lookup"><span data-stu-id="6a4ed-241">We do that in the ConfigureAddress method of the [OrderingContext.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.Infrastructure/OrderingContext.cs) class at the infrastructure level, so we do not pollute the domain model with EF infrastructure code.</span></span>

```csharp
void ConfigureAddress(EntityTypeBuilder<Address> addressConfiguration)
{
    addressConfiguration.ToTable("address", DEFAULT_SCHEMA);
    // DDD pattern comment:
    // Implementing the Address ID as a shadow property, because the
    // address is a value object and an identity is not required for a
    // value object
    // EF Core just needs the ID so it can store it in a database table
    // See: https://docs.microsoft.com/ef/core/modeling/shadow-properties
    addressConfiguration.Property<int>("Id").IsRequired();
    addressConfiguration.HasKey("Id");
}
```

#### <a name="additional-resources"></a><span data-ttu-id="6a4ed-242">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="6a4ed-242">Additional resources</span></span>

-   <span data-ttu-id="6a4ed-243">**Tabulky mapování**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span><span class="sxs-lookup"><span data-stu-id="6a4ed-243">**Table Mapping**
[*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span></span>

-   <span data-ttu-id="6a4ed-244">**Používá ke generování klíče Entity Framework Core HiLo**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span><span class="sxs-lookup"><span data-stu-id="6a4ed-244">**Use HiLo to generate keys with Entity Framework Core**
[*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span></span>

-   <span data-ttu-id="6a4ed-245">**Zálohování pole**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span><span class="sxs-lookup"><span data-stu-id="6a4ed-245">**Backing Fields**
[*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span></span>

-   <span data-ttu-id="6a4ed-246">**Steve Smith. Zapouzdřené kolekcí v Entity Framework Core**
    [*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)</span><span class="sxs-lookup"><span data-stu-id="6a4ed-246">**Steve Smith. Encapsulated Collections in Entity Framework Core**
[*http://ardalis.com/encapsulated-collections-in-entity-framework-core*](http://ardalis.com/encapsulated-collections-in-entity-framework-core)</span></span>

-   <span data-ttu-id="6a4ed-247">**Stínové vlastnosti**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="6a4ed-247">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="6a4ed-248">[Předchozí] (infrastruktury trvalost layer-design.md) [Další] (nosql-database trvalost infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="6a4ed-248">[Previous] (infrastructure-persistence-layer-design.md) [Next] (nosql-database-persistence-infrastructure.md)</span></span>
