---
title: Implementace vrstvu trvalosti infrastruktury základní Entity Framework
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace vrstvu trvalosti infrastruktury základní Entity Framework
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 6003252d7e87428c7f954b57c3b67a041e3f3b15
ms.sourcegitcommit: 979597cd8055534b63d2c6ee8322938a27d0c87b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/29/2018
ms.locfileid: "37106473"
---
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="b6cc8-103">Implementace vrstvu trvalosti infrastruktury základní Entity Framework</span><span class="sxs-lookup"><span data-stu-id="b6cc8-103">Implementing the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="b6cc8-104">Při použití relačních databází, jako je například SQL Server, Oracle nebo PostgreSQL doporučený postup je implementace vrstvu trvalosti založené na Entity Framework (EF).</span><span class="sxs-lookup"><span data-stu-id="b6cc8-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="b6cc8-105">EF podporuje LINQ a poskytuje objektů se silným typem pro váš model, jakož i zjednodušené trvalost do vaší databáze.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="b6cc8-106">Rozhraní Entity Framework má dlouho historie v rámci rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="b6cc8-107">Pokud používáte .NET Core, byste měli použít také Entity Framework Core, který běží na systému Windows nebo Linux stejným způsobem jako .NET Core.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="b6cc8-108">Základní EF je kompletní přepisování Entity Frameworku, implementováno s mnohem menší nároky a důležitá vylepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-108">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="b6cc8-109">Úvod do Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="b6cc8-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="b6cc8-110">Základní Entity Framework (EF) je lightweight rozšiřitelný, a přístup technologie a platformy verzi oblíbených datům Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="b6cc8-111">Byla zavedená s .NET Core v polovině 2016.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="b6cc8-112">Vzhledem k tomu, že Úvod do základní EF je již k dispozici v dokumentaci společnosti Microsoft, tady jednoduše poskytujeme odkazy na tyto informace.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="b6cc8-113">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="b6cc8-113">Additional resources</span></span>

