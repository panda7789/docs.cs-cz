---
title: Implementace vrstvy trvalosti infrastruktury pomocí Entity Framework Core
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Prozkoumejte podrobnosti implementace vrstvy trvalosti infrastruktury pomocí Entity Framework Core.
ms.date: 01/30/2020
ms.openlocfilehash: c91980504b0f9de859c6d211f3a1f47435b2d3cc
ms.sourcegitcommit: 046a9c22487551360e20ec39fc21eef99820a254
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2020
ms.locfileid: "83396260"
---
# <a name="implement-the-infrastructure-persistence-layer-with-entity-framework-core"></a><span data-ttu-id="2184c-103">Implementace vrstvy trvalosti infrastruktury s Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="2184c-103">Implement the infrastructure persistence layer with Entity Framework Core</span></span>

<span data-ttu-id="2184c-104">Při použití relačních databází, jako jsou SQL Server, Oracle nebo PostgreSQL, je doporučený přístup implementovat vrstvu trvalosti založenou na Entity Framework (EF).</span><span class="sxs-lookup"><span data-stu-id="2184c-104">When you use relational databases such as SQL Server, Oracle, or PostgreSQL, a recommended approach is to implement the persistence layer based on Entity Framework (EF).</span></span> <span data-ttu-id="2184c-105">EF podporuje LINQ a poskytuje objekty silného typu pro váš model a také zjednodušenou stálost databáze.</span><span class="sxs-lookup"><span data-stu-id="2184c-105">EF supports LINQ and provides strongly typed objects for your model, as well as simplified persistence into your database.</span></span>

<span data-ttu-id="2184c-106">Entity Framework má jako součást .NET Framework dlouhou historii.</span><span class="sxs-lookup"><span data-stu-id="2184c-106">Entity Framework has a long history as part of the .NET Framework.</span></span> <span data-ttu-id="2184c-107">Pokud používáte .NET Core, měli byste také použít Entity Framework Core, která běží v systému Windows nebo Linux stejným způsobem jako .NET Core.</span><span class="sxs-lookup"><span data-stu-id="2184c-107">When you use .NET Core, you should also use Entity Framework Core, which runs on Windows or Linux in the same way as .NET Core.</span></span> <span data-ttu-id="2184c-108">EF Core je ucelený přepis Entity Framework, který se implementuje s mnohem menšími nároky a důležitá vylepšení výkonu.</span><span class="sxs-lookup"><span data-stu-id="2184c-108">EF Core is a complete rewrite of Entity Framework that's implemented with a much smaller footprint and important improvements in performance.</span></span>

## <a name="introduction-to-entity-framework-core"></a><span data-ttu-id="2184c-109">Úvod do Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="2184c-109">Introduction to Entity Framework Core</span></span>

<span data-ttu-id="2184c-110">Jádro Entity Framework (EF) je odlehčená, rozšiřitelná a více platforem oblíbené technologie Entity Framework data pro přístup k datům.</span><span class="sxs-lookup"><span data-stu-id="2184c-110">Entity Framework (EF) Core is a lightweight, extensible, and cross-platform version of the popular Entity Framework data access technology.</span></span> <span data-ttu-id="2184c-111">Byla představena s .NET Core v polovině až 2016.</span><span class="sxs-lookup"><span data-stu-id="2184c-111">It was introduced with .NET Core in mid-2016.</span></span>

<span data-ttu-id="2184c-112">Vzhledem k tomu, že Úvod do EF Core je již k dispozici v dokumentaci společnosti Microsoft, jednoduše poskytujeme odkazy na tyto informace.</span><span class="sxs-lookup"><span data-stu-id="2184c-112">Since an introduction to EF Core is already available in Microsoft documentation, here we simply provide links to that information.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2184c-113">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="2184c-113">Additional resources</span></span>

