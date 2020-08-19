---
title: Implementace aplikační vrstvy mikroslužby pomocí webového rozhraní API
description: Seznamte se s vkládáním závislostí a vzorci a jejich podrobnostmi o implementaci v aplikační vrstvě webového rozhraní API.
ms.date: 08/17/2020
ms.openlocfilehash: 72395acafb403a4e34858eb2b982ec83b9f3cee1
ms.sourcegitcommit: cbb19e56d48cf88375d35d0c27554d4722761e0d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/19/2020
ms.locfileid: "88608114"
---
# <a name="implement-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="6f2f9-103">Implementace aplikační vrstvy mikroslužeb pomocí webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="6f2f9-103">Implement the microservice application layer using the Web API</span></span>

## <a name="use-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="6f2f9-104">Použití injektáže závislosti k vložení objektů infrastruktury do vrstvy aplikace</span><span class="sxs-lookup"><span data-stu-id="6f2f9-104">Use Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="6f2f9-105">Jak bylo zmíněno dříve, aplikační vrstvu lze implementovat jako součást artefaktu (sestavení), který sestavíte, například v rámci projektu webového rozhraní API nebo projektu webové aplikace MVC.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-105">As mentioned previously, the application layer can be implemented as part of the artifact (assembly) you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="6f2f9-106">V případě mikroslužby vytvořené pomocí ASP.NET Core bude aplikační vrstva obvykle vaší knihovnou webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-106">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="6f2f9-107">Pokud chcete oddělit to, co pochází z ASP.NET Core (jeho infrastruktura a řadiče) z vlastního kódu vrstvy aplikace, můžete také umístit vrstvu aplikace do samostatné knihovny tříd, ale to je volitelné.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-107">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="6f2f9-108">Například kód aplikační vrstvy řazení mikroslužba je implementován přímo jako součást projektu **objednávání. API** (ASP.NET Core projekt webového rozhraní API), jak je znázorněno na obrázku 7-23.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-108">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 7-23.</span></span>

:::image type="complex" source="./media/microservice-application-layer-implementation-web-api/ordering-api-microservice.png" alt-text="Snímek obrazovky objednávání. rozhraní API mikroslužeb v Průzkumník řešení.":::
<span data-ttu-id="6f2f9-110">Průzkumník řešení zobrazení pořadí. rozhraní API mikroslužby, které zobrazuje podsložky ve složce aplikace: chování, příkazy, DomainEventHandlers, IntegrationEvents, modely, dotazy a ověřování.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-110">The Solution Explorer view of the Ordering.API microservice, showing the subfolders under the Application folder: Behaviors, Commands, DomainEventHandlers, IntegrationEvents, Models, Queries, and Validations.</span></span>
:::image-end:::

<span data-ttu-id="6f2f9-111">**Obrázek 7-23**.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-111">**Figure 7-23**.</span></span> <span data-ttu-id="6f2f9-112">Aplikační vrstva v projektu objednávání. API ASP.NET Core Web API</span><span class="sxs-lookup"><span data-stu-id="6f2f9-112">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="6f2f9-113">ASP.NET Core obsahuje jednoduchý [integrovaný kontejner IOC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (reprezentovaný rozhraním IServiceProvider), který podporuje vkládání konstruktoru ve výchozím nastavení a ASP.NET zpřístupňuje určité služby prostřednictvím di.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-113">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="6f2f9-114">ASP.NET Core používá termín *služby* pro jakýkoli typ, který zaregistrujete, který bude VLOŽEN přes di.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-114">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="6f2f9-115">Předdefinované služby kontejneru v metodě ConfigureServices ve třídě Startup vaší aplikace nakonfigurujete.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-115">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="6f2f9-116">Vaše závislosti jsou implementované v rámci služeb, které typ vyžaduje a které zaregistrujete do kontejneru IoC.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-116">Your dependencies are implemented in the services that a type needs and that you register in the IoC container.</span></span>

<span data-ttu-id="6f2f9-117">Obvykle chcete vložit závislosti, které implementují objekty infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-117">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="6f2f9-118">Typickou závislostí pro vkládání je úložiště.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-118">A typical dependency to inject is a repository.</span></span> <span data-ttu-id="6f2f9-119">Mohli byste ale vložit jakoukoli další závislost infrastruktury, kterou můžete mít.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-119">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="6f2f9-120">Pro jednodušší implementace můžete přímo vložit objekt vzorce pracovní jednotky (objekt EF DbContext), protože DBContext je také implementace objektů trvalé infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-120">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="6f2f9-121">V následujícím příkladu uvidíte, jak .NET Core vkládá požadované objekty úložiště prostřednictvím konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-121">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="6f2f9-122">Třída je obslužná rutina příkazu, která bude zahrnuta v další části.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-122">The class is a command handler, which will get covered in the next section.</span></span>

```csharp
public class CreateOrderCommandHandler
        : IRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;
    private readonly IOrderingIntegrationEventService _orderingIntegrationEventService;
    private readonly ILogger<CreateOrderCommandHandler> _logger;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
        IOrderingIntegrationEventService orderingIntegrationEventService,
        IOrderRepository orderRepository,
        IIdentityService identityService,
        ILogger<CreateOrderCommandHandler> logger)
    {
        _orderRepository = orderRepository ?? throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ?? throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ?? throw new ArgumentNullException(nameof(mediator));
        _orderingIntegrationEventService = orderingIntegrationEventService ?? throw new ArgumentNullException(nameof(orderingIntegrationEventService));
        _logger = logger ?? throw new ArgumentNullException(nameof(logger));
    }

    public async Task<bool> Handle(CreateOrderCommand message, CancellationToken cancellationToken)
    {
        // Add Integration event to clean the basket
        var orderStartedIntegrationEvent = new OrderStartedIntegrationEvent(message.UserId);
        await _orderingIntegrationEventService.AddAndSaveEventAsync(orderStartedIntegrationEvent);

        // Add/Update the Buyer AggregateRoot
        // DDD patterns comment: Add child entities and value-objects through the Order Aggregate-Root
        // methods and constructor so validations, invariants and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State, message.Country, message.ZipCode);
        var order = new Order(message.UserId, message.UserName, address, message.CardTypeId, message.CardNumber, message.CardSecurityNumber, message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice, item.Discount, item.PictureUrl, item.Units);
        }

        _logger.LogInformation("----- Creating Order - Order: {@Order}", order);

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync(cancellationToken);
    }
}

```

<span data-ttu-id="6f2f9-123">Třída používá vložená úložiště ke spuštění transakce a uchování změn stavu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-123">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="6f2f9-124">Nezáleží na tom, zda je tato třída obslužná rutina příkazu, metoda ASP.NET Core webového rozhraní API nebo [DDD aplikační službu](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span><span class="sxs-lookup"><span data-stu-id="6f2f9-124">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="6f2f9-125">Je to nakonec jednoduchá třída, která používá úložiště, entity domény a další koordinaci aplikací podobným způsobem jako obslužná rutina příkazu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-125">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="6f2f9-126">Vkládání závislostí funguje stejným způsobem pro všechny uvedené třídy, jako v příkladu pomocí příkazu DI založeného na konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-126">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="register-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="6f2f9-127">Zaregistrujte typy implementace závislosti a rozhraní nebo abstrakce.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-127">Register the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="6f2f9-128">Před použitím objektů, které byly vloženy prostřednictvím konstruktorů, je třeba znát, kam mají být registrována rozhraní a třídy, které tvoří objekty vložené do tříd aplikace prostřednictvím DI.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-128">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="6f2f9-129">(Jako DI založené na konstruktoru, jak je uvedeno výše.)</span><span class="sxs-lookup"><span data-stu-id="6f2f9-129">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="use-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="6f2f9-130">Použijte integrovaný kontejner IoC poskytovaný ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6f2f9-130">Use the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="6f2f9-131">Použijete-li integrovaný kontejner IoC poskytovaný ASP.NET Core, zaregistrujete typy, které chcete vložit do metody ConfigureServices v souboru Startup.cs, jak je uvedeno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="6f2f9-131">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

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

