---
title: Implementace aplikační vrstvy mikroslužby pomocí webového rozhraní API
description: Seznamte se s vkládáním závislostí a vzory mediátorů a podrobnostmi jejich implementace v aplikační vrstvě webového rozhraní API.
ms.date: 01/30/2020
ms.openlocfilehash: 76562d87b09a18e4a4ecb7625a2e823bc1ccff78
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988463"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="3e824-103">Implementace aplikační vrstvy mikroslužeb pomocí webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="3e824-103">Implement the microservice application layer using the Web API</span></span>

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="3e824-104">Použití vkládání závislostí k vkládání objektů infrastruktury do aplikační vrstvy</span><span class="sxs-lookup"><span data-stu-id="3e824-104">Use Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="3e824-105">Jak již bylo zmíněno dříve, aplikační vrstva může být implementována jako součást artefaktu (sestavení), který vytváříte, například v rámci projektu webového rozhraní API nebo projektu webové aplikace MVC.</span><span class="sxs-lookup"><span data-stu-id="3e824-105">As mentioned previously, the application layer can be implemented as part of the artifact (assembly) you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="3e824-106">V případě mikroslužby vytvořené s ASP.NET Core, aplikační vrstva bude obvykle vaše knihovna webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="3e824-106">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="3e824-107">Pokud chcete oddělit to, co přichází z ASP.NET Core (jeho infrastruktury a řadiče) z vašeho kódu vlastní aplikační vrstvy, můžete také umístit aplikační vrstvu do samostatné knihovny tříd, ale to je volitelné.</span><span class="sxs-lookup"><span data-stu-id="3e824-107">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="3e824-108">Například kód aplikační vrstvy řazení mikroslužby je přímo implementována jako součást projektu **Ordering.API** (projekt ASP.NET core web API), jak je znázorněno na obrázku 7-23.</span><span class="sxs-lookup"><span data-stu-id="3e824-108">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 7-23.</span></span>

:::image type="complex" source="./media/microservice-application-layer-implementation-web-api/ordering-api-microservice.png" alt-text="Snímek obrazovky mikroslužby Ordering.API v Průzkumníku řešení.":::
<span data-ttu-id="3e824-110">Zobrazení Průzkumník řešení mikroslužby Ordering.API zobrazující podsložky ve složce Aplikace: Chování, příkazy, DomainEventHandlers, IntegrationEvents, Modely, Dotazy a ověření.</span><span class="sxs-lookup"><span data-stu-id="3e824-110">The Solution Explorer view of the Ordering.API microservice, showing the sub-folders under the Application folder: Behaviors, Commands, DomainEventHandlers, IntegrationEvents, Models, Queries and Validations.</span></span>
:::image-end:::

