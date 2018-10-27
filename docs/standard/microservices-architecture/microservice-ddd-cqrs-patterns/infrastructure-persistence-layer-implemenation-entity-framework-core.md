---
title: Implementace vrstvy trvalosti infrastruktury pomocí Entity Framework Core
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Implementace vrstvy trvalosti infrastruktury pomocí Entity Framework Core
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/12/2017
ms.openlocfilehash: 663515e0a863ef703006df0f96b4bc8a2976ca78
ms.sourcegitcommit: 9bd8f213b50f0e1a73e03bd1e840c917fbd6d20a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/25/2018
ms.locfileid: "50042802"
---
# <a name="implementing-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="1fd26-103">Implementace vrstvy trvalosti infrastruktury pomocí Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="1fd26-103">Implementing the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="1fd26-104">Při použití relačními databázemi jako SQL Server, Oracle nebo PostgreSQL doporučený postup je implementace vrstvy trvalosti založené na Entity Framework (EF).</span><span class="sxs-lookup"><span data-stu-id="1fd26-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="1fd26-105">EF podporuje LINQ a poskytuje objektů se silným typem pro váš model, jakož i zjednodušené trvalost do databáze.</span><span class="sxs-lookup"><span data-stu-id="1fd26-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="1fd26-106">Entity Framework už dlouho jako součást rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="1fd26-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="1fd26-107">Pokud používáte .NET Core, měli byste použít také Entity Framework Core, která běží na Windows nebo Linuxem v stejným způsobem jako .NET Core.</span><span class="sxs-lookup"><span data-stu-id="1fd26-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="1fd26-108">EF Core je kompletní revize Entity Framework, prováděné s mnohem menší nároky na místo a důležitá vylepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="1fd26-108">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="1fd26-109">Úvod do Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="1fd26-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="1fd26-110">Entity Framework (EF) Core je odlehčený, rozšiřitelné, a multiplatformní verze oblíbených dat Entity Framework přístup k technologii.</span><span class="sxs-lookup"><span data-stu-id="1fd26-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="1fd26-111">Byla zavedená s .NET Core v polovině 2016.</span><span class="sxs-lookup"><span data-stu-id="1fd26-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="1fd26-112">Úvod do EF Core je již k dispozici v dokumentaci společnosti Microsoft, tady jednoduše poskytujeme odkazy k těmto informacím.</span><span class="sxs-lookup"><span data-stu-id="1fd26-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="1fd26-113">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="1fd26-113">Additional resources</span></span>