-   <span data-ttu-id="b6cc8-114">**Základní Entity Framework**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span><span class="sxs-lookup"><span data-stu-id="b6cc8-114">**Entity Framework Core**
[*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span></span>

-   <span data-ttu-id="b6cc8-115">**Začínáme s ASP.NET Core a Entity Framework Core pomocí sady Visual Studio**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span><span class="sxs-lookup"><span data-stu-id="b6cc8-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio**
[*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span></span>

-   <span data-ttu-id="b6cc8-116">**Třída DbContext**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span><span class="sxs-lookup"><span data-stu-id="b6cc8-116">**DbContext Class**
[*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span></span>

-   <span data-ttu-id="b6cc8-117">**Porovnání EF základní & EF6.x**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span><span class="sxs-lookup"><span data-stu-id="b6cc8-117">**Compare EF Core & EF6.x**
[*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span></span>

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="b6cc8-118">Infrastruktury v Entity Framework Core z hlediska DDD</span><span class="sxs-lookup"><span data-stu-id="b6cc8-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="b6cc8-119">Z DDD hlediska, je důležitou schopností EF možnost používat domény entity objektů POCO, také známé v terminologii EF jako objektů POCO *kód – první entity*.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="b6cc8-120">Pokud používáte domény entity objektů POCO, tříd modelu domény jsou trvalost – které ignorují, následující [trvalost které](http://deviq.com/persistence-ignorance/) a [infrastruktury které](https://ayende.com/blog/3137/infrastructure-ignorance) zásady.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](http://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="b6cc8-121">Za vzory DDD by měl zapouzdřovat domény chování a pravidla v rámci třídy entity samostatně, takže ho můžete řídit výstupních podmínek, ověření a pravidel, při přístupu k jakékoli kolekce.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="b6cc8-122">Proto není vhodné v DDD umožňující veřejný přístup do kolekcí podřízených entit nebo hodnota objekty.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="b6cc8-123">Místo toho kterou chcete vystavit metody, které řídí, jak a kdy mohou být aktualizovány polí a vlastností kolekce, a jaké chování a akcí, má dojít, pokud k tomu dojde.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="b6cc8-124">Od verze 1.1 základní EF splňovat tyto požadavky DDD, může mít prostý pole v místo veřejné vlastnosti vaší entity.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="b6cc8-125">Pokud nechcete, aby pole entity externě přístupné, můžete vytvořit pouze atribut nebo pole místo vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="b6cc8-126">Můžete také použít privátní vlastnost Setter.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-126">You can also use private property setters.</span></span>

<span data-ttu-id="b6cc8-127">Podobným způsobem, můžete Teď máte přístup jen pro čtení k kolekce pomocí zadané jako veřejná vlastnost `IReadOnlyCollection<T>`, který je zálohovaný díky členem soukromé pole pro kolekci (například `List<T>`) ve vaší entity, které jsou závislé na EF trvalosti.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="b6cc8-128">Předchozí verze Entity Frameworku požadované vlastnosti kolekce pro podporu `ICollection<T>`, který určená, kdokoli z vývojářů pomocí třídy nadřazená entita může přidat nebo odebrat položky přes jeho vlastnost kolekce.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="b6cc8-129">Tato možnost by proti doporučené vzory v DDD.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="b6cc8-130">Můžete použít kolekci privátní při vystavení jen pro čtení `IReadOnlyCollection<T>` objektu, jak je znázorněno v následujícím příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="b6cc8-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

```csharp
public class Order : Entity
{
    // Using private fields, allowed since EF Core 1.1
    private DateTime _orderDate;
    // Other fields ...

    private readonly List<OrderItem> _orderItems; 
    public IReadOnlyCollection<OrderItem> OrderItems => _orderItems;

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

        var orderItem = new OrderItem(productId, productName, 
                                      unitPrice, discount,
                                      pictureUrl, units);
        _orderItems.Add(orderItem);
    }
}
```

<span data-ttu-id="b6cc8-131">Všimněte si, že `OrderItems` vlastnost lze přistupovat pouze jako jen pro čtení pomocí `IReadOnlyCollection<OrderItem>`.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-131">Note that the `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="b6cc8-132">Tento typ je jen pro čtení, takže je chráněný proti externí pravidelných aktualizace.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-132">This type is read-only so it is protected against regular external updates.</span></span> 

<span data-ttu-id="b6cc8-133">Základní EF poskytuje způsob, jak mapování modelu domény na fyzické databázi bez "kontaminujících" modelu domény.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="b6cc8-134">Je čistá .NET objektů POCO kódu, protože mapování akce je implementována ve vrstvu trvalosti.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="b6cc8-135">V této akci mapování budete muset konfigurovat mapování polí do databáze.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="b6cc8-136">V následujícím příkladu metody OnModelCreating informuje zvýrazněný EF základní přístup k vlastnosti OrderItems prostřednictvím jeho pole.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-136">In the following example of an OnModelCreating method, the highlighted code tells EF Core to access the OrderItems property through its field.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
        orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);
        // Other configuration

        var navigation = 
              orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        //EF access the OrderItem collection property through its backing field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        // Other configuration
    }
}
```

<span data-ttu-id="b6cc8-137">Pokud použijete pole místo vlastnosti, je entita OrderItem nastavené jako trvalé stejně, jako by se mělo seznam&lt;OrderItem&gt; vlastnost.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-137">When you use fields instead of properties, the OrderItem entity is persisted just as if it had a List&lt;OrderItem&gt; property.</span></span> <span data-ttu-id="b6cc8-138">Však zveřejňuje jednoho přístupového objektu, `AddOrderItem` metoda pro přidání nových položek do pořadí.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-138">However, it exposes a single accessor, the `AddOrderItem` method for adding new items to the order.</span></span> <span data-ttu-id="b6cc8-139">V důsledku toho chování a data jsou svázané společně a bude konzistentní v rámci aplikace kód, který používá model domény.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implementing-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="b6cc8-140">Implementace vlastní úložiště základní Entity Framework</span><span class="sxs-lookup"><span data-stu-id="b6cc8-140">Implementing custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="b6cc8-141">Na úrovni implementace úložiště je jednoduše třídu s kódem trvalosti dat, koordinuje jednotka práce (DBContext v základní EF) při provádění aktualizací, jak je znázorněno v následující třídy:</span><span class="sxs-lookup"><span data-stu-id="b6cc8-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

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

        public BuyerRepository(OrderingContext context)
        {
            _context = context ?? throw new ArgumentNullException(nameof(context));
        }

        public Buyer Add(Buyer buyer)
        {
            return _context.Buyers.Add(buyer).Entity; 
        }

        public async Task<Buyer> FindAsync(string BuyerIdentityGuid)
        {
            var buyer = await _context.Buyers
                .Include(b => b.Payments)
                .Where(b => b.FullName == BuyerIdentityGuid)
                .SingleOrDefaultAsync();

            return buyer;
        }
    }
}
```

<span data-ttu-id="b6cc8-142">Všimněte si, že rozhraní IBuyerRepository pochází z vrstvy modelu domény jako kontraktu.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-142">Note that the IBuyerRepository interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="b6cc8-143">Implementace úložiště se však provádí na trvalosti a vrstvě infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="b6cc8-144">EF DbContext přicházejí konstruktoru pomocí vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="b6cc8-145">Jsou sdílena mezi několika úložiště v rámci stejného oboru požadavku HTTP, díky jeho výchozí doba života (ServiceLifetime.Scoped) v kontejneru IoC (která může také být explicitně nastaveny službou. AddDbContext&lt;&gt;).</span><span class="sxs-lookup"><span data-stu-id="b6cc8-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (ServiceLifetime.Scoped) in the IoC container (which can also be explicitly set with services.AddDbContext&lt;&gt;).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="b6cc8-146">Metody k implementaci v úložišti (aktualizace nebo transakce a dotazy)</span><span class="sxs-lookup"><span data-stu-id="b6cc8-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="b6cc8-147">V rámci každé třídy úložiště byste měli umístit trvalost metody, které aktualizuje stav entity obsažený v jeho související agregace.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="b6cc8-148">Mějte na paměti, že existuje relace 1: 1 mezi agregace a jeho souvisejících úložiště.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="b6cc8-149">Vezměte v úvahu, že objekt entity agregační kořenové může vložených podřízených entit v rámci jeho EF grafu.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-149">Take into account that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="b6cc8-150">Například kupujících může mít více způsoby platby jako souvisejících podřízených entit.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="b6cc8-151">Vzhledem k tomu, že přístup pro řazení mikroslužbu v eShopOnContainers také podle CQS/CQRS, většinu dotazů nejsou implementované v vlastní úložiště.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="b6cc8-152">Vývojáři mají možnost používat tato zařízení k vytvoření dotazů a spojení, které potřebují pro prezentační vrstvy bez omezení, způsobené agregace, vlastní úložiště na agregaci a DDD obecně.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="b6cc8-153">Většina vlastní úložiště navrhované tímto průvodcem má několik aktualizací nebo transakční metody, ale jenom metody dotazů nutná, aby se aktualizovat data.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="b6cc8-154">Například úložiště BuyerRepository implementuje metodu asynchronně vyhledá, protože aplikace je potřeba vědět, zda existuje konkrétní kupujících před vytvořením nového kupujících související s pořadí.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="b6cc8-155">Však budete implementovat metody skutečné dotazů se získat data k odeslání do prezentační vrstvy nebo klienta aplikace, jak je uvedeno v dotazech CQRS podle flexibilní dotazy pomocí Dapper.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="b6cc8-156">Použití vlastního úložiště a kdy EF DbContext přímo</span><span class="sxs-lookup"><span data-stu-id="b6cc8-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="b6cc8-157">Třída Entity Framework DbContext podle vzorů jednotky práce a úložiště a slouží přímo z vašeho kódu, například z řadiče ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="b6cc8-158">To znamená způsob, jakým můžete vytvořit kód nejjednodušší jako mikroslužbu katalogu CRUD v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-158">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="b6cc8-159">V případech, kde chcete nejjednodušší kód možné můžete přímo použití třídy DbContext, stejně jako celá řada vývojářů.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="b6cc8-160">Ale implementace vlastní úložiště nabízí několik výhod při implementaci složitější mikroslužeb nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="b6cc8-161">Vzory jednotky práce a úložiště jsou určeny k zapouzdření vrstvu trvalosti infrastruktury, je odpojená od aplikace a vrstvy modelu domény.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="b6cc8-162">Implementace tyto vzory usnadnit používání imitované úložišť simulaci přístup k databázi.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="b6cc8-163">Obrázek 9 až 18 se zobrazí rozdíly mezi nepoužíváte úložiště (přímo pomocí EF DbContext) a kdy úložiště, které usnadňují model těchto úložiště.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-163">In Figure 9-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![](./media/image19.png)

<span data-ttu-id="b6cc8-164">**Obrázek 9 až 18**.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-164">**Figure 9-18**.</span></span> <span data-ttu-id="b6cc8-165">Použití vlastní úložiště versus prostý DbContext</span><span class="sxs-lookup"><span data-stu-id="b6cc8-165">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="b6cc8-166">Při mocking se více alternativy.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-166">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="b6cc8-167">Může model právě úložiště nebo může model celou pracovní jednotka.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-167">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="b6cc8-168">Obvykle mocking právě úložiště je dostatek a složitost a abstraktní model celou pracovní jednotka není obvykle nutné.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-168">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="b6cc8-169">Později když se zaměříme na aplikační vrstvu, zobrazí se fungování vkládání závislostí v ASP.NET Core a jak jsou implementované při použití úložiště.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-169">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="b6cc8-170">Stručně řečeno vlastní úložiště umožňují snadněji testování kódu pomocí jednotkových testů, které nejsou vliv stav dat vrstvy.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-170">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="b6cc8-171">Pokud spustíte testy, které také přístup k databázi skutečné prostřednictvím rozhraní Entity Framework, nejsou testování částí, ale testy integrace, které jsou mnohem nižší.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-171">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="b6cc8-172">Pokud jste používali DbContext přímo, jenom možnost, kterou byste měli by mohla být spouštění testů jednotek pomocí serveru SQL v paměti s předvídatelný dat pro testování částí.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-172">If you were using DbContext directly, the only choice you would have would be to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="b6cc8-173">Nebude moci řídit mock objektů a falešných dat na úrovni úložiště stejným způsobem.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-173">You would not be able to control mock objects and fake data in the same way at the repository level.</span></span> <span data-ttu-id="b6cc8-174">Samozřejmě může vždy otestovat řadiče MVC.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-174">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="b6cc8-175">EF DbContext a IUnitOfWork doba platnosti instance v vaší kontejner IoC</span><span class="sxs-lookup"><span data-stu-id="b6cc8-175">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="b6cc8-176">Objekt DbContext (zveřejněné jako objekt IUnitOfWork) může být potřeba sdílet mezi více úložiště v rámci stejného oboru požadavku HTTP.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-176">The DbContext object (exposed as an IUnitOfWork object) might need to be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="b6cc8-177">Například to platí při operaci spouštěna musí pracovat s více agregace, ani jednoduše vzhledem k tomu, že používáte více instancí úložiště.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-177">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="b6cc8-178">Je také důležité zmínit, že rozhraní IUnitOfWork je součástí vaší domény vrstvy, není typ EF jádra.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-178">It is also important to mention that the IUnitOfWork interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="b6cc8-179">Aby bylo možné provést, musí mít jeho služby dobu života nastavenu na ServiceLifetime.Scoped instanci objekt DbContext.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-179">In order to do that, the instance of the DbContext object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="b6cc8-180">Toto je výchozí doba života při registraci DbContext s služeb. AddDbContext ve vaší kontejner IoC z metody ConfigureServices souboru Startup.cs v projektu webového rozhraní API ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-180">This is the default lifetime when registering a DbContext with services.AddDbContext in your IoC container from the ConfigureServices method of the Startup.cs file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="b6cc8-181">Následující kód to znázorňuje.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-181">The following code illustrates this.</span></span>

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
                               sqlOptions => sqlOptions.MigrationsAssembly(typeof(Startup).GetTypeInfo().
                                                                                    Assembly.GetName().Name));
      },
      ServiceLifetime.Scoped // Note that Scoped is the default choice
                             // in AddDbContext. It is shown here only for
                             // pedagogic purposes.
      );
}
```

<span data-ttu-id="b6cc8-182">Režim vytváření instancí DbContext by se neměla konfigurovat jako ServiceLifetime.Transient nebo ServiceLifetime.Singleton.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-182">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="b6cc8-183">Doba platnosti instance úložiště v vaší kontejner IoC</span><span class="sxs-lookup"><span data-stu-id="b6cc8-183">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="b6cc8-184">Podobným způsobem musí být v úložišti životnost obvykle nastavená jako oboru (InstancePerLifetimeScope v Autofac).</span><span class="sxs-lookup"><span data-stu-id="b6cc8-184">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="b6cc8-185">Také může být přechodná (InstancePerDependency v Autofac), ale vaše služba bude efektivnější v paměti namapoval při použití vymezená životního cyklu.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-185">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="b6cc8-186">Všimněte si, že pomocí singleton doba platnosti pro úložiště by mohla způsobovat můžete souběžnosti závažné problémy vaší DbContext nastavena na obor životnosti (InstancePerLifetimeScope) (výchozí doba života pro DBContext).</span><span class="sxs-lookup"><span data-stu-id="b6cc8-186">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="b6cc8-187">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="b6cc8-187">Additional resources</span></span>

-   <span data-ttu-id="b6cc8-188">**Implementace úložiště a jednotky pracovních vzorů v aplikaci ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span><span class="sxs-lookup"><span data-stu-id="b6cc8-188">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application**
[*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span></span>

-   <span data-ttu-id="b6cc8-189">**Jonathan Allen. Strategie implementace pro vzor úložiště s platformou Entity Framework, Dapper a řetězec**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span><span class="sxs-lookup"><span data-stu-id="b6cc8-189">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain**
[*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span></span>

-   <span data-ttu-id="b6cc8-190">**Cesaru členka Torre. Porovnávání životnosti služby kontejner IoC jádro ASP.NET s obory instance kontejner Autofac IoC**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="b6cc8-190">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="table-mapping"></a><span data-ttu-id="b6cc8-191">Mapování tabulek</span><span class="sxs-lookup"><span data-stu-id="b6cc8-191">Table mapping</span></span>

<span data-ttu-id="b6cc8-192">Mapování tabulky identifikuje data tabulky, která mají být získaných z a uložit do databáze.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-192">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="b6cc8-193">Dříve jste viděli, jak lze pomocí entity domény (například produktu nebo pořadí doména) Generovat schéma související databáze.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-193">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="b6cc8-194">EF je důrazně uspořádaná kolem koncept *konvence*.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-194">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="b6cc8-195">Konvence adresu otázky typu "Jaký název tabulky bude?"</span><span class="sxs-lookup"><span data-stu-id="b6cc8-195">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="b6cc8-196">nebo "jaké vlastnost je primární klíč?"</span><span class="sxs-lookup"><span data-stu-id="b6cc8-196">or “What property is the primary key?”</span></span> <span data-ttu-id="b6cc8-197">Konvence jsou obvykle založené na běžné názvy – například je typické pro primární klíč jako vlastnost, která končí ID.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-197">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="b6cc8-198">Podle konvence, každá entita se nastavit tak, aby mapovat do tabulky se stejným názvem jako DbSet&lt;TEntity&gt; vlastnost, která zveřejňuje se entita na odvozené kontextu.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-198">By convention, each entity will be set up to map to a table with the same name as the DbSet&lt;TEntity&gt; property that exposes the entity on the derived context.</span></span> <span data-ttu-id="b6cc8-199">Pokud žádné DbSet&lt;TEntity&gt; hodnota je zadaný pro danou entitu, se používá název třídy.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-199">If no DbSet&lt;TEntity&gt; value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="b6cc8-200">Datových poznámek versus rozhraní Fluent API</span><span class="sxs-lookup"><span data-stu-id="b6cc8-200">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="b6cc8-201">Existuje mnoho dalších konvence EF jádra a většina z nich lze změnit pomocí datových poznámek nebo rozhraní Fluent API implementována v rámci metody OnModelCreating.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-201">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="b6cc8-202">Datových poznámek musí použít na třídy modelu entity, sami, což je více obtěžující způsob, jak z hlediska DDD.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-202">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="b6cc8-203">Je to proto, že jsou kontaminujících modelu s anotacemi dat související s databázi infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-203">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="b6cc8-204">Na druhé straně rozhraní Fluent API je pohodlný způsob, jak změnit většina konvence a mapování v rámci vrstvě infrastruktury trvalosti dat, a tak entity model vyčištění a odpojeného od infrastruktury trvalost.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-204">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="b6cc8-205">Rozhraní Fluent API a metody OnModelCreating</span><span class="sxs-lookup"><span data-stu-id="b6cc8-205">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="b6cc8-206">Jak je uvedeno, aby bylo možné změnit konvence a mapování, můžete metody OnModelCreating v třídy DbContext.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-206">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span> 

<span data-ttu-id="b6cc8-207">Řazení mikroslužbu v eShopOnContainers implementuje explicitní mapování a konfigurace v případě potřeby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-207">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities’ configuration ...
}

// At OrderEntityTypeConfiguration.cs from eShopOnContainers
class OrderEntityTypeConfiguration : IEntityTypeConfiguration<Order>
{
    public void Configure(EntityTypeBuilder<Order> orderConfiguration)
    {
            orderConfiguration.ToTable("orders", OrderingContext.DEFAULT_SCHEMA);

            orderConfiguration.HasKey(o => o.Id);

            orderConfiguration.Ignore(b => b.DomainEvents);

            orderConfiguration.Property(o => o.Id)
                .ForSqlServerUseSequenceHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

            //Address Value Object persisted as owned entity type supported since EF Core 2.0
            orderConfiguration.OwnsOne(o => o.Address);

            orderConfiguration.Property<DateTime>("OrderDate").IsRequired();
            orderConfiguration.Property<int?>("BuyerId").IsRequired(false);
            orderConfiguration.Property<int>("OrderStatusId").IsRequired();
            orderConfiguration.Property<int?>("PaymentMethodId").IsRequired(false);
            orderConfiguration.Property<string>("Description").IsRequired(false);

            var navigation = orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));
            
            // DDD Patterns comment:
            //Set as field (New since EF 1.1) to access the OrderItem collection property through its field
            navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

            orderConfiguration.HasOne<PaymentMethod>()
                .WithMany()
                .HasForeignKey("PaymentMethodId")
                .IsRequired(false)
                .OnDelete(DeleteBehavior.Restrict);

            orderConfiguration.HasOne<Buyer>()
                .WithMany()
                .IsRequired(false)
                .HasForeignKey("BuyerId");

            orderConfiguration.HasOne(o => o.OrderStatus)
                .WithMany()
                .HasForeignKey("OrderStatusId");
    }
}
```