<span data-ttu-id="6f2f9-132">Nejběžnějším vzorem při registraci typů v kontejneru IoC je registrace páru typů – rozhraní a související implementační třídy.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-132">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="6f2f9-133">Pak při vyžádání objektu z kontejneru IoC prostřednictvím libovolného konstruktoru si vyžádáte objekt určitého typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-133">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="6f2f9-134">Například v předchozím příkladu poslední řádek uvádí, že pokud některý z konstruktorů má závislost na IMyCustomRepository (rozhraní nebo abstrakci), kontejner IoC vloží instanci třídy implementace MyCustomSQLServerRepository.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-134">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="use-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="6f2f9-135">Pro registraci automatických typů použít knihovnu Scrutor</span><span class="sxs-lookup"><span data-stu-id="6f2f9-135">Use the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="6f2f9-136">Při použití funkce DI v .NET Core můžete chtít skenovat sestavení a automaticky registrovat jeho typy podle konvencí.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-136">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="6f2f9-137">Tato funkce není v současnosti k dispozici v ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-137">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="6f2f9-138">Pro to však můžete použít knihovnu [Scrutor](https://github.com/khellang/Scrutor) .</span><span class="sxs-lookup"><span data-stu-id="6f2f9-138">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="6f2f9-139">Tento přístup je vhodný, když máte desítky typů, které je třeba registrovat v kontejneru IoC.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-139">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="6f2f9-140">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="6f2f9-140">Additional resources</span></span>

- <span data-ttu-id="6f2f9-141">**Matthew krále. Registrace služeb pomocí Scrutor** </span><span class="sxs-lookup"><span data-stu-id="6f2f9-141">**Matthew King. Registering services with Scrutor** </span></span>\
  <https://www.mking.net/blog/registering-services-with-scrutor>

- <span data-ttu-id="6f2f9-142">**Kristian Hellang. Scrutor.**</span><span class="sxs-lookup"><span data-stu-id="6f2f9-142">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="6f2f9-143">Úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-143">GitHub repo.</span></span> \
  <https://github.com/khellang/Scrutor>

#### <a name="use-autofac-as-an-ioc-container"></a><span data-ttu-id="6f2f9-144">Použití Autofac jako kontejneru IoC</span><span class="sxs-lookup"><span data-stu-id="6f2f9-144">Use Autofac as an IoC container</span></span>

<span data-ttu-id="6f2f9-145">Můžete také použít další kontejnery IoC a zapojit je do kanálu ASP.NET Core, jako při řazení mikroslužby v eShopOnContainers, která používá [Autofac](https://autofac.org/).</span><span class="sxs-lookup"><span data-stu-id="6f2f9-145">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="6f2f9-146">Při použití Autofac obvykle zaregistrujete typy přes moduly, které umožňují rozdělit typy registrace mezi více soubory v závislosti na tom, kde jsou typy aplikace, stejně jako typy aplikací distribuované napříč více knihovnami tříd.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-146">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="6f2f9-147">Následuje příklad, který je [modul aplikace Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) pro projekt [Web API pro objednávání. API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) s typy, které budete chtít vložit.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-147">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

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

<span data-ttu-id="6f2f9-148">Autofac má také funkci pro [skenování sestavení a typů registru podle konvencí názvů](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span><span class="sxs-lookup"><span data-stu-id="6f2f9-148">Autofac also has a feature to [scan assemblies and register types by name conventions](https://autofac.readthedocs.io/en/latest/register/scanning.html).</span></span>

<span data-ttu-id="6f2f9-149">Proces registrace a koncepty jsou velmi podobné způsobu, jakým můžete registrovat typy s integrovaným ASP.NET Core kontejnerem IoC, ale syntaxe při použití Autofac je trochu odlišná.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-149">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core IoC container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="6f2f9-150">V příkladu kódu je abstrakce IOrderRepository zaregistrována spolu s implementační třídou OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-150">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="6f2f9-151">To znamená, že pokaždé, když konstruktor deklaruje závislost prostřednictvím abstrakce nebo rozhraní IOrderRepository, kontejner IoC vloží instanci třídy OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-151">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="6f2f9-152">Typ rozsahu instance Určuje, jak je instance sdílena mezi požadavky na stejnou službu nebo závislost.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-152">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="6f2f9-153">Při vytvoření žádosti o závislost může kontejner IoC vrátit následující:</span><span class="sxs-lookup"><span data-stu-id="6f2f9-153">When a request is made for a dependency, the IoC container can return the following:</span></span>

- <span data-ttu-id="6f2f9-154">Jedna instance na rozsah doby života (v kontejneru ASP.NET Core IoC jako *obor*).</span><span class="sxs-lookup"><span data-stu-id="6f2f9-154">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

- <span data-ttu-id="6f2f9-155">Nová instance na závislost (dále uváděná v kontejneru ASP.NET Core IoC jako *přechodné*).</span><span class="sxs-lookup"><span data-stu-id="6f2f9-155">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

- <span data-ttu-id="6f2f9-156">Jedna instance sdílená napříč všemi objekty pomocí kontejneru IoC (dále v kontejneru ASP.NET Core IoC jako *singleton*).</span><span class="sxs-lookup"><span data-stu-id="6f2f9-156">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="6f2f9-157">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="6f2f9-157">Additional resources</span></span>

- <span data-ttu-id="6f2f9-158">**Úvod do injektáže závislosti v ASP.NET Core** </span><span class="sxs-lookup"><span data-stu-id="6f2f9-158">**Introduction to Dependency Injection in ASP.NET Core** </span></span>\
  [https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection](/aspnet/core/fundamentals/dependency-injection)

- <span data-ttu-id="6f2f9-159">**Autofac.**</span><span class="sxs-lookup"><span data-stu-id="6f2f9-159">**Autofac.**</span></span> <span data-ttu-id="6f2f9-160">Oficiální dokumentace.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-160">Official documentation.</span></span> \
  <https://docs.autofac.org/en/latest/>

- <span data-ttu-id="6f2f9-161">**Porovnávání ASP.NET Core IoCch kontejnerových služeb s Autofac IoC instancemi kontejnerů – Cesar de la Torre.**</span><span class="sxs-lookup"><span data-stu-id="6f2f9-161">**Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes - Cesar de la Torre.**</span></span> \
  <https://devblogs.microsoft.com/cesardelatorre/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/>

## <a name="implement-the-command-and-command-handler-patterns"></a><span data-ttu-id="6f2f9-162">Implementace vzorů obslužných rutin příkazů a příkazů</span><span class="sxs-lookup"><span data-stu-id="6f2f9-162">Implement the Command and Command Handler patterns</span></span>

<span data-ttu-id="6f2f9-163">V příkladu typu DI-through-konstruktoru zobrazeném v předchozí části kontejner IoC vložil úložiště do konstruktoru ve třídě.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-163">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="6f2f9-164">Ale přesně tam, kde byly vloženy?</span><span class="sxs-lookup"><span data-stu-id="6f2f9-164">But exactly where were they injected?</span></span> <span data-ttu-id="6f2f9-165">V jednoduchém webovém rozhraní API (například služba katalogu eShopOnContainers) je vložíte do úrovně řadiče MVC v konstruktoru kontroleru jako součást kanálu žádosti o ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-165">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers' level, in a controller constructor, as part of the request pipeline of ASP.NET Core.</span></span> <span data-ttu-id="6f2f9-166">Nicméně v úvodním kódu této části (třída [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) ze služby Ordering. API v eShopOnContainers) je vkládání závislostí provedeno prostřednictvím konstruktoru konkrétní obslužné rutiny příkazu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-166">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="6f2f9-167">Vysvětlete, co je obslužná rutina příkazu, a proč byste ji chtěli použít.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-167">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="6f2f9-168">Vzor příkazu je vnitřně spojen se vzorem CQRS, který byl představen dříve v této příručce.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-168">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="6f2f9-169">CQRS má dvě strany.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-169">CQRS has two sides.</span></span> <span data-ttu-id="6f2f9-170">První oblast se dotazuje pomocí zjednodušených dotazů s [dapperem](https://github.com/StackExchange/dapper-dot-net) Micro ORM, které bylo vysvětleno dříve.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-170">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="6f2f9-171">Druhá oblast je příkazy, které jsou výchozím bodem pro transakce, a vstupní kanál mimo službu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-171">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="6f2f9-172">Jak je znázorněno na obrázku 7-24, je vzor založený na přijímání příkazů ze strany klienta, jejich zpracování na základě pravidel doménové struktury a nakonec trvalého uchování stavů transakcemi.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-172">As shown in Figure 7-24, the pattern is based on accepting commands from the client-side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![Diagram znázorňující tok dat vysoké úrovně od klienta k databázi.](./media/microservice-application-layer-implementation-web-api/high-level-writes-side.png)

<span data-ttu-id="6f2f9-174">**Obrázek 7-24**.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-174">**Figure 7-24**.</span></span> <span data-ttu-id="6f2f9-175">Pohled na vysoké úrovni příkazů nebo "na straně transakčního" ve vzoru CQRS</span><span class="sxs-lookup"><span data-stu-id="6f2f9-175">High-level view of the commands or "transactional side" in a CQRS pattern</span></span>

<span data-ttu-id="6f2f9-176">Obrázek 7-24 ukazuje, že aplikace uživatelského rozhraní pošle příkaz prostřednictvím rozhraní API, které se načte do `CommandHandler` , který závisí na doménovém modelu a infrastruktuře, k aktualizaci databáze.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-176">Figure 7-24 shows that the UI app sends a command through the API that gets to a `CommandHandler`, that depends on the Domain model and the Infrastructure, to update the database.</span></span>

### <a name="the-command-class"></a><span data-ttu-id="6f2f9-177">Třída příkazu</span><span class="sxs-lookup"><span data-stu-id="6f2f9-177">The command class</span></span>

<span data-ttu-id="6f2f9-178">Příkaz je požadavek, aby systém provedl akci, která mění stav systému.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-178">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="6f2f9-179">Příkazy jsou naléhavé a měly by se zpracovat jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-179">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="6f2f9-180">Vzhledem k tomu, že jsou příkazy nezbytné, jsou obvykle pojmenovány pomocí příkazu v imperativní náladě (například "Create" nebo "Update") a mohou zahrnovat agregovaný typ, například CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-180">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="6f2f9-181">Na rozdíl od události není příkaz fakt z minulosti; je to jenom žádost, a proto může být zamítnutá.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-181">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="6f2f9-182">Příkazy mohou pocházet z uživatelského rozhraní v důsledku toho, že uživatel zahajuje požadavek, nebo ze správce procesů, když správce procesu nasměruje agregaci k provedení akce.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-182">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="6f2f9-183">Důležitou vlastností příkazu je, že by měl být zpracován jedním příjemcem jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-183">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="6f2f9-184">Důvodem je to, že příkaz je jediná akce nebo transakce, kterou chcete v aplikaci provést.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-184">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="6f2f9-185">Například příkaz pro vytvoření stejné objednávky by neměl být zpracován více než jednou.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-185">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="6f2f9-186">Jedná se o důležitý rozdíl mezi příkazy a událostmi.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-186">This is an important difference between commands and events.</span></span> <span data-ttu-id="6f2f9-187">Události se můžou zpracovávat víckrát, protože událost může zajímat spousta systémů nebo mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-187">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="6f2f9-188">Kromě toho je důležité, aby byl příkaz zpracován pouze jednou pro případ, že příkaz není idempotentní.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-188">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="6f2f9-189">Příkaz je idempotentní, pokud jej lze spustit vícekrát, aniž by došlo ke změně výsledku, buď z důvodu povahy příkazu, nebo z důvodu způsobu, jakým systém zpracovává příkaz.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-189">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="6f2f9-190">Je vhodné provést příkazy a aktualizovat idempotentní, když to dává smysl v rámci obchodních pravidel a invariant vaší domény.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-190">It is a good practice to make your commands and updates idempotent when it makes sense under your domain's business rules and invariants.</span></span> <span data-ttu-id="6f2f9-191">Pokud například chcete použít stejný příklad, pokud z nějakého důvodu (opakování logiky, hacker atd.) stejný příkaz CreateOrder dosáhne vašeho systému několikrát, měli byste být schopni ho identifikovat a zajistit, aby nevytvořili více objednávek.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-191">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="6f2f9-192">K tomu je třeba v operacích připojit nějaký druh identity a určit, zda byl příkaz nebo aktualizace již zpracována.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-192">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="6f2f9-193">Odešlete příkaz jednomu příjemci. nepublikujete příkaz.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-193">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="6f2f9-194">Publikování je pro události, které jsou ve skutečnosti, že došlo k nějaké situaci a může být zajímavá pro přijímače událostí.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-194">Publishing is for events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="6f2f9-195">V případě událostí Vydavatel nemá žádné obavy o to, které příjemce obdrží událost nebo co k tomu dostanou.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-195">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="6f2f9-196">Ale události související s doménou nebo integrací jsou již v předchozích oddílech představeny jiným scénářem.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-196">But domain or integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="6f2f9-197">Příkaz je implementován se třídou, která obsahuje datová pole nebo kolekce se všemi informacemi, které jsou potřeba ke spuštění tohoto příkazu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-197">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="6f2f9-198">Příkaz je speciální druh objektu Přenos dat (DTO), který se konkrétně používá k vyžádání změn nebo transakcí.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-198">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="6f2f9-199">Samotný příkaz je založen na přesně informacích, které jsou potřeba ke zpracování příkazu, a nic dalšího.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-199">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="6f2f9-200">Následující příklad ukazuje zjednodušenou `CreateOrderCommand` třídu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-200">The following example shows the simplified `CreateOrderCommand` class.</span></span> <span data-ttu-id="6f2f9-201">Toto je neproměnlivý příkaz, který se používá při řazení mikroslužby v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-201">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

```csharp
// DDD and CQRS patterns comment: Note that it is recommended to implement immutable Commands
// In this case, its immutability is achieved by having all the setters as private
// plus only being able to update the data just once, when creating the object through its constructor.
// References on Immutable Commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://docs.microsoft.com/dotnet/csharp/programming-guide/classes-and-structs/how-to-implement-a-lightweight-class-with-auto-implemented-properties

[DataContract]
public class CreateOrderCommand
    : IRequest<bool>
{
    [DataMember]
    private readonly List<OrderItemDTO> _orderItems;

    [DataMember]
    public string UserId { get; private set; }

    [DataMember]
    public string UserName { get; private set; }

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

    public CreateOrderCommand(List<BasketItem> basketItems, string userId, string userName, string city, string street, string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = basketItems.ToOrderItemsDTO().ToList();
        UserId = userId;
        UserName = userName;
        City = city;
        Street = street;
        State = state;
        Country = country;
        ZipCode = zipcode;
        CardNumber = cardNumber;
        CardHolderName = cardHolderName;
        CardExpiration = cardExpiration;
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

<span data-ttu-id="6f2f9-202">V podstatě třída Command obsahuje všechna data, která potřebujete pro provádění obchodní transakce, pomocí objektů doménového modelu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-202">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="6f2f9-203">Příkazy jsou tedy jednoduše datové struktury, které obsahují data jen pro čtení, a žádné chování.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-203">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="6f2f9-204">Název příkazu označuje jeho účel.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-204">The command's name indicates its purpose.</span></span> <span data-ttu-id="6f2f9-205">V mnoha jazycích, jako je C#, se příkazy reprezentují jako třídy, ale nejedná se o skutečné třídy v reálném smyslu orientovaném na objekt.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-205">In many languages like C#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="6f2f9-206">V důsledku dalších charakteristik jsou příkazy neměnné, protože očekávané využití je, že jsou zpracovávány přímo doménovým modelem.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-206">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="6f2f9-207">Nemusejí se měnit během plánované životnosti.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-207">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="6f2f9-208">V třídě jazyka C# lze neměnnosti dosáhnout tak, že neexistují žádné metody setter nebo jiné metody, které mění vnitřní stav.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-208">In a C# class, immutability can be achieved by not having any setters or other methods that change the internal state.</span></span>

<span data-ttu-id="6f2f9-209">Mějte na paměti, že pokud máte v úmyslu nebo očekávat příkazy, které procházejí procesem serializace/deserializace, vlastnosti musí mít privátní metodu setter a `[DataMember]` atribut (nebo `[JsonProperty]` ).</span><span class="sxs-lookup"><span data-stu-id="6f2f9-209">Keep in mind that if you intend or expect commands to go through a serializing/deserializing process, the properties must have a private setter, and the `[DataMember]` (or `[JsonProperty]`) attribute.</span></span> <span data-ttu-id="6f2f9-210">V opačném případě deserializátor nebude moci rekonstruovat objekt v cílovém umístění s požadovanými hodnotami.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-210">Otherwise, the deserializer won't be able to reconstruct the object at the destination with the required values.</span></span> <span data-ttu-id="6f2f9-211">Můžete také použít vlastnosti, které jsou skutečně jen pro čtení, pokud má třída konstruktor s parametry pro všechny vlastnosti, s obvyklým camelCase konvencí pojmenování a přiřadí se konstruktoru jako `[JsonConstructor]` .</span><span class="sxs-lookup"><span data-stu-id="6f2f9-211">You can also use truly read-only properties if the class has a constructor with parameters for all properties, with the usual camelCase naming convention, and annotate the constructor as `[JsonConstructor]`.</span></span> <span data-ttu-id="6f2f9-212">Tato možnost však vyžaduje více kódu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-212">However, this option requires more code.</span></span>

<span data-ttu-id="6f2f9-213">Například třída příkazu pro vytvoření objednávky je pravděpodobně podobná z údajů pro pořadí, které chcete vytvořit, ale pravděpodobně nepotřebujete stejné atributy.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-213">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="6f2f9-214">Instance například nemá `CreateOrderCommand` ID objednávky, protože objednávka ještě nebyla vytvořena.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-214">For instance, `CreateOrderCommand` does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="6f2f9-215">Mnoho tříd příkazu může být jednoduché, což vyžaduje pouze několik polí o některém stavu, který je třeba změnit.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-215">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="6f2f9-216">To by znamenalo, že když měníte stav objednávky z "v procesu" na "placeno" nebo "expedovaných", pomocí příkazu podobného následujícímu:</span><span class="sxs-lookup"><span data-stu-id="6f2f9-216">That would be the case if you are just changing the status of an order from "in process" to "paid" or "shipped" by using a command similar to the following:</span></span>

```csharp
[DataContract]
public class UpdateOrderStatusCommand
    :IRequest<bool>
{
    [DataMember]
    public string Status { get; private set; }

    [DataMember]
    public string OrderId { get; private set; }

    [DataMember]
    public string BuyerIdentityGuid { get; private set; }
}
```

<span data-ttu-id="6f2f9-217">Někteří vývojáři zavedou své objekty žádosti o uživatelské rozhraní oddělené od jejich příkazu DTO, ale to je pouze preference.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-217">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="6f2f9-218">Je zdlouhavé oddělení, které není mnohem další hodnotou, a objekty jsou téměř přesně stejný tvar.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-218">It is a tedious separation with not much additional value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="6f2f9-219">Například v eShopOnContainers se některé příkazy přidávají přímo z na straně klienta.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-219">For instance, in eShopOnContainers, some commands come directly from the client-side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="6f2f9-220">Třída obslužné rutiny příkazu</span><span class="sxs-lookup"><span data-stu-id="6f2f9-220">The Command handler class</span></span>

<span data-ttu-id="6f2f9-221">Pro každý příkaz byste měli implementovat konkrétní třídu obslužné rutiny příkazu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-221">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="6f2f9-222">To znamená, jak vzor funguje, a je místo, kde budete používat objekt Command, doménové objekty a objekty úložiště infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-222">That is how the pattern works, and it's where you'll use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="6f2f9-223">Obslužná rutina příkazu je ve skutečnosti jádrem aplikační vrstvy z podmínek CQRS a DDD.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-223">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="6f2f9-224">Nicméně všechny doménové logiky by měly být obsaženy v doménových třídách, v rámci agregovaných kořenů (kořenové entity), podřízených entit nebo [doménových služeb](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ale ne v rámci obslužné rutiny příkazu, což je třída z aplikační vrstvy.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-224">However, all the domain logic should be contained in the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="6f2f9-225">Třída obslužné rutiny příkazu nabízí silné kameny v rámci způsobu, jak dosáhnout jediného principu zodpovědnosti (SRP) zmíněného v předchozí části.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-225">The command handler class offers a strong stepping stone in the way to achieve the Single Responsibility Principle (SRP) mentioned in a previous section.</span></span>

<span data-ttu-id="6f2f9-226">Obslužná rutina příkazu obdrží příkaz a získá výsledek z agregace, která je použita.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-226">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="6f2f9-227">Výsledek by měl být buď úspěšným provedením příkazu, nebo výjimkou.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-227">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="6f2f9-228">V případě výjimky by stav systému neměl být beze změny.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-228">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="6f2f9-229">Obslužná rutina příkazu obvykle provádí následující kroky:</span><span class="sxs-lookup"><span data-stu-id="6f2f9-229">The command handler usually takes the following steps:</span></span>

- <span data-ttu-id="6f2f9-230">Přijímá objekt příkazu, jako je DTO (z modulu [prostředníka](https://en.wikipedia.org/wiki/Mediator_pattern) nebo jiného objektu infrastruktury).</span><span class="sxs-lookup"><span data-stu-id="6f2f9-230">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

- <span data-ttu-id="6f2f9-231">Ověří, jestli je příkaz platný (pokud ho neověřuje zprostředkovatel).</span><span class="sxs-lookup"><span data-stu-id="6f2f9-231">It validates that the command is valid (if not validated by the mediator).</span></span>

- <span data-ttu-id="6f2f9-232">Vytvoří instanci agregované kořenové instance, která je cílem aktuálního příkazu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-232">It instantiates the aggregate root instance that is the target of the current command.</span></span>

- <span data-ttu-id="6f2f9-233">Spustí metodu na agregované kořenové instanci a získá požadovaná data z příkazu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-233">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

- <span data-ttu-id="6f2f9-234">Zachovává nový stav agregace do příslušné databáze.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-234">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="6f2f9-235">Tato poslední operace je skutečná transakce.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-235">This last operation is the actual transaction.</span></span>

<span data-ttu-id="6f2f9-236">Obvykle obslužná rutina příkazu zpracovává jedinou agregaci založenou na agregačním kořeni (kořenová entita).</span><span class="sxs-lookup"><span data-stu-id="6f2f9-236">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="6f2f9-237">Pokud by mělo být ovlivněno více agregací přijetím jednoho příkazu, můžete použít události domény k šíření stavů nebo akcí v rámci více agregací.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-237">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates.</span></span>

<span data-ttu-id="6f2f9-238">Důležitým bodem je, že při zpracování příkazu by měla být veškerá logika domény uvnitř doménového modelu (agregace), plně zapouzdřená a připravená pro testování částí.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-238">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="6f2f9-239">Obslužná rutina příkazu funguje jenom jako způsob, jak získat doménový model z databáze a jako poslední krok, aby bylo možné sdělit vrstvě infrastruktury (úložiště), aby zachovala změny při změně modelu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-239">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="6f2f9-240">Výhodou tohoto přístupu je, že můžete logiku domény Refaktorovat v izolovaném, plně zapouzdřeném, bohatým modelu doménového modelu, aniž byste museli měnit kód v vrstevch aplikace nebo infrastruktury, což je úroveň domovní instalace (obslužné rutiny příkazů, webové rozhraní API, úložiště atd.).</span><span class="sxs-lookup"><span data-stu-id="6f2f9-240">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="6f2f9-241">Pokud obslužné rutiny příkazu mají složitý, s příliš velkým množstvím logiky, může to být zápach kódu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-241">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="6f2f9-242">Přečtěte si je, a pokud najdete logiku domény, refaktorujte kód pro přesun tohoto chování domény do metod doménových objektů (agregovaná kořenová a podřízená entita).</span><span class="sxs-lookup"><span data-stu-id="6f2f9-242">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="6f2f9-243">Jako příklad třídy obslužné rutiny příkazu, následující kód ukazuje stejnou `CreateOrderCommandHandler` třídu, kterou jste viděli na začátku této kapitoly.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-243">As an example of a command handler class, the following code shows the same `CreateOrderCommandHandler` class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="6f2f9-244">V tomto případě také zvýrazní metodu popisovače a operace s objekty nebo agregacemi doménového modelu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-244">In this case, it also highlights the Handle method and the operations with the domain model objects/aggregates.</span></span>

```csharp
public class CreateOrderCommandHandler
        : IRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;
    private readonly IOrderingIntegrationEventService _orderingIntegrationEventService;
    private readonly ILogger<CreateOrderCommandHandler> _logger;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
        IOrderingIntegrationEventService orderingIntegrationEventService,
        IOrderRepository orderRepository,
        IIdentityService identityService,
        ILogger<CreateOrderCommandHandler> logger)
    {
        _orderRepository = orderRepository ?? throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ?? throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ?? throw new ArgumentNullException(nameof(mediator));
        _orderingIntegrationEventService = orderingIntegrationEventService ?? throw new ArgumentNullException(nameof(orderingIntegrationEventService));
        _logger = logger ?? throw new ArgumentNullException(nameof(logger));
    }

    public async Task<bool> Handle(CreateOrderCommand message, CancellationToken cancellationToken)
    {
        // Add Integration event to clean the basket
        var orderStartedIntegrationEvent = new OrderStartedIntegrationEvent(message.UserId);
        await _orderingIntegrationEventService.AddAndSaveEventAsync(orderStartedIntegrationEvent);

        // Add/Update the Buyer AggregateRoot
        // DDD patterns comment: Add child entities and value-objects through the Order Aggregate-Root
        // methods and constructor so validations, invariants and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State, message.Country, message.ZipCode);
        var order = new Order(message.UserId, message.UserName, address, message.CardTypeId, message.CardNumber, message.CardSecurityNumber, message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice, item.Discount, item.PictureUrl, item.Units);
        }

        _logger.LogInformation("----- Creating Order - Order: {@Order}", order);

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync(cancellationToken);
    }
}
```

<span data-ttu-id="6f2f9-245">Jedná se o další kroky, které by měla obslužná rutina příkazu provést:</span><span class="sxs-lookup"><span data-stu-id="6f2f9-245">These are additional steps a command handler should take:</span></span>

- <span data-ttu-id="6f2f9-246">Použijte data příkazu pro práci s metodami a chováním agregačního kořenového adresáře.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-246">Use the command's data to operate with the aggregate root's methods and behavior.</span></span>

- <span data-ttu-id="6f2f9-247">Interně v rámci doménových objektů přivolejte události domény při spuštění transakce, ale to je transparentní z bodu obslužné rutiny příkazu View.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-247">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

- <span data-ttu-id="6f2f9-248">Pokud je výsledkem operace agregace úspěch a po dokončení transakce, vyvolejte integrační události.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-248">If the aggregate's operation result is successful and after the transaction is finished, raise integration events.</span></span> <span data-ttu-id="6f2f9-249">(Ty můžou být vyvolány i třídami infrastruktury, jako jsou úložiště.)</span><span class="sxs-lookup"><span data-stu-id="6f2f9-249">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="6f2f9-250">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="6f2f9-250">Additional resources</span></span>

- <span data-ttu-id="6f2f9-251">**Označte Seemann. V hranicích nejsou aplikace orientované na objekty.** </span><span class="sxs-lookup"><span data-stu-id="6f2f9-251">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented** </span></span>\
  <https://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/>

- <span data-ttu-id="6f2f9-252">**Příkazy a události** </span><span class="sxs-lookup"><span data-stu-id="6f2f9-252">**Commands and events** </span></span>\
  <https://cqrs.nu/Faq/commands-and-events>

- <span data-ttu-id="6f2f9-253">**Co dělá obslužná rutina příkazu?**</span><span class="sxs-lookup"><span data-stu-id="6f2f9-253">**What does a command handler do?**</span></span> \
  <https://cqrs.nu/Faq/command-handlers>

- <span data-ttu-id="6f2f9-254">**Jimmy Bogard. Doménové vzory příkazů – obslužné rutiny** </span><span class="sxs-lookup"><span data-stu-id="6f2f9-254">**Jimmy Bogard. Domain Command Patterns – Handlers** </span></span>\
  <https://jimmybogard.com/domain-command-patterns-handlers/>

- <span data-ttu-id="6f2f9-255">**Jimmy Bogard. Doménové vzorce příkazů – ověření** </span><span class="sxs-lookup"><span data-stu-id="6f2f9-255">**Jimmy Bogard. Domain Command Patterns – Validation** </span></span>\
  <https://jimmybogard.com/domain-command-patterns-validation/>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="6f2f9-256">Kanál procesu příkazu: Jak aktivovat obslužnou rutinu příkazu</span><span class="sxs-lookup"><span data-stu-id="6f2f9-256">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="6f2f9-257">Další otázkou je postup vyvolání obslužné rutiny příkazu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-257">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="6f2f9-258">Můžete ji ručně volat z každého souvisejícího kontroleru ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-258">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="6f2f9-259">Nicméně tento přístup by byl příliš spojený a není ideální.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-259">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="6f2f9-260">Další dvě hlavní možnosti, které jsou doporučenými možnostmi, jsou:</span><span class="sxs-lookup"><span data-stu-id="6f2f9-260">The other two main options, which are the recommended options, are:</span></span>

- <span data-ttu-id="6f2f9-261">Prostřednictvím artefaktu modelu pro zpracování v paměti.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-261">Through an in-memory Mediator pattern artifact.</span></span>

- <span data-ttu-id="6f2f9-262">S asynchronní frontou zpráv mezi řadiči a obslužnými rutinami.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-262">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="use-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="6f2f9-263">Použití vzoru povýšení (v paměti) v kanálu příkazů</span><span class="sxs-lookup"><span data-stu-id="6f2f9-263">Use the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="6f2f9-264">Jak je znázorněno na obrázku 7-25, CQRS přístup k používání inteligentního modulu pro směrování, podobně jako sběrnice v paměti, která je dostatečně inteligentní pro přesměrování na správnou obslužnou rutinu příkazů na základě typu příkazu nebo DTO, který je právě přijímán.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-264">As shown in Figure 7-25, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="6f2f9-265">Jednoduché šipky mezi komponentami znázorňují závislosti mezi objekty (v mnoha případech vložené přes DI) se souvisejícími interakcemi.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-265">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![Diagram znázorňující podrobnější tok dat od klienta k databázi.](./media/microservice-application-layer-implementation-web-api/mediator-cqrs-microservice.png)

<span data-ttu-id="6f2f9-267">**Obrázek 7-25**.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-267">**Figure 7-25**.</span></span> <span data-ttu-id="6f2f9-268">Použití vzoru prostředníka v procesu v jedné mikroslužbě CQRS</span><span class="sxs-lookup"><span data-stu-id="6f2f9-268">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="6f2f9-269">Výše uvedený diagram znázorňuje přiblížení z image 7-24: řadič ASP.NET Core odesílá příkaz do kanálu příkazů MediatR, aby se dostal k příslušné obslužné rutině.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-269">The above diagram shows a zoom-in from image 7-24: the ASP.NET Core controller sends the command to MediatR's command pipeline, so they get to the appropriate handler.</span></span>

<span data-ttu-id="6f2f9-270">Důvodem použití vzorového principu je to, že v podnikových aplikacích můžou požadavky na zpracování dosáhnout složitosti.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-270">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="6f2f9-271">Chcete být schopni přidat otevřený počet vzájemně se podobných otázek, jako je protokolování, ověření, audit a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-271">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="6f2f9-272">V těchto případech můžete spoléhat na kanál prostředníka (viz [vzor zprostředkovatelů](https://en.wikipedia.org/wiki/Mediator_pattern)) a poskytnout tak prostředky pro tato dodatečná chování nebo problémy při průřezu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-272">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="6f2f9-273">Zprostředkovatel je objekt, který zapouzdřuje "How" tohoto procesu: koordinuje spouštění na základě stavu, způsob vyvolání obslužné rutiny příkazu nebo datovou část, kterou poskytnete obslužné rutině.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-273">A mediator is an object that encapsulates the "how" of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="6f2f9-274">Pomocí komponenty prostředníku můžete v centralizovaném a transparentním způsobu použít možnosti pro průřez, a to použitím dekoratéry (nebo [chování kanálu](https://github.com/jbogard/MediatR/wiki/Behaviors) od [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span><span class="sxs-lookup"><span data-stu-id="6f2f9-274">With a mediator component, you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0)).</span></span> <span data-ttu-id="6f2f9-275">Další informace najdete v tématu [dekoratér vzor](https://en.wikipedia.org/wiki/Decorator_pattern).</span><span class="sxs-lookup"><span data-stu-id="6f2f9-275">For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).</span></span>

<span data-ttu-id="6f2f9-276">Dekoratéry a chování jsou podobné [programování orientovanému na orientaci (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), které se používá jenom pro konkrétní kanál procesu spravovaný komponentou prostředníka.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-276">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="6f2f9-277">Aspekty v AOP, které implementují obavy mezi průřezy, se uplatňují na základě *aspektů Weavers* vložených v době kompilace nebo na základě zachycení volání objektů.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-277">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="6f2f9-278">Typické přístupy k AOP jsou někdy označovány jako "jako Magic", protože není snadné zjistit, jak AOP funguje.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-278">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="6f2f9-279">Při řešení vážných problémů nebo chyb může být AOP obtížné ho ladit.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-279">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="6f2f9-280">Na druhé straně jsou tyto dekoratéry/chování explicitní a použité pouze v kontextu prostředníka, takže ladění je mnohem více předvídatelné a snadné.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-280">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="6f2f9-281">Například v eShopOnContainers řazení mikroslužeb má implementaci dvou vzorových chování, třídu [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) a třídu [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) .</span><span class="sxs-lookup"><span data-stu-id="6f2f9-281">For example, in the eShopOnContainers ordering microservice, has an implementation of two sample behaviors, a [LogBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class and a [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class.</span></span> <span data-ttu-id="6f2f9-282">Implementaci chování je vysvětleno v další části zobrazením, jak eShopOnContainers používá [chování](https://github.com/jbogard/MediatR/wiki/Behaviors) [MediatR](https://www.nuget.org/packages/MediatR) .</span><span class="sxs-lookup"><span data-stu-id="6f2f9-282">The implementation of the behaviors is explained in the next section by showing how eShopOnContainers uses [MediatR](https://www.nuget.org/packages/MediatR) [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors).</span></span>

### <a name="use-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="6f2f9-283">Použití front zpráv (out-of-proc) v kanálu příkazu</span><span class="sxs-lookup"><span data-stu-id="6f2f9-283">Use message queues (out-of-proc) in the command's pipeline</span></span>

<span data-ttu-id="6f2f9-284">Další možností je použít asynchronní zprávy založené na zprostředkovatelích nebo frontách zpráv, jak je znázorněno na obrázku 7-26.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-284">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 7-26.</span></span> <span data-ttu-id="6f2f9-285">Tato možnost může být také kombinována s komponentou prostředníka před obslužnou rutinou příkazu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-285">That option could also be combined with the mediator component right before the command handler.</span></span>

![Diagram znázorňující tok dat pomocí fronty zpráv HA](./media/microservice-application-layer-implementation-web-api/add-ha-message-queue.png)

<span data-ttu-id="6f2f9-287">**Obrázek 7-26**.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-287">**Figure 7-26**.</span></span> <span data-ttu-id="6f2f9-288">Použití front zpráv (mimo proces a komunikace mezi procesy) pomocí příkazů CQRS</span><span class="sxs-lookup"><span data-stu-id="6f2f9-288">Using message queues (out of the process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="6f2f9-289">Kanál příkazu může být také zpracován frontou zpráv vysoké dostupnosti pro doručení příkazů příslušné obslužné rutině.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-289">Command's pipeline can also be handled by a high availability message queue to deliver the commands to the appropriate handler.</span></span> <span data-ttu-id="6f2f9-290">Použití front zpráv k přijetí příkazů může dále zkomplikovat kanál příkazu, protože pravděpodobně budete muset kanál rozdělit do dvou procesů, které jsou připojeny prostřednictvím externí fronty zpráv.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-290">Using message queues to accept the commands can further complicate your command's pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="6f2f9-291">Stále byste měli použít, pokud potřebujete mít lepší škálovatelnost a výkon na základě asynchronního zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-291">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="6f2f9-292">Vezměte v úvahu, že v případě obrázku 7-26 tento kontroler pouze odešle příkaz do fronty a vrátí.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-292">Consider that in the case of Figure 7-26, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="6f2f9-293">Potom obslužné rutiny příkazu zpracovávají zprávy vlastním tempem.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-293">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="6f2f9-294">To je skvělé výhody front: fronta zpráv může fungovat jako vyrovnávací paměť v případech, kdy je potřeba škálovatelnost technologie Hyper-v případě potřeby, jako jsou například akcie nebo jakýkoli jiný scénář s velkým objemem příchozích dat.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-294">That is a great benefit of queues: the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="6f2f9-295">Z důvodu asynchronního povaze front zpráv je však nutné zjistit, jak komunikovat s klientskou aplikací o úspěšnosti nebo selhání procesu příkazu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-295">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command's process.</span></span> <span data-ttu-id="6f2f9-296">Jako pravidlo byste nikdy neměli používat příkazy "Fire and zapomenout".</span><span class="sxs-lookup"><span data-stu-id="6f2f9-296">As a rule, you should never use "fire and forget" commands.</span></span> <span data-ttu-id="6f2f9-297">Každá obchodní aplikace potřebuje zjistit, jestli byl příkaz úspěšně zpracován, nebo alespoň ověřený a přijatý.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-297">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="6f2f9-298">Proto schopnost reagovat na klienta po ověření zprávy příkazu, která byla odeslána do asynchronní fronty, představuje složitost systému, jak je popsáno v procesu příkazu procesu, který vrací výsledek operace po spuštění transakce.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-298">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation's result after running the transaction.</span></span> <span data-ttu-id="6f2f9-299">Pomocí front může být nutné vrátit výsledek příkazového procesu prostřednictvím dalších zpráv výsledků operací, které budou vyžadovat další součásti a vlastní komunikaci ve vašem systému.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-299">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="6f2f9-300">Kromě toho asynchronní příkazy jsou jednosměrné příkazy, které v mnoha případech nemusí být potřeba, jak je vysvětleno v následujícím zajímavém Exchangi mezi Burtsev Alexey a Greg Youngem v [online konverzaci](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span><span class="sxs-lookup"><span data-stu-id="6f2f9-300">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

> <span data-ttu-id="6f2f9-301">\[Burtsev Alexey \] hledáme spoustu kódu, kde lidé používají asynchronní zpracování příkazů nebo jednosměrné příkazy pro zasílání zpráv bez jakéhokoli důvodu (neprovádí žádnou dlouhou operaci). neprovádí ale externí asynchronní kód, nejedná se dokonce o hranice mezi aplikacemi a pomocí sběrnice zpráv.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-301">\[Burtsev Alexey\] I find lots of code where people use async command handling or one-way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross-application boundary to be using message bus).</span></span> <span data-ttu-id="6f2f9-302">Proč zavádějí tuto zbytečný složitost?</span><span class="sxs-lookup"><span data-stu-id="6f2f9-302">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="6f2f9-303">A ve skutečnosti jsem neviděl příklad kódu CQRS s blokujícími obslužnými rutinami příkazů, i když bude ve většině případů fungovat přesně dobře.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-303">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>
>
> <span data-ttu-id="6f2f9-304">\[Greg Young. \] \[ .. \] asynchronní příkaz neexistuje; jedná se o skutečnou jinou událost.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-304">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="6f2f9-305">Pokud je potřeba přijmout, co pošlete, a vyvolat událost, Pokud nesouhlasíte, už Neoznamujeme, že se něco nestane, ale nejedná se \[ o příkaz \] .</span><span class="sxs-lookup"><span data-stu-id="6f2f9-305">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something \[that is, it's not a command\].</span></span> <span data-ttu-id="6f2f9-306">Je to vám řekněte mi, že se něco udělalo.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-306">It's you telling me something has been done.</span></span> <span data-ttu-id="6f2f9-307">Vypadá to jako mírně rozdíl v prvním, ale má mnoho aspektů.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-307">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="6f2f9-308">Asynchronní příkazy významně zvyšují složitost systému, protože neexistuje žádný jednoduchý způsob, jak označovat selhání.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-308">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="6f2f9-309">Proto nejsou asynchronní příkazy jiné doporučovány než při vyžadování požadavků na škálování nebo ve zvláštních případech při komunikaci interních mikroslužeb prostřednictvím zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-309">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="6f2f9-310">V těchto případech je třeba navrhnout samostatné vytváření sestav a systém obnovení pro selhání.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-310">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="6f2f9-311">V počáteční verzi eShopOnContainers bylo rozhodnuto použít synchronní zpracování příkazů spouštěné z požadavků HTTP a řízených vzorem pojmenování.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-311">In the initial version of eShopOnContainers, it was decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="6f2f9-312">To umožňuje snadno vrátit úspěch nebo neúspěch procesu, jako v implementaci [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/netcore1.1/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) .</span><span class="sxs-lookup"><span data-stu-id="6f2f9-312">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/netcore1.1/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="6f2f9-313">V každém případě by to mělo být rozhodnutí založené na obchodních požadavcích vaší aplikace nebo mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-313">In any case, this should be a decision based on your application's or microservice's business requirements.</span></span>

## <a name="implement-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="6f2f9-314">Implementace kanálu procesu příkazu pomocí vzoru povedení (MediatR)</span><span class="sxs-lookup"><span data-stu-id="6f2f9-314">Implement the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="6f2f9-315">V rámci ukázkové implementace tato příručka navrhuje použití kanálu v rámci procesu založeného na vzorci pro řízení příkazů pro příjem příkazů a směrování příkazů v paměti na pravé obslužné rutiny příkazů.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-315">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and route commands, in memory, to the right command handlers.</span></span> <span data-ttu-id="6f2f9-316">Průvodce také navrhuje použití [chování](https://github.com/jbogard/MediatR/wiki/Behaviors) , aby bylo možné oddělit různé aspekty.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-316">The guide also proposes applying [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="6f2f9-317">Pro implementaci v .NET Core je k dispozici více Open Source knihoven, které implementují vzor povýšení.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-317">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="6f2f9-318">Knihovna použitá v tomto průvodci je [MediatR](https://github.com/jbogard/MediatR) open source knihovna (vytvořená Jimmy Bogard), ale můžete použít jiný přístup.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-318">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="6f2f9-319">MediatR je malá a jednoduchá knihovna, která umožňuje zpracovávat zprávy v paměti jako příkaz, a to při použití dekoratéry nebo chování.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-319">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="6f2f9-320">Použití vzorového vztahu vám pomůže omezit spojování a izolovat obavy o požadovanou práci a automaticky se připojit k obslužné rutině, která provádí tuto práci – v tomto případě do obslužných rutin příkazů.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-320">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="6f2f9-321">Dalším dobrým důvodem pro použití vzoru prostředníka bylo při prohlížení této příručky vysvětleno v Jimmy Bogard:</span><span class="sxs-lookup"><span data-stu-id="6f2f9-321">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

> <span data-ttu-id="6f2f9-322">Domnívám se, že se tady může poznamenat testování – nabízí skvělé konzistentní okno s chováním systému.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-322">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="6f2f9-323">Požadavky, reakce. Zjistili jsme, že tento aspekt je poměrně užitečný při sestavování konzistentně se chovajících testů.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-323">Request-in, response-out. We've found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="6f2f9-324">Nejprve se podíváme na vzorový kontroler WebAPI, kde byste ve skutečnosti použili objekt prostředníka.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-324">First, let's look at a sample WebAPI controller where you actually would use the mediator object.</span></span> <span data-ttu-id="6f2f9-325">Pokud jste nepoužívali objekt prostředníka, je nutné vložit všechny závislosti pro tento kontroler, například objekt protokolovacího nástroje a další.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-325">If you weren't using the mediator object, you'd need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="6f2f9-326">Proto by konstruktor byl složitý.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-326">Therefore, the constructor would be complicated.</span></span> <span data-ttu-id="6f2f9-327">Na druhou stranu platí, že pokud použijete objekt prostředníkem, může být konstruktor vašeho kontroleru mnohem jednodušší, ale pouze pár závislostí místo mnoha závislostí, pokud jste měli jeden za operaci křížového vyjmutí, jak je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="6f2f9-327">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies if you had one per cross-cutting operation, as in the following example:</span></span>

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

<span data-ttu-id="6f2f9-328">Můžete vidět, že zprostředkovatel poskytuje čistý a štíhlý konstruktor webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-328">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="6f2f9-329">Kromě toho v rámci metod kontroleru je kód pro odeslání příkazu do objektu prostředníku skoro jeden řádek:</span><span class="sxs-lookup"><span data-stu-id="6f2f9-329">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

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

### <a name="implement-idempotent-commands"></a><span data-ttu-id="6f2f9-330">Implementace příkazů idempotentní</span><span class="sxs-lookup"><span data-stu-id="6f2f9-330">Implement idempotent Commands</span></span>

<span data-ttu-id="6f2f9-331">V **eShopOnContainers**, pokročilejší příklad, který je uveden výše, odesílá objekt CreateOrderCommand z řazení mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-331">In **eShopOnContainers**, a more advanced example than the above is submitting a CreateOrderCommand object from the Ordering microservice.</span></span> <span data-ttu-id="6f2f9-332">Ale vzhledem k tomu, že je obchodní proces objednávání trochu složitější a v našem případě se ve skutečnosti spouští v mikroslužbě košíku, tato akce odeslání objektu CreateOrderCommand se provádí z obslužné rutiny události Integration-Event s názvem [UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) namísto jednoduchého WebApi kontroleru volaného z klientské aplikace jako v předchozím jednodušším příkladu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-332">But since the Ordering business process is a bit more complex and, in our case, it actually starts in the Basket microservice, this action of submitting the CreateOrderCommand object is performed from an integration-event handler named [UserCheckoutAcceptedIntegrationEventHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/IntegrationEvents/EventHandling/UserCheckoutAcceptedIntegrationEventHandler.cs) instead of a simple WebAPI controller called from the client App as in the previous simpler example.</span></span>

<span data-ttu-id="6f2f9-333">Nicméně akce odeslání příkazu do MediatR je poměrně podobná, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-333">Nevertheless, the action of submitting the Command to MediatR is pretty similar, as shown in the following code.</span></span>

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

<span data-ttu-id="6f2f9-334">V tomto případě je však také poněkud pokročilejší, protože implementujeme také příkazy idempotentní.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-334">However, this case is also slightly more advanced because we're also implementing idempotent commands.</span></span> <span data-ttu-id="6f2f9-335">Proces CreateOrderCommand by měl být idempotentní, takže pokud se stejná zpráva bude duplikována prostřednictvím sítě z jakéhokoli důvodu, jako je třeba opakování, stejné obchodní objednávky se zpracují jenom jednou.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-335">The CreateOrderCommand process should be idempotent, so if the same message comes duplicated through the network, because of any reason, like retries, the same business order will be processed just once.</span></span>

<span data-ttu-id="6f2f9-336">To je implementováno zabalením příkazu Business (v tomto případě CreateOrderCommand) a vložením do obecného IdentifiedCommand, které je sledováno IDENTIFIKÁTORem každé zprávy přicházející přes síť, která musí být idempotentní.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-336">This is implemented by wrapping the business command (in this case CreateOrderCommand) and embedding it into a generic IdentifiedCommand, which is tracked by an ID of every message coming through the network that has to be idempotent.</span></span>

<span data-ttu-id="6f2f9-337">V následujícím kódu vidíte, že IdentifiedCommand není nic více než DTO s a ID plus zabalený objekt Business Command.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-337">In the code below, you can see that the IdentifiedCommand is nothing more than a DTO with and ID plus the wrapped business command object.</span></span>

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

<span data-ttu-id="6f2f9-338">Pak CommandHandler – pro IdentifiedCommand s názvem [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) bude v podstatě kontrolovat, zda ID přicházející jako součást zprávy již v tabulce existuje.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-338">Then the CommandHandler for the IdentifiedCommand named [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs) will basically check if the ID coming as part of the message already exists in a table.</span></span> <span data-ttu-id="6f2f9-339">Pokud již existuje, tento příkaz nebude zpracován znovu, takže se chová jako příkaz idempotentní.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-339">If it already exists, that command won't be processed again, so it behaves as an idempotent command.</span></span> <span data-ttu-id="6f2f9-340">Tento kód infrastruktury provádí `_requestManager.ExistAsync` volání metody níže.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-340">That infrastructure code is performed by the `_requestManager.ExistAsync` method call below.</span></span>

```csharp
// IdentifiedCommandHandler.cs
public class IdentifiedCommandHandler<T, R> : IRequestHandler<IdentifiedCommand<T, R>, R>
        where T : IRequest<R>
{
    private readonly IMediator _mediator;
    private readonly IRequestManager _requestManager;
    private readonly ILogger<IdentifiedCommandHandler<T, R>> _logger;

    public IdentifiedCommandHandler(
        IMediator mediator,
        IRequestManager requestManager,
        ILogger<IdentifiedCommandHandler<T, R>> logger)
    {
        _mediator = mediator;
        _requestManager = requestManager;
        _logger = logger ?? throw new System.ArgumentNullException(nameof(logger));
    }

    /// <summary>
    /// Creates the result value to return if a previous request was found
    /// </summary>
    /// <returns></returns>
    protected virtual R CreateResultForDuplicateRequest()
    {
        return default(R);
    }

    /// <summary>
    /// This method handles the command. It just ensures that no other request exists with the same ID, and if this is the case
    /// just enqueues the original inner command.
    /// </summary>
    /// <param name="message">IdentifiedCommand which contains both original command & request ID</param>
    /// <returns>Return value of inner command or default value if request same ID was found</returns>
    public async Task<R> Handle(IdentifiedCommand<T, R> message, CancellationToken cancellationToken)
    {
        var alreadyExists = await _requestManager.ExistAsync(message.Id);
        if (alreadyExists)
        {
            return CreateResultForDuplicateRequest();
        }
        else
        {
            await _requestManager.CreateRequestForCommandAsync<T>(message.Id);
            try
            {
                var command = message.Command;
                var commandName = command.GetGenericTypeName();
                var idProperty = string.Empty;
                var commandId = string.Empty;

                switch (command)
                {
                    case CreateOrderCommand createOrderCommand:
                        idProperty = nameof(createOrderCommand.UserId);
                        commandId = createOrderCommand.UserId;
                        break;

                    case CancelOrderCommand cancelOrderCommand:
                        idProperty = nameof(cancelOrderCommand.OrderNumber);
                        commandId = $"{cancelOrderCommand.OrderNumber}";
                        break;

                    case ShipOrderCommand shipOrderCommand:
                        idProperty = nameof(shipOrderCommand.OrderNumber);
                        commandId = $"{shipOrderCommand.OrderNumber}";
                        break;

                    default:
                        idProperty = "Id?";
                        commandId = "n/a";
                        break;
                }

                _logger.LogInformation(
                    "----- Sending command: {CommandName} - {IdProperty}: {CommandId} ({@Command})",
                    commandName,
                    idProperty,
                    commandId,
                    command);

                // Send the embeded business command to mediator so it runs its related CommandHandler
                var result = await _mediator.Send(command, cancellationToken);

                _logger.LogInformation(
                    "----- Command result: {@Result} - {CommandName} - {IdProperty}: {CommandId} ({@Command})",
                    result,
                    commandName,
                    idProperty,
                    commandId,
                    command);

                return result;
            }
            catch
            {
                return default(R);
            }
        }
    }
}
```

<span data-ttu-id="6f2f9-341">Vzhledem k tomu, že IdentifiedCommand funguje jako obálka obchodního příkazu, když je potřeba zpracovat obchodní příkaz, protože se nejedná o opakované ID, pak převezme příkaz interní firmy a znovu ho odešle na poskytovatele, jako v poslední části kódu uvedeného výše, pokud je spuštěný `_mediator.Send(message.Command)` , z [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span><span class="sxs-lookup"><span data-stu-id="6f2f9-341">Since the IdentifiedCommand acts like a business command's envelope, when the business command needs to be processed because it is not a repeated ID, then it takes that inner business command and resubmits it to Mediator, as in the last part of the code shown above when running `_mediator.Send(message.Command)`, from the [IdentifiedCommandHandler.cs](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/IdentifiedCommandHandler.cs).</span></span>

<span data-ttu-id="6f2f9-342">Při tomto postupu bude probíhat odkazování a spuštění obslužné rutiny obchodního příkazu, v tomto případě [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs), který spouští transakce proti objednávce databáze, jak je znázorněno v následujícím kódu.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-342">When doing that, it will link and run the business command handler, in this case, the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs), which is running transactions against the Ordering database, as shown in the following code.</span></span>

```csharp
// CreateOrderCommandHandler.cs
public class CreateOrderCommandHandler
        : IRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;
    private readonly IIdentityService _identityService;
    private readonly IMediator _mediator;
    private readonly IOrderingIntegrationEventService _orderingIntegrationEventService;
    private readonly ILogger<CreateOrderCommandHandler> _logger;

    // Using DI to inject infrastructure persistence Repositories
    public CreateOrderCommandHandler(IMediator mediator,
        IOrderingIntegrationEventService orderingIntegrationEventService,
        IOrderRepository orderRepository,
        IIdentityService identityService,
        ILogger<CreateOrderCommandHandler> logger)
    {
        _orderRepository = orderRepository ?? throw new ArgumentNullException(nameof(orderRepository));
        _identityService = identityService ?? throw new ArgumentNullException(nameof(identityService));
        _mediator = mediator ?? throw new ArgumentNullException(nameof(mediator));
        _orderingIntegrationEventService = orderingIntegrationEventService ?? throw new ArgumentNullException(nameof(orderingIntegrationEventService));
        _logger = logger ?? throw new ArgumentNullException(nameof(logger));
    }

    public async Task<bool> Handle(CreateOrderCommand message, CancellationToken cancellationToken)
    {
        // Add Integration event to clean the basket
        var orderStartedIntegrationEvent = new OrderStartedIntegrationEvent(message.UserId);
        await _orderingIntegrationEventService.AddAndSaveEventAsync(orderStartedIntegrationEvent);

        // Add/Update the Buyer AggregateRoot
        // DDD patterns comment: Add child entities and value-objects through the Order Aggregate-Root
        // methods and constructor so validations, invariants and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State, message.Country, message.ZipCode);
        var order = new Order(message.UserId, message.UserName, address, message.CardTypeId, message.CardNumber, message.CardSecurityNumber, message.CardHolderName, message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice, item.Discount, item.PictureUrl, item.Units);
        }

        _logger.LogInformation("----- Creating Order - Order: {@Order}", order);

        _orderRepository.Add(order);

        return await _orderRepository.UnitOfWork
            .SaveEntitiesAsync(cancellationToken);
    }
}
```

### <a name="register-the-types-used-by-mediatr"></a><span data-ttu-id="6f2f9-343">Zaregistrujte typy používané pomocí MediatR</span><span class="sxs-lookup"><span data-stu-id="6f2f9-343">Register the types used by MediatR</span></span>

<span data-ttu-id="6f2f9-344">Aby MediatR informace o třídách obslužných rutin příkazů, je nutné zaregistrovat třídy poskytovatele a obslužné rutiny příkazu v kontejneru IoC.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-344">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="6f2f9-345">Ve výchozím nastavení používá MediatR jako kontejner IoC Autofac, ale můžete použít i integrovaný kontejner ASP.NET Core IoC nebo jakýkoli jiný kontejner podporovaný MediatR.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-345">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="6f2f9-346">Následující kód ukazuje, jak registrovat typy a příkazy poskytovatele při použití Autofac modulů.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-346">The following code shows how to register Mediator's types and commands when using Autofac modules.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(typeof(CreateOrderCommand).GetTypeInfo().Assembly)
                .AsClosedTypesOf(typeof(IRequestHandler<,>));
        // Other types registration
        //...
    }
}
```