-   <span data-ttu-id="1fd26-114">**Entity Framework Core**
    [*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span><span class="sxs-lookup"><span data-stu-id="1fd26-114">**Entity Framework Core**
[*https://docs.microsoft.com/ef/core/*](https://docs.microsoft.com/ef/core/)</span></span>

-   <span data-ttu-id="1fd26-115">**Začínáme s ASP.NET Core a Entity Framework Core pomocí sady Visual Studio**
    [*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span><span class="sxs-lookup"><span data-stu-id="1fd26-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio**
[*https://docs.microsoft.com/aspnet/core/data/ef-mvc/*](https://docs.microsoft.com/aspnet/core/data/ef-mvc/)</span></span>

-   <span data-ttu-id="1fd26-116">**Třídy DbContext**
    [*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span><span class="sxs-lookup"><span data-stu-id="1fd26-116">**DbContext Class**
[*https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext*](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.dbcontext)</span></span>

-   <span data-ttu-id="1fd26-117">**Porovnání EF Core a EF6.x**
    [*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span><span class="sxs-lookup"><span data-stu-id="1fd26-117">**Compare EF Core & EF6.x**
[*https://docs.microsoft.com/ef/efcore-and-ef6/index*](https://docs.microsoft.com/ef/efcore-and-ef6/index)</span></span>

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="1fd26-118">Infrastruktura v Entity Framework Core z hlediska DDD</span><span class="sxs-lookup"><span data-stu-id="1fd26-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="1fd26-119">Z DDD hlediska, je důležité funkce EF umožňuje používat entity domény POCO, označuje se taky v, řečeno terminologií EF jako POCO *založeno na kódu entity*.</span><span class="sxs-lookup"><span data-stu-id="1fd26-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="1fd26-120">Pokud používáte entity domény POCO, vaše doménové třídy modelu jsou ignorujících, následující [trvalost neznalosti](https://deviq.com/persistence-ignorance/) a [infrastruktury neznalosti](https://ayende.com/blog/3137/infrastructure-ignorance) zásady.</span><span class="sxs-lookup"><span data-stu-id="1fd26-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](https://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="1fd26-121">Za vzorů DDD by měl zapouzdření domény chování a pravidel v rámci třídy entita, takže ho můžete řídit výstupních podmínek, ověření a pravidla při přístupu k žádné kolekce.</span><span class="sxs-lookup"><span data-stu-id="1fd26-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="1fd26-122">Proto není vhodné v DDD umožní veřejný přístup ke kolekcím podřízené entity nebo hodnota objekty.</span><span class="sxs-lookup"><span data-stu-id="1fd26-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="1fd26-123">Místo toho chcete vystavit metody, které řídí, kdy a jak můžete aktualizovat pole a kolekce vlastností, a jaké chování a akce dojde, pokud k tomu dojde.</span><span class="sxs-lookup"><span data-stu-id="1fd26-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="1fd26-124">Od verze EF Core 1.1 splňovat tyto požadavky na DDD může mít jednoduchého pole v entitách místo veřejné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1fd26-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="1fd26-125">Pokud nechcete, aby pole entity externě dostupná, můžete vytvořit pouze atribut nebo pole namísto vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1fd26-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="1fd26-126">Můžete také použít privátní vlastnost Setter.</span><span class="sxs-lookup"><span data-stu-id="1fd26-126">You can also use private property setters.</span></span>

<span data-ttu-id="1fd26-127">Podobným způsobem, můžete teď mít přístup jen pro čtení ke kolekcím s použitím veřejné vlastnosti typu `IReadOnlyCollection<T>`, který je zálohovaný díky člena soukromé pole pro kolekci (podobně jako `List<T>`) ve vaší entitě, která závisí na EF trvalosti.</span><span class="sxs-lookup"><span data-stu-id="1fd26-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="1fd26-128">Předchozí verze rozhraní Entity Framework požadované vlastnosti kolekce pro podporu `ICollection<T>`, který znamenalo, že každý vývojář horizontálních oddílů pomocí třídy nadřazená entita může přidat nebo odebrat položky prostřednictvím její vlastnosti kolekce.</span><span class="sxs-lookup"><span data-stu-id="1fd26-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="1fd26-129">Tato možnost by proti doporučené vzory v DDD.</span><span class="sxs-lookup"><span data-stu-id="1fd26-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="1fd26-130">Můžete použít soukromé kolekce při zobrazení jen pro čtení `IReadOnlyCollection<T>` objektu, jak je znázorněno v následujícím příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="1fd26-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

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

<span data-ttu-id="1fd26-131">Všimněte si, že `OrderItems` vlastnosti lze přistupovat pouze jako jen pro čtení pomocí `IReadOnlyCollection<OrderItem>`.</span><span class="sxs-lookup"><span data-stu-id="1fd26-131">Note that the `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="1fd26-132">Tento typ je jen pro čtení, takže je chráněný proti externí pravidelné aktualizace.</span><span class="sxs-lookup"><span data-stu-id="1fd26-132">This type is read-only so it is protected against regular external updates.</span></span> 

<span data-ttu-id="1fd26-133">EF Core nabízí způsob, jak mapovat model domény do fyzické databáze bez "kontaminujících" doménový model.</span><span class="sxs-lookup"><span data-stu-id="1fd26-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="1fd26-134">Je čistě .NET objektů POCO kódu, protože akce mapování je implementována v vrstvy trvalosti.</span><span class="sxs-lookup"><span data-stu-id="1fd26-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="1fd26-135">V této akci mapování budete muset nakonfigurovat mapování polí pro databází.</span><span class="sxs-lookup"><span data-stu-id="1fd26-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="1fd26-136">V následujícím příkladu je to metoda OnModelCreating říká zvýrazněný kód EF Core pro přístup k vlastnosti OrderItems prostřednictvím jeho pole.</span><span class="sxs-lookup"><span data-stu-id="1fd26-136">In the following example of an OnModelCreating method, the highlighted code tells EF Core to access the OrderItems property through its field.</span></span>

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

<span data-ttu-id="1fd26-137">Při použití polí místo vlastností OrderItem entity je trvalý stejně, jako kdyby byla seznam&lt;OrderItem&gt; vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1fd26-137">When you use fields instead of properties, the OrderItem entity is persisted just as if it had a List&lt;OrderItem&gt; property.</span></span> <span data-ttu-id="1fd26-138">Však poskytuje jeden přistupující objekt, `AddOrderItem` metoda pro přidání nových položek do pořadí.</span><span class="sxs-lookup"><span data-stu-id="1fd26-138">However, it exposes a single accessor, the `AddOrderItem` method for adding new items to the order.</span></span> <span data-ttu-id="1fd26-139">V důsledku toho chování a data jsou spojených dohromady a budou konzistentní v rámci jakýkoli kód aplikace, který používá model domény.</span><span class="sxs-lookup"><span data-stu-id="1fd26-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implementing-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="1fd26-140">Implementace vlastního úložiště s Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="1fd26-140">Implementing custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="1fd26-141">Na úrovni implementace úložiště je jednoduše třídu s kódem trvalosti dat koordinuje přes určitou jednotku práce (DBContext v EF Core) při provádění aktualizací, jak je znázorněno v následující třídy:</span><span class="sxs-lookup"><span data-stu-id="1fd26-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

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

<span data-ttu-id="1fd26-142">Všimněte si, že rozhraní IBuyerRepository pochází z vrstvě doménového modelu jako kontrakt.</span><span class="sxs-lookup"><span data-stu-id="1fd26-142">Note that the IBuyerRepository interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="1fd26-143">Implementace úložiště se však provádí na stálost a vrstvy infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="1fd26-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="1fd26-144">EF DbContext prochází konstruktoru pomocí vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="1fd26-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="1fd26-145">Je sdílen mezi více úložišť v rámci stejného oboru požadavku HTTP, díky výchozí dobu života (ServiceLifetime.Scoped) v kontejneru IoC (což lze také explicitně nastavit službami. AddDbContext&lt;&gt;).</span><span class="sxs-lookup"><span data-stu-id="1fd26-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (ServiceLifetime.Scoped) in the IoC container (which can also be explicitly set with services.AddDbContext&lt;&gt;).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="1fd26-146">Metody k implementaci v úložišti (aktualizace nebo transakce a dotazy)</span><span class="sxs-lookup"><span data-stu-id="1fd26-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="1fd26-147">V rámci každé třídy úložiště byste měli umístit trvalost metody, které aktualizuje stav entity obsažené podle jeho související agregace.</span><span class="sxs-lookup"><span data-stu-id="1fd26-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="1fd26-148">Mějte na paměti, že je relace 1: 1 mezi agregaci a její související úložiště.</span><span class="sxs-lookup"><span data-stu-id="1fd26-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="1fd26-149">Vezměte v úvahu, že objekt agregační kořenové entity může být vloženy podřízené entity v rámci jeho EF grafu.</span><span class="sxs-lookup"><span data-stu-id="1fd26-149">Take into account that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="1fd26-150">Kupující například může mít více způsoby platby jako související podřízené entity.</span><span class="sxs-lookup"><span data-stu-id="1fd26-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="1fd26-151">Vzhledem k tomu, že přístup k řazení mikroslužeb v aplikaci eShopOnContainers také podle CQS/modelu CQRS, většina dotazů, které nejsou implementované ve vlastní úložiště.</span><span class="sxs-lookup"><span data-stu-id="1fd26-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="1fd26-152">Vývojáři moci svobodně vytvářet dotazy a spojení, které potřebují pro prezentační vrstva bez omezení stanovené agregace, vlastní úložiště za agregaci a DDD obecně.</span><span class="sxs-lookup"><span data-stu-id="1fd26-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="1fd26-153">Většina vlastních úložišť navrhl Tato příručka má několik aktualizací nebo transakční metody, ale pouze metody dotazu nutná, aby se data aktualizovat.</span><span class="sxs-lookup"><span data-stu-id="1fd26-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="1fd26-154">Například BuyerRepository úložiště implementuje metody asynchronně vyhledá, protože aplikace je potřeba vědět, jestli konkrétní kupujících existuje. před vytvořením nové odběratele související s objednávkou.</span><span class="sxs-lookup"><span data-stu-id="1fd26-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="1fd26-155">Však jsou implementované metody skutečné dotazu zobrazíte data k odeslání do prezentační vrstvy nebo klientské aplikace, jak je uvedeno v modelu CQRS dotazů založených na použití Dapperem flexibilní dotazy.</span><span class="sxs-lookup"><span data-stu-id="1fd26-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="1fd26-156">Používání vlastního úložiště versus přímo pomocí EF DbContext</span><span class="sxs-lookup"><span data-stu-id="1fd26-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="1fd26-157">Třídy DbContext v Entity Framework je podle vzorů pracovní jednotky a úložiště a můžou používat přímo v kódu, například z kontroler ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="1fd26-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="1fd26-158">To znamená tak, jak můžete vytvořit nejjednodušší kód, stejně jako v katalogu mikroslužby CRUD v aplikaci eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="1fd26-158">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="1fd26-159">V případech, kde chcete nejjednodušší kód je to možné můžete přímo použít třídy DbContext, stejně jako mnoho vývojářů.</span><span class="sxs-lookup"><span data-stu-id="1fd26-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="1fd26-160">Nicméně implementace vlastního úložiště poskytuje několik výhod při provádění složitějších mikroslužby nebo aplikace.</span><span class="sxs-lookup"><span data-stu-id="1fd26-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="1fd26-161">Tyto vzory se dají pracovní jednotky a úložiště jsou určeny k zapouzdření vrstvy trvalosti infrastruktury, takže je oddělený od aplikace a vrstvy modelu domény.</span><span class="sxs-lookup"><span data-stu-id="1fd26-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="1fd26-162">Implementaci těchto vzorců můžete využívají mock úložišť, které simulují přístup k databázi.</span><span class="sxs-lookup"><span data-stu-id="1fd26-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="1fd26-163">Obrázek 9-18 se zobrazí rozdíly mezi bez použití úložiště (přímo pomocí EF DbContext) oproti použití úložiště, které usnadňují napodobení taková úložiště.</span><span class="sxs-lookup"><span data-stu-id="1fd26-163">In Figure 9-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![](./media/image19.png)

<span data-ttu-id="1fd26-164">**Obrázek 9-18**.</span><span class="sxs-lookup"><span data-stu-id="1fd26-164">**Figure 9-18**.</span></span> <span data-ttu-id="1fd26-165">Používání vlastního úložiště a prostý DbContext</span><span class="sxs-lookup"><span data-stu-id="1fd26-165">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="1fd26-166">Při vytvoření modelu se více alternativy.</span><span class="sxs-lookup"><span data-stu-id="1fd26-166">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="1fd26-167">Může napodobení jenom úložiště nebo může napodobení celou jednotku práce.</span><span class="sxs-lookup"><span data-stu-id="1fd26-167">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="1fd26-168">Obvykle napodobování jenom úložiště je dostatek a složitosti se abstraktní a napodobení celou jednotku práce obvykle není potřeba.</span><span class="sxs-lookup"><span data-stu-id="1fd26-168">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="1fd26-169">Později když jsme se zaměřit na aplikační vrstvu, zobrazí se fungování injektáž závislostí v ASP.NET Core a jak je implementován při použití úložiště.</span><span class="sxs-lookup"><span data-stu-id="1fd26-169">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="1fd26-170">Stručně řečeno vlastní úložiště využijete k otestování kódu snadněji s testy jednotek, které nejsou ovlivněny stav dat vrstvy.</span><span class="sxs-lookup"><span data-stu-id="1fd26-170">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="1fd26-171">Pokud spouštíte testy, které také přístup k databázi skutečné přes rozhraní Entity Framework, nejsou testy jednotek, ale integrační testy, které jsou mnohem pomalejší.</span><span class="sxs-lookup"><span data-stu-id="1fd26-171">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="1fd26-172">Pokud jste používali DbContext přímo, pouze možnost, kterou byste měli by pro spouštění testů jednotek s použitím SQL serveru v paměti s předvídatelným dat pro testování částí.</span><span class="sxs-lookup"><span data-stu-id="1fd26-172">If you were using DbContext directly, the only choice you would have would be to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="1fd26-173">Nebude moct řídit mock objektů a falešných dat stejně jako na úrovni úložiště.</span><span class="sxs-lookup"><span data-stu-id="1fd26-173">You would not be able to control mock objects and fake data in the same way at the repository level.</span></span> <span data-ttu-id="1fd26-174">Samozřejmě může vždy testovací kontrolery MVC.</span><span class="sxs-lookup"><span data-stu-id="1fd26-174">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="1fd26-175">Životnost instance EF DbContext a IUnitOfWork ve vašem kontejneru IoC</span><span class="sxs-lookup"><span data-stu-id="1fd26-175">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="1fd26-176">Objekt DbContext (vystavena jako objekt IUnitOfWork) může být nutné sdílet mezi více úložišť v rámci stejného oboru požadavku HTTP.</span><span class="sxs-lookup"><span data-stu-id="1fd26-176">The DbContext object (exposed as an IUnitOfWork object) might need to be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="1fd26-177">Například to platí při prováděnou operace musí zacházet s více agregace nebo jednoduše vzhledem k tomu, že používáte více instancí úložiště.</span><span class="sxs-lookup"><span data-stu-id="1fd26-177">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="1fd26-178">Je také důležité zmínit, že rozhraní IUnitOfWork je součástí domény vrstvy, není typem EF Core.</span><span class="sxs-lookup"><span data-stu-id="1fd26-178">It is also important to mention that the IUnitOfWork interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="1fd26-179">K tomu, musí mít jeho služby dobu života nastavenu na ServiceLifetime.Scoped instanci objektu DbContext.</span><span class="sxs-lookup"><span data-stu-id="1fd26-179">In order to do that, the instance of the DbContext object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="1fd26-180">Toto je výchozí doba života, při registraci DbContext pomocí služby. AddDbContext ve vašem kontejneru IoC z metody ConfigureServices Startup.cs soubor v projektu webového rozhraní API ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="1fd26-180">This is the default lifetime when registering a DbContext with services.AddDbContext in your IoC container from the ConfigureServices method of the Startup.cs file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="1fd26-181">Následující kód to znázorňuje.</span><span class="sxs-lookup"><span data-stu-id="1fd26-181">The following code illustrates this.</span></span>

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

<span data-ttu-id="1fd26-182">Režim instanciace DbContext by neměl být nakonfigurován jako ServiceLifetime.Transient nebo ServiceLifetime.Singleton.</span><span class="sxs-lookup"><span data-stu-id="1fd26-182">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="1fd26-183">Životnost instance úložiště ve vašem kontejneru IoC</span><span class="sxs-lookup"><span data-stu-id="1fd26-183">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="1fd26-184">Podobným způsobem musí být obvykle nastavená doba života úložiště jako s vymezeným oborem (InstancePerLifetimeScope v Autofac).</span><span class="sxs-lookup"><span data-stu-id="1fd26-184">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="1fd26-185">Také může být přechodná (InstancePerDependency Autofac), ale vaše služba bude mnohem efektivnější, pokud jde o paměti, při použití s vymezeným oborem životnost.</span><span class="sxs-lookup"><span data-stu-id="1fd26-185">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="1fd26-186">Všimněte si, že pomocí typu singleton životnost úložiště, které může způsobit vážné souběžnosti problémy Pokud váš kontext databáze je nastavena na obor (InstancePerLifetimeScope) životnost (výchozí doba života pro DBContext).</span><span class="sxs-lookup"><span data-stu-id="1fd26-186">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="1fd26-187">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="1fd26-187">Additional resources</span></span>

-   <span data-ttu-id="1fd26-188">**Implementace úložiště a jednotky pracovních vzorů v aplikaci ASP.NET MVC**
    [*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span><span class="sxs-lookup"><span data-stu-id="1fd26-188">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application**
[*https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application*](https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application)</span></span>

-   <span data-ttu-id="1fd26-189">**Jonathan Allen. Strategie implementace pro model úložiště s Dapper, Entity Framework a řetězce**
    [*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span><span class="sxs-lookup"><span data-stu-id="1fd26-189">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain**
[*https://www.infoq.com/articles/repository-implementation-strategies*](https://www.infoq.com/articles/repository-implementation-strategies)</span></span>

-   <span data-ttu-id="1fd26-190">**De la Torre Cesarovi. Porovnání doby života služby kontejner ASP.NET Core IoC s obory instance kontejner Autofac IoC**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="1fd26-190">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="table-mapping"></a><span data-ttu-id="1fd26-191">Mapování tabulek</span><span class="sxs-lookup"><span data-stu-id="1fd26-191">Table mapping</span></span>

<span data-ttu-id="1fd26-192">Mapování tabulek identifikuje měl posílat dotaz z tabulky dat a uložit do databáze.</span><span class="sxs-lookup"><span data-stu-id="1fd26-192">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="1fd26-193">Dříve jste viděli použití domény entity (například doména produktu nebo pořadí) k vygenerování schématu databáze.</span><span class="sxs-lookup"><span data-stu-id="1fd26-193">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="1fd26-194">EF důrazně navržené s ohledem na konceptu *konvence*.</span><span class="sxs-lookup"><span data-stu-id="1fd26-194">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="1fd26-195">Konvence adresu otázky typu "Jaký název tabulky bude?"</span><span class="sxs-lookup"><span data-stu-id="1fd26-195">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="1fd26-196">nebo "co vlastnost je primárním klíčem?"</span><span class="sxs-lookup"><span data-stu-id="1fd26-196">or “What property is the primary key?”</span></span> <span data-ttu-id="1fd26-197">Konvence většinou vycházejí konvenční názvy, například je typické pro primární klíč, bude vlastnost, která končí ID.</span><span class="sxs-lookup"><span data-stu-id="1fd26-197">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="1fd26-198">Podle konvence, každá entita se nastavit tak, aby mapovat do tabulky se stejným názvem jako DbSet&lt;TEntity&gt; vlastnost, která zveřejňuje entity v kontextu odvozené.</span><span class="sxs-lookup"><span data-stu-id="1fd26-198">By convention, each entity will be set up to map to a table with the same name as the DbSet&lt;TEntity&gt; property that exposes the entity on the derived context.</span></span> <span data-ttu-id="1fd26-199">Pokud žádné DbSet&lt;TEntity&gt; hodnota je k dispozici pro danou entitu, se používá název třídy.</span><span class="sxs-lookup"><span data-stu-id="1fd26-199">If no DbSet&lt;TEntity&gt; value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="1fd26-200">Datové poznámky a rozhraní Fluent API</span><span class="sxs-lookup"><span data-stu-id="1fd26-200">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="1fd26-201">Existuje mnoho dalších konvence EF Core a většina z nich můžete změnit pomocí anotacemi dat nebo Fluent API implementovaná v metodě OnModelCreating.</span><span class="sxs-lookup"><span data-stu-id="1fd26-201">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="1fd26-202">Anotací dat musí být použita u tříd modelu entity, sami, což je víc obtěžující způsob, jak z hlediska DDD.</span><span class="sxs-lookup"><span data-stu-id="1fd26-202">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="1fd26-203">Je to proto, že jsou kontaminujících modelu s anotacemi dat související s infrastrukturou databáze.</span><span class="sxs-lookup"><span data-stu-id="1fd26-203">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="1fd26-204">Na druhé straně rozhraní Fluent API je pohodlný způsob, jak změnit většina konvence a mapování v rámci vaší vrstvu infrastruktury trvalosti dat, takže modelu entity budou čisté a oddělený od infrastruktury trvalosti.</span><span class="sxs-lookup"><span data-stu-id="1fd26-204">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="1fd26-205">Rozhraní Fluent API a OnModelCreating – metoda</span><span class="sxs-lookup"><span data-stu-id="1fd26-205">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="1fd26-206">Jak už bylo zmíněno, chcete-li změnit mapování a konvence můžete OnModelCreating metodu do třídy DbContext.</span><span class="sxs-lookup"><span data-stu-id="1fd26-206">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span> 

<span data-ttu-id="1fd26-207">Pořadí mikroslužeb v aplikaci eShopOnContainers implementuje explicitního mapování a konfigurace, pokud je nepotřebujete, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="1fd26-207">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

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

<span data-ttu-id="1fd26-208">Můžete nastavit všechna rozhraní Fluent API mapování v rámci stejné metody OnModelCreating, ale doporučuje se rozdělit tento kód a mít více tříd konfigurace, jeden pro každou entitu, jak je znázorněno v příkladu.</span><span class="sxs-lookup"><span data-stu-id="1fd26-208">You could set all the Fluent API mappings within the same OnModelCreating method, but it is advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="1fd26-209">Zejména u modelů, zejména velkých je vhodné mít samostatné konfigurace třídy pro konfiguraci typy různých entit.</span><span class="sxs-lookup"><span data-stu-id="1fd26-209">Especially for particularly large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="1fd26-210">Kódem v příkladu ukazuje několik explicitní deklarace a mapování.</span><span class="sxs-lookup"><span data-stu-id="1fd26-210">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="1fd26-211">EF Core konvence však mnohé z těchto mapování automaticky, takže skutečný kód, který je třeba ve vašem případě může být menší.</span><span class="sxs-lookup"><span data-stu-id="1fd26-211">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>


### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="1fd26-212">Dobrý den/Lo algoritmus v EF Core</span><span class="sxs-lookup"><span data-stu-id="1fd26-212">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="1fd26-213">Zajímavým aspektem kód v předchozím příkladu je, že používá [Dobrý den/Lo algoritmus](https://vladmihalcea.com/the-hilo-algorithm/) jako strategie generování klíčů.</span><span class="sxs-lookup"><span data-stu-id="1fd26-213">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="1fd26-214">Dobrý den/Lo algoritmus je užitečné, když budete potřebovat jedinečné klíče.</span><span class="sxs-lookup"><span data-stu-id="1fd26-214">The Hi/Lo algorithm is useful when you need unique keys.</span></span> <span data-ttu-id="1fd26-215">Jako souhrn algoritmus Hi-Lo přiřadí jedinečné identifikátory řádky tabulky během není v závislosti na tom okamžitě ukládání řádku v databázi.</span><span class="sxs-lookup"><span data-stu-id="1fd26-215">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="1fd26-216">Tímto způsobem můžete rovnou začít využívat identifikátory, jak se stane s ID regulární sekvenční databází.</span><span class="sxs-lookup"><span data-stu-id="1fd26-216">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="1fd26-217">Dobrý den/Lo algoritmus popisuje mechanismus pro generování bezpečné ID na straně klienta, nikoli v databázi.</span><span class="sxs-lookup"><span data-stu-id="1fd26-217">The Hi/Lo algorithm describes a mechanism for generating safe IDs on the client side rather than in the database.</span></span> <span data-ttu-id="1fd26-218">*Bezpečné* v tomto kontextu označuje bez kolizí.</span><span class="sxs-lookup"><span data-stu-id="1fd26-218">*Safe* in this context means without collisions.</span></span> <span data-ttu-id="1fd26-219">Tento algoritmus je zajímavé z těchto důvodů:</span><span class="sxs-lookup"><span data-stu-id="1fd26-219">This algorithm is interesting for these reasons:</span></span>

-   <span data-ttu-id="1fd26-220">Nedojde k poškození vzor jednotkou práce.</span><span class="sxs-lookup"><span data-stu-id="1fd26-220">It does not break the Unit of Work pattern.</span></span>

-   <span data-ttu-id="1fd26-221">Nevyžaduje se, že má zpáteční převod generátorů pořadí způsob, jak provést v jiných systémech DBMS.</span><span class="sxs-lookup"><span data-stu-id="1fd26-221">It does not require round trips the way sequence generators do in other DBMSs.</span></span>

-   <span data-ttu-id="1fd26-222">Generuje lidské čitelné identifikátor, na rozdíl od techniky, které používají identifikátory GUID.</span><span class="sxs-lookup"><span data-stu-id="1fd26-222">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="1fd26-223">EF Core podporuje [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) ForSqlServerUseSequenceHiLo metodou, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="1fd26-223">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the ForSqlServerUseSequenceHiLo method, as shown in the preceding example.</span></span>

### <a name="mapping-fields-instead-of-properties"></a><span data-ttu-id="1fd26-224">Mapování polí místo vlastností</span><span class="sxs-lookup"><span data-stu-id="1fd26-224">Mapping fields instead of properties</span></span>

<span data-ttu-id="1fd26-225">Pomocí této funkce dostupné od verze EF Core 1.1, můžete přímo namapovat sloupce pole.</span><span class="sxs-lookup"><span data-stu-id="1fd26-225">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="1fd26-226">Je možné používat vlastnosti ve třídě entity a pouze pro mapování sloupců z tabulky na pole.</span><span class="sxs-lookup"><span data-stu-id="1fd26-226">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="1fd26-227">Běžným účelem pro, který by privátní pole pro všechny vnitřní stav, které není potřeba přistupovat z mimo entitu.</span><span class="sxs-lookup"><span data-stu-id="1fd26-227">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span> 

<span data-ttu-id="1fd26-228">Můžete udělat pomocí jednoho pole nebo také s kolekcemi, jako je třeba `List<>` pole.</span><span class="sxs-lookup"><span data-stu-id="1fd26-228">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="1fd26-229">Tento bod jsem už zmínili dřív když jsme probírali modelování tříd modelu domény, ale tady vidíte, jak se pomocí provádí mapování `PropertyAccessMode.Field` konfigurace zvýrazněných v předchozím kódu.</span><span class="sxs-lookup"><span data-stu-id="1fd26-229">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="using-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="1fd26-230">Použití stínové vlastnosti v EF Core, skrytý na úrovni infrastruktury</span><span class="sxs-lookup"><span data-stu-id="1fd26-230">Using shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="1fd26-231">Stínové vlastnosti v EF Core jsou vlastnosti, které neexistují v třídě modelu entity.</span><span class="sxs-lookup"><span data-stu-id="1fd26-231">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="1fd26-232">Hodnoty a stavy z těchto vlastností jsou zachovány v čistě [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) třídy na úrovni infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="1fd26-232">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>


## <a name="implementing-the-specification-pattern"></a><span data-ttu-id="1fd26-233">Implementace vzoru specifikace</span><span class="sxs-lookup"><span data-stu-id="1fd26-233">Implementing the Specification pattern</span></span>

<span data-ttu-id="1fd26-234">Zavedeném dříve v části návrhu, vzor specifikace (úplného názvu bude vzor dotazu specification) je vzor Domain-Driven Design navržený místem, kde můžete ukládat definice dotazu s volitelné, řazení a stránkování logiku.</span><span class="sxs-lookup"><span data-stu-id="1fd26-234">As introduced earlier in the design section, the Specification pattern (its full name would be Query-specification pattern) is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span> <span data-ttu-id="1fd26-235">Vzor specifikace definuje dotaz v objektu.</span><span class="sxs-lookup"><span data-stu-id="1fd26-235">The Specification pattern defines a query in an object.</span></span> <span data-ttu-id="1fd26-236">Například pokud chcete zapouzdřit stránkovaného dotaz, který vyhledá některé produkty můžete vytvořit PagedProduct specifikace, která přebírá nezbytné vstupní parametry (pageNumber pageSize, filter, atd.).</span><span class="sxs-lookup"><span data-stu-id="1fd26-236">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="1fd26-237">Metoda v libovolném adresáři (obvykle List() přetížení) by potom přijměte ISpecification a spustíte očekávané dotaz založený na specifikaci.</span><span class="sxs-lookup"><span data-stu-id="1fd26-237">Then, any Repository’s method (usually a List() overload) would accept an ISpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="1fd26-238">Příklad obecného rozhraní specifikace je následující kód z [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb).</span><span class="sxs-lookup"><span data-stu-id="1fd26-238">An example of a generic Specification interface is the following code from [eShopOnweb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span> 

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

<span data-ttu-id="1fd26-239">Implementace obecný specifikace základní třídy je následující.</span><span class="sxs-lookup"><span data-stu-id="1fd26-239">Then, the implementation of a generic specification base class is the following.</span></span>

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

<span data-ttu-id="1fd26-240">Specifikace načte jeden nákupní košík entity košíku ID nebo ID kupujících, ke kterému patří košíku.</span><span class="sxs-lookup"><span data-stu-id="1fd26-240">The following specification loads a single basket entity given either the basket’s ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="1fd26-241">Bude [nemůžou dočkat, až zatížení](https://docs.microsoft.com/ef/core/querying/related-data) kolekce položek nákupním košíku.</span><span class="sxs-lookup"><span data-stu-id="1fd26-241">It will [eager load](https://docs.microsoft.com/ef/core/querying/related-data) the basket’s Items collection.</span></span>

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

<span data-ttu-id="1fd26-242">A nakonec můžete vidět dole použití obecného úložiště EF specifikace filtru a zatížení eager data související s danou entitu typu T.</span><span class="sxs-lookup"><span data-stu-id="1fd26-242">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

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
<span data-ttu-id="1fd26-243">Kromě zapouzdření logiku filtrování, specifikace určit tvar dat, který se má vrátit, včetně vlastnosti, které chcete vyplnit.</span><span class="sxs-lookup"><span data-stu-id="1fd26-243">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span> 

<span data-ttu-id="1fd26-244">I když není doporučenou vrátit IQueryable z úložiště, je naprosto bez problémů se dají použít v rámci tohoto úložiště k vytvoření sady výsledků.</span><span class="sxs-lookup"><span data-stu-id="1fd26-244">Although we don't recommended to return IQueryable from a repository, it’s perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="1fd26-245">Zobrazí se tento přístup používá se v seznamu výše uvedené, metody, která používá přechodných výrazů IQueryable k vytvoření dotazu na seznam zahrnuje před provedením dotazu s kritérii pro specifikaci na posledním řádku.</span><span class="sxs-lookup"><span data-stu-id="1fd26-245">You can see this approach used in the List method above, which uses intermediate IQueryable expressions to build up the query’s list of includes before executing the query with the specification’s criteria on the last line.</span></span>


#### <a name="additional-resources"></a><span data-ttu-id="1fd26-246">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="1fd26-246">Additional resources</span></span>

-   <span data-ttu-id="1fd26-247">**Mapování tabulek**
    [*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span><span class="sxs-lookup"><span data-stu-id="1fd26-247">**Table Mapping**
[*https://docs.microsoft.com/ef/core/modeling/relational/tables*](https://docs.microsoft.com/ef/core/modeling/relational/tables)</span></span>

-   <span data-ttu-id="1fd26-248">**Použití HiLo generování klíčů s Entity Framework Core**
    [*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span><span class="sxs-lookup"><span data-stu-id="1fd26-248">**Use HiLo to generate keys with Entity Framework Core**
[*http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/*](http://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/)</span></span>

-   <span data-ttu-id="1fd26-249">**Pomocná pole**
    [*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span><span class="sxs-lookup"><span data-stu-id="1fd26-249">**Backing Fields**
[*https://docs.microsoft.com/ef/core/modeling/backing-field*](https://docs.microsoft.com/ef/core/modeling/backing-field)</span></span>

-   <span data-ttu-id="1fd26-250">**Steve Smith. Zapouzdřený objekt kolekce v Entity Framework Core**
    [*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)</span><span class="sxs-lookup"><span data-stu-id="1fd26-250">**Steve Smith. Encapsulated Collections in Entity Framework Core**
[*https://ardalis.com/encapsulated-collections-in-entity-framework-core*](https://ardalis.com/encapsulated-collections-in-entity-framework-core)</span></span>

-   <span data-ttu-id="1fd26-251">**Stínové vlastnosti**
    [*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span><span class="sxs-lookup"><span data-stu-id="1fd26-251">**Shadow Properties**
[*https://docs.microsoft.com/ef/core/modeling/shadow-properties*](https://docs.microsoft.com/ef/core/modeling/shadow-properties)</span></span>

-   <span data-ttu-id="1fd26-252">**Vzor specifikace**
    [*https://deviq.com/specification-pattern/*](https://deviq.com/specification-pattern/)</span><span class="sxs-lookup"><span data-stu-id="1fd26-252">**The Specification pattern**
[*https://deviq.com/specification-pattern/*](https://deviq.com/specification-pattern/)</span></span>
    

>[!div class="step-by-step"]
<span data-ttu-id="1fd26-253">[Předchozí](infrastructure-persistence-layer-design.md)
[další](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="1fd26-253">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>