<span data-ttu-id="b6cc8-208">Můžete nastavit všechna rozhraní Fluent API mapování v rámci stejné metody OnModelCreating, ale doporučuje se oddílu tento kód a mít více tříd konfigurace, jeden pro každou entitu, jak je znázorněno v příkladu.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-208">You could set all the Fluent API mappings within the same OnModelCreating method, but it is advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="b6cc8-209">Zejména pro zvlášť velké modely se doporučuje mít třídy samostatné konfigurace pro konfiguraci různých entity typů.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-209">Especially for particularly large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="b6cc8-210">V příkladu kód ukazuje několik explicitní deklarace a mapování.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-210">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="b6cc8-211">Ale EF základní konvence tomu mnoho z těchto mapování automaticky, skutečný kód, který je nutné ve vašem případě může být menší.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-211">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>


### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="b6cc8-212">Algoritmus HIS použití/Lo v EF jádra</span><span class="sxs-lookup"><span data-stu-id="b6cc8-212">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="b6cc8-213">Zajímavé aspekt kódu v předchozím příkladu je, že používá [HIS použití/Lo algoritmus](https://vladmihalcea.com/the-hilo-algorithm/) jako strategie generování klíče.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-213">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="b6cc8-214">Algoritmus HIS použití/Lo je užitečné, když potřebujete jedinečné klíče.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-214">The Hi/Lo algorithm is useful when you need unique keys.</span></span> <span data-ttu-id="b6cc8-215">Jako souhrn přiřadí algoritmus HIS použití-u jedinečné identifikátory řádky tabulky při není v závislosti na ukládání řádek v databázi okamžitě.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-215">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="b6cc8-216">Díky tomu můžete začít používat identifikátory hned, jak se stane s standardní sekvenční databázi ID.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-216">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="b6cc8-217">Algoritmus HIS použití/Lo popisuje mechanismus pro generování bezpečné ID na straně klienta a nikoli v databázi.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-217">The Hi/Lo algorithm describes a mechanism for generating safe IDs on the client side rather than in the database.</span></span> <span data-ttu-id="b6cc8-218">*Bezpečné* v tomto kontextu znamená bez kolizí.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-218">*Safe* in this context means without collisions.</span></span> <span data-ttu-id="b6cc8-219">Tento algoritmus je zajímavé z těchto důvodů:</span><span class="sxs-lookup"><span data-stu-id="b6cc8-219">This algorithm is interesting for these reasons:</span></span>

