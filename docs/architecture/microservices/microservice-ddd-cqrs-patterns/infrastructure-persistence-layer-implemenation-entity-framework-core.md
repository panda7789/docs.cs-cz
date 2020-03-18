---
title: Implementace vrstvy trvalosti infrastruktury pomocí Entity Framework Core
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Prozkoumejte podrobnosti implementace pro vrstvu trvalost infrastruktury pomocí jádra entity frameworku.
ms.date: 01/30/2020
ms.openlocfilehash: 63579dc74ba52551bc1ee02a57337c1b17fdf396
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79401625"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="e4270-103">Implementace vrstvy trvalosti infrastruktury pomocí jádra entity</span><span class="sxs-lookup"><span data-stu-id="e4270-103">Implement the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="e4270-104">Při použití relační databáze, jako je SQL Server, Oracle nebo PostgreSQL, doporučeným přístupem je implementace vrstvy trvalosti na základě entity framework (EF).</span><span class="sxs-lookup"><span data-stu-id="e4270-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="e4270-105">EF podporuje LINQ a poskytuje objekty silného typu pro váš model, stejně jako zjednodušenou trvalost do databáze.</span><span class="sxs-lookup"><span data-stu-id="e4270-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="e4270-106">Entity Framework má dlouhou historii jako součást rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="e4270-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="e4270-107">Při použití .NET Core, měli byste také použít Entity Framework Core, který běží na Windows nebo Linux stejným způsobem jako .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e4270-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="e4270-108">EF Core je kompletní přepsání entity frameworku, implementované s mnohem menším půdorysem a důležitým zlepšením výkonu.</span><span class="sxs-lookup"><span data-stu-id="e4270-108">EF Core is a complete rewrite of Entity Framework, implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="e4270-109">Úvod do jádra rámce entity</span><span class="sxs-lookup"><span data-stu-id="e4270-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="e4270-110">Entity Framework (EF) Core je lehká, rozšiřitelná a multiplatformní verze populární technologie přístupu k datům Entity Framework.</span><span class="sxs-lookup"><span data-stu-id="e4270-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="e4270-111">To bylo představeno s .NET Core v polovině roku 2016.</span><span class="sxs-lookup"><span data-stu-id="e4270-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="e4270-112">Vzhledem k tomu, že úvod do EF Core je již k dispozici v dokumentaci společnosti Microsoft, zde jednoduše poskytujeme odkazy na tyto informace.</span><span class="sxs-lookup"><span data-stu-id="e4270-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e4270-113">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="e4270-113">Additional resources</span></span>