<span data-ttu-id="3e824-111">**Obrázek 7-23**.</span><span class="sxs-lookup"><span data-stu-id="3e824-111">**Figure 7-23**.</span></span> <span data-ttu-id="3e824-112">Aplikační vrstva v projektu Ordering.API ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="3e824-112">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="3e824-113">ASP.NET Core obsahuje jednoduchý [integrovaný kontejner IoC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (reprezentovaný rozhraním IServiceProvider), který ve výchozím nastavení podporuje vkládání konstruktoru a ASP.NET zpřístupňuje určité služby prostřednictvím di.</span><span class="sxs-lookup"><span data-stu-id="3e824-113">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="3e824-114">ASP.NET Core používá termín *služby* pro všechny typy, které zaregistrujete, které budou vloženy prostřednictvím DI.</span><span class="sxs-lookup"><span data-stu-id="3e824-114">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="3e824-115">Služby integrovaného kontejneru nakonfigurujete v metodě ConfigureServices ve třídě Startup vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="3e824-115">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="3e824-116">Vaše závislosti jsou implementovány ve službách, které typ potřebuje a které se zaregistrujete v kontejneru IoC.</span><span class="sxs-lookup"><span data-stu-id="3e824-116">Your dependencies are implemented in the services that a type needs and that you register in the IoC container.</span></span>

<span data-ttu-id="3e824-117">Obvykle chcete vložit závislosti, které implementují objekty infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="3e824-117">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="3e824-118">Velmi typická závislost na injekci je úložiště.</span><span class="sxs-lookup"><span data-stu-id="3e824-118">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="3e824-119">Ale můžete vložit jakékoli jiné infrastruktury závislost, která může mít.</span><span class="sxs-lookup"><span data-stu-id="3e824-119">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="3e824-120">Pro jednodušší implementace můžete přímo vložit objekt vzor jednotky práce (EF DbContext objekt), protože DBContext je také implementace objektů trvalosti infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="3e824-120">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="3e824-121">V následujícím příkladu uvidíte, jak rozhraní .NET Core vstřikuje požadované objekty úložiště prostřednictvím konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="3e824-121">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="3e824-122">Třída je obslužná rutina příkazu, kterou budeme pokrýt v další části.</span><span class="sxs-lookup"><span data-stu-id="3e824-122">The class is a command handler, which we will cover in the next section.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="3e824-123">Třída používá vložené úložiště k provedení transakce a zachovat změny stavu.</span><span class="sxs-lookup"><span data-stu-id="3e824-123">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="3e824-124">Nezáleží na tom, zda je tato třída obslužnou rutinou příkazu, metodou řadiče ASP.NET Core Web API nebo [aplikační službou DDD](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span><span class="sxs-lookup"><span data-stu-id="3e824-124">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="3e824-125">Je to nakonec jednoduchá třída, která používá úložiště, entity domény a další koordinaci aplikací způsobem podobným obslužné rutině příkazu.</span><span class="sxs-lookup"><span data-stu-id="3e824-125">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="3e824-126">Vkládání závislostí funguje stejným způsobem pro všechny uvedené třídy, jako v příkladu pomocí DI na základě konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="3e824-126">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="3e824-127">Registrace typů implementace závislostí a rozhraní nebo abstrakcí</span><span class="sxs-lookup"><span data-stu-id="3e824-127">Register the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="3e824-128">Před použitím objektů vstřikovaných prostřednictvím konstruktory, musíte vědět, kde zaregistrovat rozhraní a třídy, které vytvářejí objekty vložené do tříd aplikace prostřednictvím DI.</span><span class="sxs-lookup"><span data-stu-id="3e824-128">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="3e824-129">(Stejně jako DI na základě konstruktoru, jak je znázorněno výše.)</span><span class="sxs-lookup"><span data-stu-id="3e824-129">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="3e824-130">Používejte vestavěný ioc kontejner dodaný ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="3e824-130">Use the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="3e824-131">Při použití integrovaného kontejneru IoC poskytovaného ASP.NET Core zaregistrujete typy, které chcete vložit do metody ConfigureServices v souboru Startup.cs, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="3e824-131">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
        c.UseSqlServer(Configuration["ConnectionString"]),
        ServiceLifetime.Scoped);

    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

<span data-ttu-id="3e824-132">Nejběžnější vzor při registraci typů v kontejneru IoC je zaregistrovat dvojici typů – rozhraní a jeho související implementace třídy.</span><span class="sxs-lookup"><span data-stu-id="3e824-132">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="3e824-133">Potom při vyžádání objektu z kontejneru IoC prostřednictvím libovolného konstruktoru, požádáte o objekt určitého typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="3e824-133">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="3e824-134">Například v předchozím příkladu poslední řádek uvádí, že když některý z konstruktorů mají závislost na IMyCustomRepository (rozhraní nebo abstrakce), kontejner IoC vloží instanci třídy implementace MyCustomSQLServerRepository.</span><span class="sxs-lookup"><span data-stu-id="3e824-134">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="3e824-135">Použití knihovny Scrutor pro automatickou registraci typů</span><span class="sxs-lookup"><span data-stu-id="3e824-135">Use the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="3e824-136">Při použití DI v .NET Core, můžete chtít mít možnost skenovat sestavení a automaticky zaregistrovat jeho typy podle konvence.</span><span class="sxs-lookup"><span data-stu-id="3e824-136">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="3e824-137">Tato funkce není v současné době k dispozici v ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e824-137">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="3e824-138">K tomu však můžete použít knihovnu [Scrutor.](https://github.com/khellang/Scrutor)</span><span class="sxs-lookup"><span data-stu-id="3e824-138">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="3e824-139">Tento přístup je vhodný, pokud máte desítky typů, které je třeba zaregistrovat v kontejneru IoC.</span><span class="sxs-lookup"><span data-stu-id="3e824-139">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="3e824-140">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="3e824-140">Additional resources</span></span>

- <span data-ttu-id="3e824-141">**Matthew King, to je ono. Registrace služeb u společnosti Scrutor** </span><span class="sxs-lookup"><span data-stu-id="3e824-141">**Matthew King. Registering services with Scrutor** </span></span>\
  <https://www.mking.net/blog/registering-services-with-scrutor>

- <span data-ttu-id="3e824-142">**Kristian Hellang. Scrutor.**</span><span class="sxs-lookup"><span data-stu-id="3e824-142">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="3e824-143">úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="3e824-143">GitHub repo.</span></span> \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a><span data-ttu-id="3e824-144">Použití aplikace Autofac jako kontejneru ioC</span><span class="sxs-lookup"><span data-stu-id="3e824-144">Use Autofac as an IoC container</span></span>

<span data-ttu-id="3e824-145">Můžete také použít další ioc kontejnery a připojit je do kanálu ASP.NET Core, jako v objednávání mikroslužby v eShopOnContainers, který používá [Autofac](https://autofac.org/).</span><span class="sxs-lookup"><span data-stu-id="3e824-145">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="3e824-146">Při použití Autofac obvykle zaregistrujete typy prostřednictvím modulů, které umožňují rozdělit typy registrace mezi více souborů v závislosti na tom, kde jsou vaše typy, stejně jako byste mohli mít typy aplikací distribuovány mezi více knihovnami tříd.</span><span class="sxs-lookup"><span data-stu-id="3e824-146">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="3e824-147">Například následující je [modul aplikace Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) pro projekt [Ordering.API web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) s typy, které budete chtít vložit.</span><span class="sxs-lookup"><span data-stu-id="3e824-147">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

```csharp
public class ApplicationModule : Autofac.Module
{
    public string QueriesConnectionString { get; }
    public ApplicationModule(string qconstr)
    {
        QueriesConnectionString = qconstr;
    }

    protected override void Load(ContainerBuilder builder)
    {
        builder.Register(c => new OrderQueries(QueriesConnectionString))
            .As<IOrderQueries>()
            .InstancePerLifetimeScope();
        builder.RegisterType<BuyerRepository>()
            .As<IBuyerRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<OrderRepository>()
            .As<IOrderRepository>()
            .InstancePerLifetimeScope();
        builder.RegisterType<RequestManager>()
            .As<IRequestManager>()
            .InstancePerLifetimeScope();
   }
}
```

<span data-ttu-id="3e824-148">Autofac má také funkci pro [skenování sestavení a registrovat typy podle konvencí názvů](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span><span class="sxs-lookup"><span data-stu-id="3e824-148">Autofac also has a feature to [scan assemblies and register types by name conventions](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span></span>

<span data-ttu-id="3e824-149">Proces registrace a koncepty jsou velmi podobné způsobu, jakým můžete registrovat typy s vestavěným ASP.NET kontejneru Core IoC, ale syntaxe při použití Autofac je trochu jiná.</span><span class="sxs-lookup"><span data-stu-id="3e824-149">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core IoC container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="3e824-150">V ukázkovém kódu je registrována abstrakce IOrderRepository spolu s implementační třídou OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="3e824-150">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="3e824-151">To znamená, že vždy, když konstruktor deklaruje závislost prostřednictvím abstrakce Nebo rozhraní IOrderRepository, kontejner IoC vloží instanci třídy OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="3e824-151">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="3e824-152">Typ oboru instance určuje, jak je instance sdílena mezi požadavky pro stejnou službu nebo závislost.</span><span class="sxs-lookup"><span data-stu-id="3e824-152">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="3e824-153">Při požadavku na závislost kontejner ioC můžete vrátit následující:</span><span class="sxs-lookup"><span data-stu-id="3e824-153">When a request is made for a dependency, the IoC container can return the following:</span></span>

- <span data-ttu-id="3e824-154">Jedna instance na rozsah životnosti (uvedená v kontejneru ASP.NET core ioc podle *rozsahu).*</span><span class="sxs-lookup"><span data-stu-id="3e824-154">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

- <span data-ttu-id="3e824-155">Nová instance na závislost (uvedená v kontejneru ASP.NET core ioc jako *přechodná).*</span><span class="sxs-lookup"><span data-stu-id="3e824-155">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

- <span data-ttu-id="3e824-156">Jedna instance sdílená mezi všemi objekty pomocí kontejneru IoC (označovaná v kontejneru ASP.NET core ioc jako *singleton).*</span><span class="sxs-lookup"><span data-stu-id="3e824-156">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="3e824-157">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="3e824-157">Additional resources</span></span>

- <span data-ttu-id="3e824-158">**Úvod do vkládání závislostí v ASP.NET core** </span><span class="sxs-lookup"><span data-stu-id="3e824-158">**Introduction to Dependency Injection in ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- <span data-ttu-id="3e824-159">**Autofac.**</span><span class="sxs-lookup"><span data-stu-id="3e824-159">**Autofac.**</span></span> <span data-ttu-id="3e824-160">Oficiální dokumentace.</span><span class="sxs-lookup"><span data-stu-id="3e824-160">Official documentation.</span></span> \
  <https://docs.autofac.org/en/latest/>

- <span data-ttu-id="3e824-161">**Porovnání ASP.NET životnosti kontejneru Core IoC s obory instancí kontejneru Autofac IoC - Cesar de la Torre.**</span><span class="sxs-lookup"><span data-stu-id="3e824-161">**Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes - Cesar de la Torre.**</span></span> \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a><span data-ttu-id="3e824-162">Implementace vzorů Příkaz a Obslužná rutina příkazů</span><span class="sxs-lookup"><span data-stu-id="3e824-162">Implement the Command and Command Handler patterns</span></span>

<span data-ttu-id="3e824-163">V příkladu konstruktoru DI-through-constructor ukázáno v předchozí části kontejner IoC vstřikoval úložiště prostřednictvím konstruktoru ve třídě.</span><span class="sxs-lookup"><span data-stu-id="3e824-163">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="3e824-164">Ale kam přesně jim byla píchnutá injekce?</span><span class="sxs-lookup"><span data-stu-id="3e824-164">But exactly where were they injected?</span></span> <span data-ttu-id="3e824-165">V jednoduché webové rozhraní API (například mikroslužby katalogu v eShopOnContainers) je vložíte na úrovni řadičů MVC v konstruktoru řadiče jako součást kanálu požadavků ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="3e824-165">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers' level, in a controller constructor, as part of the request pipeline of ASP.NET Core.</span></span> <span data-ttu-id="3e824-166">V počátečním kódu této části (třída [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) ze služby Ordering.API v eShopOnContainers) se však vkládání závislostí provádí prostřednictvím konstruktoru konkrétní obslužné rutiny příkazu.</span><span class="sxs-lookup"><span data-stu-id="3e824-166">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="3e824-167">Dovolte nám vysvětlit, co je obslužná rutina příkazu a proč byste ji chtěli používat.</span><span class="sxs-lookup"><span data-stu-id="3e824-167">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="3e824-168">Command vzor je vnitřně souvisí se vzorem CQRS, který byl zaveden dříve v této příručce.</span><span class="sxs-lookup"><span data-stu-id="3e824-168">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="3e824-169">CQRS má dvě strany.</span><span class="sxs-lookup"><span data-stu-id="3e824-169">CQRS has two sides.</span></span> <span data-ttu-id="3e824-170">První oblastí jsou dotazy, pomocí zjednodušených dotazů s [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, který byl vysvětlen dříve.</span><span class="sxs-lookup"><span data-stu-id="3e824-170">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="3e824-171">Druhá oblast je příkazy, které jsou výchozím bodem pro transakce a vstupní kanál mimo službu.</span><span class="sxs-lookup"><span data-stu-id="3e824-171">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="3e824-172">Jak je znázorněno na obrázku 7-24, vzor je založen na přijímání příkazů ze strany klienta, jejich zpracování na základě pravidel modelu domény a nakonec trvalé stavy s transakcemi.</span><span class="sxs-lookup"><span data-stu-id="3e824-172">As shown in Figure 7-24, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![Diagram znázorňující tok dat vysoké úrovně z klienta do databáze.](./media/microservice-application-layer-implementation-web-api/high-level-writes-side.png)

<span data-ttu-id="3e824-174">**Obrázek 7-24**.</span><span class="sxs-lookup"><span data-stu-id="3e824-174">**Figure 7-24**.</span></span> <span data-ttu-id="3e824-175">Zobrazení příkazů na vysoké úrovni nebo "transakční strana" ve vzoru CQRS</span><span class="sxs-lookup"><span data-stu-id="3e824-175">High-level view of the commands or "transactional side" in a CQRS pattern</span></span>

<span data-ttu-id="3e824-176">Obrázek 7-24 ukazuje, že aplikace rozhraní odesílá příkaz `CommandHandler`prostřednictvím rozhraní API, který se dostane do , který závisí na modelu domény a infrastruktury, aktualizovat databázi.</span><span class="sxs-lookup"><span data-stu-id="3e824-176">Figure 7-24 shows that the UI app sends a command through the API that gets to a `CommandHandler`, that depends on the Domain model and the Infrastructure, to update the database.</span></span>

### <a name="the-command-class"></a><span data-ttu-id="3e824-177">Třída příkazů</span><span class="sxs-lookup"><span data-stu-id="3e824-177">The command class</span></span>

<span data-ttu-id="3e824-178">Příkaz je požadavek, aby systém provedl akci, která mění stav systému.</span><span class="sxs-lookup"><span data-stu-id="3e824-178">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="3e824-179">Příkazy jsou nezbytné a měly by být zpracovány pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="3e824-179">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="3e824-180">Vzhledem k tomu, že příkazy jsou imperativy, jsou obvykle pojmenovány se slovesem v imperativní náladě (například "create" nebo "update") a mohou zahrnovat agregační typ, například CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="3e824-180">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="3e824-181">Na rozdíl od události, příkaz není fakt z minulosti; je to pouze žádost, a proto může být zamítnuta.</span><span class="sxs-lookup"><span data-stu-id="3e824-181">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="3e824-182">Příkazy mohou pocházet z uživatelského rozhraní v důsledku, že uživatel iniciuje požadavek, nebo od správce procesů, když správce procesů řídí agregaci k provedení akce.</span><span class="sxs-lookup"><span data-stu-id="3e824-182">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="3e824-183">Důležitou vlastností příkazu je, že by měl být zpracován pouze jednou jedním přijímačem.</span><span class="sxs-lookup"><span data-stu-id="3e824-183">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="3e824-184">Důvodem je, že příkaz je jedna akce nebo transakce, které chcete provést v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3e824-184">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="3e824-185">Například stejný příkaz vytvoření objednávky by neměl být zpracován více než jednou.</span><span class="sxs-lookup"><span data-stu-id="3e824-185">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="3e824-186">To je důležitý rozdíl mezi příkazy a událostmi.</span><span class="sxs-lookup"><span data-stu-id="3e824-186">This is an important difference between commands and events.</span></span> <span data-ttu-id="3e824-187">Události mohou být zpracovány vícekrát, protože mnoho systémů nebo mikroslužeb může mít zájem o událost.</span><span class="sxs-lookup"><span data-stu-id="3e824-187">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="3e824-188">Kromě toho je důležité, aby příkaz byl zpracován pouze jednou v případě, že příkaz není idempotentní.</span><span class="sxs-lookup"><span data-stu-id="3e824-188">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="3e824-189">Příkaz je idempotentní, pokud jej lze provést vícekrát bez změny výsledku, a to buď z důvodu povahy příkazu, nebo z důvodu způsobu, jakým systém zpracovává příkaz.</span><span class="sxs-lookup"><span data-stu-id="3e824-189">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="3e824-190">Je vhodné, aby vaše příkazy a aktualizace idempotentní, když to dává smysl podle obchodních pravidel vaší domény a invariants.</span><span class="sxs-lookup"><span data-stu-id="3e824-190">It is a good practice to make your commands and updates idempotent when it makes sense under your domain's business rules and invariants.</span></span> <span data-ttu-id="3e824-191">Chcete-li například použít stejný příklad, pokud z nějakého důvodu (opakování logiky, hacking, atd.) stejný příkaz CreateOrder dosáhne vašeho systému vícekrát, měli byste být schopni jej identifikovat a zajistit, že nevytvoříte více objednávek.</span><span class="sxs-lookup"><span data-stu-id="3e824-191">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="3e824-192">Chcete-li tak učinit, je třeba připojit nějaký druh identity v operacích a zjistit, zda příkaz nebo aktualizace již byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="3e824-192">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="3e824-193">Odešlete příkaz jednomu příjemci; nepublikujete příkaz.</span><span class="sxs-lookup"><span data-stu-id="3e824-193">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="3e824-194">Publikování je pro události, které uvádějí skutečnost – že se něco stalo a může být zajímavé pro příjemce událostí.</span><span class="sxs-lookup"><span data-stu-id="3e824-194">Publishing is for events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="3e824-195">V případě událostí, vydavatel nemá žádné obavy o tom, které přijímače získat událost nebo co dělají.</span><span class="sxs-lookup"><span data-stu-id="3e824-195">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="3e824-196">Ale události domény nebo integrace jsou jiný příběh, který již byl zaveden v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="3e824-196">But domain or integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="3e824-197">Příkaz je implementován s třídou, která obsahuje datová pole nebo kolekce se všemi informacemi, které jsou potřebné k provedení tohoto příkazu.</span><span class="sxs-lookup"><span data-stu-id="3e824-197">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="3e824-198">Příkaz je zvláštní druh objektu přenosu dat (DTO), který se používá speciálně k vyžádání změn nebo transakcí.</span><span class="sxs-lookup"><span data-stu-id="3e824-198">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="3e824-199">Samotný příkaz je založen přesně na informacích, které jsou potřebné pro zpracování příkazu, a nic víc.</span><span class="sxs-lookup"><span data-stu-id="3e824-199">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="3e824-200">Následující příklad ukazuje zjednodušenou `CreateOrderCommand` třídu.</span><span class="sxs-lookup"><span data-stu-id="3e824-200">The following example shows the simplified `CreateOrderCommand` class.</span></span> <span data-ttu-id="3e824-201">Toto je neměnný příkaz, který se používá v řazení mikroslužby v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="3e824-201">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

```csharp
// DDD and CQRS patterns comment
// Note that we recommend that you implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties
[DataContract]
public class CreateOrderCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;
    [DataMember]
    public string City { get; private set; }
    [DataMember]
    public string Street { get; private set; }
    [DataMember]
    public string State { get; private set; }
    [DataMember]
    public string Country { get; private set; }
    [DataMember]
    public string ZipCode { get; private set; }
    [DataMember]
    public string CardNumber { get; private set; }
    [DataMember]
    public string CardHolderName { get; private set; }
    [DataMember]
    public DateTime CardExpiration { get; private set; }
    [DataMember]
    public string CardSecurityNumber { get; private set; }
    [DataMember]
    public int CardTypeId { get; private set; }
    [DataMember]
    public IEnumerable<OrderItemDTO> OrderItems => _orderItems;

    public CreateOrderCommand()
    {
        _orderItems = new List<OrderItemDTO>();
    }

    public CreateOrderCommand(List<BasketItem> basketItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = MapToOrderItems(basketItems);
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardSecurityNumber = cardSecurityNumber;
        CardTypeId = cardTypeId;
        CardExpiration = cardExpiration;
    }

    public class OrderItemDTO
    {
        public int ProductId { get; set; }
        public string ProductName { get; set; }
        public decimal UnitPrice { get; set; }
        public decimal Discount { get; set; }
        public int Units { get; set; }
        public string PictureUrl { get; set; }
    }
}
```

<span data-ttu-id="3e824-202">V podstatě třída příkazu obsahuje všechna data, která potřebujete pro provádění obchodní transakce pomocí objektů modelu domény.</span><span class="sxs-lookup"><span data-stu-id="3e824-202">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="3e824-203">Příkazy jsou tedy jednoduše datové struktury, které obsahují data jen pro čtení a žádné chování.</span><span class="sxs-lookup"><span data-stu-id="3e824-203">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="3e824-204">Název příkazu označuje jeho účel.</span><span class="sxs-lookup"><span data-stu-id="3e824-204">The command's name indicates its purpose.</span></span> <span data-ttu-id="3e824-205">V mnoha jazycích, jako je C#, příkazy jsou reprezentovány jako třídy, ale nejsou pravdivé třídy v reálném objektově orientovaný smysl.</span><span class="sxs-lookup"><span data-stu-id="3e824-205">In many languages like C#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="3e824-206">Jako další charakteristiku jsou příkazy neměnné, protože očekávané využití je, že jsou zpracovány přímo modelem domény.</span><span class="sxs-lookup"><span data-stu-id="3e824-206">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="3e824-207">Během předpokládaného života se nemusí měnit.</span><span class="sxs-lookup"><span data-stu-id="3e824-207">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="3e824-208">Ve třídě C# nelze neměnnost dosáhnout tím, že nemá žádné nastavení nebo jiné metody, které mění vnitřní stav.</span><span class="sxs-lookup"><span data-stu-id="3e824-208">In a C# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="3e824-209">Mějte na paměti, že pokud máte v úmyslu nebo očekáváte, že příkazy projdou procesem `[DataMember]` serializace a deserializace, vlastnosti musí mít soukromý setter a (nebo `[JsonProperty]`) atribut.</span><span class="sxs-lookup"><span data-stu-id="3e824-209">Keep in mind that if you intend or expect commands to go through a serializing/deserializing process, the properties must have a private setter, and the `[DataMember]` (or `[JsonProperty]`) attribute.</span></span> <span data-ttu-id="3e824-210">V opačném případě deserializátor nebude možné rekonstruovat objekt v cílovém umístění s požadovanými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="3e824-210">Otherwise, the deserializer won't be able to reconstruct the object at destination with the required values.</span></span> <span data-ttu-id="3e824-211">Můžete také použít skutečně jen pro čtení vlastnosti, pokud třída má konstruktor s parametry pro všechny vlastnosti, s `[JsonConstructor]`obvyklou camelCase konvence pojmenování a anotovat konstruktor jako .</span><span class="sxs-lookup"><span data-stu-id="3e824-211">You can also use truly read-only properties if the class has a constructor with parameters for all properties, with the usual camelCase naming convention, and annotate the constructor as `[JsonConstructor]`.</span></span> <span data-ttu-id="3e824-212">Tato možnost však vyžaduje více kódu.</span><span class="sxs-lookup"><span data-stu-id="3e824-212">However, this option requires more code.</span></span>

<span data-ttu-id="3e824-213">Například třída příkazů pro vytvoření objednávky je pravděpodobně podobná z hlediska dat pořadí, ve kterém chcete vytvořit, ale pravděpodobně nepotřebujete stejné atributy.</span><span class="sxs-lookup"><span data-stu-id="3e824-213">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="3e824-214">Například `CreateOrderCommand` nemá ID objednávky, protože objednávka ještě nebyla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="3e824-214">For instance, `CreateOrderCommand` does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="3e824-215">Mnoho tříd příkazů může být jednoduché, vyžadující pouze několik polí o některém stavu, který je třeba změnit.</span><span class="sxs-lookup"><span data-stu-id="3e824-215">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="3e824-216">To by bylo v případě, že jste právě mění stav objednávky z "v procesu" na "placené" nebo "odeslány" pomocí příkazu podobnénásledující:</span><span class="sxs-lookup"><span data-stu-id="3e824-216">That would be the case if you are just changing the status of an order from "in process" to "paid" or "shipped" by using a command similar to the following:</span></span>

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IAsyncRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

<span data-ttu-id="3e824-217">Někteří vývojáři, aby jejich objekty požadavku ui oddělit od jejich příkazu DTO, ale to je jen otázkou preference.</span><span class="sxs-lookup"><span data-stu-id="3e824-217">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="3e824-218">Jedná se o únavné oddělení s nevelkou přidanou hodnotou a objekty mají téměř přesně stejný tvar.</span><span class="sxs-lookup"><span data-stu-id="3e824-218">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="3e824-219">Například v eShopOnContainers některé příkazy pocházejí přímo ze strany klienta.</span><span class="sxs-lookup"><span data-stu-id="3e824-219">For instance, in eShopOnContainers, some commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="3e824-220">Třída obslužné rutiny příkazu</span><span class="sxs-lookup"><span data-stu-id="3e824-220">The Command handler class</span></span>

<span data-ttu-id="3e824-221">Pro každý příkaz byste měli implementovat určitou třídu obslužné rutiny příkazu.</span><span class="sxs-lookup"><span data-stu-id="3e824-221">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="3e824-222">Tak funguje vzor a je místo, kde budete používat objekt příkazu, objekty domény a objekty úložiště infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="3e824-222">That is how the pattern works, and it's where you'll use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="3e824-223">Obslužná rutina příkazu je ve skutečnosti srdcem aplikační vrstvy z hlediska CQRS a DDD.</span><span class="sxs-lookup"><span data-stu-id="3e824-223">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="3e824-224">Všechny logiky domény by však měly být obsaženy ve třídách domény – v rámci agregačních kořenových adresářů (kořenové entity), podřízených entit nebo [doménových služeb](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ale ne v rámci obslužné rutiny příkazu, což je třída z aplikační vrstvy.</span><span class="sxs-lookup"><span data-stu-id="3e824-224">However, all the domain logic should be contained in the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="3e824-225">Třída obslužné rutiny příkazu nabízí silný odrazový můstek v cestě k dosažení principu jednotné odpovědnosti (SRP) uvedeného v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="3e824-225">The command handler class offers a strong stepping stone in the way to achieve the Single Responsibility Principle (SRP) mentioned in a previous section.</span></span>

<span data-ttu-id="3e824-226">Obslužná rutina příkazu obdrží příkaz a získá výsledek z agregace, která se používá.</span><span class="sxs-lookup"><span data-stu-id="3e824-226">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="3e824-227">Výsledkem by mělo být úspěšné spuštění příkazu nebo výjimka.</span><span class="sxs-lookup"><span data-stu-id="3e824-227">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="3e824-228">V případě výjimky by měl být stav systému nezměněn.</span><span class="sxs-lookup"><span data-stu-id="3e824-228">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="3e824-229">Obslužná rutina příkazu obvykle provádí následující kroky:</span><span class="sxs-lookup"><span data-stu-id="3e824-229">The command handler usually takes the following steps:</span></span>

- <span data-ttu-id="3e824-230">Přijímá objekt příkazu, jako DTO (z [mediátoru](https://en.wikipedia.org/wiki/Mediator_pattern) nebo jiného objektu infrastruktury).</span><span class="sxs-lookup"><span data-stu-id="3e824-230">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

- <span data-ttu-id="3e824-231">Ověří, zda je příkaz platný (pokud není ověřen mediátorem).</span><span class="sxs-lookup"><span data-stu-id="3e824-231">It validates that the command is valid (if not validated by the mediator).</span></span>

- <span data-ttu-id="3e824-232">Konkretizoval agregační kořenovou instanci, která je cílem aktuálního příkazu.</span><span class="sxs-lookup"><span data-stu-id="3e824-232">It instantiates the aggregate root instance that is the target of the current command.</span></span>

- <span data-ttu-id="3e824-233">Spustí metodu na agregační kořenové instanci, získání požadovaných dat z příkazu.</span><span class="sxs-lookup"><span data-stu-id="3e824-233">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

- <span data-ttu-id="3e824-234">Zachová nový stav agregace do související databáze.</span><span class="sxs-lookup"><span data-stu-id="3e824-234">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="3e824-235">Tato poslední operace je skutečná transakce.</span><span class="sxs-lookup"><span data-stu-id="3e824-235">This last operation is the actual transaction.</span></span>

<span data-ttu-id="3e824-236">Obslužná rutina příkazu se obvykle zabývá jedinou agregací řízenou jeho agregační kořenovou (kořenovou entitou).</span><span class="sxs-lookup"><span data-stu-id="3e824-236">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="3e824-237">Pokud by příjem jednoho příkazu měl ovlivnit více agregací, můžete použít události domény k šíření stavů nebo akcí napříč více agregacemi.</span><span class="sxs-lookup"><span data-stu-id="3e824-237">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates.</span></span>

<span data-ttu-id="3e824-238">Důležitým bodem je, že při zpracování příkazu by měla být veškerá logika domény uvnitř modelu domény (agregace), plně zapouzdřena a připravena pro testování částí.</span><span class="sxs-lookup"><span data-stu-id="3e824-238">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="3e824-239">Obslužná rutina příkazu funguje pouze jako způsob, jak získat model domény z databáze a jako poslední krok, sdělit vrstvu infrastruktury (úložiště) zachovat změny při změně modelu.</span><span class="sxs-lookup"><span data-stu-id="3e824-239">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="3e824-240">Výhodou tohoto přístupu je, že můžete refaktorovat logiku domény v izolovaném, plně zapouzdřeném, bohatém modelu behaviorální domény bez změny kódu ve vrstvách aplikace nebo infrastruktury, což jsou úroveň instalace (obslužné rutiny příkazů, webové rozhraní API, repozitáře atd.).</span><span class="sxs-lookup"><span data-stu-id="3e824-240">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="3e824-241">Když příkaz obslužné rutiny získat složité, s příliš mnoho logiky, které může být zápach kódu.</span><span class="sxs-lookup"><span data-stu-id="3e824-241">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="3e824-242">Zkontrolujte je a pokud najdete logiku domény, refaktorovat kód přesunout chování domény na metody objektů domény (agregační kořenové a podřízené entity).</span><span class="sxs-lookup"><span data-stu-id="3e824-242">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="3e824-243">Jako příklad třídy obslužné rutiny `CreateOrderCommandHandler` příkazu následující kód ukazuje stejnou třídu, kterou jste viděli na začátku této kapitoly.</span><span class="sxs-lookup"><span data-stu-id="3e824-243">As an example of a command handler class, the following code shows the same `CreateOrderCommandHandler` class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="3e824-244">V tomto případě chceme zvýraznit Handle metodu a operace s objekty modelu domény/agregace.</span><span class="sxs-lookup"><span data-stu-id="3e824-244">In this case, we want to highlight the Handle method and the operations with the domain model objects/aggregates.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

<span data-ttu-id="3e824-245">Jedná se o další kroky, které by měla obslužná rutina příkazu provést:</span><span class="sxs-lookup"><span data-stu-id="3e824-245">These are additional steps a command handler should take:</span></span>

- <span data-ttu-id="3e824-246">Data příkazu slouží k provozu s metodami a chováním agregačního kořenového adresáře.</span><span class="sxs-lookup"><span data-stu-id="3e824-246">Use the command's data to operate with the aggregate root's methods and behavior.</span></span>

- <span data-ttu-id="3e824-247">Interně v rámci objekty domény, raise události domény při provádění transakce, ale to je transparentní z hlediska obslužné rutiny příkazu.</span><span class="sxs-lookup"><span data-stu-id="3e824-247">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

- <span data-ttu-id="3e824-248">Pokud je výsledek operace agregace úspěšný a po dokončení transakce, zvyšte události integrace.</span><span class="sxs-lookup"><span data-stu-id="3e824-248">If the aggregate's operation result is successful and after the transaction is finished, raise integration events.</span></span> <span data-ttu-id="3e824-249">(Ty mohou být také vyvolány třídami infrastruktury, jako jsou repozitáře.)</span><span class="sxs-lookup"><span data-stu-id="3e824-249">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="3e824-250">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="3e824-250">Additional resources</span></span>

- <span data-ttu-id="3e824-251">**Mark Seemann. Na hranicích nejsou aplikace objektově orientované.** </span><span class="sxs-lookup"><span data-stu-id="3e824-251">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented** </span></span>\
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- <span data-ttu-id="3e824-252">**Příkazy a události** </span><span class="sxs-lookup"><span data-stu-id="3e824-252">**Commands and events** </span></span>\
  <https://cqrs.nu/Faq/commands-and-events>

- <span data-ttu-id="3e824-253">**K čemu dělá obslužná rutina příkazu?**</span><span class="sxs-lookup"><span data-stu-id="3e824-253">**What does a command handler do?**</span></span> \
  <https://cqrs.nu/Faq/command-handlers>

- <span data-ttu-id="3e824-254">**Jimmyho Bogarda. Vzory příkazů domény – obslužné rutiny** </span><span class="sxs-lookup"><span data-stu-id="3e824-254">**Jimmy Bogard. Domain Command Patterns – Handlers** </span></span>\
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- <span data-ttu-id="3e824-255">**Jimmyho Bogarda. Vzory příkazů domény – ověření** </span><span class="sxs-lookup"><span data-stu-id="3e824-255">**Jimmy Bogard. Domain Command Patterns – Validation** </span></span>\
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="3e824-256">Kanál procesu příkazu: jak spustit obslužnou rutinu příkazu</span><span class="sxs-lookup"><span data-stu-id="3e824-256">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="3e824-257">Další otázkou je, jak vyvolat obslužnou rutinu příkazu.</span><span class="sxs-lookup"><span data-stu-id="3e824-257">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="3e824-258">Můžete ručně volat z každého souvisejícího ASP.NET core řadič.</span><span class="sxs-lookup"><span data-stu-id="3e824-258">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="3e824-259">Tento přístup by však byl příliš spojený a není ideální.</span><span class="sxs-lookup"><span data-stu-id="3e824-259">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="3e824-260">Další dvě hlavní možnosti, které jsou doporučené možnosti, jsou:</span><span class="sxs-lookup"><span data-stu-id="3e824-260">The other two main options, which are the recommended options, are:</span></span>

- <span data-ttu-id="3e824-261">Prostřednictvím artefaktu vzoru mediátoru v paměti.</span><span class="sxs-lookup"><span data-stu-id="3e824-261">Through an in-memory Mediator pattern artifact.</span></span>

- <span data-ttu-id="3e824-262">S asynchronní fronty zpráv, mezi řadiči a obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="3e824-262">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="3e824-263">Použití vzoru mediátoru (v paměti) v kanálu příkazů</span><span class="sxs-lookup"><span data-stu-id="3e824-263">Use the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="3e824-264">Jak je znázorněno na obrázku 7-25, v přístupu CQRS používáte inteligentní mediátor, podobný sběrnici v paměti, která je dostatečně chytrá, aby přesměrovala na správnou obslužnou rutinu příkazu na základě typu příkazu nebo přijatého DTO.</span><span class="sxs-lookup"><span data-stu-id="3e824-264">As shown in Figure 7-25, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="3e824-265">Jednotlivé černé šipky mezi součástmi představují závislosti mezi objekty (v mnoha případech injekčně prostřednictvím DI) s jejich související interakce.</span><span class="sxs-lookup"><span data-stu-id="3e824-265">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![Diagram znázorňující podrobnější tok dat z klienta do databáze.](./media/microservice-application-layer-implementation-web-api/mediator-cqrs-microservice.png)

<span data-ttu-id="3e824-267">**Obrázek 7-25**.</span><span class="sxs-lookup"><span data-stu-id="3e824-267">**Figure 7-25**.</span></span> <span data-ttu-id="3e824-268">Použití vzoru mediátoru v procesu v jedné mikroslužbě CQRS</span><span class="sxs-lookup"><span data-stu-id="3e824-268">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="3e824-269">Výše uvedený diagram znázorňuje přiblížení z obrázku 7-24: řadič ASP.NET Core odešle příkaz do kanálu příkazů MediatR, takže se dostanou k příslušné obslužné rutině.</span><span class="sxs-lookup"><span data-stu-id="3e824-269">The above diagram shows a zoom-in from image 7-24: the ASP.NET Core controller sends the command to MediatR's command pipeline, so they get to the appropriate handler.</span></span>

<span data-ttu-id="3e824-270">Důvod, proč použití vzoru mediátoru dává smysl, je, že v podnikových aplikacích se požadavky na zpracování mohou zkomplikovat.</span><span class="sxs-lookup"><span data-stu-id="3e824-270">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="3e824-271">Chcete mít možnost přidat otevřený počet průřezových problémů, jako je protokolování, ověřování, audit a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="3e824-271">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="3e824-272">V těchto případech se můžete spolehnout na kanál mediátora (viz [Vzor mediátora)](https://en.wikipedia.org/wiki/Mediator_pattern)poskytnout prostředky pro tyto další chování nebo průřezové obavy.</span><span class="sxs-lookup"><span data-stu-id="3e824-272">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="3e824-273">Mediátor je objekt, který zapouzdřuje "jak" tohoto procesu: koordinuje provádění na základě stavu, způsob, jakým je vyvolána obslužná rutina příkazu, nebo datová část, kterou poskytnete obslužné rutině.</span><span class="sxs-lookup"><span data-stu-id="3e824-273">A mediator is an object that encapsulates the "how" of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="3e824-274">U součásti mediátora můžete použít průřezové obavy centralizovaným a transparentním způsobem použitím [dekorátorů](https://github.com/jbogard/MediatR/wiki/Behaviors) (nebo chování potrubí od [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span><span class="sxs-lookup"><span data-stu-id="3e824-274">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span></span> <span data-ttu-id="3e824-275">Další informace naleznete [decorator vzor](https://en.wikipedia.org/wiki/Decorator_pattern).</span><span class="sxs-lookup"><span data-stu-id="3e824-275">For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).</span></span>

<span data-ttu-id="3e824-276">Dekoratory a chování jsou podobné [aspekty orientované programování (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), platí pouze pro konkrétní proces kanálu spravované ho komponenty mediátora.</span><span class="sxs-lookup"><span data-stu-id="3e824-276">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="3e824-277">Aspekty v AOP, které implementují průřezové obavy, jsou použity na základě *aspektu tkalců* vstřikovaných v době kompilace nebo na základě zachycení volání objektu.</span><span class="sxs-lookup"><span data-stu-id="3e824-277">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="3e824-278">Oba typické Přístupy AOP jsou někdy řekl, aby práce "jako kouzlo," protože to není snadné vidět, jak AOP dělá svou práci.</span><span class="sxs-lookup"><span data-stu-id="3e824-278">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="3e824-279">Při řešení závažných problémů nebo chyb může být obtížné ladit AOP.</span><span class="sxs-lookup"><span data-stu-id="3e824-279">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="3e824-280">Na druhou stranu tyto decorators/behaviors jsou explicitní a použít pouze v kontextu mediátora, takže ladění je mnohem předvídatelnější a snadné.</span><span class="sxs-lookup"><span data-stu-id="3e824-280">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="3e824-281">Například v eShopOnContainers objednávání mikroslužby jsme implementovali dvě ukázkové chování, [Třída LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) a třída [ValidatorBehavior.](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs)</span><span class="sxs-lookup"><span data-stu-id="3e824-281">For example, in the eShopOnContainers ordering microservice, we implemented two sample behaviors, a [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class and a [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class.</span></span> <span data-ttu-id="3e824-282">Implementace chování je vysvětlena v další části tím, že ukazuje, jak eShopOnContainers používá [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [chování](https://github.com/jbogard/MediatR/wiki/Behaviors).</span><span class="sxs-lookup"><span data-stu-id="3e824-282">The implementation of the behaviors is explained in the next section by showing how eShopOnContainers uses [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors).</span></span>

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="3e824-283">Použití front zpráv (mimo proc) v kanálu příkazu</span><span class="sxs-lookup"><span data-stu-id="3e824-283">Use message queues (out-of-proc) in the command's pipeline</span></span>

<span data-ttu-id="3e824-284">Další možností je použití asynchronních zpráv založených na zprostředkovatelích nebo frontách zpráv, jak je znázorněno na obrázku 7-26.</span><span class="sxs-lookup"><span data-stu-id="3e824-284">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 7-26.</span></span> <span data-ttu-id="3e824-285">Tato možnost by mohla být také kombinována s komponentou mediátora přímo před obslužnou rutinou příkazu.</span><span class="sxs-lookup"><span data-stu-id="3e824-285">That option could also be combined with the mediator component right before the command handler.</span></span>

![Diagram znázorňující tok dat pomocí fronty zpráv HA.](./media/microservice-application-layer-implementation-web-api/add-ha-message-queue.png)

<span data-ttu-id="3e824-287">**Obrázek 7-26**.</span><span class="sxs-lookup"><span data-stu-id="3e824-287">**Figure 7-26**.</span></span> <span data-ttu-id="3e824-288">Použití front zpráv (mimo proces a meziprocesová komunikace) s příkazy CQRS</span><span class="sxs-lookup"><span data-stu-id="3e824-288">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="3e824-289">Kanál příkazu může být také zpracován frontou zpráv s vysokou dostupností pro doručení příkazů příslušné obslužné rutině.</span><span class="sxs-lookup"><span data-stu-id="3e824-289">Command's pipeline can also be handled by a high availability message queue to deliver the commands to the appropriate handler.</span></span> <span data-ttu-id="3e824-290">Použití fronty zpráv k přijetí příkazů může dále komplikovat kanálu příkazu, protože pravděpodobně budete muset rozdělit kanál do dvou procesů připojených prostřednictvím fronty externích zpráv.</span><span class="sxs-lookup"><span data-stu-id="3e824-290">Using message queues to accept the commands can further complicate your command's pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="3e824-291">Přesto by měl být použit, pokud potřebujete mít lepší škálovatelnost a výkon na základě asynchronní zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="3e824-291">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="3e824-292">Zvažte, že v případě obrázku 7-26 řadič pouze odešle zprávu příkazu do fronty a vrátí.</span><span class="sxs-lookup"><span data-stu-id="3e824-292">Consider that in the case of Figure 7-26, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="3e824-293">Potom obslužné rutiny příkazů zpracovávají zprávy vlastním tempem.</span><span class="sxs-lookup"><span data-stu-id="3e824-293">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="3e824-294">To je velká výhoda front: fronta zpráv může fungovat jako vyrovnávací paměť v případech, kdy je potřeba hyper škálovatelnost, například pro stavy nebo jakýkoli jiný scénář s velkým objemem dat příchozího přenosu dat.</span><span class="sxs-lookup"><span data-stu-id="3e824-294">That is a great benefit of queues: the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="3e824-295">Z důvodu asynchronní povahy front zpráv je však nutné zjistit, jak komunikovat s klientskou aplikací o úspěchu nebo neúspěchu procesu příkazu.</span><span class="sxs-lookup"><span data-stu-id="3e824-295">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command's process.</span></span> <span data-ttu-id="3e824-296">Zpravidla byste nikdy neměli používat příkazy "oheň a zapomenout".</span><span class="sxs-lookup"><span data-stu-id="3e824-296">As a rule, you should never use "fire and forget" commands.</span></span> <span data-ttu-id="3e824-297">Každá obchodní aplikace potřebuje vědět, zda byl příkaz zpracován úspěšně nebo alespoň ověřen a přijat.</span><span class="sxs-lookup"><span data-stu-id="3e824-297">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="3e824-298">Proto je schopen reagovat na klienta po ověření příkazu zprávy, která byla odeslána do asynchronní fronty zvyšuje složitost systému, ve srovnání s procesem příkazu v procesu v procesu, který vrátí výsledek operace po spuštění transakce.</span><span class="sxs-lookup"><span data-stu-id="3e824-298">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation's result after running the transaction.</span></span> <span data-ttu-id="3e824-299">Pomocí front může být nutné vrátit výsledek procesu příkazu prostřednictvím jiných zpráv výsledků operace, které budou vyžadovat další součásti a vlastní komunikaci v systému.</span><span class="sxs-lookup"><span data-stu-id="3e824-299">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="3e824-300">Kromě toho asynchronní příkazy jsou jednosměrné příkazy, které v mnoha případech nemusí být potřeba, jak je vysvětleno v následující zajímavé výměně mezi Burtsev Alexey a Greg Young v [online konverzaci](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span><span class="sxs-lookup"><span data-stu-id="3e824-300">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

> <span data-ttu-id="3e824-301">\[Burtsev Alexey najdu spoustu kódu, kde lidé používají asynchronní příkaz zpracování nebo jednosměrný příkaz zasílání zpráv bez jakéhokoli důvodu, aby tak učinily\] (nejsou dělat nějaké dlouhé operace, nejsou provádění externí asynchronní kód, nemají ani přes hranice aplikace, které mají být pomocí sběrnice zpráv).</span><span class="sxs-lookup"><span data-stu-id="3e824-301">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="3e824-302">Proč zavádějí tuto zbytečnou složitost?</span><span class="sxs-lookup"><span data-stu-id="3e824-302">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="3e824-303">A vlastně jsem neviděl příklad kódu CQRS s blokováním obslužných rutin příkazů, i když to bude fungovat v pohodě ve většině případů.</span><span class="sxs-lookup"><span data-stu-id="3e824-303">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>
>
> <span data-ttu-id="3e824-304">\[Greg\] \[Mladý ... \] asynchronní příkaz neexistuje; Je to vlastně další událost.</span><span class="sxs-lookup"><span data-stu-id="3e824-304">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="3e824-305">Pokud musím přijmout to, co mi pošlete a vyvolat událost, pokud nesouhlasím, už mi říkáte, abych udělal něco, co \[je, není to příkaz\].</span><span class="sxs-lookup"><span data-stu-id="3e824-305">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something \[that is, it's not a command\].</span></span> <span data-ttu-id="3e824-306">Říkáš mi, že se něco stalo.</span><span class="sxs-lookup"><span data-stu-id="3e824-306">It's you telling me something has been done.</span></span> <span data-ttu-id="3e824-307">To se zdá jako mírný rozdíl na první, ale to má mnoho důsledků.</span><span class="sxs-lookup"><span data-stu-id="3e824-307">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="3e824-308">Asynchronní příkazy výrazně zvyšují složitost systému, protože neexistuje žádný jednoduchý způsob, jak označit selhání.</span><span class="sxs-lookup"><span data-stu-id="3e824-308">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="3e824-309">Proto asynchronní příkazy nejsou doporučeny jiné než při škálování požadavky jsou potřeba nebo ve zvláštních případech při komunikaci interní mikroslužeb prostřednictvím zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="3e824-309">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="3e824-310">V těchto případech je nutné navrhnout samostatný systém vykazování a obnovení pro selhání.</span><span class="sxs-lookup"><span data-stu-id="3e824-310">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="3e824-311">V počáteční verzi eShopOnContainers jsme se rozhodli použít synchronní zpracování příkazů, začalo z HTTP požadavků a řízeno vzorem Mediátora.</span><span class="sxs-lookup"><span data-stu-id="3e824-311">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="3e824-312">To vám snadno umožňuje vrátit úspěch nebo neúspěch procesu, jako v implementaci [CreateOrderCommandHandler.](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs)</span><span class="sxs-lookup"><span data-stu-id="3e824-312">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="3e824-313">V každém případě by to mělo být rozhodnutí založené na obchodních požadavcích vaší aplikace nebo mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="3e824-313">In any case, this should be a decision based on your application's or microservice's business requirements.</span></span>

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="3e824-314">Implementace kanálu procesu příkazu se vzorem mediátora (MediatR)</span><span class="sxs-lookup"><span data-stu-id="3e824-314">Implement the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="3e824-315">Jako ukázkovou implementaci tato příručka navrhuje použití kanálu v procesu založeného na vzoru mediátoru k řízení příkazů a příkazů trasy v paměti na správné obslužné rutiny příkazů.</span><span class="sxs-lookup"><span data-stu-id="3e824-315">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and route commands, in memory, to the right command handlers.</span></span> <span data-ttu-id="3e824-316">Průvodce také navrhuje použití [chování](https://github.com/jbogard/MediatR/wiki/Behaviors) s cílem oddělit průřezové obavy.</span><span class="sxs-lookup"><span data-stu-id="3e824-316">The guide also proposes applying [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="3e824-317">Pro implementaci v .NET Core je k dispozici více knihoven s otevřeným zdrojovým kódem, které implementují vzor Mediator.</span><span class="sxs-lookup"><span data-stu-id="3e824-317">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="3e824-318">Knihovna použitá v této příručce je open-source knihovna [MediatR](https://github.com/jbogard/MediatR) (vytvořená Jimmy Bogard), ale můžete použít jiný přístup.</span><span class="sxs-lookup"><span data-stu-id="3e824-318">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="3e824-319">MediatR je malá a jednoduchá knihovna, která umožňuje zpracovávat zprávy v paměti jako příkaz při použití dekorátorů nebo chování.</span><span class="sxs-lookup"><span data-stu-id="3e824-319">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="3e824-320">Použití vzoru mediátoru pomáhá snížit párování a izolovat obavy požadované práce, zatímco automatické připojení k obslužné rutině, která provádí tuto práci – v tomto případě k obslužné rutině příkazů.</span><span class="sxs-lookup"><span data-stu-id="3e824-320">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="3e824-321">Dalším dobrým důvodem pro použití mediator vzor byl vysvětlen Jimmy Bogard při kontrole této příručky:</span><span class="sxs-lookup"><span data-stu-id="3e824-321">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

> <span data-ttu-id="3e824-322">Myslím, že by stálo za zmínku testování zde - poskytuje pěkný konzistentní okno do chování vašeho systému.</span><span class="sxs-lookup"><span data-stu-id="3e824-322">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="3e824-323">Požadavek-in, odpověď-out. Zjistili jsme, že aspekt docela cenné při budování důsledně chovat testy.</span><span class="sxs-lookup"><span data-stu-id="3e824-323">Request-in, response-out. We've found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="3e824-324">Nejprve se podívejme na ukázkový řadič WebAPI, kde byste skutečně použili objekt mediátora.</span><span class="sxs-lookup"><span data-stu-id="3e824-324">First, let's look at a sample WebAPI controller where you actually would use the mediator object.</span></span> <span data-ttu-id="3e824-325">Pokud jste nepoužívali objekt mediátoru, budete muset vložit všechny závislosti pro tento řadič, věci jako objekt protokolování a další.</span><span class="sxs-lookup"><span data-stu-id="3e824-325">If you weren't using the mediator object, you'd need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="3e824-326">Proto by konstruktor být poměrně složité.</span><span class="sxs-lookup"><span data-stu-id="3e824-326">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="3e824-327">Na druhou stranu, pokud použijete objekt mediátoru, konstruktor řadiče může být mnohem jednodušší, jen s několika závislostmi namísto mnoha závislostí, pokud jste měli jednu na operaci průřezu, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3e824-327">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class MyMicroserviceController : Controller
{
    public MyMicroserviceController(IMediator mediator,
                                    IMyMicroserviceQueries microserviceQueries)
    {
        // ...
    }
}
```

<span data-ttu-id="3e824-328">Uvidíte, že mediátor poskytuje čistý a štíhlý konstruktor řadiče webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="3e824-328">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="3e824-329">Kromě toho v rámci metody kontroleru kód pro odeslání příkazu do objektu mediátora je téměř jeden řádek:</span><span class="sxs-lookup"><span data-stu-id="3e824-329">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> ExecuteBusinessOperation([FromBody]RunOpCommand
                                                               runOperationCommand)
{
    var commandResult = await _mediator.SendAsync(runOperationCommand);

    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

### <a name="implement-idempotent-commands"></a><span data-ttu-id="3e824-330">Implementace idempotentních příkazů</span><span class="sxs-lookup"><span data-stu-id="3e824-330">Implement idempotent Commands</span></span>

<span data-ttu-id="3e824-331">V **eShopOnContainers**, pokročilejší příklad než výše je odeslání CreateOrderCommand objekt z objednávání mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="3e824-331">In **eShopOnContainers**, a more advanced example than the above is submitting a CreateOrderCommand object from the Ordering microservice.</span></span> <span data-ttu-id="3e824-332">Ale protože objednání obchodní proces je trochu složitější a v našem případě se skutečně spustí v mikroslužbě košíku, tato akce odeslání CreateOrderCommand objekt se provádí z obslužné rutiny události integrace s názvem [UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) namísto jednoduchého řadiče WebAPI volána z klientské aplikace jako v předchozím jednoduššípříkladu.</span><span class="sxs-lookup"><span data-stu-id="3e824-332">But since the Ordering business process is a bit more complex and, in our case, it actually starts in the Basket microservice, this action of submitting the CreateOrderCommand object is performed from an integration-event handler named [UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) instead of a simple WebAPI controller called from the client App as in the previous simpler example.</span></span>

<span data-ttu-id="3e824-333">Nicméně, akce odeslání příkazu MediatR je docela podobný, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="3e824-333">Nevertheless, the action of submitting the Command to MediatR is pretty similar, as shown in the following code.</span></span>

```csharp
var createOrderCommand = new CreateOrderCommand(eventMsg.Basket.Items,
                                                eventMsg.UserId, eventMsg.City,
                                                eventMsg.Street, eventMsg.State,
                                                eventMsg.Country, eventMsg.ZipCode,
                                                eventMsg.CardNumber,
                                                eventMsg.CardHolderName,
                                                eventMsg.CardExpiration,
                                                eventMsg.CardSecurityNumber,
                                                eventMsg.CardTypeId);

var requestCreateOrder = new IdentifiedCommand<CreateOrderCommand,bool>(createOrderCommand,
                                                                        eventMsg.RequestId);
result = await _mediator.Send(requestCreateOrder);
```

<span data-ttu-id="3e824-334">Tento případ je však také trochu pokročilejší, protože také implementujeme idempotentní příkazy.</span><span class="sxs-lookup"><span data-stu-id="3e824-334">However, this case is also a little bit more advanced because we're also implementing idempotent commands.</span></span> <span data-ttu-id="3e824-335">Proces CreateOrderCommand by měl být idempotentní, takže pokud je stejná zpráva duplikována prostřednictvím sítě, z jakéhokoli důvodu, jako je opakování, bude stejný obchodní příkaz zpracován pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="3e824-335">The CreateOrderCommand process should be idempotent, so if the same message comes duplicated through the network, because of any reason, like retries, the same business order will be processed just once.</span></span>

<span data-ttu-id="3e824-336">To je implementováno zabalením obchodního příkazu (v tomto případě CreateOrderCommand) a vložením do obecného IdentifiedCommand, který je sledován ID každé zprávy přicházející prostřednictvím sítě, která musí být idempotentní.</span><span class="sxs-lookup"><span data-stu-id="3e824-336">This is implemented by wrapping the business command (in this case CreateOrderCommand) and embedding it into a generic IdentifiedCommand which is tracked by an ID of every message coming through the network that has to be idempotent.</span></span>

<span data-ttu-id="3e824-337">V níže uvedeném kódu uvidíte, že IdentifiedCommand není nic jiného než DTO s a ID plus zabalené obchodní příkaz objektu.</span><span class="sxs-lookup"><span data-stu-id="3e824-337">In the code below, you can see that the IdentifiedCommand is nothing more than a DTO with and ID plus the wrapped business command object.</span></span>

```csharp
public class IdentifiedCommand<T, R> : IRequest<R>
    where T : IRequest<R>
{
    public T Command { get; }
    public Guid Id { get; }
    public IdentifiedCommand(T command, Guid id)
    {
        Command = command;
        Id = id;
    }
}
```

<span data-ttu-id="3e824-338">Potom CommandHandler pro IdentifiedCommand s názvem [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) bude v podstatě zkontrolovat, zda ID přichází jako součást zprávy již existuje v tabulce.</span><span class="sxs-lookup"><span data-stu-id="3e824-338">Then the CommandHandler for the IdentifiedCommand named [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) will basically check if the ID coming as part of the message already exists in a table.</span></span> <span data-ttu-id="3e824-339">Pokud již existuje, tento příkaz nebude znovu zpracován, takže se chová jako idempotentní příkaz.</span><span class="sxs-lookup"><span data-stu-id="3e824-339">If it already exists, that command won't be processed again, so it behaves as an idempotent command.</span></span> <span data-ttu-id="3e824-340">Tento kód infrastruktury `_requestManager.ExistAsync` se provádí pomocí volání metody níže.</span><span class="sxs-lookup"><span data-stu-id="3e824-340">That infrastructure code is performed by the `_requestManager.ExistAsync` method call below.</span></span>

```csharp
// IdentifiedCommandHandler.cs
public class IdentifiedCommandHandler<T, R> :
                                   IAsyncRequestHandler<IdentifiedCommand<T, R>, R>
                                   where T : IRequest<R>
{
    private readonly IMediator _mediator;
    private readonly IRequestManager _requestManager;

    public IdentifiedCommandHandler(IMediator mediator,
                                    IRequestManager requestManager)
    {
        _mediator = mediator;
        _requestManager = requestManager;
    }

    protected virtual R CreateResultForDuplicateRequest()
    {
        return default(R);
    }

    public async Task<R> Handle(IdentifiedCommand<T, R> message)
    {
        var alreadyExists = await _requestManager.ExistAsync(message.Id);
        if (alreadyExists)
        {
            return CreateResultForDuplicateRequest();
        }
        else
        {
            await _requestManager.CreateRequestForCommandAsync<T>(message.Id);

            // Send the embedded business command to mediator
            // so it runs its related CommandHandler
            var result = await _mediator.Send(message.Command);

            return result;
        }
    }
}
```

<span data-ttu-id="3e824-341">Vzhledem k tomu, identifiedcommand funguje jako obálka obchodního příkazu, když obchodní příkaz musí být zpracovány, protože není opakované Id, pak se, že vnitřní obchodní příkaz `_mediator.Send(message.Command)`a re-odešle jej mediator, jako v poslední části kódu je uvedeno výše při spuštění , z [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span><span class="sxs-lookup"><span data-stu-id="3e824-341">Since the IdentifiedCommand acts like a business command's envelope, when the business command needs to be processed because it is not a repeated Id, then it takes that inner business command and re-submits it to Mediator, as in the last part of the code shown above when running `_mediator.Send(message.Command)`, from the [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span></span>

<span data-ttu-id="3e824-342">Když to dělá, bude propojovat a spouštět obslužnou rutinu obchodního příkazu, v tomto případě [CreateOrderCommandHandler,](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) který spouštějí transakce proti objednávání databáze, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="3e824-342">When doing that, it will link and run the business command handler, in this case, the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) which is running transactions against the Ordering database, as shown in the following code.</span></span>

```csharp
// CreateOrderCommandHandler.cs
public class CreateOrderCommandHandler
                                   : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
                                     IOrderRepository orderRepository,
                                     IIdentityService identityService)
    {
        _orderRepository = orderRepository ??
                          throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ??
                          throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ??
                                 throw new ArgumentNullException(nameof(mediator));
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        // Add/Update the Buyer AggregateRoot
        var address = new Address(message.Street, message.City, message.State,
                                  message.Country, message.ZipCode);
        var order = new Order(message.UserId, address, message.CardTypeId,
                              message.CardNumber, message.CardSecurityNumber,
                              message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                               item.Discount, item.PictureUrl, item.Units);
        }

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
    }
}
```

### <a name="register-the-types-used-by-mediatr"></a><span data-ttu-id="3e824-343">Registrace typů používaných programem MediatR</span><span class="sxs-lookup"><span data-stu-id="3e824-343">Register the types used by MediatR</span></span>

<span data-ttu-id="3e824-344">Aby byl MediatR informován o třídách obslužné rutiny příkazů, musíte zaregistrovat třídy mediátorů a třídy obslužné rutiny příkazů v kontejneru IoC.</span><span class="sxs-lookup"><span data-stu-id="3e824-344">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="3e824-345">Ve výchozím nastavení používá MediatR Autofac jako kontejner IoC, ale můžete také použít předdefinovaný ASP.NET kontejneru Core IoC nebo jiného kontejneru podporovaného programem MediatR.</span><span class="sxs-lookup"><span data-stu-id="3e824-345">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="3e824-346">Následující kód ukazuje, jak zaregistrovat typy a příkazy mediátora při použití modulů Autofac.</span><span class="sxs-lookup"><span data-stu-id="3e824-346">The following code shows how to register Mediator's types and commands when using Autofac modules.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
    }
}
```

<span data-ttu-id="3e824-347">To je místo, kde "kouzlo se stane" s MediatR.</span><span class="sxs-lookup"><span data-stu-id="3e824-347">This is where "the magic happens" with MediatR.</span></span>

<span data-ttu-id="3e824-348">Vzhledem k tomu, `IAsyncRequestHandler<T>` že každý příkaz obslužná rutina `RegisteredAssemblyTypes` implementuje `IAsyncRequestHandler` obecné rozhraní, `CommandHandlers` při `Commands`registraci sestavení, kód `CommandHandler` registruje se všemi typy označené jako při vztahu s jejich , díky vztahu uvedenéve třídě, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="3e824-348">Because each command handler implements the generic `IAsyncRequestHandler<T>` interface, when registering the assemblies, the code registers with `RegisteredAssemblyTypes` all the types marked as `IAsyncRequestHandler` while relating the `CommandHandlers` with their `Commands`, thanks to the relationship stated at the `CommandHandler` class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="3e824-349">To je kód, který koreluje příkazy s obslužnými rutinami příkazů.</span><span class="sxs-lookup"><span data-stu-id="3e824-349">That is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="3e824-350">Obslužná rutina je pouze `RequestHandler<T>`jednoduchá třída, ale dědí z , kde T je typ příkazu a MediatR zajišťuje, že je vyvolána se správnou datovou částí (příkaz).</span><span class="sxs-lookup"><span data-stu-id="3e824-350">The handler is just a simple class, but it inherits from `RequestHandler<T>`, where T is the command type, and MediatR makes sure it is invoked with the correct payload (the command).</span></span>

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a><span data-ttu-id="3e824-351">Použití průřezových zájmů při zpracování příkazů pomocí příkazů v programu MediatR</span><span class="sxs-lookup"><span data-stu-id="3e824-351">Apply cross-cutting concerns when processing commands with the Behaviors in MediatR</span></span>

<span data-ttu-id="3e824-352">Je tu ještě jedna věc: možnost aplikovat průřezové obavy na potrubí mediátorů.</span><span class="sxs-lookup"><span data-stu-id="3e824-352">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="3e824-353">Můžete také vidět na konci kódu registračního modulu Autofac, jak registruje typ chování, konkrétně vlastní LoggingBehavior třídy a ValidatorBehavior třídy.</span><span class="sxs-lookup"><span data-stu-id="3e824-353">You can also see at the end of the Autofac registration module code how it registers a behavior type, specifically, a custom LoggingBehavior class and a ValidatorBehavior class.</span></span> <span data-ttu-id="3e824-354">Ale můžete přidat i další vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="3e824-354">But you could add other custom behaviors, too.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IAsyncRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IAsyncRequestHandler<,>));
        // Other types registration
        //...
        builder.RegisterGeneric(typeof(LoggingBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
        builder.RegisterGeneric(typeof(ValidatorBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
    }
}
```

<span data-ttu-id="3e824-355">Že [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) třídy lze implementovat jako následující kód, který protokoluje informace o příkazu obslužné rutiny, která je spuštěna a zda byla úspěšná nebo ne.</span><span class="sxs-lookup"><span data-stu-id="3e824-355">That [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

```csharp
public class LoggingBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly ILogger<LoggingBehavior<TRequest, TResponse>> _logger;
    public LoggingBehavior(ILogger<LoggingBehavior<TRequest, TResponse>> logger) =>
                                                                  _logger = logger;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        _logger.LogInformation($"Handling {typeof(TRequest).Name}");
        var response = await next();
        _logger.LogInformation($"Handled {typeof(TResponse).Name}");
        return response;
    }
}
```

<span data-ttu-id="3e824-356">Pouze implementací této třídy chování a registrací v kanálu (v MediatorModule výše), všechny příkazy zpracované prostřednictvím MediatR bude protokolování informací o provádění.</span><span class="sxs-lookup"><span data-stu-id="3e824-356">Just by implementing this behavior class and by registering it in the pipeline (in the MediatorModule above), all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="3e824-357">EShopOnContainers objednávání mikroslužby také platí druhé chování pro základní ověření, [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) třídy, která závisí na knihovně [FluentValidation,](https://github.com/JeremySkinner/FluentValidation) jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="3e824-357">The eShopOnContainers ordering microservice also applies a second behavior for basic validations, the [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

```csharp
public class ValidatorBehavior<TRequest, TResponse>
         : IPipelineBehavior<TRequest, TResponse>
{
    private readonly IValidator<TRequest>[] _validators;
    public ValidatorBehavior(IValidator<TRequest>[] validators) =>
                                                         _validators = validators;

    public async Task<TResponse> Handle(TRequest request,
                                        RequestHandlerDelegate<TResponse> next)
    {
        var failures = _validators
            .Select(v => v.Validate(request))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();

        if (failures.Any())
        {
            throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                        new ValidationException("Validation exception", failures));
        }

        var response = await next();
        return response;
    }
}
```

<span data-ttu-id="3e824-358">Chování zde vyvolává výjimku, pokud se ověření nezdaří, ale můžete také vrátit výsledný objekt, který obsahuje výsledek příkazu, pokud byl úspěšný, nebo ověřovací zprávy v případě, že tomu tak nebylo.</span><span class="sxs-lookup"><span data-stu-id="3e824-358">The behavior here is raising an exception if validation fails, but you could also return a result object, containing the command result if it succeeded or the validation messages in case it didn't.</span></span> <span data-ttu-id="3e824-359">To by pravděpodobně usnadnilo zobrazení výsledků ověření uživateli.</span><span class="sxs-lookup"><span data-stu-id="3e824-359">This would probably make it easier to display validation results to the user.</span></span>

<span data-ttu-id="3e824-360">Potom na základě knihovny [FluentValidation](https://github.com/JeremySkinner/FluentValidation) jsme vytvořili ověření dat předaná pomocí příkazu CreateOrderCommand, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="3e824-360">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

```csharp
public class CreateOrderCommandValidator : AbstractValidator<CreateOrderCommand>
{
    public CreateOrderCommandValidator()
    {
        RuleFor(command => command.City).NotEmpty();
        RuleFor(command => command.Street).NotEmpty();
        RuleFor(command => command.State).NotEmpty();
        RuleFor(command => command.Country).NotEmpty();
        RuleFor(command => command.ZipCode).NotEmpty();
        RuleFor(command => command.CardNumber).NotEmpty().Length(12, 19);
        RuleFor(command => command.CardHolderName).NotEmpty();
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).Must(ContainOrderItems).WithMessage("No order items found");
    }

    private bool BeValidExpirationDate(DateTime dateTime)
    {
        return dateTime >= DateTime.UtcNow;
    }

    private bool ContainOrderItems(IEnumerable<OrderItemDTO> orderItems)
    {
        return orderItems.Any();
    }
}

```

<span data-ttu-id="3e824-361">Můžete vytvořit další ověření.</span><span class="sxs-lookup"><span data-stu-id="3e824-361">You could create additional validations.</span></span> <span data-ttu-id="3e824-362">Toto je velmi čistý a elegantní způsob, jak implementovat ověření příkazu.</span><span class="sxs-lookup"><span data-stu-id="3e824-362">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="3e824-363">Podobným způsobem můžete implementovat další chování pro další aspekty nebo průřezové obavy, které chcete použít na příkazy při jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="3e824-363">In a similar way, you could implement other behaviors for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="3e824-364">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="3e824-364">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="3e824-365">Vzor mediátora</span><span class="sxs-lookup"><span data-stu-id="3e824-365">The mediator pattern</span></span>

- <span data-ttu-id="3e824-366">**Vzor mediátora** </span><span class="sxs-lookup"><span data-stu-id="3e824-366">**Mediator pattern** </span></span>\
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a><span data-ttu-id="3e824-367">Dekoratér vzor</span><span class="sxs-lookup"><span data-stu-id="3e824-367">The decorator pattern</span></span>

- <span data-ttu-id="3e824-368">**Dekoratér vzor** </span><span class="sxs-lookup"><span data-stu-id="3e824-368">**Decorator pattern** </span></span>\
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="3e824-369">Zprostředkovatel (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="3e824-369">MediatR (Jimmy Bogard)</span></span>

- <span data-ttu-id="3e824-370">**Zprostředkovatel.**</span><span class="sxs-lookup"><span data-stu-id="3e824-370">**MediatR.**</span></span> <span data-ttu-id="3e824-371">úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="3e824-371">GitHub repo.</span></span> \
  <https://github.com/jbogard/MediatR>

- <span data-ttu-id="3e824-372">**CQRS s MediatR a AutoMapper** </span><span class="sxs-lookup"><span data-stu-id="3e824-372">**CQRS with MediatR and AutoMapper** </span></span>\
  <https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/>

- <span data-ttu-id="3e824-373">**Dejte své ovladače na dietu: POSTs a příkazy.**</span><span class="sxs-lookup"><span data-stu-id="3e824-373">**Put your controllers on a diet: POSTs and commands.**</span></span> \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- <span data-ttu-id="3e824-374">**Řešení průřezových problémů pomocí potrubí mediátorů** </span><span class="sxs-lookup"><span data-stu-id="3e824-374">**Tackling cross-cutting concerns with a mediator pipeline** </span></span>\
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- <span data-ttu-id="3e824-375">**CQRS a REST: perfektní shoda** </span><span class="sxs-lookup"><span data-stu-id="3e824-375">**CQRS and REST: the perfect match** </span></span>\
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- <span data-ttu-id="3e824-376">**Příklady kanálu MediatR** </span><span class="sxs-lookup"><span data-stu-id="3e824-376">**MediatR Pipeline Examples** </span></span>\
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- <span data-ttu-id="3e824-377">**Svislá testovací svítidla pro mediatr a ASP.NET jádra** </span><span class="sxs-lookup"><span data-stu-id="3e824-377">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core** </span></span>\
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- <span data-ttu-id="3e824-378">**Byla vydána rozšíření MediatR pro vkládání závislostí společnosti Microsoft** </span><span class="sxs-lookup"><span data-stu-id="3e824-378">**MediatR Extensions for Microsoft Dependency Injection Released** </span></span>\
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a><span data-ttu-id="3e824-379">Plynulá validace</span><span class="sxs-lookup"><span data-stu-id="3e824-379">Fluent validation</span></span>

- <span data-ttu-id="3e824-380">**Jeremy Skinner. FluentValidation.**</span><span class="sxs-lookup"><span data-stu-id="3e824-380">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="3e824-381">úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="3e824-381">GitHub repo.</span></span> \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> <span data-ttu-id="3e824-382">[Předchozí](microservice-application-layer-web-api-design.md)
> [další](../implement-resilient-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="3e824-382">[Previous](microservice-application-layer-web-api-design.md)
[Next](../implement-resilient-applications/index.md)</span></span>