-   <span data-ttu-id="b6cc8-220">Nedochází k přerušení vzoru pracovní jednotky.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-220">It does not break the Unit of Work pattern.</span></span>

-   <span data-ttu-id="b6cc8-221">Nevyžaduje se, že odezev generátory pořadí způsob, jak provést v jiné systémy DBMS.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-221">It does not require round trips the way sequence generators do in other DBMSs.</span></span>

-   <span data-ttu-id="b6cc8-222">Vygeneruje lidského čitelný identifikátor, na rozdíl od techniky, které používají identifikátory GUID.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-222">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="b6cc8-223">Jádro EF podporuje [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) ForSqlServerUseSequenceHiLo metodou, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-223">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the ForSqlServerUseSequenceHiLo method, as shown in the preceding example.</span></span>

### <a name="mapping-fields-instead-of-properties"></a><span data-ttu-id="b6cc8-224">Mapování polí místo vlastnosti</span><span class="sxs-lookup"><span data-stu-id="b6cc8-224">Mapping fields instead of properties</span></span>

<span data-ttu-id="b6cc8-225">Pomocí této funkce dostupné od verze 1.1 základní EF, můžete přímo namapovat sloupce na pole.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-225">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="b6cc8-226">Je možné nechcete použít vlastnosti ve třídě entity a jenom pro mapování sloupce z tabulky na pole.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-226">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="b6cc8-227">Běžně používá pro který by privátní pole pro všechny vnitřní stav, která nemusí být subjekty mimo entity.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-227">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span> 