<span data-ttu-id="6f2f9-347">V takovém případě se s MediatR stane "Magic".</span><span class="sxs-lookup"><span data-stu-id="6f2f9-347">This is where "the magic happens" with MediatR.</span></span>

<span data-ttu-id="6f2f9-348">Jelikož obslužná rutina příkazu implementuje obecné `IRequestHandler<T>` rozhraní, při registraci sestavení pomocí `RegisteredAssemblyTypes` metody všechny typy označené jako `IRequestHandler` také jsou zaregistrovány spolu s jejich `Commands` .</span><span class="sxs-lookup"><span data-stu-id="6f2f9-348">As each command handler implements the generic `IRequestHandler<T>` interface, when you register the assemblies using `RegisteredAssemblyTypes` method all the types marked as `IRequestHandler` also gets registered with their `Commands`.</span></span> <span data-ttu-id="6f2f9-349">Například:</span><span class="sxs-lookup"><span data-stu-id="6f2f9-349">For   example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="6f2f9-350">To je kód, který koreluje příkazy s obslužnými rutinami příkazů.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-350">That is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="6f2f9-351">Obslužná rutina je pouze jednoduchá třída, ale dědí z `RequestHandler<T>` , kde T je typ příkazu a MediatR zajistí, že je vyvolána se správnou datovou částí (příkaz).</span><span class="sxs-lookup"><span data-stu-id="6f2f9-351">The handler is just a simple class, but it inherits from `RequestHandler<T>`, where T is the command type, and MediatR makes sure it is invoked with the correct payload (the command).</span></span>