- <span data-ttu-id="2184c-114">**Entity Framework Core** </span><span class="sxs-lookup"><span data-stu-id="2184c-114">**Entity Framework Core** </span></span>\
  [https://docs.microsoft.com/ef/core/](/ef/core/)

- <span data-ttu-id="2184c-115">**Začínáme s ASP.NET Core a Entity Framework Core pomocí sady Visual Studio** </span><span class="sxs-lookup"><span data-stu-id="2184c-115">**Getting started with ASP.NET Core and Entity Framework Core using Visual Studio** </span></span>\
  [https://docs.microsoft.com/aspnet/core/data/ef-mvc/](/aspnet/core/data/ef-mvc/)

- <span data-ttu-id="2184c-116">**DbContext – třída** </span><span class="sxs-lookup"><span data-stu-id="2184c-116">**DbContext Class** </span></span>\
  [https://docs.microsoft.com/dotnet/api/microsoft.entityframeworkcore.dbcontext](xref:Microsoft.EntityFrameworkCore.DbContext)

- <span data-ttu-id="2184c-117">**Compare EF Core & EF6. x** </span><span class="sxs-lookup"><span data-stu-id="2184c-117">**Compare EF Core & EF6.x** </span></span>\
  [https://docs.microsoft.com/ef/efcore-and-ef6/index](/ef/efcore-and-ef6/index)

## <a name="infrastructure-in-entity-framework-core-from-a-ddd-perspective"></a><span data-ttu-id="2184c-118">Infrastruktura v Entity Framework Core z DDD perspektivy</span><span class="sxs-lookup"><span data-stu-id="2184c-118">Infrastructure in Entity Framework Core from a DDD perspective</span></span>

<span data-ttu-id="2184c-119">Z bodu DDD je důležitou schopností EF použití doménových entit POCO, označovaných také v terminologii EF jako POCO *entity Code-First*.</span><span class="sxs-lookup"><span data-stu-id="2184c-119">From a DDD point of view, an important capability of EF is the ability to use POCO domain entities, also known in EF terminology as POCO *code-first entities*.</span></span> <span data-ttu-id="2184c-120">Pokud používáte doménové entity POCO, vaše třídy doménového modelu jsou ignorovány, a to po [ignorování perzistence](https://deviq.com/persistence-ignorance/) a principu [ignorování infrastruktury](https://ayende.com/blog/3137/infrastructure-ignorance) .</span><span class="sxs-lookup"><span data-stu-id="2184c-120">If you use POCO domain entities, your domain model classes are persistence-ignorant, following the [Persistence Ignorance](https://deviq.com/persistence-ignorance/) and the [Infrastructure Ignorance](https://ayende.com/blog/3137/infrastructure-ignorance) principles.</span></span>

<span data-ttu-id="2184c-121">V případě vzorů na DDD byste měli zapouzdřit chování domény a pravidla v rámci samotné třídy entity, aby při přístupu k libovolné kolekci mohla řídit invariantní, ověřování a pravidla.</span><span class="sxs-lookup"><span data-stu-id="2184c-121">Per DDD patterns, you should encapsulate domain behavior and rules within the entity class itself, so it can control invariants, validations, and rules when accessing any collection.</span></span> <span data-ttu-id="2184c-122">Proto není dobrým zvykem v DDD, aby bylo možné získat veřejný přístup ke kolekcím podřízených entit nebo objektů hodnot.</span><span class="sxs-lookup"><span data-stu-id="2184c-122">Therefore, it is not a good practice in DDD to allow public access to collections of child entities or value objects.</span></span> <span data-ttu-id="2184c-123">Místo toho chcete vystavit metody, které řídí, jak a kdy je možné aktualizovat vaše pole a kolekce vlastností a jaké chování a akce by měly nastat, pokud k tomu dojde.</span><span class="sxs-lookup"><span data-stu-id="2184c-123">Instead, you want to expose methods that control how and when your fields and property collections can be updated, and what behavior and actions should occur when that happens.</span></span>

<span data-ttu-id="2184c-124">Vzhledem k tomu, že EF Core 1,1 pro splnění těchto DDD požadavků, můžete místo veřejných vlastností použít ve svých entitách prostá pole.</span><span class="sxs-lookup"><span data-stu-id="2184c-124">Since EF Core 1.1, to satisfy those DDD requirements, you can have plain fields in your entities instead of public properties.</span></span> <span data-ttu-id="2184c-125">Pokud nechcete, aby pole entity bylo externě přístupné, můžete namísto vlastnosti vytvořit pouze atribut nebo pole.</span><span class="sxs-lookup"><span data-stu-id="2184c-125">If you do not want an entity field to be externally accessible, you can just create the attribute or field instead of a property.</span></span> <span data-ttu-id="2184c-126">Lze také použít metody setter pro soukromé vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2184c-126">You can also use private property setters.</span></span>

<span data-ttu-id="2184c-127">Podobným způsobem teď můžete mít k kolekcím přístup jen pro čtení pomocí veřejné vlastnosti zadané jako `IReadOnlyCollection<T>` , která je zajištěná členem soukromého pole pro kolekci (jako `List<T>` ) ve vaší entitě, která spoléhá na EF pro trvalost.</span><span class="sxs-lookup"><span data-stu-id="2184c-127">In a similar way, you can now have read-only access to collections by using a public property typed as  `IReadOnlyCollection<T>`, which is backed by a private field member for the collection (like a `List<T>`) in your entity that relies on EF for persistence.</span></span> <span data-ttu-id="2184c-128">Předchozí verze Entity Framework vyžadovaly podporu vlastností kolekce `ICollection<T>` , což znamenalo, že každý vývojář používající nadřazenou třídu entity může přidat nebo odebrat položky prostřednictvím svých kolekcí vlastností.</span><span class="sxs-lookup"><span data-stu-id="2184c-128">Previous versions of Entity Framework required collection properties to support `ICollection<T>`, which meant that any developer using the parent entity class could add or remove items through its property collections.</span></span> <span data-ttu-id="2184c-129">Tato možnost by byla v porovnání s doporučenými vzory v DDD.</span><span class="sxs-lookup"><span data-stu-id="2184c-129">That possibility would be against the recommended patterns in DDD.</span></span>

<span data-ttu-id="2184c-130">Můžete použít soukromou kolekci při vystavení objektu jen pro čtení `IReadOnlyCollection<T>` , jak je znázorněno v následujícím příkladu kódu:</span><span class="sxs-lookup"><span data-stu-id="2184c-130">You can use a private collection while exposing a read-only `IReadOnlyCollection<T>` object, as shown in the following code example:</span></span>

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

<span data-ttu-id="2184c-131">`OrderItems`K vlastnosti lze získat přístup pouze jako jen pro čtení pomocí `IReadOnlyCollection<OrderItem>` .</span><span class="sxs-lookup"><span data-stu-id="2184c-131">The `OrderItems` property can only be accessed as read-only using `IReadOnlyCollection<OrderItem>`.</span></span> <span data-ttu-id="2184c-132">Tento typ je jen pro čtení, takže je chráněný před běžnými externími aktualizacemi.</span><span class="sxs-lookup"><span data-stu-id="2184c-132">This type is read-only so it is protected against regular external updates.</span></span>

<span data-ttu-id="2184c-133">EF Core poskytuje způsob mapování doménového modelu na fyzickou databázi bez "kontaminujících" doménového modelu.</span><span class="sxs-lookup"><span data-stu-id="2184c-133">EF Core provides a way to map the domain model to the physical database without "contaminating" the domain model.</span></span> <span data-ttu-id="2184c-134">Je to čistě POCO kód .NET, protože akce mapování je implementovaná v perzistentní vrstvě.</span><span class="sxs-lookup"><span data-stu-id="2184c-134">It is pure .NET POCO code, because the mapping action is implemented in the persistence layer.</span></span> <span data-ttu-id="2184c-135">V této akci mapování je nutné nakonfigurovat mapování polí na databázi.</span><span class="sxs-lookup"><span data-stu-id="2184c-135">In that mapping action, you need to configure the fields-to-database mapping.</span></span> <span data-ttu-id="2184c-136">V následujícím příkladu `OnModelCreating` metody z `OrderingContext` a `OrderEntityTypeConfiguration` třídy volá volání, aby `SetPropertyAccessMode` EF Core přístup k `OrderItems` vlastnosti prostřednictvím jejího pole.</span><span class="sxs-lookup"><span data-stu-id="2184c-136">In the following example of the `OnModelCreating` method from `OrderingContext` and the `OrderEntityTypeConfiguration` class, the call to `SetPropertyAccessMode` tells EF Core to access the `OrderItems` property through its field.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities' configuration ...
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

<span data-ttu-id="2184c-137">Při použití polí namísto vlastností `OrderItem` je entita trvale, jako by měla `List<OrderItem>` vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2184c-137">When you use fields instead of properties, the `OrderItem` entity is persisted as if it had a `List<OrderItem>` property.</span></span> <span data-ttu-id="2184c-138">Nicméně zpřístupňuje jeden přistupující objekt, `AddOrderItem` metodu pro přidání nových položek do objednávky.</span><span class="sxs-lookup"><span data-stu-id="2184c-138">However, it exposes a single accessor, the `AddOrderItem` method, for adding new items to the order.</span></span> <span data-ttu-id="2184c-139">Výsledkem je, že chování a data jsou vzájemně propojeny a budou konzistentní v jakémkoli kódu aplikace, který používá doménový model.</span><span class="sxs-lookup"><span data-stu-id="2184c-139">As a result, behavior and data are tied together and will be consistent throughout any application code that uses the domain model.</span></span>

## <a name="implement-custom-repositories-with-entity-framework-core"></a><span data-ttu-id="2184c-140">Implementace vlastních úložišť pomocí Entity Framework Core</span><span class="sxs-lookup"><span data-stu-id="2184c-140">Implement custom repositories with Entity Framework Core</span></span>

<span data-ttu-id="2184c-141">Na úrovni implementace je úložiště jednoduše třída, která má kód trvalosti dat koordinovaný podle pracovní jednotky (DBContext v EF Core) při provádění aktualizací, jak je znázorněno v následující třídě:</span><span class="sxs-lookup"><span data-stu-id="2184c-141">At the implementation level, a repository is simply a class with data persistence code coordinated by a unit of work (DBContext in EF Core) when performing updates, as shown in the following class:</span></span>

```csharp
// using directives...
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

        public async Task<Buyer> FindAsync(string buyerIdentityGuid)
        {
            var buyer = await _context.Buyers
                .Include(b => b.Payments)
                .Where(b => b.FullName == buyerIdentityGuid)
                .SingleOrDefaultAsync();

            return buyer;
        }
    }
}
```

<span data-ttu-id="2184c-142">`IBuyerRepository`Rozhraní přichází z modelu doménové vrstvy jako kontrakt.</span><span class="sxs-lookup"><span data-stu-id="2184c-142">The `IBuyerRepository` interface comes from the domain model layer as a contract.</span></span> <span data-ttu-id="2184c-143">Implementace úložiště se ale provádí na vrstvě trvalosti a infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="2184c-143">However, the repository implementation is done at the persistence and infrastructure layer.</span></span>

<span data-ttu-id="2184c-144">EF DbContext dochází prostřednictvím konstruktoru prostřednictvím injektáže závislosti.</span><span class="sxs-lookup"><span data-stu-id="2184c-144">The EF DbContext comes through the constructor through Dependency Injection.</span></span> <span data-ttu-id="2184c-145">V kontejneru IoC je sdílená mezi několika úložištěmi v rámci stejného oboru požadavku HTTP, a to díky výchozímu života ( `ServiceLifetime.Scoped` ) v kontejneru (dá se taky explicitně nastavit pomocí `services.AddDbContext<>` ).</span><span class="sxs-lookup"><span data-stu-id="2184c-145">It is shared between multiple repositories within the same HTTP request scope, thanks to its default lifetime (`ServiceLifetime.Scoped`) in the IoC container (which can also be explicitly set with `services.AddDbContext<>`).</span></span>

### <a name="methods-to-implement-in-a-repository-updates-or-transactions-versus-queries"></a><span data-ttu-id="2184c-146">Metody pro implementaci v úložišti (aktualizace nebo transakce oproti dotazům)</span><span class="sxs-lookup"><span data-stu-id="2184c-146">Methods to implement in a repository (updates or transactions versus queries)</span></span>

<span data-ttu-id="2184c-147">V rámci každé třídy úložiště byste měli umístit metody trvalosti, které aktualizují stav entit obsažených v související agregaci.</span><span class="sxs-lookup"><span data-stu-id="2184c-147">Within each repository class, you should put the persistence methods that update the state of entities contained by its related aggregate.</span></span> <span data-ttu-id="2184c-148">Nezapomeňte, že mezi agregovaným a souvisejícím úložištěm je relace 1:1.</span><span class="sxs-lookup"><span data-stu-id="2184c-148">Remember there is one-to-one relationship between an aggregate and its related repository.</span></span> <span data-ttu-id="2184c-149">Vezměte v úvahu, že objekt agregované kořenové entity může mít vložené podřízené entity v rámci svého grafu EF.</span><span class="sxs-lookup"><span data-stu-id="2184c-149">Consider that an aggregate root entity object might have embedded child entities within its EF graph.</span></span> <span data-ttu-id="2184c-150">Například kupující může mít více způsobů platby jako související podřízené entity.</span><span class="sxs-lookup"><span data-stu-id="2184c-150">For example, a buyer might have multiple payment methods as related child entities.</span></span>

<span data-ttu-id="2184c-151">Vzhledem k tomu, že je přístup k mikroslužbám řazení v eShopOnContainers také založen na CQS/CQRS, většina dotazů není implementována ve vlastních úložištích.</span><span class="sxs-lookup"><span data-stu-id="2184c-151">Since the approach for the ordering microservice in eShopOnContainers is also based on CQS/CQRS, most of the queries are not implemented in custom repositories.</span></span> <span data-ttu-id="2184c-152">Vývojáři mají volnost v vytváření dotazů a spojení, která potřebují pro prezentační vrstvu bez omezení vyplývajících z agregací, vlastních úložišť na agregaci a na DDD všeobecně.</span><span class="sxs-lookup"><span data-stu-id="2184c-152">Developers have the freedom to create the queries and joins they need for the presentation layer without the restrictions imposed by aggregates, custom repositories per aggregate, and DDD in general.</span></span> <span data-ttu-id="2184c-153">Většina vlastních úložišť navržených v tomto průvodci má několik metod aktualizace nebo transakcí, ale pouze metody dotazů, které jsou potřeba k aktualizaci dat.</span><span class="sxs-lookup"><span data-stu-id="2184c-153">Most of the custom repositories suggested by this guide have several update or transactional methods but just the query methods needed to get data to be updated.</span></span> <span data-ttu-id="2184c-154">Například úložiště BuyerRepository implementuje metodu FindAsync, protože aplikace musí před vytvořením nového nákupčího souvisejícího s objednávkou zjistit, zda existuje konkrétní kupující.</span><span class="sxs-lookup"><span data-stu-id="2184c-154">For example, the BuyerRepository repository implements a FindAsync method, because the application needs to know whether a particular buyer exists before creating a new buyer related to the order.</span></span>

<span data-ttu-id="2184c-155">Nicméně reálné metody dotazů pro odeslání dat do prezentační vrstvy nebo klientských aplikací jsou implementovány, jak je uvedeno v dotazech CQRS na základě flexibilních dotazů pomocí Dapperem.</span><span class="sxs-lookup"><span data-stu-id="2184c-155">However, the real query methods to get data to send to the presentation layer or client apps are implemented, as mentioned, in the CQRS queries based on flexible queries using Dapper.</span></span>

### <a name="using-a-custom-repository-versus-using-ef-dbcontext-directly"></a><span data-ttu-id="2184c-156">Použití vlastního úložiště versus přímé použití EF DbContext</span><span class="sxs-lookup"><span data-stu-id="2184c-156">Using a custom repository versus using EF DbContext directly</span></span>

<span data-ttu-id="2184c-157">Třída Entity Framework DbContext je založena na pracovní jednotce a vzorech úložiště a lze ji použít přímo z vašeho kódu, jako je například z kontroleru ASP.NET Core MVC.</span><span class="sxs-lookup"><span data-stu-id="2184c-157">The Entity Framework DbContext class is based on the Unit of Work and Repository patterns and can be used directly from your code, such as from an ASP.NET Core MVC controller.</span></span> <span data-ttu-id="2184c-158">Pracovní jednotka a vzorce úložiště mají za následek nejjednodušší kód, jako v rámci mikroslužby katalogu CRUD v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="2184c-158">The Unit of Work and Repository patterns result in the simplest code, as in the CRUD catalog microservice in eShopOnContainers.</span></span> <span data-ttu-id="2184c-159">V případech, kdy chcete nejjednodušší kód, můžete chtít přímo použít třídu DbContext, protože to mnoho vývojářů.</span><span class="sxs-lookup"><span data-stu-id="2184c-159">In cases where you want the simplest code possible, you might want to directly use the DbContext class, as many developers do.</span></span>

<span data-ttu-id="2184c-160">Implementace vlastních úložišť ale poskytuje několik výhod při implementaci složitějších mikroslužeb nebo aplikací.</span><span class="sxs-lookup"><span data-stu-id="2184c-160">However, implementing custom repositories provides several benefits when implementing more complex microservices or applications.</span></span> <span data-ttu-id="2184c-161">Pracovní jednotka a vzorce úložiště mají za cíl zapouzdřit vrstvu trvalosti infrastruktury, aby byla oddělená od vrstev aplikace a doménového modelu.</span><span class="sxs-lookup"><span data-stu-id="2184c-161">The Unit of Work and Repository patterns are intended to encapsulate the infrastructure persistence layer so it is decoupled from the application and domain-model layers.</span></span> <span data-ttu-id="2184c-162">Implementace těchto vzorů může usnadnit použití povedených úložišť, které simulují přístup k databázi.</span><span class="sxs-lookup"><span data-stu-id="2184c-162">Implementing these patterns can facilitate the use of mock repositories simulating access to the database.</span></span>

<span data-ttu-id="2184c-163">Na obrázku 7-18 se můžete podívat na rozdíly mezi nepoužíváním úložišť (přímo pomocí DbContext EF) a s využitím úložišť, což usnadňuje navýšení těchto úložišť.</span><span class="sxs-lookup"><span data-stu-id="2184c-163">In Figure 7-18, you can see the differences between not using repositories (directly using the EF DbContext) versus using repositories, which makes it easier to mock those repositories.</span></span>

![Diagram znázorňující komponenty a tok dat v těchto dvou úložištích.](./media/infrastructure-persistence-layer-implemenation-entity-framework-core/custom-repo-versus-db-context.png)

<span data-ttu-id="2184c-165">**Obrázek 7-18**.</span><span class="sxs-lookup"><span data-stu-id="2184c-165">**Figure 7-18**.</span></span> <span data-ttu-id="2184c-166">Použití vlastních úložišť oproti jednoduchému DbContext</span><span class="sxs-lookup"><span data-stu-id="2184c-166">Using custom repositories versus a plain DbContext</span></span>

<span data-ttu-id="2184c-167">Obrázek 7-18 ukazuje, že při použití vlastního úložiště se přidá vrstva abstrakce, která se dá použít ke snadnému testování pomocí napodobení úložiště.</span><span class="sxs-lookup"><span data-stu-id="2184c-167">Figure 7-18 shows that using a custom repository adds an abstraction layer that can be used to ease testing by mocking the repository.</span></span> <span data-ttu-id="2184c-168">Při napodobování je k dispozici více alternativ.</span><span class="sxs-lookup"><span data-stu-id="2184c-168">There are multiple alternatives when mocking.</span></span> <span data-ttu-id="2184c-169">Mohli byste napodobovat jenom úložiště nebo byste mohli napodobovat celou pracovní jednotku.</span><span class="sxs-lookup"><span data-stu-id="2184c-169">You could mock just repositories or you could mock a whole unit of work.</span></span> <span data-ttu-id="2184c-170">Obvykle je napodobení pouze úložišť dostatečně a složitost pro abstrakci a navýšení celé pracovní jednotky většinou není potřeba.</span><span class="sxs-lookup"><span data-stu-id="2184c-170">Usually mocking just the repositories is enough, and the complexity to abstract and mock a whole unit of work is usually not needed.</span></span>

<span data-ttu-id="2184c-171">Později, když se zaměříme na aplikační vrstvu, uvidíte, jak funguje vkládání závislostí v ASP.NET Core a jak je implementováno při použití úložišť.</span><span class="sxs-lookup"><span data-stu-id="2184c-171">Later, when we focus on the application layer, you will see how Dependency Injection works in ASP.NET Core and how it is implemented when using repositories.</span></span>

<span data-ttu-id="2184c-172">V krátkém případě vlastní úložiště umožňují testovat kód snadněji pomocí testů jednotek, které nejsou ovlivněny stavem datové vrstvy.</span><span class="sxs-lookup"><span data-stu-id="2184c-172">In short, custom repositories allow you to test code more easily with unit tests that are not impacted by the data tier state.</span></span> <span data-ttu-id="2184c-173">Pokud spustíte testy, které také přistupují ke skutečné databázi prostřednictvím Entity Framework, nejedná se o testy jednotek, ale integrační testy, které jsou mnohem pomalejší.</span><span class="sxs-lookup"><span data-stu-id="2184c-173">If you run tests that also access the actual database through the Entity Framework, they are not unit tests but integration tests, which are a lot slower.</span></span>

<span data-ttu-id="2184c-174">Pokud jste používali DbContext přímo, museli byste ji napředt nebo spustit testy jednotek pomocí SQL Server v paměti s předvídatelnými daty pro testování částí.</span><span class="sxs-lookup"><span data-stu-id="2184c-174">If you were using DbContext directly, you would have to mock it or to run unit tests by using an in-memory SQL Server with predictable data for unit tests.</span></span> <span data-ttu-id="2184c-175">Ale napodobování DbContext nebo řízení falešných dat vyžaduje více práce, než na úrovni úložiště.</span><span class="sxs-lookup"><span data-stu-id="2184c-175">But mocking the DbContext or controlling fake data requires more work than mocking at the repository level.</span></span> <span data-ttu-id="2184c-176">Je samozřejmě možné vždy otestovat řadiče MVC.</span><span class="sxs-lookup"><span data-stu-id="2184c-176">Of course, you could always test the MVC controllers.</span></span>

## <a name="ef-dbcontext-and-iunitofwork-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="2184c-177">Životnost instance EF DbContext a IUnitOfWork ve vašem kontejneru IoC</span><span class="sxs-lookup"><span data-stu-id="2184c-177">EF DbContext and IUnitOfWork instance lifetime in your IoC container</span></span>

<span data-ttu-id="2184c-178">`DbContext`Objekt (vystavený jako `IUnitOfWork` objekt) by měl být sdílen mezi více úložišť v rámci stejného oboru požadavku HTTP.</span><span class="sxs-lookup"><span data-stu-id="2184c-178">The `DbContext` object (exposed as an `IUnitOfWork` object) should be shared among multiple repositories within the same HTTP request scope.</span></span> <span data-ttu-id="2184c-179">Jedná se například o hodnotu true, pokud se prováděná operace musí zabývat více agregacemi, nebo jednoduše, protože používáte více instancí úložiště.</span><span class="sxs-lookup"><span data-stu-id="2184c-179">For example, this is true when the operation being executed must deal with multiple aggregates, or simply because you are using multiple repository instances.</span></span> <span data-ttu-id="2184c-180">Je také důležité uvést, že `IUnitOfWork` rozhraní je součástí vaší doménové vrstvy, nikoli typu EF Core.</span><span class="sxs-lookup"><span data-stu-id="2184c-180">It is also important to mention that the `IUnitOfWork` interface is part of your domain layer, not an EF Core type.</span></span>

<span data-ttu-id="2184c-181">Aby to bylo možné, musí `DbContext` mít instance objektu nastavenou dobu platnosti služby na ServiceLifetime. scoped.</span><span class="sxs-lookup"><span data-stu-id="2184c-181">In order to do that, the instance of the `DbContext` object has to have its service lifetime set to ServiceLifetime.Scoped.</span></span> <span data-ttu-id="2184c-182">Toto je výchozí doba života při registraci `DbContext` `services.AddDbContext` v v kontejneru IOC z metody ConfigureServices `Startup.cs` souboru v projektu webového rozhraní API ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="2184c-182">This is the default lifetime when registering a `DbContext` with `services.AddDbContext` in your IoC container from the ConfigureServices method of the `Startup.cs` file in your ASP.NET Core Web API project.</span></span> <span data-ttu-id="2184c-183">Následující kód to znázorňuje.</span><span class="sxs-lookup"><span data-stu-id="2184c-183">The following code illustrates this.</span></span>

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

<span data-ttu-id="2184c-184">Režim vytváření instancí DbContext by neměl být nakonfigurovaný jako ServiceLifetime. přechodný nebo ServiceLifetime. singleton.</span><span class="sxs-lookup"><span data-stu-id="2184c-184">The DbContext instantiation mode should not be configured as ServiceLifetime.Transient or ServiceLifetime.Singleton.</span></span>

## <a name="the-repository-instance-lifetime-in-your-ioc-container"></a><span data-ttu-id="2184c-185">Doba života instance úložiště ve vašem kontejneru IoC</span><span class="sxs-lookup"><span data-stu-id="2184c-185">The repository instance lifetime in your IoC container</span></span>

<span data-ttu-id="2184c-186">Podobným způsobem je, že životnost úložiště by měla být obvykle nastavena jako vymezená (InstancePerLifetimeScope v Autofac).</span><span class="sxs-lookup"><span data-stu-id="2184c-186">In a similar way, repository's lifetime should usually be set as scoped (InstancePerLifetimeScope in Autofac).</span></span> <span data-ttu-id="2184c-187">Může to být také přechodný (InstancePerDependency v Autofac), ale vaše služba bude efektivnější v souvislosti s pamětí při použití vymezené životnosti.</span><span class="sxs-lookup"><span data-stu-id="2184c-187">It could also be transient (InstancePerDependency in Autofac), but your service will be more efficient in regards memory when using the scoped lifetime.</span></span>

```csharp
// Registering a Repository in Autofac IoC container
builder.RegisterType<OrderRepository>()
    .As<IOrderRepository>()
    .InstancePerLifetimeScope();
```

<span data-ttu-id="2184c-188">Použití životnosti singleton pro úložiště může způsobit vážné problémy s souběžnou dostupností, když je DbContext nastavené na rozsah (InstancePerLifetimeScope) životního cyklu (výchozí doba pro DBContext).</span><span class="sxs-lookup"><span data-stu-id="2184c-188">Using the singleton lifetime for the repository could cause you serious concurrency problems when your DbContext is set to scoped (InstancePerLifetimeScope) lifetime (the default lifetimes for a DBContext).</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2184c-189">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="2184c-189">Additional resources</span></span>

- <span data-ttu-id="2184c-190">**Implementace vzorového úložiště a pracovní jednotky v aplikaci ASP.NET MVC** </span><span class="sxs-lookup"><span data-stu-id="2184c-190">**Implementing the Repository and Unit of Work Patterns in an ASP.NET MVC Application** </span></span>\
  <https://www.asp.net/mvc/overview/older-versions/getting-started-with-ef-5-using-mvc-4/implementing-the-repository-and-unit-of-work-patterns-in-an-asp-net-mvc-application>

- <span data-ttu-id="2184c-191">**Jonathana Allen. Strategie implementace pro model úložiště s Entity Framework, Dapperem a řetězem** </span><span class="sxs-lookup"><span data-stu-id="2184c-191">**Jonathan Allen. Implementation Strategies for the Repository Pattern with Entity Framework, Dapper, and Chain** </span></span>\
  <https://www.infoq.com/articles/repository-implementation-strategies>

- <span data-ttu-id="2184c-192">**Cesar de la Torre. Porovnávání ASP.NET Corech životností kontejnerových služeb s Autofac IoC instancemi kontejnerů** </span><span class="sxs-lookup"><span data-stu-id="2184c-192">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes** </span></span>\
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="table-mapping"></a><span data-ttu-id="2184c-193">Mapování tabulek</span><span class="sxs-lookup"><span data-stu-id="2184c-193">Table mapping</span></span>

<span data-ttu-id="2184c-194">Mapování tabulek identifikuje tabulková data, která mají být dotazována a uložena do databáze.</span><span class="sxs-lookup"><span data-stu-id="2184c-194">Table mapping identifies the table data to be queried from and saved to the database.</span></span> <span data-ttu-id="2184c-195">Dříve jste viděli, jak můžete použít doménové entity (například doménu produktu nebo objednávky) k vygenerování souvisejícího schématu databáze.</span><span class="sxs-lookup"><span data-stu-id="2184c-195">Previously you saw how domain entities (for example, a product or order domain) can be used to generate a related database schema.</span></span> <span data-ttu-id="2184c-196">EF je silně navržený kolem konceptu *konvencí*.</span><span class="sxs-lookup"><span data-stu-id="2184c-196">EF is strongly designed around the concept of *conventions*.</span></span> <span data-ttu-id="2184c-197">Otázky adres, jako je například "jaký bude název tabulky?"</span><span class="sxs-lookup"><span data-stu-id="2184c-197">Conventions address questions like "What will the name of a table be?"</span></span> <span data-ttu-id="2184c-198">nebo "jaká vlastnost je primární klíč?"</span><span class="sxs-lookup"><span data-stu-id="2184c-198">or "What property is the primary key?"</span></span> <span data-ttu-id="2184c-199">Konvence jsou obvykle založené na konvenčních názvech.</span><span class="sxs-lookup"><span data-stu-id="2184c-199">Conventions are typically based on conventional names.</span></span> <span data-ttu-id="2184c-200">Například je typický pro primární klíč jako vlastnost, která končí na `Id` .</span><span class="sxs-lookup"><span data-stu-id="2184c-200">For example, it is typical for the primary key to be a property that ends with `Id`.</span></span>

<span data-ttu-id="2184c-201">Podle konvence se Každá entita nastaví tak, aby se namapovala na tabulku se stejným názvem, jako má `DbSet<TEntity>` vlastnost, která zpřístupňuje entitu v odvozeném kontextu.</span><span class="sxs-lookup"><span data-stu-id="2184c-201">By convention, each entity will be set up to map to a table with the same name as the `DbSet<TEntity>` property that exposes the entity on the derived context.</span></span> <span data-ttu-id="2184c-202">Pokud `DbSet<TEntity>` pro danou entitu není zadána žádná hodnota, použije se název třídy.</span><span class="sxs-lookup"><span data-stu-id="2184c-202">If no `DbSet<TEntity>` value is provided for the given entity, the class name is used.</span></span>

### <a name="data-annotations-versus-fluent-api"></a><span data-ttu-id="2184c-203">Datové poznámky versus rozhraní API Fluent</span><span class="sxs-lookup"><span data-stu-id="2184c-203">Data Annotations versus Fluent API</span></span>

<span data-ttu-id="2184c-204">Existuje mnoho dalších konvencí EF Core a většinu z nich lze změnit pomocí datových poznámek nebo rozhraní API Fluent implementovaných v rámci metody OnModelCreating.</span><span class="sxs-lookup"><span data-stu-id="2184c-204">There are many additional EF Core conventions, and most of them can be changed by using either data annotations or Fluent API, implemented within the OnModelCreating method.</span></span>

<span data-ttu-id="2184c-205">Datové poznámky musí být použity na samotných třídách modelů entit, což je výraznější způsob zobrazení z bodu DDD.</span><span class="sxs-lookup"><span data-stu-id="2184c-205">Data annotations must be used on the entity model classes themselves, which is a more intrusive way from a DDD point of view.</span></span> <span data-ttu-id="2184c-206">Důvodem je to, že máte v případě, že máte v tomto modelu v angličtině, datové poznámky týkající se databáze infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="2184c-206">This is because you are contaminating your model with data annotations related to the infrastructure database.</span></span> <span data-ttu-id="2184c-207">Na druhé straně je rozhraní Fluent API pohodlný způsob, jak změnit většinu konvencí a mapování v rámci vrstvy infrastruktury pro trvalost dat, takže model entity bude čistý a oddělený od infrastruktury trvalosti.</span><span class="sxs-lookup"><span data-stu-id="2184c-207">On the other hand, Fluent API is a convenient way to change most conventions and mappings within your data persistence infrastructure layer, so the entity model will be clean and decoupled from the persistence infrastructure.</span></span>

### <a name="fluent-api-and-the-onmodelcreating-method"></a><span data-ttu-id="2184c-208">Rozhraní Fluent API a metoda OnModelCreating</span><span class="sxs-lookup"><span data-stu-id="2184c-208">Fluent API and the OnModelCreating method</span></span>

<span data-ttu-id="2184c-209">Jak bylo zmíněno, chcete-li změnit konvence a mapování, můžete použít metodu OnModelCreating ve třídě DbContext.</span><span class="sxs-lookup"><span data-stu-id="2184c-209">As mentioned, in order to change conventions and mappings, you can use the OnModelCreating method in the DbContext class.</span></span>

<span data-ttu-id="2184c-210">Řazení mikroslužeb v eShopOnContainers implementuje explicitní mapování a konfiguraci v případě potřeby, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="2184c-210">The ordering microservice in eShopOnContainers implements explicit mapping and configuration, when needed, as shown in the following code.</span></span>

```csharp
// At OrderingContext.cs from eShopOnContainers
protected override void OnModelCreating(ModelBuilder modelBuilder)
{
   // ...
   modelBuilder.ApplyConfiguration(new OrderEntityTypeConfiguration());
   // Other entities' configuration ...
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

<span data-ttu-id="2184c-211">V rámci stejné metody můžete nastavit všechna mapování Fluent rozhraní API `OnModelCreating` , ale je vhodné rozdělit kód na oddíly a mít více tříd konfigurace, jednu pro každou entitu, jak je znázorněno v příkladu.</span><span class="sxs-lookup"><span data-stu-id="2184c-211">You could set all the Fluent API mappings within the same `OnModelCreating` method, but it's advisable to partition that code and have multiple configuration classes, one per entity, as shown in the example.</span></span> <span data-ttu-id="2184c-212">Zejména u velkých modelů je vhodné mít samostatné třídy konfigurace pro konfiguraci různých typů entit.</span><span class="sxs-lookup"><span data-stu-id="2184c-212">Especially for large models, it is advisable to have separate configuration classes for configuring different entity types.</span></span>

<span data-ttu-id="2184c-213">Kód v příkladu ukazuje několik explicitních deklarací a mapování.</span><span class="sxs-lookup"><span data-stu-id="2184c-213">The code in the example shows a few explicit declarations and mapping.</span></span> <span data-ttu-id="2184c-214">EF Core konvence ale mnoho z těchto mapování provede automaticky, takže skutečný kód, který byste potřebovali v případě, může být menší.</span><span class="sxs-lookup"><span data-stu-id="2184c-214">However, EF Core conventions do many of those mappings automatically, so the actual code you would need in your case might be smaller.</span></span>

### <a name="the-hilo-algorithm-in-ef-core"></a><span data-ttu-id="2184c-215">Algoritmus Hi/Lo v EF Core</span><span class="sxs-lookup"><span data-stu-id="2184c-215">The Hi/Lo algorithm in EF Core</span></span>

<span data-ttu-id="2184c-216">Zajímavým aspektem kódu v předchozím příkladu je, že jako strategii generování klíčů používá [algoritmus Hi/Lo](https://vladmihalcea.com/the-hilo-algorithm/) .</span><span class="sxs-lookup"><span data-stu-id="2184c-216">An interesting aspect of code in the preceding example is that it uses the [Hi/Lo algorithm](https://vladmihalcea.com/the-hilo-algorithm/) as the key generation strategy.</span></span>

<span data-ttu-id="2184c-217">Algoritmus Hi/Lo je užitečný v případě, že před potvrzením změn potřebujete jedinečné klíče.</span><span class="sxs-lookup"><span data-stu-id="2184c-217">The Hi/Lo algorithm is useful when you need unique keys before committing changes.</span></span> <span data-ttu-id="2184c-218">Jako souhrn přiřadí algoritmus Hi-Lo jedinečné identifikátory řádkům tabulky, a to i v závislosti na tom, že se řádek v databázi okamžitě ukládá.</span><span class="sxs-lookup"><span data-stu-id="2184c-218">As a summary, the Hi-Lo algorithm assigns unique identifiers to table rows while not depending on storing the row in the database immediately.</span></span> <span data-ttu-id="2184c-219">To vám umožní začít používat identifikátory hned, jak se děje s pravidelnými sekvenčními identifikátory databáze.</span><span class="sxs-lookup"><span data-stu-id="2184c-219">This lets you start using the identifiers right away, as happens with regular sequential database IDs.</span></span>

<span data-ttu-id="2184c-220">Algoritmus Hi/Lo popisuje mechanismus pro získání dávky jedinečných ID ze související databázové sekvence.</span><span class="sxs-lookup"><span data-stu-id="2184c-220">The Hi/Lo algorithm describes a mechanism for getting a batch of unique IDs from a related database sequence.</span></span> <span data-ttu-id="2184c-221">Tato ID je bezpečné použít, protože databáze zaručuje jedinečnost, takže mezi uživateli nebudou žádné kolize.</span><span class="sxs-lookup"><span data-stu-id="2184c-221">These IDs are safe to use because the database guarantees the uniqueness, so there will be no collisions between users.</span></span> <span data-ttu-id="2184c-222">Tento algoritmus je zajímavý z těchto důvodů:</span><span class="sxs-lookup"><span data-stu-id="2184c-222">This algorithm is interesting for these reasons:</span></span>

- <span data-ttu-id="2184c-223">Neruší vzorek pracovní jednotky.</span><span class="sxs-lookup"><span data-stu-id="2184c-223">It does not break the Unit of Work pattern.</span></span>

- <span data-ttu-id="2184c-224">Získá ID sekvencí v dávkách, aby se minimalizovala výměna zpráv do databáze.</span><span class="sxs-lookup"><span data-stu-id="2184c-224">It gets sequence IDs in batches, to minimize round trips to the database.</span></span>

- <span data-ttu-id="2184c-225">Vygeneruje lidský čitelný identifikátor, na rozdíl od technik, které používají identifikátory GUID.</span><span class="sxs-lookup"><span data-stu-id="2184c-225">It generates a human readable identifier, unlike techniques that use GUIDs.</span></span>

<span data-ttu-id="2184c-226">EF Core podporuje [Hilo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) s `UseHiLo` metodou, jak je znázorněno v předchozím příkladu.</span><span class="sxs-lookup"><span data-stu-id="2184c-226">EF Core supports [HiLo](https://stackoverflow.com/questions/282099/whats-the-hi-lo-algorithm) with the `UseHiLo` method, as shown in the preceding example.</span></span>

### <a name="map-fields-instead-of-properties"></a><span data-ttu-id="2184c-227">Mapování polí namísto vlastností</span><span class="sxs-lookup"><span data-stu-id="2184c-227">Map fields instead of properties</span></span>

<span data-ttu-id="2184c-228">Pomocí této funkce, která je dostupná od EF Core 1,1, můžete přímo namapovat sloupce na pole.</span><span class="sxs-lookup"><span data-stu-id="2184c-228">With this feature, available since EF Core 1.1, you can directly map columns to fields.</span></span> <span data-ttu-id="2184c-229">Je možné, že ve třídě entity nebudete moci používat vlastnosti a pouze mapovat sloupce z tabulky na pole.</span><span class="sxs-lookup"><span data-stu-id="2184c-229">It is possible to not use properties in the entity class, and just to map columns from a table to fields.</span></span> <span data-ttu-id="2184c-230">Běžně se používá pro všechny interní stavy, které nemusejí být k dispozici mimo entitu.</span><span class="sxs-lookup"><span data-stu-id="2184c-230">A common use for that would be private fields for any internal state that do not need to be accessed from outside the entity.</span></span>

<span data-ttu-id="2184c-231">Můžete to provést s jedním polem nebo také s kolekcemi, jako je `List<>` pole.</span><span class="sxs-lookup"><span data-stu-id="2184c-231">You can do this with single fields or also with collections, like a `List<>` field.</span></span> <span data-ttu-id="2184c-232">Tento bod byl zmíněn dříve, když jsme probrali modelování tříd doménového modelu, ale tady vidíte, jak se toto mapování provádí s `PropertyAccessMode.Field` konfigurací zvýrazněnou v předchozím kódu.</span><span class="sxs-lookup"><span data-stu-id="2184c-232">This point was mentioned earlier when we discussed modeling the domain model classes, but here you can see how that mapping is performed with the `PropertyAccessMode.Field` configuration highlighted in the previous code.</span></span>

### <a name="use-shadow-properties-in-ef-core-hidden-at-the-infrastructure-level"></a><span data-ttu-id="2184c-233">Použití vlastností stínu v EF Core skryté na úrovni infrastruktury</span><span class="sxs-lookup"><span data-stu-id="2184c-233">Use shadow properties in EF Core, hidden at the infrastructure level</span></span>

<span data-ttu-id="2184c-234">Vlastnosti stínu v EF Core jsou vlastnosti, které neexistují v modelu třídy entity.</span><span class="sxs-lookup"><span data-stu-id="2184c-234">Shadow properties in EF Core are properties that do not exist in your entity class model.</span></span> <span data-ttu-id="2184c-235">Hodnoty a stavy těchto vlastností se v úrovni infrastruktury uchovávají čistě ve třídě [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) .</span><span class="sxs-lookup"><span data-stu-id="2184c-235">The values and states of these properties are maintained purely in the [ChangeTracker](https://docs.microsoft.com/ef/core/api/microsoft.entityframeworkcore.changetracking.changetracker) class at the infrastructure level.</span></span>

## <a name="implement-the-query-specification-pattern"></a><span data-ttu-id="2184c-236">Implementace vzoru specifikace dotazu</span><span class="sxs-lookup"><span data-stu-id="2184c-236">Implement the Query Specification pattern</span></span>

<span data-ttu-id="2184c-237">Jak je uvedeno dříve v oddílu návrhu, je vzor návrhu založený na doméně navržený jako místo, kde můžete vložit definici dotazu s volitelnou logikou řazení a stránkování.</span><span class="sxs-lookup"><span data-stu-id="2184c-237">As introduced earlier in the design section, the Query Specification pattern is a Domain-Driven Design pattern designed as the place where you can put the definition of a query with optional sorting and paging logic.</span></span>

<span data-ttu-id="2184c-238">Vzor specifikace dotazu definuje dotaz v objektu.</span><span class="sxs-lookup"><span data-stu-id="2184c-238">The Query Specification pattern defines a query in an object.</span></span> <span data-ttu-id="2184c-239">Chcete-li například zapouzdřit stránkovaný dotaz, který vyhledává některé produkty, můžete vytvořit specifikaci PagedProduct, která bude přebírá nezbytné vstupní parametry (pageNumber, pageSize, Filter atd.).</span><span class="sxs-lookup"><span data-stu-id="2184c-239">For example, in order to encapsulate a paged query that searches for some products you can create a PagedProduct specification that takes the necessary input parameters (pageNumber, pageSize, filter, etc.).</span></span> <span data-ttu-id="2184c-240">Potom v rámci libovolné metody úložiště (obvykle přetížení seznamu ()) přijme IQuerySpecification a spustí očekávaný dotaz na základě této specifikace.</span><span class="sxs-lookup"><span data-stu-id="2184c-240">Then, within any Repository method (usually a List() overload) it would accept an IQuerySpecification and run the expected query based on that specification.</span></span>

<span data-ttu-id="2184c-241">Příkladem rozhraní Obecné specifikace je následující kód z [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span><span class="sxs-lookup"><span data-stu-id="2184c-241">An example of a generic Specification interface is the following code from [eShopOnWeb](https://github.com/dotnet-architecture/eShopOnWeb).</span></span>

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

<span data-ttu-id="2184c-242">Pak je implementace základní třídy Obecné specifikace následující.</span><span class="sxs-lookup"><span data-stu-id="2184c-242">Then, the implementation of a generic specification base class is the following.</span></span>

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

<span data-ttu-id="2184c-243">Následující specifikace načte jednu entitu košíku, která má buď ID košíku, nebo ID kupujícího, ke kterému patří košík.</span><span class="sxs-lookup"><span data-stu-id="2184c-243">The following specification loads a single basket entity given either the basket's ID or the ID of the buyer to whom the basket belongs.</span></span> <span data-ttu-id="2184c-244">Bude [eagerly načíst](/ef/core/querying/related-data) `Items` kolekci koše.</span><span class="sxs-lookup"><span data-stu-id="2184c-244">It will [eagerly load](/ef/core/querying/related-data) the basket's `Items` collection.</span></span>

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

<span data-ttu-id="2184c-245">A nakonec vidíte, jak obecné úložiště EF může tuto specifikaci použít k filtrování a Eager dat, která se vztahují k danému typu entity T.</span><span class="sxs-lookup"><span data-stu-id="2184c-245">And finally, you can see below how a generic EF Repository can use such a specification to filter and eager-load data related to a given entity type T.</span></span>

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

<span data-ttu-id="2184c-246">Kromě zapouzdření logiky filtrování může specifikace určit tvar dat, která mají být vrácena, včetně vlastností, které mají být naplněny.</span><span class="sxs-lookup"><span data-stu-id="2184c-246">In addition to encapsulating filtering logic, the specification can specify the shape of the data to be returned, including which properties to populate.</span></span>

<span data-ttu-id="2184c-247">I když nedoporučujeme vracet `IQueryable` z úložiště, je zcela dobré ho v úložišti použít k sestavení sady výsledků.</span><span class="sxs-lookup"><span data-stu-id="2184c-247">Although we don't recommend returning `IQueryable` from a repository, it's perfectly fine to use them within the repository to build up a set of results.</span></span> <span data-ttu-id="2184c-248">Tento přístup můžete zobrazit v metodě seznamu výše, která používá mezilehlé `IQueryable` výrazy k sestavení seznamu obsahuje dotaz, před provedením dotazu s kritérii specifikace na posledním řádku.</span><span class="sxs-lookup"><span data-stu-id="2184c-248">You can see this approach used in the List method above, which uses intermediate `IQueryable` expressions to build up the query's list of includes before executing the query with the specification's criteria on the last line.</span></span>

### <a name="additional-resources"></a><span data-ttu-id="2184c-249">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="2184c-249">Additional resources</span></span>

- <span data-ttu-id="2184c-250">**Mapování tabulek** </span><span class="sxs-lookup"><span data-stu-id="2184c-250">**Table Mapping** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/relational/tables](/ef/core/modeling/relational/tables)

- <span data-ttu-id="2184c-251">**Pomocí HiLo vygenerujte klíče s Entity Framework Core** </span><span class="sxs-lookup"><span data-stu-id="2184c-251">**Use HiLo to generate keys with Entity Framework Core** </span></span>\
  <https://www.talkingdotnet.com/use-hilo-to-generate-keys-with-entity-framework-core/>

- <span data-ttu-id="2184c-252">**Zálohovaná pole** </span><span class="sxs-lookup"><span data-stu-id="2184c-252">**Backing Fields** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/backing-field](/ef/core/modeling/backing-field)

- <span data-ttu-id="2184c-253">**Steve Smith. Zapouzdřené kolekce v Entity Framework Core** </span><span class="sxs-lookup"><span data-stu-id="2184c-253">**Steve Smith. Encapsulated Collections in Entity Framework Core** </span></span>\
  <https://ardalis.com/encapsulated-collections-in-entity-framework-core>

- <span data-ttu-id="2184c-254">**Vlastnosti stínu** </span><span class="sxs-lookup"><span data-stu-id="2184c-254">**Shadow Properties** </span></span>\
  [https://docs.microsoft.com/ef/core/modeling/shadow-properties](/ef/core/modeling/shadow-properties)

- <span data-ttu-id="2184c-255">**Vzor specifikace** </span><span class="sxs-lookup"><span data-stu-id="2184c-255">**The Specification pattern** </span></span>\
  <https://deviq.com/specification-pattern/>

> [!div class="step-by-step"]
> <span data-ttu-id="2184c-256">[Předchozí](infrastructure-persistence-layer-design.md) 
>  [Další](nosql-database-persistence-infrastructure.md)</span><span class="sxs-lookup"><span data-stu-id="2184c-256">[Previous](infrastructure-persistence-layer-design.md)
[Next](nosql-database-persistence-infrastructure.md)</span></span>