<span data-ttu-id="b6cc8-228">To provedete pomocí jednoho pole nebo také pomocí kolekcí, jako je třeba `List<>` pole.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-228">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="b6cc8-229">Tento bod již bylo zmíněno dříve když jsme se bavili modelování třídy modelu domény, ale zde se zobrazí, jak se provádí mapování pomocí `PropertyAccessMode.Field` konfigurace zvýrazněných v předchozí kód.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-229">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="using-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="b6cc8-230">Použití stínové vlastnosti v EF jádra, skrytý na úrovni infrastruktury</span><span class="sxs-lookup"><span data-stu-id="b6cc8-230">Using shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="b6cc8-231">Vlastnosti stínové v základní EF jsou vlastnosti, které nejsou k dispozici do třídy modelu entity.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-231">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="b6cc8-232">Hodnoty a stavy tyto vlastnosti jsou zachována výhradně v [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) třídy na úrovni infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-232">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>


## <a name="implementing-the-specification-pattern"></a><span data-ttu-id="b6cc8-233">Implementace vzoru specifikace</span><span class="sxs-lookup"><span data-stu-id="b6cc8-233">Implementing the Specification pattern</span></span>

<span data-ttu-id="b6cc8-234">Zavádí dříve v části návrhu, je vzor specifikace (plným názvem být specifikaci dotazu vzor) vzor návrhu Domain-Driven určená jako místo, kde můžete ukládat definici dotazu s volitelné, řazení a stránkování logiku.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-234">As introduced earlier in the design section, the Specification pattern (its full name would be Query-specification pattern) is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span> <span data-ttu-id="b6cc8-235">Vzor specifikace definuje dotazu v objektu.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-235">The Specification pattern defines a query in an object.</span></span> <span data-ttu-id="b6cc8-236">Chcete-li zapouzdření stránkové dotaz, který hledá některé produkty, například můžete vytvořit specifikaci PagedProduct, která se mají potřebné vstupní parametry (pageNumber pageSize, filtr, atd.).</span><span class="sxs-lookup"><span data-stu-id="b6cc8-236">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="b6cc8-237">Metoda žádné úložiště (obvykle přetížení List()) by pak přijměte ISpecification a spusťte očekávané dotaz založený na této specifikaci.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-237">Then, any Repository’s method (usually a List() overload) would accept an ISpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="b6cc8-238">Následující kód je například obecné specifikace rozhraní [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb).</span><span class="sxs-lookup"><span data-stu-id="b6cc8-238">An example of a generic Specification interface is the following code from [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span> 