## <a name="apply-cross-cutting-concerns-when-processing-commands-with-the-behaviors-in-mediatr"></a><span data-ttu-id="6f2f9-352">Při zpracování příkazů s chováním v MediatR použít různé aspekty při vyjmutí</span><span class="sxs-lookup"><span data-stu-id="6f2f9-352">Apply cross-cutting concerns when processing commands with the Behaviors in MediatR</span></span>

<span data-ttu-id="6f2f9-353">K dispozici je ještě více věcí: schopnost použít průřezy v rámci kanálu pro proporcování.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-353">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="6f2f9-354">Můžete také vidět na konci registračního modulu Autofac, jak registruje typ chování, konkrétně vlastní třídu LoggingBehavior a třídu ValidatorBehavior.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-354">You can also see at the end of the Autofac registration module code how it registers a behavior type, specifically, a custom LoggingBehavior class and a ValidatorBehavior class.</span></span> <span data-ttu-id="6f2f9-355">Můžete ale také přidat další vlastní chování.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-355">But you could add other custom behaviors, too.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();

        // Register all the Command classes (they implement IRequestHandler)
        // in assembly holding the Commands
        builder.RegisterAssemblyTypes(
                              typeof(CreateOrderCommand).GetTypeInfo().Assembly).
                                   AsClosedTypesOf(typeof(IRequestHandler<,>));
        // Other types registration
        //...
        builder.RegisterGeneric(typeof(LoggingBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
        builder.RegisterGeneric(typeof(ValidatorBehavior<,>)).
                                                   As(typeof(IPipelineBehavior<,>));
    }
}
```

<span data-ttu-id="6f2f9-356">Tato třída [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) může být implementována jako následující kód, který protokoluje informace o spuštěné obslužné rutině příkazu a zda byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-356">That [LoggingBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/LoggingBehavior.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

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

<span data-ttu-id="6f2f9-357">Pouze implementací této třídy chování a jejich registrací do kanálu (ve výše uvedeném MediatorModule) budou všechny příkazy zpracované prostřednictvím MediatR protokolovány informace o spuštění.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-357">Just by implementing this behavior class and by registering it in the pipeline (in the MediatorModule above), all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="6f2f9-358">Mikroslužba řazení eShopOnContainers také používá druhé chování pro základní ověřování, třídu [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) , která spoléhá na knihovnu [FluentValidation](https://github.com/JeremySkinner/FluentValidation) , jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="6f2f9-358">The eShopOnContainers ordering microservice also applies a second behavior for basic validations, the [ValidatorBehavior](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Behaviors/ValidatorBehavior.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

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

<span data-ttu-id="6f2f9-359">Zde chování vyvolává výjimku, pokud se ověření nepovede, ale můžete také vrátit výsledný objekt, který obsahuje výsledek příkazu, pokud byl úspěšný, nebo ověřovací zprávy v případě, že nedošlo k chybě.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-359">Here the behavior is raising an exception if validation fails, but you could also return a result object, containing the command result if it succeeded or the validation messages in case it didn't.</span></span> <span data-ttu-id="6f2f9-360">To by pravděpodobně bylo snazší zobrazit výsledky ověřování uživateli.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-360">This would probably make it easier to display validation results to the user.</span></span>

<span data-ttu-id="6f2f9-361">Pak na základě knihovny [FluentValidation](https://github.com/JeremySkinner/FluentValidation) vytvoříte ověření pro data předaná pomocí CreateOrderCommand, jak je uvedeno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="6f2f9-361">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, you would create validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

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

<span data-ttu-id="6f2f9-362">Mohli byste vytvořit další ověření.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-362">You could create additional validations.</span></span> <span data-ttu-id="6f2f9-363">Jedná se o velmi čistý a elegantní způsob implementace příkazů pro ověřování.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-363">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="6f2f9-364">Podobným způsobem můžete implementovat jiné chování pro další aspekty nebo problémy mimo průřez, které chcete použít pro příkazy při jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-364">In a similar way, you could implement other behaviors for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="6f2f9-365">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="6f2f9-365">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="6f2f9-366">Vzor zprostředkovatelů</span><span class="sxs-lookup"><span data-stu-id="6f2f9-366">The mediator pattern</span></span>

- <span data-ttu-id="6f2f9-367">**Vzor zprostředkovatelů** </span><span class="sxs-lookup"><span data-stu-id="6f2f9-367">**Mediator pattern** </span></span>\
  [https://en.wikipedia.org/wiki/Mediator\_pattern](https://en.wikipedia.org/wiki/Mediator_pattern)

##### <a name="the-decorator-pattern"></a><span data-ttu-id="6f2f9-368">Vzor dekoratér</span><span class="sxs-lookup"><span data-stu-id="6f2f9-368">The decorator pattern</span></span>

- <span data-ttu-id="6f2f9-369">**Vzor dekoratér** </span><span class="sxs-lookup"><span data-stu-id="6f2f9-369">**Decorator pattern** </span></span>\
  [https://en.wikipedia.org/wiki/Decorator\_pattern](https://en.wikipedia.org/wiki/Decorator_pattern)

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="6f2f9-370">MediatR (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="6f2f9-370">MediatR (Jimmy Bogard)</span></span>

- <span data-ttu-id="6f2f9-371">**MediatR.**</span><span class="sxs-lookup"><span data-stu-id="6f2f9-371">**MediatR.**</span></span> <span data-ttu-id="6f2f9-372">Úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-372">GitHub repo.</span></span> \
  <https://github.com/jbogard/MediatR>

- <span data-ttu-id="6f2f9-373">**CQRS s MediatR a automapper** </span><span class="sxs-lookup"><span data-stu-id="6f2f9-373">**CQRS with MediatR and AutoMapper** </span></span>\
  <https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/>

- <span data-ttu-id="6f2f9-374">**Vložte své řadiče do diety: příspěvky a příkazy.**</span><span class="sxs-lookup"><span data-stu-id="6f2f9-374">**Put your controllers on a diet: POSTs and commands.**</span></span> \
  <https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/>

- <span data-ttu-id="6f2f9-375">**Řešení potíží při průřezu s využitím kanálu prořezávání** </span><span class="sxs-lookup"><span data-stu-id="6f2f9-375">**Tackling cross-cutting concerns with a mediator pipeline** </span></span>\
  <https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/>

- <span data-ttu-id="6f2f9-376">**CQRS a REST: perfektní shoda** </span><span class="sxs-lookup"><span data-stu-id="6f2f9-376">**CQRS and REST: the perfect match** </span></span>\
  <https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/>

- <span data-ttu-id="6f2f9-377">**Příklady MediatR kanálu** </span><span class="sxs-lookup"><span data-stu-id="6f2f9-377">**MediatR Pipeline Examples** </span></span>\
  <https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/>

- <span data-ttu-id="6f2f9-378">**Testovací přípravek pro MediatR a ASP.NET Core – svislé řezy** </span><span class="sxs-lookup"><span data-stu-id="6f2f9-378">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core** </span></span>\
  <https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>

- <span data-ttu-id="6f2f9-379">**Vydaná rozšíření MediatR pro vkládání závislostí Microsoftu** </span><span class="sxs-lookup"><span data-stu-id="6f2f9-379">**MediatR Extensions for Microsoft Dependency Injection Released** </span></span>\
  <https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/>

##### <a name="fluent-validation"></a><span data-ttu-id="6f2f9-380">Ověření Fluent</span><span class="sxs-lookup"><span data-stu-id="6f2f9-380">Fluent validation</span></span>

- <span data-ttu-id="6f2f9-381">**Jeremy Skinner. FluentValidation.**</span><span class="sxs-lookup"><span data-stu-id="6f2f9-381">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="6f2f9-382">Úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="6f2f9-382">GitHub repo.</span></span> \
  <https://github.com/JeremySkinner/FluentValidation>

> [!div class="step-by-step"]
> <span data-ttu-id="6f2f9-383">[Předchozí](microservice-application-layer-web-api-design.md) 
>  [Další](../implement-resilient-applications/index.md)</span><span class="sxs-lookup"><span data-stu-id="6f2f9-383">[Previous](microservice-application-layer-web-api-design.md)
[Next](../implement-resilient-applications/index.md)</span></span>