- <span data-ttu-id="e4270-114">**Jádro rámce entity** </span><span class="sxs-lookup"><span data-stu-id="e4270-114">**Entity Framework Core** </span></span>\
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- <span data-ttu-id="e4270-115">**Začínáme s ASP.NET jádra a frameworku entity pomocí sady Visual Studio** </span><span class="sxs-lookup"><span data-stu-id="e4270-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio** </span></span>\
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- <span data-ttu-id="e4270-116">**Třída DbContext** </span><span class="sxs-lookup"><span data-stu-id="e4270-116">**DbContext Class** </span></span>\
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- <span data-ttu-id="e4270-117">**Porovnání ef jádra & EF6.x** </span><span class="sxs-lookup"><span data-stu-id="e4270-117">**Compare EF Core & EF6.x** </span></span>\
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="e4270-118">Infrastruktura v jádru entity z hlediska DDD</span><span class="sxs-lookup"><span data-stu-id="e4270-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="e4270-119">Z hlediska DDD je důležitou schopností EF schopnost používat entity domény POCO, známé také v terminologii EF jako *entity poco code first*.</span><span class="sxs-lookup"><span data-stu-id="e4270-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="e4270-120">Pokud používáte entity domény POCO, vaše třídy modelu domény jsou neznalost inaste, podle zásad [neznalosti trvalosti](https://deviq.com/persistence-ignorance/) a [infrastruktury nevědomosti.](https://ayende.com/blog/3137/infrastructure-ignorance)</span><span class="sxs-lookup"><span data-stu-id="e4270-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](https://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="e4270-121">Podle vzorů DDD byste měli zapouzdřit chování domény a pravidla v rámci samotné třídy entity, aby mohla řídit invarianty, ověření a pravidla při přístupu k libovolné kolekci.</span><span class="sxs-lookup"><span data-stu-id="e4270-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="e4270-122">Proto není v DDD vhodné povolit veřejný přístup k kolekcím podřízených entit nebo hodnotových objektů.</span><span class="sxs-lookup"><span data-stu-id="e4270-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="e4270-123">Místo toho chcete vystavit metody, které řídí, jak a kdy mohou být aktualizovány vaše pole a kolekce vlastností a jaké chování a akce by mělo dojít, když k tomu dojde.</span><span class="sxs-lookup"><span data-stu-id="e4270-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="e4270-124">Vzhledem k tomu, EF Core 1.1, ke splnění těchto požadavků DDD, můžete mít prostý chod ve vašich entit namísto veřejných vlastností.</span><span class="sxs-lookup"><span data-stu-id="e4270-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="e4270-125">Pokud nechcete, aby pole entity bylo externě přístupné, můžete místo vlastnosti vytvořit atribut nebo pole.</span><span class="sxs-lookup"><span data-stu-id="e4270-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="e4270-126">Můžete také použít soukromé nemovitosti setters.</span><span class="sxs-lookup"><span data-stu-id="e4270-126">You can also use private property setters.</span></span>

<span data-ttu-id="e4270-127">Podobným způsobem můžete nyní mít přístup jen pro čtení ke kolekcím `IReadOnlyCollection<T>`pomocí veřejné vlastnosti zadané jako , která je `List<T>`zálohována soukromým členem pole pro kolekci (jako ) ve vaší entitě, která závisí na EF pro trvalost.</span><span class="sxs-lookup"><span data-stu-id="e4270-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="e4270-128">Předchozí verze entity Framework požadované vlastnosti kolekce pro podporu `ICollection<T>`, což znamenalo, že každý vývojář pomocí třídy nadřazené entity můžete přidat nebo odebrat položky prostřednictvím svých kolekcí vlastností.</span><span class="sxs-lookup"><span data-stu-id="e4270-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="e4270-129">Tato možnost by byla v rozporu s doporučenými vzory v DDD.</span><span class="sxs-lookup"><span data-stu-id="e4270-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="e4270-130">Můžete použít soukromou kolekci při vystavení `IReadOnlyCollection<T>` objektu jen pro čtení, jak je znázorněno v následujícím příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="e4270-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

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

<span data-ttu-id="e4270-131">Všimněte `OrderItems` si, že vlastnost lze přistupovat `IReadOnlyCollection<OrderItem>`pouze jako jen pro čtení pomocí .</span><span class="sxs-lookup"><span data-stu-id="e4270-131">Note that the `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="e4270-132">Tento typ je jen pro čtení, takže je chráněn před pravidelnými externími aktualizacemi.</span><span class="sxs-lookup"><span data-stu-id="e4270-132">This type is read-only so it is protected against regular external updates.</span></span>

<span data-ttu-id="e4270-133">EF Core poskytuje způsob, jak mapovat model domény do fyzické databáze bez "kontaminace" modelu domény.</span><span class="sxs-lookup"><span data-stu-id="e4270-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="e4270-134">Je to čistý kód POCO .NET, protože akce mapování je implementována ve vrstvě trvalosti.</span><span class="sxs-lookup"><span data-stu-id="e4270-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="e4270-135">V této akci mapování je třeba nakonfigurovat mapování polí na databázi.</span><span class="sxs-lookup"><span data-stu-id="e4270-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="e4270-136">V následujícím příkladu `OnModelCreating` metody `OrderingContext` z `OrderEntityTypeConfiguration` a třídy `SetPropertyAccessMode` volání říká EF `OrderItems` Core pro přístup k vlastnosti prostřednictvím jeho pole.</span><span class="sxs-lookup"><span data-stu-id="e4270-136">In the following example of the `OnModelCreating` method from `OrderingContext` and the `OrderEntityTypeConfiguration` class, the call to `SetPropertyAccessMode` tells EF Core to access the `OrderItems` property through its field.</span></span>

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

<span data-ttu-id="e4270-137">Při použití polí namísto `OrderItem` vlastností je entita trvalá, stejně `List<OrderItem>` jako kdyby měla vlastnost.</span><span class="sxs-lookup"><span data-stu-id="e4270-137">When you use fields instead of properties, the `OrderItem` entity is persisted just as if it had a `List<OrderItem>` property.</span></span> <span data-ttu-id="e4270-138">Však zpřístupňuje jeden přistupující `AddOrderItem` ho, metoda pro přidání nových položek do pořadí.</span><span class="sxs-lookup"><span data-stu-id="e4270-138">However, it exposes a single accessor, the `AddOrderItem` method, for adding new items to the order.</span></span> <span data-ttu-id="e4270-139">V důsledku toho jsou chování a data spojeny dohromady a budou konzistentní v celém kódu aplikace, který používá model domény.</span><span class="sxs-lookup"><span data-stu-id="e4270-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implement-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="e4270-140">Implementace vlastních úložišť pomocí jádra entity frameworku</span><span class="sxs-lookup"><span data-stu-id="e4270-140">Implement custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="e4270-141">Na úrovni implementace je úložiště jednoduše třídou s kódem trvalost dat koordinovanou jednotkou práce (DBContext v EF Core) při provádění aktualizací, jak je znázorněno v následující třídě:</span><span class="sxs-lookup"><span data-stu-id="e4270-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

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

<span data-ttu-id="e4270-142">Všimněte si, že rozhraní IBuyerRepository pochází z vrstvy modelu domény jako smlouvy.</span><span class="sxs-lookup"><span data-stu-id="e4270-142">Note that the IBuyerRepository interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="e4270-143">Implementace úložiště se však provádí ve vrstvě trvalosti a infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="e4270-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="e4270-144">EF DbContext přichází prostřednictvím konstruktoru prostřednictvím vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="e4270-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="e4270-145">Je sdílena mezi více úložišť v rámci stejného oboru`ServiceLifetime.Scoped`požadavku HTTP, díky jeho výchozí životnosti `services.AddDbContext<>`( ) v kontejneru IoC (který lze také explicitně nastavit).</span><span class="sxs-lookup"><span data-stu-id="e4270-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (`ServiceLifetime.Scoped`) in the IoC container (which can also be explicitly set with `services.AddDbContext<>`).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="e4270-146">Metody implementace v úložišti (aktualizace nebo transakce versus dotazy)</span><span class="sxs-lookup"><span data-stu-id="e4270-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="e4270-147">V rámci každé třídy úložiště byste měli umístit metody trvalosti, které aktualizují stav entit obsažených v související agregaci.</span><span class="sxs-lookup"><span data-stu-id="e4270-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="e4270-148">Nezapomeňte, že existuje vztah 1:1 mezi agregací a souvisejícím úložištěm.</span><span class="sxs-lookup"><span data-stu-id="e4270-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="e4270-149">Zvažte, že agregovaný objekt kořenové entity může mít vložené podřízené entity v rámci svého EF grafu.</span><span class="sxs-lookup"><span data-stu-id="e4270-149">Consider that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="e4270-150">Kupující může mít například více platebních metod jako spřízněné podřízené entity.</span><span class="sxs-lookup"><span data-stu-id="e4270-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="e4270-151">Vzhledem k tomu, že přístup pro řazení mikroslužeb v eShopOnContainers je také založen na CQS/CQRS, většina dotazů nejsou implementovány ve vlastních úložištích.</span><span class="sxs-lookup"><span data-stu-id="e4270-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="e4270-152">Vývojáři mají svobodu vytvářet dotazy a spojení, které potřebují pro prezentační vrstvu bez omezení uložených agregacemi, vlastními úložišti na agregaci a DDD obecně.</span><span class="sxs-lookup"><span data-stu-id="e4270-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="e4270-153">Většina vlastních úložišť navržených touto příručkou má několik metod aktualizace nebo transakce, ale pouze metody dotazu potřebné k aktualizaci dat.</span><span class="sxs-lookup"><span data-stu-id="e4270-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="e4270-154">Například BuyerRepository úložiště implementuje FindAsync metodu, protože aplikace potřebuje vědět, zda konkrétní kupující existuje před vytvořením nového kupujícího související s objednávkou.</span><span class="sxs-lookup"><span data-stu-id="e4270-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="e4270-155">Skutečné metody dotazu pro získání dat k odeslání do prezentační vrstvy nebo klientských aplikací jsou však implementovány, jak je uvedeno, v dotazech CQRS na základě flexibilních dotazů pomocí Dapper.</span><span class="sxs-lookup"><span data-stu-id="e4270-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="e4270-156">Použití vlastního úložiště versus přímé použití EF DbContext</span><span class="sxs-lookup"><span data-stu-id="e4270-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="e4270-157">Entity Framework DbContext Třída je založena na jednotky práce a úložiště vzory a lze použít přímo z vašeho kódu, například z ASP.NET core MVC řadič.</span><span class="sxs-lookup"><span data-stu-id="e4270-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns, and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="e4270-158">To je způsob, jak můžete vytvořit nejjednodušší kód, jako v katalogu CRUD mikroslužby v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="e4270-158">That is the way you can create the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="e4270-159">V případech, kdy chcete nejjednodušší možný kód, můžete chtít přímo použít třídu DbContext, jako mnoho vývojářů.</span><span class="sxs-lookup"><span data-stu-id="e4270-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="e4270-160">Implementace vlastních úložišť však poskytuje několik výhod při implementaci složitějších mikroslužeb nebo aplikací.</span><span class="sxs-lookup"><span data-stu-id="e4270-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="e4270-161">Vzory jednotky práce a úložiště jsou určeny k zapouzdření vrstvy trvalosti infrastruktury tak, aby byla oddělena od vrstev modelu aplikace a domény.</span><span class="sxs-lookup"><span data-stu-id="e4270-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain model layers.</span></span> <span data-ttu-id="e4270-162">Implementace těchto vzorů může usnadnit použití mock repozitáře simulující přístup k databázi.</span><span class="sxs-lookup"><span data-stu-id="e4270-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="e4270-163">Na obrázku 7-18 můžete vidět rozdíly mezi nepoužívání maže (přímo pomocí EF DbContext) a pomocí úložišť, které usnadňují zesměšňovat tyto repozitáře.</span><span class="sxs-lookup"><span data-stu-id="e4270-163">In Figure 7-18 you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories which make it easier to mock those repositories.</span></span>

![Diagram znázorňující součásti a tok dat ve dvou úložištích.](./media/infrastructure-persistence-layer-implemenation-entity-framework-core/custom-repo-versus-db-context.png)

<span data-ttu-id="e4270-165">**Obrázek 7-18**.</span><span class="sxs-lookup"><span data-stu-id="e4270-165">**Figure 7-18**.</span></span> <span data-ttu-id="e4270-166">Použití vlastních úložišť versus prostého kontextu DbContext</span><span class="sxs-lookup"><span data-stu-id="e4270-166">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="e4270-167">Obrázek 7-18 ukazuje, že pomocí vlastního úložiště přidá vrstvu abstrakce, která může být použita k usnadnění testování zesměšňováním úložiště.</span><span class="sxs-lookup"><span data-stu-id="e4270-167">Figure 7-18 shows that using a custom repository adds an abstraction layer that can be used to ease testing by mocking the repository.</span></span> <span data-ttu-id="e4270-168">Existuje několik alternativ při zesměšňování.</span><span class="sxs-lookup"><span data-stu-id="e4270-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="e4270-169">Dalo by se zesměšňovat jen repozitáře, nebo byste mohli zesměšňovat celou jednotku práce.</span><span class="sxs-lookup"><span data-stu-id="e4270-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="e4270-170">Obvykle zesměšňovat jen repozitáře je dost, a složitost abstraktní a zesměšňovat celou jednotku práce je obvykle není potřeba.</span><span class="sxs-lookup"><span data-stu-id="e4270-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="e4270-171">Později, když se zaměříme na aplikační vrstvu, uvidíte, jak funguje vkládání závislostí v ASP.NET Core a jak se implementuje při používání úložišť.</span><span class="sxs-lookup"><span data-stu-id="e4270-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="e4270-172">Stručně řečeno, vlastní úložiště umožňují testovat kód snadněji s testy částí, které nejsou ovlivněny stavem datové vrstvy.</span><span class="sxs-lookup"><span data-stu-id="e4270-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="e4270-173">Pokud spustíte testy, které také přístup k databázi prostřednictvím entity framework, nejsou testy částí, ale integrační testy, které jsou mnohem pomalejší.</span><span class="sxs-lookup"><span data-stu-id="e4270-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="e4270-174">Pokud jste používali DbContext přímo, budete muset zesměšňovat nebo spustit testy částí pomocí SQL Server v paměti s předvídatelná data pro testování částí.</span><span class="sxs-lookup"><span data-stu-id="e4270-174">If you were using DbContext directly, you would have to mock it or to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="e4270-175">Ale zesměšňování DbContext nebo ovládání falešných dat vyžaduje více práce než zesměšňování na úrovni úložiště.</span><span class="sxs-lookup"><span data-stu-id="e4270-175">But mocking the DbContext or controlling fake data requires more work than mocking at the repository level.</span></span> <span data-ttu-id="e4270-176">Samozřejmě můžete vždy otestovat řadiče MVC.</span><span class="sxs-lookup"><span data-stu-id="e4270-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="e4270-177">Ef DbContext a IUnitOfWork životnost instance v kontejneru IoC</span><span class="sxs-lookup"><span data-stu-id="e4270-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="e4270-178">Objekt `DbContext` (vystavený `IUnitOfWork` jako objekt) by měl být sdílen mezi více úložišť v rámci stejného oboru požadavku HTTP.</span><span class="sxs-lookup"><span data-stu-id="e4270-178">The `DbContext` object (exposed as an `IUnitOfWork` object) should be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="e4270-179">Například to platí, když operace, která je prováděna, musí řešit více agregací nebo jednoduše proto, že používáte více instancí úložiště.</span><span class="sxs-lookup"><span data-stu-id="e4270-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="e4270-180">Je také důležité zmínit, `IUnitOfWork` že rozhraní je součástí vrstvy domény, nikoli typu EF Core.</span><span class="sxs-lookup"><span data-stu-id="e4270-180">It is also important to mention that the `IUnitOfWork` interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="e4270-181">Za tímto účelem musí `DbContext` mít instance objektu nastavenou na servicelifetime.Scoped.</span><span class="sxs-lookup"><span data-stu-id="e4270-181">In order to do that, the instance of the `DbContext` object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="e4270-182">Toto je výchozí doba `DbContext` života `services.AddDbContext` při registraci s v kontejneru `Startup.cs` IoC z ConfigureServices metoda souboru v projektu ASP.NET core web api.</span><span class="sxs-lookup"><span data-stu-id="e4270-182">This is the default lifetime when registering a `DbContext` with `services.AddDbContext` in your IoC container from the ConfigureServices method of the `Startup.cs` file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="e4270-183">Následující kód to znázorňuje.</span><span class="sxs-lookup"><span data-stu-id="e4270-183">The following code illustrates this.</span></span>

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

<span data-ttu-id="e4270-184">Režim instance DbContext by neměl být nakonfigurován jako ServiceLifetime.Transient nebo ServiceLifetime.Singleton.</span><span class="sxs-lookup"><span data-stu-id="e4270-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="e4270-185">Životnost instance úložiště v kontejneru IoC</span><span class="sxs-lookup"><span data-stu-id="e4270-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="e4270-186">Podobným způsobem by měla být obvykle nastavena životnost úložiště jako obor (InstancePerLifetimeScope v Autofac).</span><span class="sxs-lookup"><span data-stu-id="e4270-186">In a similar way, repository’s lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="e4270-187">Může být také přechodné (InstancePerDependency v Autofac), ale vaše služba bude efektivnější, pokud jde o paměť při použití rozsahem životnost.</span><span class="sxs-lookup"><span data-stu-id="e4270-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="e4270-188">Všimněte si, že pomocí životnosti singleton pro úložiště může způsobit vážné problémy souběžnosti při dbContext je nastavena na rozsah (InstancePerLifetimeScope) životnost (výchozí životnost dbcontext).</span><span class="sxs-lookup"><span data-stu-id="e4270-188">Note that using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e4270-189">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="e4270-189">Additional resources</span></span>

- <span data-ttu-id="e4270-190">**Implementace úložiště a jednotky pracovních vzorů v ASP.NET aplikace MVC** </span><span class="sxs-lookup"><span data-stu-id="e4270-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application** </span></span>\
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- <span data-ttu-id="e4270-191">**Jonathanallen, to je ono. Prováděcí strategie pro model úložiště s rámcem entity, dapper a řetězce** </span><span class="sxs-lookup"><span data-stu-id="e4270-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain** </span></span>\
  <https://www.infoq.com/articles/repository-implementation-strategies>

- <span data-ttu-id="e4270-192">**Cesar de la Torre. Porovnání ASP.NET životnosti služby kontejneru Core IoC s obory instancí kontejneru Autofac IoC** </span><span class="sxs-lookup"><span data-stu-id="e4270-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a><span data-ttu-id="e4270-193">Mapování tabulek</span><span class="sxs-lookup"><span data-stu-id="e4270-193">Table mapping</span></span>

<span data-ttu-id="e4270-194">Mapování tabulky identifikuje data tabulky, která mají být dotazována z databáze a uložena do ní.</span><span class="sxs-lookup"><span data-stu-id="e4270-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="e4270-195">Dříve jste viděli, jak lze entity domény (například produkt nebo doména objednávky) použít ke generování souvisejícího schématu databáze.</span><span class="sxs-lookup"><span data-stu-id="e4270-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="e4270-196">EF je silně koncipovanou kolem konceptu *konvencí*.</span><span class="sxs-lookup"><span data-stu-id="e4270-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="e4270-197">Konvence se zabývají otázkami jako "Jaký bude název tabulky?"</span><span class="sxs-lookup"><span data-stu-id="e4270-197">Conventions address questions like “What will the name of a table be?”</span></span> <span data-ttu-id="e4270-198">nebo "Jaká vlastnost je primárním klíčem?"</span><span class="sxs-lookup"><span data-stu-id="e4270-198">or “What property is the primary key?”</span></span> <span data-ttu-id="e4270-199">Konvence jsou obvykle založeny na konvenční názvy – například je typické pro primární klíč je vlastnost, která končí Id.</span><span class="sxs-lookup"><span data-stu-id="e4270-199">Conventions are typically based on conventional names—for example, it is typical for the primary key to be a property that ends with Id.</span></span>

<span data-ttu-id="e4270-200">Podle konvence bude každá entita nastavena tak, aby `DbSet<TEntity>` mapovala tabulku se stejným názvem jako vlastnost, která entitu zveřejňuje v odvozeném kontextu.</span><span class="sxs-lookup"><span data-stu-id="e4270-200">By convention, each entity will be set up to map to a table with the same name as the `DbSet<TEntity>` property that exposes the entity on the derived context.</span></span> <span data-ttu-id="e4270-201">Pokud `DbSet<TEntity>` pro danou entitu není k dispozici žádná hodnota, použije se název třídy.</span><span class="sxs-lookup"><span data-stu-id="e4270-201">If no `DbSet<TEntity>` value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="e4270-202">Poznámky k datům versus fluent api</span><span class="sxs-lookup"><span data-stu-id="e4270-202">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="e4270-203">Existuje mnoho dalších EF Core konvence a většina z nich lze změnit pomocí anotací dat nebo Fluent API, implementované v rámci OnModelCreating metody.</span><span class="sxs-lookup"><span data-stu-id="e4270-203">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="e4270-204">Poznámky k datům musí být použity na samotných třídách modelu entity, což je z hlediska DDD rušivější způsob.</span><span class="sxs-lookup"><span data-stu-id="e4270-204">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="e4270-205">Důvodem je, že kontaminujete model datovými anotacemi souvisejícími s databází infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="e4270-205">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="e4270-206">Na druhou stranu Fluent API je pohodlný způsob, jak změnit většinu konvencí a mapování v rámci vrstvy infrastruktury trvalosti dat, takže model entity bude čistý a oddělený od infrastruktury trvalosti.</span><span class="sxs-lookup"><span data-stu-id="e4270-206">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="e4270-207">Fluent API a metoda OnModelCreating</span><span class="sxs-lookup"><span data-stu-id="e4270-207">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="e4270-208">Jak již bylo zmíněno, chcete-li změnit konvence a mapování, můžete použít OnModelCreating metoda v DbContext třídy.</span><span class="sxs-lookup"><span data-stu-id="e4270-208">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span>

<span data-ttu-id="e4270-209">Řazení mikroslužby v eShopOnContainers implementuje explicitní mapování a konfiguraci, v případě potřeby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="e4270-209">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

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
            .UseHiLo("orderseq", OrderingContext.DEFAULT_SCHEMA);

        //Address value object persisted as owned entity type supported since EF Core 2.0
        orderConfiguration
            .OwnsOne(o => o.Address, a =>
            {
                a.WithOwner();
            });

        orderConfiguration
            .Property<int?>("_buyerId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("BuyerId")
            .IsRequired(false);

        orderConfiguration
            .Property<DateTime>("_orderDate")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderDate")
            .IsRequired();

        orderConfiguration
            .Property<int>("_orderStatusId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("OrderStatusId")
            .IsRequired();

        orderConfiguration
            .Property<int?>("_paymentMethodId")
            .UsePropertyAccessMode(PropertyAccessMode.Field)
            .HasColumnName("PaymentMethodId")
            .IsRequired(false);

        orderConfiguration.Property<string>("Description").IsRequired(false);

        var navigation = orderConfiguration.Metadata.FindNavigation(nameof(Order.OrderItems));

        // DDD Patterns comment:
        //Set as field (New since EF 1.1) to access the OrderItem collection property through its field
        navigation.SetPropertyAccessMode(PropertyAccessMode.Field);

        orderConfiguration.HasOne<PaymentMethod>()
            .WithMany()
            .HasForeignKey("_paymentMethodId")
            .IsRequired(false)
            .OnDelete(DeleteBehavior.Restrict);

        orderConfiguration.HasOne<Buyer>()
            .WithMany()
            .IsRequired(false)
            .HasForeignKey("_buyerId");

        orderConfiguration.HasOne(o => o.OrderStatus)
            .WithMany()
            .HasForeignKey("_orderStatusId");
    }
}
```

<span data-ttu-id="e4270-210">Můžete nastavit všechna mapování rozhraní API `OnModelCreating` Fluent v rámci stejné metody, ale je vhodné rozdělit tento kód a mít více konfiguračních tříd, jeden na entitu, jak je znázorněno v příkladu.</span><span class="sxs-lookup"><span data-stu-id="e4270-210">You could set all the Fluent API mappings within the same `OnModelCreating` method, but it's advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="e4270-211">Zejména u velkých modelů je vhodné mít samostatné třídy konfigurace pro konfiguraci různých typů entit.</span><span class="sxs-lookup"><span data-stu-id="e4270-211">Especially for large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="e4270-212">Kód v příkladu ukazuje několik explicitní deklarace a mapování.</span><span class="sxs-lookup"><span data-stu-id="e4270-212">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="e4270-213">Ef Core konvence však mnoho z těchto mapování automaticky, takže skutečný kód, který byste potřebovali ve vašem případě může být menší.</span><span class="sxs-lookup"><span data-stu-id="e4270-213">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="e4270-214">Algoritmus Hi/Lo v EF core</span><span class="sxs-lookup"><span data-stu-id="e4270-214">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="e4270-215">Zajímavým aspektem kódu v předchozím příkladu je, že používá [algoritmus Hi/Lo](https://vladmihalcea.com/the-hilo-algorithm/) jako strategii generování klíčů.</span><span class="sxs-lookup"><span data-stu-id="e4270-215">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="e4270-216">Algoritmus Hi/Lo je užitečný, když potřebujete jedinečné klíče před potvrzením změn.</span><span class="sxs-lookup"><span data-stu-id="e4270-216">The Hi/Lo algorithm is useful when you need unique keys before committing changes.</span></span> <span data-ttu-id="e4270-217">Jako souhrn algoritmus Hi-Lo přiřadí jedinečné identifikátory řádkům tabulky, aniž by to v závislosti na okamžitém uložení řádku v databázi.</span><span class="sxs-lookup"><span data-stu-id="e4270-217">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="e4270-218">To vám umožní začít používat identifikátory hned, jak se to děje s pravidelnými sekvenčními ID databáze.</span><span class="sxs-lookup"><span data-stu-id="e4270-218">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="e4270-219">Algoritmus Hi/Lo popisuje mechanismus pro získání dávky jedinečných ID z související databázové sekvence.</span><span class="sxs-lookup"><span data-stu-id="e4270-219">The Hi/Lo algorithm describes a mechanism for getting a batch of unique IDs from a related database sequence.</span></span> <span data-ttu-id="e4270-220">Tyto ID jsou bezpečné použití, protože databáze zaručuje jedinečnost, takže nedojde ke kolizím mezi uživateli.</span><span class="sxs-lookup"><span data-stu-id="e4270-220">These IDs are safe to use because the database guarantees the uniqueness, so there will be no collisions between users.</span></span> <span data-ttu-id="e4270-221">Tento algoritmus je zajímavý z těchto důvodů:</span><span class="sxs-lookup"><span data-stu-id="e4270-221">This algorithm is interesting for these reasons:</span></span>

- <span data-ttu-id="e4270-222">Nepřeruší vzor jednotky práce.</span><span class="sxs-lookup"><span data-stu-id="e4270-222">It does not break the Unit of Work pattern.</span></span>

- <span data-ttu-id="e4270-223">Získá id sekvence v dávkách, aby se minimalizovalo zpáteční cesty do databáze.</span><span class="sxs-lookup"><span data-stu-id="e4270-223">It gets sequence IDs in batches, to minimize round trips to the database.</span></span>

- <span data-ttu-id="e4270-224">Generuje lidský čitelný identifikátor, na rozdíl od technik, které používají identifikátory GUID.</span><span class="sxs-lookup"><span data-stu-id="e4270-224">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="e4270-225">EF Core podporuje [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) s `UseHiLo` metodou, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="e4270-225">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the `UseHiLo` method, as shown in the preceding example.</span></span>

### <a name="map-fields-instead-of-properties"></a><span data-ttu-id="e4270-226">Mapování polí místo vlastností</span><span class="sxs-lookup"><span data-stu-id="e4270-226">Map fields instead of properties</span></span>

<span data-ttu-id="e4270-227">Pomocí této funkce, která je k dispozici od EF Core 1.1, můžete přímo mapovat sloupce na pole.</span><span class="sxs-lookup"><span data-stu-id="e4270-227">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="e4270-228">Je možné nepoužívat vlastnosti ve třídě entity a pouze mapovat sloupce z tabulky na pole.</span><span class="sxs-lookup"><span data-stu-id="e4270-228">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="e4270-229">Běžné použití, které by soukromé pole pro všechny vnitřní stav, které není nutné přistupovat z mimo entitu.</span><span class="sxs-lookup"><span data-stu-id="e4270-229">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="e4270-230">Můžete to provést s jednotlivými poli nebo `List<>` také s kolekcemi, jako je pole.</span><span class="sxs-lookup"><span data-stu-id="e4270-230">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="e4270-231">Tento bod byl zmíněn dříve, když jsme diskutovali modelování tříd modelu domény, `PropertyAccessMode.Field` ale zde můžete vidět, jak se provádí toto mapování s konfigurací zvýrazněnou v předchozím kódu.</span><span class="sxs-lookup"><span data-stu-id="e4270-231">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="e4270-232">Použití vlastností stínů v ef jádru, skrytých na úrovni infrastruktury</span><span class="sxs-lookup"><span data-stu-id="e4270-232">Use shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="e4270-233">Vlastnosti stínů v jádru EF jsou vlastnosti, které neexistují v modelu třídy entit.</span><span class="sxs-lookup"><span data-stu-id="e4270-233">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="e4270-234">Hodnoty a stavy těchto vlastností jsou udržovány čistě ve třídě [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) na úrovni infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="e4270-234">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

## <a name="implement-the-query-specification-pattern"></a><span data-ttu-id="e4270-235">Implementace vzoru specifikace dotazu</span><span class="sxs-lookup"><span data-stu-id="e4270-235">Implement the Query Specification pattern</span></span>

<span data-ttu-id="e4270-236">Jak bylo zavedeno dříve v části návrhu, vzor specifikace dotazu je vzor návrhu řízeného doménou navržený jako místo, kam můžete umístit definici dotazu s volitelnou logikou řazení a stránkování.</span><span class="sxs-lookup"><span data-stu-id="e4270-236">As introduced earlier in the design section, the Query Specification pattern is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span>

<span data-ttu-id="e4270-237">Vzor Specifikace dotazu definuje dotaz v objektu.</span><span class="sxs-lookup"><span data-stu-id="e4270-237">The Query Specification pattern defines a query in an object.</span></span> <span data-ttu-id="e4270-238">Chcete-li například zapouzdřit stránkovaný dotaz, který vyhledá některé produkty, můžete vytvořit specifikaci PagedProduct, která přebírá potřebné vstupní parametry (pageNumber, pageSize, filter atd.).</span><span class="sxs-lookup"><span data-stu-id="e4270-238">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="e4270-239">Potom v rámci jakékoli metody úložiště (obvykle List() přetížení) by přijmout IQuerySpecification a spustit očekávaný dotaz na základě této specifikace.</span><span class="sxs-lookup"><span data-stu-id="e4270-239">Then, within any Repository method (usually a List() overload) it would accept an IQuerySpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="e4270-240">Příkladem obecného rozhraní Specifikace je následující kód z [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span><span class="sxs-lookup"><span data-stu-id="e4270-240">An example of a generic Specification interface is the following code from [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

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

<span data-ttu-id="e4270-241">Implementace základní třídy obecné specifikace je potom následující.</span><span class="sxs-lookup"><span data-stu-id="e4270-241">Then, the implementation of a generic specification base class is the following.</span></span>

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

<span data-ttu-id="e4270-242">Následující specifikace načte jednu entitu košíku, která je uvedena buď ID košíku, nebo ID kupujícího, kterému košík patří.</span><span class="sxs-lookup"><span data-stu-id="e4270-242">The following specification loads a single basket entity given either the basket’s ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="e4270-243">Bude [dychtivě načíst](https://docs.microsoft.com/ef/core/querying/related-data) kolekce položek košíku.</span><span class="sxs-lookup"><span data-stu-id="e4270-243">It will [eagerly load](https://docs.microsoft.com/ef/core/querying/related-data) the basket’s Items collection.</span></span>

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

<span data-ttu-id="e4270-244">A nakonec můžete vidět níže, jak obecné EF úložiště můžete použít takové specifikace filtrovat a dychtivé načítání dat souvisejících s danou entitou typu T.</span><span class="sxs-lookup"><span data-stu-id="e4270-244">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

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

<span data-ttu-id="e4270-245">Kromě logiky zapouzdření filtrování může specifikace určit tvar dat, která mají být vrácena, včetně vlastností, které mají být naplněny.</span><span class="sxs-lookup"><span data-stu-id="e4270-245">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span>

<span data-ttu-id="e4270-246">I když nedoporučujeme vrátit `IQueryable` se z úložiště, je naprosto v pořádku je použít v úložišti k vytvoření sady výsledků.</span><span class="sxs-lookup"><span data-stu-id="e4270-246">Although we don’t recommend to return `IQueryable` from a repository, it’s perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="e4270-247">Tento přístup použitý ve výše uvedené metodě `IQueryable` List, která používá zprostředkující výrazy k sestavení seznamu zahrnutí dotazu před provedením dotazu s kritérii specifikace na posledním řádku.</span><span class="sxs-lookup"><span data-stu-id="e4270-247">You can see this approach used in the List method above, which uses intermediate `IQueryable` expressions to build up the query’s list of includes before executing the query with the specification’s criteria on the last line.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="e4270-248">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="e4270-248">Additional resources</span></span>

- <span data-ttu-id="e4270-249">**Mapování tabulky** </span><span class="sxs-lookup"><span data-stu-id="e4270-249">**Table Mapping** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- <span data-ttu-id="e4270-250">**Použití HiLo ke generování klíčů pomocí jádra entity frameworku** </span><span class="sxs-lookup"><span data-stu-id="e4270-250">**Use HiLo to generate keys with Entity Framework Core** </span></span>\
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- <span data-ttu-id="e4270-251">**Doprovodná pole** </span><span class="sxs-lookup"><span data-stu-id="e4270-251">**Backing Fields** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- <span data-ttu-id="e4270-252">**Steva Smithe. Zapouzdřené kolekce v jádru entity frameworku** </span><span class="sxs-lookup"><span data-stu-id="e4270-252">**Steve Smith. Encapsulated Collections in Entity Framework Core** </span></span>\
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- <span data-ttu-id="e4270-253">**Vlastnosti stínu** </span><span class="sxs-lookup"><span data-stu-id="e4270-253">**Shadow Properties** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="e4270-254">**Vzor specifikace** </span><span class="sxs-lookup"><span data-stu-id="e4270-254">**The Specification pattern** </span></span>\
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> <span data-ttu-id="e4270-255">[Předchozí](infrastructure-persistence-layer-design.md)
> [další](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="e4270-255">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>