```csharp
// GENERIC SPECIFICATION INTERFACE
// https://github.com/dotnet-architecture/eShopOnWeb 

public interface ISpecification<T>
{
    Expression<Func<T, bool>> Criteria { get; }
    List<Expression<Func<T, object>>> Includes { get; }
    List<string> IncludeStrings { get; }
}
```

<span data-ttu-id="b6cc8-239">Potom implementace specifikace obecné základní třídy je následující.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-239">Then, the implementation of a generic specification base class is the following.</span></span>

```csharp
// GENERIC SPECIFICATION IMPLEMENTATION (BASE CLASS)
// https://github.com/dotnet-architecture/eShopOnWeb
 
public abstract class BaseSpecification<T> : ISpecification<T>
{
    public BaseSpecification(Expression<Func<T, bool>> criteria)
    {
        Criteria = criteria;
    }
    public Expression<Func<T, bool>> Criteria { get; }

    public List<Expression<Func<T, object>>> Includes { get; } = 
                                           new List<Expression<Func<T, object>>>();

    public List<string> IncludeStrings { get; } = new List<string>();
 
    protected virtual void AddInclude(Expression<Func<T, object>> includeExpression)
    {
        Includes.Add(includeExpression);
    }
    
    // string-based includes allow for including children of children
    // e.g. Basket.Items.Product
    protected virtual void AddInclude(string includeString)
    {
        IncludeStrings.Add(includeString);
    }
}
```

<span data-ttu-id="b6cc8-240">V následující specifikaci načte košík jedné entity, danou košíku ID nebo ID kupujících, do kterého patří košíku.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-240">The following specification loads a single basket entity given either the basket’s ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="b6cc8-241">Zruší [přes zatížení](https://docs.microsoft.com/en-us/ef/core/querying/related-data) kolekce položky košíku.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-241">It will [eager load](https://docs.microsoft.com/en-us/ef/core/querying/related-data) the basket’s Items collection.</span></span>

```csharp
// SAMPLE QUERY SPECIFICATION IMPLEMENTATION

public class BasketWithItemsSpecification : BaseSpecification<Basket>
{
    public BasketWithItemsSpecification(int basketId)
        : base(b => b.Id == basketId)
    {
        AddInclude(b => b.Items);
    }
    public BasketWithItemsSpecification(string buyerId)
        : base(b => b.BuyerId == buyerId)
    {
        AddInclude(b => b.Items);
    }
}
```

<span data-ttu-id="b6cc8-242">A nakonec se zobrazí pod jak obecné EF úložiště můžete použít tyto specifikace na filtr a eager zatížení dat souvisejících s danou entitu typu T.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-242">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

```csharp
// GENERIC EF REPOSITORY WITH SPECIFICATION
// https://github.com/dotnet-architecture/eShopOnWeb

public IEnumerable<T> List(ISpecification<T> spec)
{
    // fetch a Queryable that includes all expression-based includes
    var queryableResultWithIncludes = spec.Includes
        .Aggregate(_dbContext.Set<T>().AsQueryable(),
            (current, include) => current.Include(include));
 
    // modify the IQueryable to include any string-based include statements
    var secondaryResult = spec.IncludeStrings
        .Aggregate(queryableResultWithIncludes,
            (current, include) => current.Include(include));
 
    // return the result of the query using the specification's criteria expression
    return secondaryResult
                    .Where(spec.Criteria)
                    .AsEnumerable();
}
```
<span data-ttu-id="b6cc8-243">Kromě zapouzdřením filtrování logiku, specifikace zadejte obrazec data, která mají být vráceny, včetně vlastnosti, které k naplnění.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-243">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span> 

<span data-ttu-id="b6cc8-244">I když nepodporujeme doporučené vrácení IQueryable z úložiště, je v pořádku perfektně jejich použití v rámci úložiště vytvořit sadu výsledků.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-244">Although we don't recommended to return IQueryable from a repository, it’s perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="b6cc8-245">Zobrazí se tento postup použít v seznamu metodu výše, která používá zprostředkující IQueryable výrazy k sestavení dotazu seznamu zahrnuje před provedením dotazu s kritérii v specifikaci na posledním řádku.</span><span class="sxs-lookup"><span data-stu-id="b6cc8-245">You can see this approach used in the List method above, which uses intermediate IQueryable expressions to build up the query’s list of includes before executing the query with the specification’s criteria on the last line.</span></span>


#### <a name="additional-resources"></a><span data-ttu-id="b6cc8-246">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="b6cc8-246">Additional resources</span></span>

-   <span data-ttu-id="b6cc8-247">**Mapování tabulek**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span><span class="sxs-lookup"><span data-stu-id="b6cc8-247">**Table Mapping**
[*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span></span>

-   <span data-ttu-id="b6cc8-248">**Použití HiLo ke generování klíče Entity Framework Core**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span><span class="sxs-lookup"><span data-stu-id="b6cc8-248">**Use HiLo to generate keys with Entity Framework Core**
[*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span></span>

-   <span data-ttu-id="b6cc8-249">**Základní pole**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span><span class="sxs-lookup"><span data-stu-id="b6cc8-249">**Backing Fields**
[*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span></span>

-   <span data-ttu-id="b6cc8-250">**Steve Smith. Obsah zapouzdřeného kolekcí v Entity Framework Core**
    [*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)</span><span class="sxs-lookup"><span data-stu-id="b6cc8-250">**Steve Smith. Encapsulated Collections in Entity Framework Core**
[*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)</span></span>

-   <span data-ttu-id="b6cc8-251">**Stínové vlastnosti**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="b6cc8-251">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="b6cc8-252">**Specifikace vzor**
    [*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)</span><span class="sxs-lookup"><span data-stu-id="b6cc8-252">**The Specification pattern**
[*http://deviq.com/specification-pattern/*](http://deviq.com/specification-pattern/)</span></span>
    

>[!div class="step-by-step"]
<span data-ttu-id="b6cc8-253">[Předchozí](infrastructure-persistence-layer-design.md)
[další](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="b6cc8-253">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>
