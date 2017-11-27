---
title: "Implementace aplikační vrstvu mikroslužbu pomocí rozhraní Web API"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace aplikační vrstvu mikroslužbu pomocí rozhraní Web API"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: d505a2561ae9b8dee05e803fd639387b63b28b70
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-the-microservice-application-layer-using-the-web-api"></a><span data-ttu-id="07be2-104">Implementace aplikační vrstvu mikroslužbu pomocí rozhraní Web API</span><span class="sxs-lookup"><span data-stu-id="07be2-104">Implementing the microservice application layer using the Web API</span></span>

## <a name="using-dependency-injection-to-inject-infrastructure-objects-into-your-application-layer"></a><span data-ttu-id="07be2-105">Pomocí vkládání závislostí vložení objektů infrastruktury do vaší aplikační vrstvy</span><span class="sxs-lookup"><span data-stu-id="07be2-105">Using Dependency Injection to inject infrastructure objects into your application layer</span></span>

<span data-ttu-id="07be2-106">Jak je uvedeno nahoře, aplikační vrstvu můžete implementovat jako součást artefaktů, který vytváříte, například v projektu webového rozhraní API nebo projekt aplikace MVC.</span><span class="sxs-lookup"><span data-stu-id="07be2-106">As mentioned previously, the application layer can be implemented as part of the artifact you are building, such as within a Web API project or an MVC web app project.</span></span> <span data-ttu-id="07be2-107">V případě mikroslužbu, vytvořené s ASP.NET Core aplikační vrstvu bude obvykle knihovnu webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="07be2-107">In the case of a microservice built with ASP.NET Core, the application layer will usually be your Web API library.</span></span> <span data-ttu-id="07be2-108">Pokud chcete k oddělení, co pochází z ASP.NET Core (jeho infrastruktury a řadičů) z vašeho kódu vrstvy vlastní aplikaci, umístíte vaší aplikační vrstvy může také v knihovně samostatné třídy, ale který je volitelné.</span><span class="sxs-lookup"><span data-stu-id="07be2-108">If you want to separate what is coming from ASP.NET Core (its infrastructure plus your controllers) from your custom application layer code, you could also place your application layer in a separate class library, but that is optional.</span></span>

<span data-ttu-id="07be2-109">Například kód aplikace vrstvy řazení mikroslužbu přímo implementována jako součást **Ordering.API** projektu (projektu webového rozhraní API ASP.NET Core), jako uvedené v obrázek 9-19.</span><span class="sxs-lookup"><span data-stu-id="07be2-109">For instance, the application layer code of the ordering microservice is directly implemented as part of the **Ordering.API** project (an ASP.NET Core Web API project), as shown in Figure 9-19.</span></span>

![](./media/image20.png)

<span data-ttu-id="07be2-110">**Obrázek 9-19**.</span><span class="sxs-lookup"><span data-stu-id="07be2-110">**Figure 9-19**.</span></span> <span data-ttu-id="07be2-111">Aplikační vrstvu v projektu webového rozhraní API pro jádro ASP.NET Ordering.API</span><span class="sxs-lookup"><span data-stu-id="07be2-111">The application layer in the Ordering.API ASP.NET Core Web API project</span></span>

<span data-ttu-id="07be2-112">ASP.NET Core zahrnuje jednoduchou [předdefinované kontejner IoC](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (představované rozhraní IServiceProvider), která podporuje vkládání konstruktor ve výchozím nastavení a ASP.NET zpřístupní určité služby prostřednictvím DI.</span><span class="sxs-lookup"><span data-stu-id="07be2-112">ASP.NET Core includes a simple [built-in IoC container](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection) (represented by the IServiceProvider interface) that supports constructor injection by default, and ASP.NET makes certain services available through DI.</span></span> <span data-ttu-id="07be2-113">ASP.NET Core používá termín *služby* pro všechny typy zaregistrujete, které budou vloženy prostřednictvím DI.</span><span class="sxs-lookup"><span data-stu-id="07be2-113">ASP.NET Core uses the term *service* for any of the types you register that will be injected through DI.</span></span> <span data-ttu-id="07be2-114">Nakonfigurujete integrované kontejneru služby v metodě ConfigureServices ve třídě spuštění vaší aplikace.</span><span class="sxs-lookup"><span data-stu-id="07be2-114">You configure the built-in container's services in the ConfigureServices method in your application's Startup class.</span></span> <span data-ttu-id="07be2-115">Závislostmi se implementují ve služby, které potřebuje typu.</span><span class="sxs-lookup"><span data-stu-id="07be2-115">Your dependencies are implemented in the services that a type needs.</span></span>

<span data-ttu-id="07be2-116">Obvykle je vhodné pro vkládání závislosti, které implementují objekty infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="07be2-116">Typically, you want to inject dependencies that implement infrastructure objects.</span></span> <span data-ttu-id="07be2-117">Velmi typické závislost vložení je úložiště.</span><span class="sxs-lookup"><span data-stu-id="07be2-117">A very typical dependency to inject is a repository.</span></span> <span data-ttu-id="07be2-118">Ale může vložit žádné další infrastrukturu závislost, která může mít.</span><span class="sxs-lookup"><span data-stu-id="07be2-118">But you could inject any other infrastructure dependency that you may have.</span></span> <span data-ttu-id="07be2-119">Pro jednodušší implementací může přímo vložit vzor objektu pracovní jednotky (objekt EF DbContext), protože DBContext se také implementace objektů trvalost vaší infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="07be2-119">For simpler implementations, you could directly inject your Unit of Work pattern object (the EF DbContext object), because the DBContext is also the implementation of your infrastructure persistence objects.</span></span>

<span data-ttu-id="07be2-120">V následujícím příkladu vidíte, jak je .NET Core vložení požadované úložiště objektů pomocí konstruktoru.</span><span class="sxs-lookup"><span data-stu-id="07be2-120">In the following example, you can see how .NET Core is injecting the required repository objects through the constructor.</span></span> <span data-ttu-id="07be2-121">Třída je obslužná rutina příkazu, který vám nabídneme v další části.</span><span class="sxs-lookup"><span data-stu-id="07be2-121">The class is a command handler, which we will cover in the next section.</span></span>

```csharp
// Sample command handler
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IOrderRepository _orderRepository;

    // Constructor where Dependencies are injected
    public CreateOrderCommandHandler(IOrderRepository orderRepository)
    {
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // ... Additional code
        //
        // Create the Order AggregateRoot
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var address = new Address(message.Street, message.City, message.State,
            message.Country, message.ZipCode);
        var order = new Order(address, message.CardTypeId, message.CardNumber,
            message.CardSecurityNumber,
            message.CardHolderName,
            message.CardExpiration);

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        //Persist the Order through the Repository
        _orderRepository.Add(order);
        var result = await _orderRepository.UnitOfWork
            .SaveEntitiesAsync();
        return result > 0;
    }
}
```

<span data-ttu-id="07be2-122">Třída vloženého úložiště používá ke spouštění transakce a zachová tak změny stavu.</span><span class="sxs-lookup"><span data-stu-id="07be2-122">The class uses the injected repositories to execute the transaction and persist the state changes.</span></span> <span data-ttu-id="07be2-123">Nezáleží, jestli je obslužná rutina příkazu, metody kontroleru webového rozhraní API ASP.NET Core třídy nebo [služba aplikace DDD](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span><span class="sxs-lookup"><span data-stu-id="07be2-123">It does not matter whether that class is a command handler, an ASP.NET Core Web API controller method, or a [DDD Application Service](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/).</span></span> <span data-ttu-id="07be2-124">Nakonec je jednoduchý třídu, která používá úložiště, entity domény a další aplikace koordinaci způsobem podobná obslužná rutina příkazu.</span><span class="sxs-lookup"><span data-stu-id="07be2-124">It is ultimately a simple class that uses repositories, domain entities, and other application coordination in a fashion similar to a command handler.</span></span> <span data-ttu-id="07be2-125">Stejným způsobem jako pro všechny uvedené třídy, jako v příkladu pomocí DI podle konstruktoru funguje vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="07be2-125">Dependency Injection works the same way for all the mentioned classes, as in the example using DI based on the constructor.</span></span>

### <a name="registering-the-dependency-implementation-types-and-interfaces-or-abstractions"></a><span data-ttu-id="07be2-126">Probíhá registrace závislosti implementace typy a rozhraní nebo abstrakce</span><span class="sxs-lookup"><span data-stu-id="07be2-126">Registering the dependency implementation types and interfaces or abstractions</span></span>

<span data-ttu-id="07be2-127">Než použijete objekty vložit prostřednictvím konstruktory, musíte vědět, kde k registraci rozhraní a třídy, které vytváří objekty vloženy do vaší třídy aplikace prostřednictvím DI.</span><span class="sxs-lookup"><span data-stu-id="07be2-127">Before you use the objects injected through constructors, you need to know where to register the interfaces and classes that produce the objects injected into your application classes through DI.</span></span> <span data-ttu-id="07be2-128">(Například DI na základě konstruktoru, jak je uvedený výše.)</span><span class="sxs-lookup"><span data-stu-id="07be2-128">(Like DI based on the constructor, as shown previously.)</span></span>

#### <a name="using-the-built-in-ioc-container-provided-by-aspnet-core"></a><span data-ttu-id="07be2-129">Pomocí předdefinovaných kontejner IoC poskytované ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="07be2-129">Using the built-in IoC container provided by ASP.NET Core</span></span>

<span data-ttu-id="07be2-130">Pokud používáte integrované kontejner IoC poskytované ASP.NET Core, zaregistrujte se typy, které chcete vložit v metodě ConfigureServices v souboru Startup.cs, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="07be2-130">When you use the built-in IoC container provided by ASP.NET Core, you register the types you want to inject in the ConfigureServices method in the Startup.cs file, as in the following code:</span></span>

```csharp
// Registration of types into ASP.NET Core built-in container
public void ConfigureServices(IServiceCollection services)
{
    // Register out-of-the-box framework services.
    services.AddDbContext<CatalogContext>(c =>
    {
        c.UseSqlServer(Configuration["ConnectionString"]);
    },
    ServiceLifetime.Scoped
    );
    services.AddMvc();
    // Register custom application dependencies.
    services.AddScoped<IMyCustomRepository, MyCustomSQLRepository>();
}
```

<span data-ttu-id="07be2-131">Nejběžnější vzor, když zaregistrujete typy na kontejner IoC k registraci pár typy – rozhraní a jeho souvisejících implementace třídy.</span><span class="sxs-lookup"><span data-stu-id="07be2-131">The most common pattern when registering types in an IoC container is to register a pair of types—an interface and its related implementation class.</span></span> <span data-ttu-id="07be2-132">Pokud budete požadovat objekt z kontejneru IoC prostřednictvím žádné konstruktor, pak požádáte objekt určitého typu rozhraní.</span><span class="sxs-lookup"><span data-stu-id="07be2-132">Then when you request an object from the IoC container through any constructor, you request an object of a certain type of interface.</span></span> <span data-ttu-id="07be2-133">Například v předchozím příkladu poslední řádek stavy, pokud žádné z vaší konstruktory jsou závislé na IMyCustomRepository (rozhraní nebo abstrakce), kontejner IoC bude instance implementace MyCustomSQLServerRepository vložit Třída.</span><span class="sxs-lookup"><span data-stu-id="07be2-133">For instance, in the previous example, the last line states that when any of your constructors have a dependency on IMyCustomRepository (interface or abstraction), the IoC container will inject an instance of the MyCustomSQLServerRepository implementation class.</span></span>

#### <a name="using-the-scrutor-library-for-automatic-types-registration"></a><span data-ttu-id="07be2-134">Použití knihovny Scrutor pro registraci automatické typy</span><span class="sxs-lookup"><span data-stu-id="07be2-134">Using the Scrutor library for automatic types registration</span></span>

<span data-ttu-id="07be2-135">Při použití DI v .NET Core, můžete být skenovat sestavení a automatickou registraci typy jejího podle konvence.</span><span class="sxs-lookup"><span data-stu-id="07be2-135">When using DI in .NET Core, you might want to be able to scan an assembly and automatically register its types by convention.</span></span> <span data-ttu-id="07be2-136">Tato funkce není aktuálně k dispozici v ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="07be2-136">This feature is not currently available in ASP.NET Core.</span></span> <span data-ttu-id="07be2-137">Můžete však použít [Scrutor](https://github.com/khellang/Scrutor) knihovny pro tento.</span><span class="sxs-lookup"><span data-stu-id="07be2-137">However, you can use the [Scrutor](https://github.com/khellang/Scrutor) library for that.</span></span> <span data-ttu-id="07be2-138">Tento přístup je vhodné, když máte desítek typy, které musí být registrované ve vašem kontejner IoC.</span><span class="sxs-lookup"><span data-stu-id="07be2-138">This approach is convenient when you have dozens of types that need to be registered in your IoC container.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="07be2-139">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="07be2-139">Additional resources</span></span>

-   <span data-ttu-id="07be2-140">**Matthew krále. Registrace služby Scrutor**
    [*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)</span><span class="sxs-lookup"><span data-stu-id="07be2-140">**Matthew King. Registering services with Scrutor**
[*https://mking.io/blog/registering-services-with-scrutor*](https://mking.io/blog/registering-services-with-scrutor)</span></span>

<!-- -->

-   <span data-ttu-id="07be2-141">**Kristian Hellang. Scrutor.**</span><span class="sxs-lookup"><span data-stu-id="07be2-141">**Kristian Hellang. Scrutor.**</span></span> <span data-ttu-id="07be2-142">Úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="07be2-142">GitHub repo.</span></span>
    [<span data-ttu-id="07be2-143">*https://github.com/khellang/Scrutor*</span><span class="sxs-lookup"><span data-stu-id="07be2-143">*https://github.com/khellang/Scrutor*</span></span>](https://github.com/khellang/Scrutor)

#### <a name="using-autofac-as-an-ioc-container"></a><span data-ttu-id="07be2-144">Použití Autofac jako kontejner IoC</span><span class="sxs-lookup"><span data-stu-id="07be2-144">Using Autofac as an IoC container</span></span>

<span data-ttu-id="07be2-145">Můžete také používat další technologie IoC kontejnery a připojte je kanálu ASP.NET Core, stejně jako řazení mikroslužbu v eShopOnContainers, který používá [Autofac](https://autofac.org/).</span><span class="sxs-lookup"><span data-stu-id="07be2-145">You can also use additional IoC containers and plug them into the ASP.NET Core pipeline, as in the ordering microservice in eShopOnContainers, which uses [Autofac](https://autofac.org/).</span></span> <span data-ttu-id="07be2-146">Při použití Autofac obvykle zaregistrovat typy prostřednictvím modulů, které umožňují rozdělení typy registrace mezi více souborů, v závislosti na tom, kde vaše typy jsou, stejně jako typy aplikací, které jsou rozmístěny v několika knihovny tříd může mít.</span><span class="sxs-lookup"><span data-stu-id="07be2-146">When using Autofac you typically register the types via modules, which allow you to split the registration types between multiple files depending on where your types are, just as you could have the application types distributed across multiple class libraries.</span></span>

<span data-ttu-id="07be2-147">Například následující je [modulu aplikace Autofac](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) pro [Ordering.API webového rozhraní API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) projektu s typy můžete vložit.</span><span class="sxs-lookup"><span data-stu-id="07be2-147">For example, the following is the [Autofac application module](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Infrastructure/AutofacModules/ApplicationModule.cs) for the [Ordering.API Web API](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Services/Ordering/Ordering.API) project with the types you will want to inject.</span></span>

```csharp
public class ApplicationModule
    :Autofac.Module
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

<span data-ttu-id="07be2-148">Proces registrace a Koncepty jsou velmi podobně jako typy můžete zaregistrovat pomocí předdefinovaných iOS kontejneru ASP.NET Core, ale syntaxe při použití Autofac je trochu liší.</span><span class="sxs-lookup"><span data-stu-id="07be2-148">The registration process and concepts are very similar to the way you can register types with the built-in ASP.NET Core iOS container, but the syntax when using Autofac is a bit different.</span></span>

<span data-ttu-id="07be2-149">V příkladu kódu je zaregistrován abstrakci IOrderRepository společně s třída implementace OrderRepository.</span><span class="sxs-lookup"><span data-stu-id="07be2-149">In the example code, the abstraction IOrderRepository is registered along with the implementation class OrderRepository.</span></span> <span data-ttu-id="07be2-150">To znamená, že vždy, když konstruktor je deklarace závislost prostřednictvím abstrakce IOrderRepository nebo rozhraní, kontejner IoC bude instance třídy OrderRepository vložit.</span><span class="sxs-lookup"><span data-stu-id="07be2-150">This means that whenever a constructor is declaring a dependency through the IOrderRepository abstraction or interface, the IoC container will inject an instance of the OrderRepository class.</span></span>

<span data-ttu-id="07be2-151">Typ oboru instance Určuje, jak sdílet instanci mezi požadavky pro stejné služby nebo závislostí.</span><span class="sxs-lookup"><span data-stu-id="07be2-151">The instance scope type determines how an instance is shared between requests for the same service or dependency.</span></span> <span data-ttu-id="07be2-152">Po odeslání žádosti pro závislost na kontejner IoC vrátit následující:</span><span class="sxs-lookup"><span data-stu-id="07be2-152">When a request is made for a dependency, the IoC container can return the following:</span></span>

-   <span data-ttu-id="07be2-153">Jedna instance pro každý obor doba platnosti (uvedených v kontejneru ASP.NET Core IoC jako *obor*).</span><span class="sxs-lookup"><span data-stu-id="07be2-153">A single instance per lifetime scope (referred to in the ASP.NET Core IoC container as *scoped*).</span></span>

-   <span data-ttu-id="07be2-154">Nová instance za závislosti (uvedených v kontejneru ASP.NET Core IoC jako *přechodný*).</span><span class="sxs-lookup"><span data-stu-id="07be2-154">A new instance per dependency (referred to in the ASP.NET Core IoC container as *transient*).</span></span>

-   <span data-ttu-id="07be2-155">Jedna instance sdílet všechny objekty pomocí kontejner IoC (uvedených v kontejneru ASP.NET Core IoC jako *singleton*).</span><span class="sxs-lookup"><span data-stu-id="07be2-155">A single instance shared across all objects using the IoC container (referred to in the ASP.NET Core IoC container as *singleton*).</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="07be2-156">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="07be2-156">Additional resources</span></span>

-   <span data-ttu-id="07be2-157">**Úvod do vkládání závislostí v ASP.NET Core**
    [*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)</span><span class="sxs-lookup"><span data-stu-id="07be2-157">**Introduction to Dependency Injection in ASP.NET Core**
[*https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection*](https://docs.microsoft.com/aspnet/core/fundamentals/dependency-injection)</span></span>

-   <span data-ttu-id="07be2-158">**Autofac.**</span><span class="sxs-lookup"><span data-stu-id="07be2-158">**Autofac.**</span></span> <span data-ttu-id="07be2-159">Oficiální dokumentaci.</span><span class="sxs-lookup"><span data-stu-id="07be2-159">Official documentation.</span></span>
    [<span data-ttu-id="07be2-160">*http://docs.autofac.org/en/Latest/*</span><span class="sxs-lookup"><span data-stu-id="07be2-160">*http://docs.autofac.org/en/latest/*</span></span>](http://docs.autofac.org/en/latest/)

-   <span data-ttu-id="07be2-161">**Cesaru členka Torre. Porovnávání životnosti služby kontejner IoC jádro ASP.NET s obory instance kontejner Autofac IoC**
    [*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/ Comparing-ASP-NET-Core-IOC-Service-LIFE-Times-and-autofac-IOC-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span><span class="sxs-lookup"><span data-stu-id="07be2-161">**Cesar de la Torre. Comparing ASP.NET Core IoC container service lifetimes with Autofac IoC container instance scopes**
[*https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/*](https://blogs.msdn.microsoft.com/cesardelatorre/2017/01/26/comparing-asp-net-core-ioc-service-life-times-and-autofac-ioc-instance-scopes/)</span></span>

## <a name="implementing-the-command-and-command-handler-patterns"></a><span data-ttu-id="07be2-162">Implementace vzorů příkaz a obslužná rutina příkazu</span><span class="sxs-lookup"><span data-stu-id="07be2-162">Implementing the Command and Command Handler patterns</span></span>

<span data-ttu-id="07be2-163">V příkladu DI prostřednictvím konstruktor uvedené v předchozí části se kontejner IoC vložení úložiště prostřednictvím konstruktor v třídě.</span><span class="sxs-lookup"><span data-stu-id="07be2-163">In the DI-through-constructor example shown in the previous section, the IoC container was injecting repositories through a constructor in a class.</span></span> <span data-ttu-id="07be2-164">Ale přesně kde se budou vloženy?</span><span class="sxs-lookup"><span data-stu-id="07be2-164">But exactly where were they injected?</span></span> <span data-ttu-id="07be2-165">V jednoduché webové rozhraní API (například mikroslužbu katalogu v eShopOnContainers) vložit je na úrovni řadiče MVC, v konstruktoru řadiče.</span><span class="sxs-lookup"><span data-stu-id="07be2-165">In a simple Web API (for example, the catalog microservice in eShopOnContainers), you inject them at the MVC controllers level, in a controller constructor.</span></span> <span data-ttu-id="07be2-166">Ale v této části počáteční kódu ( [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) třídy z Ordering.API služby v rámci eShopOnContainers), vkládání závislostí se provádí pomocí konstruktoru konkrétní příkaz Obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="07be2-166">However, in the initial code of this section (the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) class from the Ordering.API service in eShopOnContainers), the injection of dependencies is done through the constructor of a particular command handler.</span></span> <span data-ttu-id="07be2-167">Dejte nám vysvětlují, jaké obslužná rutina příkazu je a proč ji používat.</span><span class="sxs-lookup"><span data-stu-id="07be2-167">Let us explain what a command handler is and why you would want to use it.</span></span>

<span data-ttu-id="07be2-168">Příkaz vzor nesouvisí vnitřně CQRS vzor, která byla zavedená dříve v tomto průvodci.</span><span class="sxs-lookup"><span data-stu-id="07be2-168">The Command pattern is intrinsically related to the CQRS pattern that was introduced earlier in this guide.</span></span> <span data-ttu-id="07be2-169">CQRS má dvě strany.</span><span class="sxs-lookup"><span data-stu-id="07be2-169">CQRS has two sides.</span></span> <span data-ttu-id="07be2-170">První oblast je dotazy, zjednodušené dotazy s pomocí [Dapper](https://github.com/StackExchange/dapper-dot-net) malých ORM, který je popsaný výše.</span><span class="sxs-lookup"><span data-stu-id="07be2-170">The first area is queries, using simplified queries with the [Dapper](https://github.com/StackExchange/dapper-dot-net) micro ORM, which was explained previously.</span></span> <span data-ttu-id="07be2-171">Druhý oblast je příkazy, které jsou výchozím bodem pro transakce a vstupní kanál z mimo službu.</span><span class="sxs-lookup"><span data-stu-id="07be2-171">The second area is commands, which are the starting point for transactions, and the input channel from outside the service.</span></span>

<span data-ttu-id="07be2-172">Jak znázorňuje obrázek 9-20, vzor je založena na přijímá příkazy ze strany klienta, je na základě pravidel modelu domény zpracování a nakonec uložením stavy s transakce.</span><span class="sxs-lookup"><span data-stu-id="07be2-172">As shown in Figure 9-20, the pattern is based on accepting commands from the client side, processing them based on the domain model rules, and finally persisting the states with transactions.</span></span>

![](./media/image21.png)

<span data-ttu-id="07be2-173">**Obrázek 9-20**.</span><span class="sxs-lookup"><span data-stu-id="07be2-173">**Figure 9-20**.</span></span> <span data-ttu-id="07be2-174">Podrobný pohled na příkazy nebo "transakcí" straně ve tvaru CQRS</span><span class="sxs-lookup"><span data-stu-id="07be2-174">High-level view of the commands or “transactional side” in a CQRS pattern</span></span>

### <a name="the-command-class"></a><span data-ttu-id="07be2-175">Příkaz – třída</span><span class="sxs-lookup"><span data-stu-id="07be2-175">The command class</span></span>

<span data-ttu-id="07be2-176">Příkaz je žádost o systému a provést akci, která změní stav systému.</span><span class="sxs-lookup"><span data-stu-id="07be2-176">A command is a request for the system to perform an action that changes the state of the system.</span></span> <span data-ttu-id="07be2-177">Příkazy jsou nutné a měla by být zpracována pouze jednou.</span><span class="sxs-lookup"><span data-stu-id="07be2-177">Commands are imperative, and should be processed just once.</span></span>

<span data-ttu-id="07be2-178">Vzhledem k tomu, že jsou příkazy závazné, mají obvykle název s příkazem imperativní chuť (například "vytvořit" nebo "aktualizovat") a může obsahují agregační typu, například CreateOrderCommand.</span><span class="sxs-lookup"><span data-stu-id="07be2-178">Since commands are imperatives, they are typically named with a verb in the imperative mood (for example, "create" or "update"), and they might include the aggregate type, such as CreateOrderCommand.</span></span> <span data-ttu-id="07be2-179">Na rozdíl od události není příkaz faktu v minulosti; je pouze požadavek a proto může být odmítnuta.</span><span class="sxs-lookup"><span data-stu-id="07be2-179">Unlike an event, a command is not a fact from the past; it is only a request, and thus may be refused.</span></span>

<span data-ttu-id="07be2-180">Příkazy můžete pocházejí z uživatelského rozhraní v důsledku uživatele žádost o inicializaci nebo ze Správce procesu, když správce proces je odkazovat agregace k provedení akce.</span><span class="sxs-lookup"><span data-stu-id="07be2-180">Commands can originate from the UI as a result of a user initiating a request, or from a process manager when the process manager is directing an aggregate to perform an action.</span></span>

<span data-ttu-id="07be2-181">Důležitou vlastností příkazu je, že ho měla by být zpracována pouze jednou podle jednoho příjemce.</span><span class="sxs-lookup"><span data-stu-id="07be2-181">An important characteristic of a command is that it should be processed just once by a single receiver.</span></span> <span data-ttu-id="07be2-182">Je to proto, že je příkaz jednu akci nebo transakce, kterou chcete provést v aplikaci.</span><span class="sxs-lookup"><span data-stu-id="07be2-182">This is because a command is a single action or transaction you want to perform in the application.</span></span> <span data-ttu-id="07be2-183">Stejný příkaz pořadí vytváření například by nemělo zpracovat více než jednou.</span><span class="sxs-lookup"><span data-stu-id="07be2-183">For example, the same order creation command should not be processed more than once.</span></span> <span data-ttu-id="07be2-184">Toto je důležitý rozdíl mezi příkazy a události.</span><span class="sxs-lookup"><span data-stu-id="07be2-184">This is an important difference between commands and events.</span></span> <span data-ttu-id="07be2-185">Události může zpracovat více než jednou., protože mnoho systémy nebo mikroslužeb může být zajímá události.</span><span class="sxs-lookup"><span data-stu-id="07be2-185">Events may be processed multiple times, because many systems or microservices might be interested in the event.</span></span>

<span data-ttu-id="07be2-186">Kromě toho je důležité, aby příkaz zpracovat pouze jednou v případě, že příkaz není idempotent.</span><span class="sxs-lookup"><span data-stu-id="07be2-186">In addition, it is important that a command be processed only once in case the command is not idempotent.</span></span> <span data-ttu-id="07be2-187">Příkaz je idempotent, pokud se Dal spustit několikrát beze změny výsledek, vzhledem k povaze příkaz nebo kvůli způsobu, jakým systém zpracovává příkaz.</span><span class="sxs-lookup"><span data-stu-id="07be2-187">A command is idempotent if it can be executed multiple times without changing the result, either because of the nature of the command, or because of the way the system handles the command.</span></span>

<span data-ttu-id="07be2-188">Je vhodné vytvořit příkazech a aktualizuje idempotent, když má smysl v rámci vaší doméně obchodní pravidla a výstupních podmínek.</span><span class="sxs-lookup"><span data-stu-id="07be2-188">It is a good practice to make your commands and updates idempotent when it makes sense under your domain’s business rules and invariants.</span></span> <span data-ttu-id="07be2-189">Například pokud chcete použít stejný příklad, pokud z nějakého důvodu (logika opakovaných pokusů, hackerům, atd.) stejný příkaz CreateOrder dosáhne systému vícekrát, byste měli moct identifikovat ji a ujistěte se, nevytvářejte více objednávek.</span><span class="sxs-lookup"><span data-stu-id="07be2-189">For instance, to use the same example, if for any reason (retry logic, hacking, etc.) the same CreateOrder command reaches your system multiple times, you should be able to identify it and ensure that you do not create multiple orders.</span></span> <span data-ttu-id="07be2-190">K tomu potřebujete připojit nějaký druh identity v konzoli operations a zjistit, jestli se příkaz nebo aktualizace již byla zpracována.</span><span class="sxs-lookup"><span data-stu-id="07be2-190">To do so, you need to attach some kind of identity in the operations and identify whether the command or update was already processed.</span></span>

<span data-ttu-id="07be2-191">Odeslat příkaz na jednoho příjemce; Nepublikujte příkaz.</span><span class="sxs-lookup"><span data-stu-id="07be2-191">You send a command to a single receiver; you do not publish a command.</span></span> <span data-ttu-id="07be2-192">Publikování je pro události integrace, které stavu faktu – něco došlo a může být zajímavé pro přijímače událostí.</span><span class="sxs-lookup"><span data-stu-id="07be2-192">Publishing is for integration events that state a fact—that something has happened and might be interesting for event receivers.</span></span> <span data-ttu-id="07be2-193">V případě událostí má vydavatele obavu, o kterých příjemci získat událost nebo co dělají ho.</span><span class="sxs-lookup"><span data-stu-id="07be2-193">In the case of events, the publisher has no concerns about which receivers get the event or what they do it.</span></span> <span data-ttu-id="07be2-194">Ale události integrace jsou různé scénáře už zavedená v předchozích částech.</span><span class="sxs-lookup"><span data-stu-id="07be2-194">But integration events are a different story already introduced in previous sections.</span></span>

<span data-ttu-id="07be2-195">Příkaz je implementováno s třídu, která obsahuje pole dat nebo kolekcí se veškeré informace, které je nutné k provedení tohoto příkazu.</span><span class="sxs-lookup"><span data-stu-id="07be2-195">A command is implemented with a class that contains data fields or collections with all the information that is needed in order to execute that command.</span></span> <span data-ttu-id="07be2-196">Příkaz je zvláštní druh z dat přenosu objektu (DTO), který konkrétně slouží k žádosti o změny nebo transakce.</span><span class="sxs-lookup"><span data-stu-id="07be2-196">A command is a special kind of Data Transfer Object (DTO), one that is specifically used to request changes or transactions.</span></span> <span data-ttu-id="07be2-197">Samotný příkaz vychází přesně informace potřebné pro příkaz a žádné další zpracování.</span><span class="sxs-lookup"><span data-stu-id="07be2-197">The command itself is based on exactly the information that is needed for processing the command, and nothing more.</span></span>

<span data-ttu-id="07be2-198">Následující příklad ukazuje zjednodušený CreateOrderCommand třídy.</span><span class="sxs-lookup"><span data-stu-id="07be2-198">The following example shows the simplified CreateOrderCommand class.</span></span> <span data-ttu-id="07be2-199">Toto je neměnné příkaz, který se používá v řazení mikroslužbu v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="07be2-199">This is an immutable command that is used in the ordering microservice in eShopOnContainers.</span></span>

```csharp
// DDD and CQRS patterns comment
// Note that it is recommended that yuo implement immutable commands
// In this case, immutability is achieved by having all the setters as private
// plus being able to update the data just once, when creating the object
// through the constructor.
// References on immutable commands:
// http://cqrs.nu/Faq
// https://docs.spine3.org/motivation/immutability.html
// http://blog.gauffin.org/2012/06/griffin-container-introducing-command-support/
// https://msdn.microsoft.com/en-us/library/bb383979.aspx
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

    public CreateOrderCommand(List<OrderItemDTO> orderItems, string city,
        string street,
        string state, string country, string zipcode,
        string cardNumber, string cardHolderName, DateTime cardExpiration,
        string cardSecurityNumber, int cardTypeId) : this()
    {
        _orderItems = orderItems;
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

<span data-ttu-id="07be2-200">V podstatě třída příkaz obsahuje všechna data, které potřebujete k provádění transakcí firmy pomocí objekty modelu domény.</span><span class="sxs-lookup"><span data-stu-id="07be2-200">Basically, the command class contains all the data you need for performing a business transaction by using the domain model objects.</span></span> <span data-ttu-id="07be2-201">Proto jsou příkazy jednoduše datové struktury, které obsahují data jen pro čtení a žádné chování.</span><span class="sxs-lookup"><span data-stu-id="07be2-201">Thus, commands are simply data structures that contain read-only data, and no behavior.</span></span> <span data-ttu-id="07be2-202">Název příkazu označuje jeho účel.</span><span class="sxs-lookup"><span data-stu-id="07be2-202">The command’s name indicates its purpose.</span></span> <span data-ttu-id="07be2-203">V mnoha jazycích, jako je C\#, příkazy jsou reprezentovány jako třídy, ale nejsou true třídy v tom smyslu, skutečně objektově orientovaný.</span><span class="sxs-lookup"><span data-stu-id="07be2-203">In many languages like C\#, commands are represented as classes, but they are not true classes in the real object-oriented sense.</span></span>

<span data-ttu-id="07be2-204">Jako další vlastnosti jsou příkazy nedá změnit, protože očekávané využití je, že jsou zpracovány přímo pomocí modelu domény.</span><span class="sxs-lookup"><span data-stu-id="07be2-204">As an additional characteristic, commands are immutable, because the expected usage is that they are processed directly by the domain model.</span></span> <span data-ttu-id="07be2-205">Není potřeba změnit během své předpokládané životnosti.</span><span class="sxs-lookup"><span data-stu-id="07be2-205">They do not need to change during their projected lifetime.</span></span> <span data-ttu-id="07be2-206">V a C\# třída, lze dosáhnout neměnitelnosti nemá žádné setter nebo jiné metody, které změní vnitřní stav.</span><span class="sxs-lookup"><span data-stu-id="07be2-206">In a C\# class, immutability can be achieved by not having any setters or other methods that change internal state.</span></span>

<span data-ttu-id="07be2-207">Například je pravděpodobně podobný z hlediska data pořadí, ve kterém chcete vytvořit třídu příkazu pro vytvoření pořadí, ale pravděpodobně není nutné provést stejné atributy.</span><span class="sxs-lookup"><span data-stu-id="07be2-207">For example, the command class for creating an order is probably similar in terms of data to the order you want to create, but you probably do not need the same attributes.</span></span> <span data-ttu-id="07be2-208">Například CreateOrderCommand nemá pořadí ID, protože ještě nebyl vytvořen pořadí.</span><span class="sxs-lookup"><span data-stu-id="07be2-208">For instance, CreateOrderCommand does not have an order ID, because the order has not been created yet.</span></span>

<span data-ttu-id="07be2-209">Mnoho tříd příkaz může být jednoduchý, které vyžadují pouze několik polí o některé stavu, který je potřeba změnit.</span><span class="sxs-lookup"><span data-stu-id="07be2-209">Many command classes can be simple, requiring only a few fields about some state that needs to be changed.</span></span> <span data-ttu-id="07be2-210">Který by byl tento případ Pokud měníte jenom stav pořadí z "proces v" na "placené" nebo "shipped" pomocí příkazu, který je podobný následujícímu:</span><span class="sxs-lookup"><span data-stu-id="07be2-210">That would be the case if you are just changing the status of an order from “in process” to “paid” or “shipped” by using a command similar to the following:</span></span>

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

<span data-ttu-id="07be2-211">Někteří vývojáři zvýšit jejich žádost objekty uživatelského rozhraní odděleně od jejich příkaz DTOs, ale který stačí preference.</span><span class="sxs-lookup"><span data-stu-id="07be2-211">Some developers make their UI request objects separate from their command DTOs, but that is just a matter of preference.</span></span> <span data-ttu-id="07be2-212">Je zdlouhavé oddělení se nevěnuje přidanou hodnotu a objekty jsou téměř úplně stejné tvaru.</span><span class="sxs-lookup"><span data-stu-id="07be2-212">It is a tedious separation with not much added value, and the objects are almost exactly the same shape.</span></span> <span data-ttu-id="07be2-213">V eShopOnContainers, například příkazy pocházejí přímo ze strany klienta.</span><span class="sxs-lookup"><span data-stu-id="07be2-213">For instance, in eShopOnContainers, the commands come directly from the client side.</span></span>

### <a name="the-command-handler-class"></a><span data-ttu-id="07be2-214">Obslužná rutina příkazu – třída</span><span class="sxs-lookup"><span data-stu-id="07be2-214">The Command Handler class</span></span>

<span data-ttu-id="07be2-215">Měli byste implementovat třídu obslužné rutiny konkrétní příkaz u každého příkazu.</span><span class="sxs-lookup"><span data-stu-id="07be2-215">You should implement a specific command handler class for each command.</span></span> <span data-ttu-id="07be2-216">To je, jak funguje vzoru a je kde budete používat objektu command, objektů domény a objektů úložiště infrastruktury.</span><span class="sxs-lookup"><span data-stu-id="07be2-216">That is how the pattern works, and it is where you will use the command object, the domain objects, and the infrastructure repository objects.</span></span> <span data-ttu-id="07be2-217">Obslužná rutina je ve skutečnosti jádrem aplikační vrstvu z hlediska CQRS a DDD.</span><span class="sxs-lookup"><span data-stu-id="07be2-217">The command handler is in fact the heart of the application layer in terms of CQRS and DDD.</span></span> <span data-ttu-id="07be2-218">Však veškerou logiku domény by měly být obsaženy v rámci domény třídy – v rámci agregační kořeny (kořenové entity), podřízených entit nebo [služby domény](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), ale není v rámci obslužná rutina, která je třída z aplikace vrstva.</span><span class="sxs-lookup"><span data-stu-id="07be2-218">However, all the domain logic should be contained within the domain classes—within the aggregate roots (root entities), child entities, or [domain services](https://lostechies.com/jimmybogard/2008/08/21/services-in-domain-driven-design/), but not within the command handler, which is a class from the application layer.</span></span>

<span data-ttu-id="07be2-219">Obslužná rutina příkazu přijme příkaz a získá výsledek z agregaci, která se používá.</span><span class="sxs-lookup"><span data-stu-id="07be2-219">A command handler receives a command and obtains a result from the aggregate that is used.</span></span> <span data-ttu-id="07be2-220">Výsledek musí být buď úspěšné provedení příkazu, nebo k výjimce.</span><span class="sxs-lookup"><span data-stu-id="07be2-220">The result should be either successful execution of the command, or an exception.</span></span> <span data-ttu-id="07be2-221">V případě výjimky musí být stav systému beze změny.</span><span class="sxs-lookup"><span data-stu-id="07be2-221">In the case of an exception, the system state should be unchanged.</span></span>

<span data-ttu-id="07be2-222">Obslužná rutina trvá obvykle následující kroky:</span><span class="sxs-lookup"><span data-stu-id="07be2-222">The command handler usually takes the following steps:</span></span>

-   <span data-ttu-id="07be2-223">Obdrží objektu command, jako je DTO (z [zprostředkovatel](https://en.wikipedia.org/wiki/Mediator_pattern) nebo jiného objektu infrastruktury).</span><span class="sxs-lookup"><span data-stu-id="07be2-223">It receives the command object, like a DTO (from the [mediator](https://en.wikipedia.org/wiki/Mediator_pattern) or other infrastructure object).</span></span>

-   <span data-ttu-id="07be2-224">Ověřuje příkaz je neplatný (Pokud není ověřen zprostředkovatel).</span><span class="sxs-lookup"><span data-stu-id="07be2-224">It validates that the command is valid (if not validated by the mediator).</span></span>

-   <span data-ttu-id="07be2-225">Vytvoření instance agregační kořenové instanci, která je cílem aktuální příkaz.</span><span class="sxs-lookup"><span data-stu-id="07be2-225">It instantiates the aggregate root instance that is the target of the current command.</span></span>

-   <span data-ttu-id="07be2-226">V instanci agregační kořenové, získávání požadovaná data z tohoto příkazu se provede metodu.</span><span class="sxs-lookup"><span data-stu-id="07be2-226">It executes the method on the aggregate root instance, getting the required data from the command.</span></span>

-   <span data-ttu-id="07be2-227">Zůstává v nový stav agregace k související databázi.</span><span class="sxs-lookup"><span data-stu-id="07be2-227">It persists the new state of the aggregate to its related database.</span></span> <span data-ttu-id="07be2-228">Tato poslední operace je aktuální transakci.</span><span class="sxs-lookup"><span data-stu-id="07be2-228">This last operation is the actual transaction.</span></span>

<span data-ttu-id="07be2-229">Se jeden agregace vycházejí z jeho agregační kořenové (kořenové entity) se obvykle týká obslužná rutina příkazu.</span><span class="sxs-lookup"><span data-stu-id="07be2-229">Typically, a command handler deals with a single aggregate driven by its aggregate root (root entity).</span></span> <span data-ttu-id="07be2-230">Pokud více agregace by měl být ovlivněn příjem jeden příkaz, můžete použít události domény ke rozšíří stavy nebo akcí na více agregace</span><span class="sxs-lookup"><span data-stu-id="07be2-230">If multiple aggregates should be impacted by the reception of a single command, you could use domain events to propagate states or actions across multiple aggregates</span></span>

<span data-ttu-id="07be2-231">Zde důležité je, že při zpracování příkazu, veškerou logiku domény musí být uvnitř modelu domény (agregace) plně zapouzdřené a připravena k testování jednotek.</span><span class="sxs-lookup"><span data-stu-id="07be2-231">The important point here is that when a command is being processed, all the domain logic should be inside the domain model (the aggregates), fully encapsulated and ready for unit testing.</span></span> <span data-ttu-id="07be2-232">Obslužná rutina funguje stejně jako způsob, jak získat modelu domény z databáze a jako poslední krok, říct vrstvě infrastruktury (úložiště) a zachová tak změny při změně modelu.</span><span class="sxs-lookup"><span data-stu-id="07be2-232">The command handler just acts as a way to get the domain model from the database, and as the final step, to tell the infrastructure layer (repositories) to persist the changes when the model is changed.</span></span> <span data-ttu-id="07be2-233">Výhodou tohoto přístupu je, že můžete Refaktorovat logiku domény ve model domény izolované, plně zapouzdřené, bohaté, chování beze změny kódu v aplikaci nebo infrastruktury vrstvy, které jsou na úrovni vložení (obslužné rutiny příkazů, webového rozhraní API, úložiště atd.).</span><span class="sxs-lookup"><span data-stu-id="07be2-233">The advantage of this approach is that you can refactor the domain logic in an isolated, fully encapsulated, rich, behavioral domain model without changing code in the application or infrastructure layers, which are the plumbing level (command handlers, Web API, repositories, etc.).</span></span>

<span data-ttu-id="07be2-234">Při obslužné rutiny příkazů získat komplexní, se příliš mnoho logikou, který může být pach kódu.</span><span class="sxs-lookup"><span data-stu-id="07be2-234">When command handlers get complex, with too much logic, that can be a code smell.</span></span> <span data-ttu-id="07be2-235">Zkontrolujte je a pokud najít logiku domény Refaktorovat kód přesunout této domény chování metody objektů domény (agregační kořenové a podřízené entity).</span><span class="sxs-lookup"><span data-stu-id="07be2-235">Review them, and if you find domain logic, refactor the code to move that domain behavior to the methods of the domain objects (the aggregate root and child entity).</span></span>

<span data-ttu-id="07be2-236">Jako příklad třídu obslužné rutiny příkaz následující kód ukazuje stejnou třídu CreateOrderCommandHandler, kterou jste viděli na začátku této kapitoly.</span><span class="sxs-lookup"><span data-stu-id="07be2-236">As an example of a command handler class, the following code shows the same CreateOrderCommandHandler class that you saw at the beginning of this chapter.</span></span> <span data-ttu-id="07be2-237">V takovém případě jsme zdůraznily metody zpracování a operace s objekty nebo agregace modelu domény.</span><span class="sxs-lookup"><span data-stu-id="07be2-237">In this case we have highlighted the Handle method and the operations with the domain model objects/aggregates.</span></span>

```csharp
public class CreateOrderCommandHandler
    : IAsyncRequestHandler<CreateOrderCommand, bool>
{
    private readonly IBuyerRepository _buyerRepository;
    private readonly IOrderRepository _orderRepository;

    public CreateOrderCommandHandler(IBuyerRepository buyerRepository,
        IOrderRepository orderRepository)
    {
        if (buyerRepository == null)
        {
            throw new ArgumentNullException(nameof(buyerRepository));
        }
        if (orderRepository == null)
        {
            throw new ArgumentNullException(nameof(orderRepository));
        }

        _buyerRepository = buyerRepository;
        _orderRepository = orderRepository;
    }

    public async Task<bool> Handle(CreateOrderCommand message)
    {
        //
        // Additional code ...
        //
        // Create the Order aggregate root
        // Add child entities and value objects through the Order aggregate root
        // methods and constructor so validations, invariants, and business logic
        // make sure that consistency is preserved across the whole aggregate
        var order = new Order(buyer.Id, payment.Id,
            new Address(message.Street,
            message.City, message.State,
            message.Country, message.ZipCode));

        foreach (var item in message.OrderItems)
        {
            order.AddOrderItem(item.ProductId, item.ProductName, item.UnitPrice,
                item.Discount, item.PictureUrl, item.Units);
        }

        // Persist the Order through the aggregate's repository
        _orderRepository.Add(order);
        return await _orderRepository.UnitOfWork.SaveChangesAsync();
    }
}
```

<span data-ttu-id="07be2-238">Toto jsou obslužná rutina příkazu by měl provést další kroky:</span><span class="sxs-lookup"><span data-stu-id="07be2-238">These are additional steps a command handler should take:</span></span>

-   <span data-ttu-id="07be2-239">Pomocí příkazu dat pracovat s agregační kořenu metody a chování.</span><span class="sxs-lookup"><span data-stu-id="07be2-239">Use the command’s data to operate with the aggregate root’s methods and behavior.</span></span>

-   <span data-ttu-id="07be2-240">Interně v rámci objektů domény vyvolávání událostí domény transakce se spustí, ale který je transparentní z hlediska of obslužná rutina příkazu.</span><span class="sxs-lookup"><span data-stu-id="07be2-240">Internally within the domain objects, raise domain events while the transaction is executed, but that is transparent from a command handler point of view.</span></span>

-   <span data-ttu-id="07be2-241">Pokud je na agregaci výsledek operace úspěšná, a po dokončení transakce, zvýšit obslužná rutina události integrace.</span><span class="sxs-lookup"><span data-stu-id="07be2-241">If the aggregate’s operation result is successful and after the transaction is finished, raise integration events command handler.</span></span> <span data-ttu-id="07be2-242">(Toto může také vydána infrastruktury třídy jako úložiště.)</span><span class="sxs-lookup"><span data-stu-id="07be2-242">(These might also be raised by infrastructure classes like repositories.)</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="07be2-243">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="07be2-243">Additional resources</span></span>

-   <span data-ttu-id="07be2-244">**Označit Seemann. V hranicích, jsou aplikace není objektově orientované**
    [*http://blog.ploeh.dk/2011/05/31/AttheBoundaries, orientované ApplicationsareNotObject /*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)</span><span class="sxs-lookup"><span data-stu-id="07be2-244">**Mark Seemann. At the Boundaries, Applications are Not Object-Oriented**
[*http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/*](http://blog.ploeh.dk/2011/05/31/AttheBoundaries,ApplicationsareNotObject-Oriented/)</span></span>

-   <span data-ttu-id="07be2-245">**Příkazy a události**
    [*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)</span><span class="sxs-lookup"><span data-stu-id="07be2-245">**Commands and events**
[*http://cqrs.nu/Faq/commands-and-events*](http://cqrs.nu/Faq/commands-and-events)</span></span>

-   <span data-ttu-id="07be2-246">**Obslužná rutina příkazu k čemu slouží? ** 
     [ *http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)</span><span class="sxs-lookup"><span data-stu-id="07be2-246">**What does a command handler do?**
[*http://cqrs.nu/Faq/command-handlers*](http://cqrs.nu/Faq/command-handlers)</span></span>

-   <span data-ttu-id="07be2-247">**Jimmy Bogard. Vzory příkaz domény – obslužné rutiny**
    [*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)</span><span class="sxs-lookup"><span data-stu-id="07be2-247">**Jimmy Bogard. Domain Command Patterns – Handlers**
[*https://jimmybogard.com/domain-command-patterns-handlers/*](https://jimmybogard.com/domain-command-patterns-handlers/)</span></span>

-   <span data-ttu-id="07be2-248">**Jimmy Bogard. Vzory příkaz domény – ověření**
    [*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)</span><span class="sxs-lookup"><span data-stu-id="07be2-248">**Jimmy Bogard. Domain Command Patterns – Validation**
[*https://jimmybogard.com/domain-command-patterns-validation/*](https://jimmybogard.com/domain-command-patterns-validation/)</span></span>

## <a name="the-command-process-pipeline-how-to-trigger-a-command-handler"></a><span data-ttu-id="07be2-249">Příkaz proces kanálu: spouštění obslužná rutina příkazu</span><span class="sxs-lookup"><span data-stu-id="07be2-249">The Command process pipeline: how to trigger a command handler</span></span>

<span data-ttu-id="07be2-250">Další otázka se postup vyvolání obslužná rutina příkazu.</span><span class="sxs-lookup"><span data-stu-id="07be2-250">The next question is how to invoke a command handler.</span></span> <span data-ttu-id="07be2-251">Ručně ji může volat z každého související řadiče ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="07be2-251">You could manually call it from each related ASP.NET Core controller.</span></span> <span data-ttu-id="07be2-252">Ale že přístup budou příliš doplněná a není ideální.</span><span class="sxs-lookup"><span data-stu-id="07be2-252">However, that approach would be too coupled and is not ideal.</span></span>

<span data-ttu-id="07be2-253">Další dvě hlavní možnosti, které jsou doporučené možnosti, jsou:</span><span class="sxs-lookup"><span data-stu-id="07be2-253">The other two main options, which are the recommended options, are:</span></span>

-   <span data-ttu-id="07be2-254">Prostřednictvím artefakt vzor zprostředkovatel v paměti.</span><span class="sxs-lookup"><span data-stu-id="07be2-254">Through an in-memory Mediator pattern artifact.</span></span>

-   <span data-ttu-id="07be2-255">S frontu asynchronní zpráv mezi řadiče a obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="07be2-255">With an asynchronous message queue, in between controllers and handlers.</span></span>

### <a name="using-the-mediator-pattern-in-memory-in-the-command-pipeline"></a><span data-ttu-id="07be2-256">Použití vzoru zprostředkovatel (v paměti) v příkazu kanálu</span><span class="sxs-lookup"><span data-stu-id="07be2-256">Using the Mediator pattern (in-memory) in the command pipeline</span></span>

<span data-ttu-id="07be2-257">Jak znázorňuje obrázek 9 – 21, v rámci CQRS přístupu použijete inteligentního zprostředkovatel, podobně jako sběrnici v paměti, což je dostatečně inteligentní přesměrování na základě typu příkazu nebo DTO přijímání správné obslužná rutina.</span><span class="sxs-lookup"><span data-stu-id="07be2-257">As shown in Figure 9-21, in a CQRS approach you use an intelligent mediator, similar to an in-memory bus, which is smart enough to redirect to the right command handler based on the type of the command or DTO being received.</span></span> <span data-ttu-id="07be2-258">Jeden černé šipky mezi součástmi představují závislosti mezi objekty (v mnoha případech vložit prostřednictvím DI) s jejich odpovídající interakce.</span><span class="sxs-lookup"><span data-stu-id="07be2-258">The single black arrows between components represent the dependencies between objects (in many cases, injected through DI) with their related interactions.</span></span>

![](./media/image22.png)

<span data-ttu-id="07be2-259">**Obrázek 9 – 21**.</span><span class="sxs-lookup"><span data-stu-id="07be2-259">**Figure 9-21**.</span></span> <span data-ttu-id="07be2-260">Použití vzoru zprostředkovatel v procesu v jednom mikroslužbu CQRS</span><span class="sxs-lookup"><span data-stu-id="07be2-260">Using the Mediator pattern in process in a single CQRS microservice</span></span>

<span data-ttu-id="07be2-261">Z důvodu, který pomocí vzoru zprostředkovatel smysl je, že v podnikových aplikacích zpracování požadavků můžete získat složitá.</span><span class="sxs-lookup"><span data-stu-id="07be2-261">The reason that using the Mediator pattern makes sense is that in enterprise applications, the processing requests can get complicated.</span></span> <span data-ttu-id="07be2-262">Chcete mít možnost Přidat otevřete počet mezi vyjímání otázky, jako je protokolování, ověření, auditování a zabezpečení.</span><span class="sxs-lookup"><span data-stu-id="07be2-262">You want to be able to add an open number of cross-cutting concerns like logging, validations, audit, and security.</span></span> <span data-ttu-id="07be2-263">V těchto případech můžete spoléhat na kanál zprostředkovatel (najdete v části [zprostředkovatel vzor](https://en.wikipedia.org/wiki/Mediator_pattern)) pro zajištění způsob tyto doplňující chování nebo mezi vyjímání otázky.</span><span class="sxs-lookup"><span data-stu-id="07be2-263">In these cases, you can rely on a mediator pipeline (see [Mediator pattern](https://en.wikipedia.org/wiki/Mediator_pattern)) to provide a means for these extra behaviors or cross-cutting concerns.</span></span>

<span data-ttu-id="07be2-264">Zprostředkovatel je objekt, který zapouzdří "jak" tohoto procesu: ho koordinuje spuštění na základě stavu, je vyvolána způsob obslužná rutina příkazu nebo datové části zadejte do obslužné rutiny.</span><span class="sxs-lookup"><span data-stu-id="07be2-264">A mediator is an object that encapsulates the “how” of this process: it coordinates execution based on state, the way a command handler is invoked, or the payload you provide to the handler.</span></span> <span data-ttu-id="07be2-265">Pomocí součásti zprostředkovatel můžete použít mezi vyjímání obavy centralizované a transparentním způsobem použitím dekoratéry (nebo [kanálu chování](https://github.com/jbogard/MediatR/wiki/Behaviors) od zprostředkovatel v3).</span><span class="sxs-lookup"><span data-stu-id="07be2-265">With a mediator component you can apply cross-cutting concerns in a centralized and transparent way by applying decorators (or [pipeline behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) since Mediator v3).</span></span> <span data-ttu-id="07be2-266">(Další informace najdete v tématu [Dekoratéra vzor](https://en.wikipedia.org/wiki/Decorator_pattern).)</span><span class="sxs-lookup"><span data-stu-id="07be2-266">(For more information, see the [Decorator pattern](https://en.wikipedia.org/wiki/Decorator_pattern).)</span></span>

<span data-ttu-id="07be2-267">Dekoratéry a chování jsou podobné [aspekt orientované programování (CHOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), pouze u konkrétní proces kanálu spravuje komponentu zprostředkovatel.</span><span class="sxs-lookup"><span data-stu-id="07be2-267">Decorators and behaviors are similar to [Aspect Oriented Programming (AOP)](https://en.wikipedia.org/wiki/Aspect-oriented_programming), only applied to a specific process pipeline managed by the mediator component.</span></span> <span data-ttu-id="07be2-268">Aspekty v CHOP, které implementují mezi vyjímání otázky se používají na základě *aspekt weavers* podle zachycení volání objektu nebo vložit během kompilace.</span><span class="sxs-lookup"><span data-stu-id="07be2-268">Aspects in AOP that implement cross-cutting concerns are applied based on *aspect weavers* injected at compilation time or based on object call interception.</span></span> <span data-ttu-id="07be2-269">Obou přístupů typické CHOP se někdy říká, že fungují "jako"magic, protože není snadno zjistit, jak funguje CHOP svou práci.</span><span class="sxs-lookup"><span data-stu-id="07be2-269">Both typical AOP approaches are sometimes said to work "like magic," because it is not easy to see how AOP does its work.</span></span> <span data-ttu-id="07be2-270">Při plánování práce s závažných problémech nebo oznámení chyb, může být obtížné ladění CHOP.</span><span class="sxs-lookup"><span data-stu-id="07be2-270">When dealing with serious issues or bugs, AOP can be difficult to debug.</span></span> <span data-ttu-id="07be2-271">Tyto dekoratéry chování jsou na druhé straně explicitní a použité jen v kontextu zprostředkovatel, tak ladění je mnohem víc předvídatelný a snadné.</span><span class="sxs-lookup"><span data-stu-id="07be2-271">On the other hand, these decorators/behaviors are explicit and applied only in the context of the mediator, so debugging is much more predictable and easy.</span></span>

<span data-ttu-id="07be2-272">Například v eShopOnContainers řazení mikroslužbu, implementovali jsme dva dekoratéry ukázka, [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) třídy a [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) třídy.</span><span class="sxs-lookup"><span data-stu-id="07be2-272">For example, in the eShopOnContainers ordering microservice, we implemented two sample decorators, a [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) class and a [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) class.</span></span> <span data-ttu-id="07be2-273">Implementace dekoratéra je vysvětleno v další části.</span><span class="sxs-lookup"><span data-stu-id="07be2-273">The decorator’s implementation is explained in the next section.</span></span> <span data-ttu-id="07be2-274">Všimněte si, že v budoucí verzi, bude eShopOnContainers migrovat do [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) a přesunout do [chování](https://github.com/jbogard/MediatR/wiki/Behaviors) místo použití dekorátory.</span><span class="sxs-lookup"><span data-stu-id="07be2-274">Note that in a future version, eShopOnContainers will migrate to [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) and move to [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) instead of using decorators.</span></span>

### <a name="using-message-queues-out-of-proc-in-the-commands-pipeline"></a><span data-ttu-id="07be2-275">Pomocí fronty zpráv (out-of-proc) v příkazu kanálu</span><span class="sxs-lookup"><span data-stu-id="07be2-275">Using message queues (out-of-proc) in the command’s pipeline</span></span>

<span data-ttu-id="07be2-276">Další možnost je použít asynchronní zprávy na základě zprostředkovatelé nebo fronty zpráv, jak je znázorněno v obrázek 9 – 22.</span><span class="sxs-lookup"><span data-stu-id="07be2-276">Another choice is to use asynchronous messages based on brokers or message queues, as shown in Figure 9-22.</span></span> <span data-ttu-id="07be2-277">Tato možnost může být spojen s komponentu zprostředkovatel bezprostředně před obslužná rutina příkazu.</span><span class="sxs-lookup"><span data-stu-id="07be2-277">That option could also be combined with the mediator component right before the command handler.</span></span>

![](./media/image23.png)

<span data-ttu-id="07be2-278">**Obrázek 9 – 22**.</span><span class="sxs-lookup"><span data-stu-id="07be2-278">**Figure 9-22**.</span></span> <span data-ttu-id="07be2-279">Pomocí příkazů CQRS fronty zpráv (mimo proces a komunikaci mezi procesy)</span><span class="sxs-lookup"><span data-stu-id="07be2-279">Using message queues (out of process and inter-process communication) with CQRS commands</span></span>

<span data-ttu-id="07be2-280">Pomocí zprávy fronty přijmout, že můžete další příkazy zkomplikovat kanálu váš příkaz, protože budete pravděpodobně muset kanál rozdělit do dvou procesů připojené prostřednictvím fronty externí zpráv.</span><span class="sxs-lookup"><span data-stu-id="07be2-280">Using message queues to accept the commands can further complicate your command’s pipeline, because you will probably need to split the pipeline into two processes connected through the external message queue.</span></span> <span data-ttu-id="07be2-281">Stále by měl použít pokud potřebujete mít lepší škálovatelnost a výkon podle asynchronní zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="07be2-281">Still, it should be used if you need to have improved scalability and performance based on asynchronous messaging.</span></span> <span data-ttu-id="07be2-282">Zvažte, že v případě obrázek 9 22, řadičem právě odešle příkaz zprávy do fronty a vrátí.</span><span class="sxs-lookup"><span data-stu-id="07be2-282">Consider that in the case of Figure 9-22, the controller just posts the command message into the queue and returns.</span></span> <span data-ttu-id="07be2-283">Obslužné rutiny příkazů pak zpracování zpráv vlastním tempem.</span><span class="sxs-lookup"><span data-stu-id="07be2-283">Then the command handlers process the messages at their own pace.</span></span> <span data-ttu-id="07be2-284">To znamená uvítali front – fronty zpráv vystupovat jako vyrovnávací paměť v případech hyper škálovatelnost je potřebné, například pro akcií nebo všechny další scénáře s k velkému počtu vstupní data.</span><span class="sxs-lookup"><span data-stu-id="07be2-284">That is a great benefit of queues—the message queue can act as a buffer in cases when hyper scalability is needed, such as for stocks or any other scenario with a high volume of ingress data.</span></span>

<span data-ttu-id="07be2-285">Ale kvůli asynchronní povaha fronty zpráv, musíte zjistit, jak komunikaci s aplikací klienta o úspěchu nebo neúspěchu procesu příkaz.</span><span class="sxs-lookup"><span data-stu-id="07be2-285">However, because of the asynchronous nature of message queues, you need to figure out how to communicate with the client application about the success or failure of the command’s process.</span></span> <span data-ttu-id="07be2-286">Platí pravidlo nikdy byste neměli používat "fire a zapomněli" příkazy.</span><span class="sxs-lookup"><span data-stu-id="07be2-286">As a rule, you should never use “fire and forget” commands.</span></span> <span data-ttu-id="07be2-287">Každé obchodní aplikace je potřeba vědět, pokud příkaz byla úspěšně zpracována, nebo aspoň ověřit a přijmout.</span><span class="sxs-lookup"><span data-stu-id="07be2-287">Every business application needs to know if a command was processed successfully, or at least validated and accepted.</span></span>

<span data-ttu-id="07be2-288">Proto schopnost reagovat na klienta po ověření příkaz zprávu, která byla odeslána do asynchronní fronty přidá složitost k vašemu systému, ve srovnání se příkazu v procesu proces, který vrátí výsledek operace po spuštění transakce.</span><span class="sxs-lookup"><span data-stu-id="07be2-288">Thus, being able to respond to the client after validating a command message that was submitted to an asynchronous queue adds complexity to your system, as compared to an in-process command process that returns the operation’s result after running the transaction.</span></span> <span data-ttu-id="07be2-289">Pomocí front, budete možná muset vrátit výsledek procesu příkaz prostřednictvím jiné operace výsledek zprávy, které se bude vyžadovat další součásti a vlastní komunikace v systému.</span><span class="sxs-lookup"><span data-stu-id="07be2-289">Using queues, you might need to return the result of the command process through other operation result messages, which will require additional components and custom communication in your system.</span></span>

<span data-ttu-id="07be2-290">Kromě toho jsou asynchronní příkazy jednosměrný příkazů, které jsou v mnoha případech nemusí být potřeba, jak je vysvětleno v následující zajímavé výměny mezi Burtsev Alexey a Gregu malé v [online konverzace](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span><span class="sxs-lookup"><span data-stu-id="07be2-290">Additionally, async commands are one-way commands, which in many cases might not be needed, as is explained in the following interesting exchange between Burtsev Alexey and Greg Young in an [online conversation](https://groups.google.com/forum/#!msg/dddcqrs/xhJHVxDx2pM/WP9qP8ifYCwJ):</span></span>

<span data-ttu-id="07be2-291">\[Burtsev Alexey\] najít velké množství kódu kde lidí používá asynchronní zpracování příkazu nebo jedním ze způsobů příkaz zasílání zpráv bez jakéhokoli důvodu Uděláte to tak (jejich nejsou prováděním dlouhé operace, budou nejsou provádění kódu externí asynchronní, se i nepřecházejí aplikace předěl, který má být pomocí sběrnice zpráv).</span><span class="sxs-lookup"><span data-stu-id="07be2-291">\[Burtsev Alexey\] I find lots of code where people use async command handling or one way command messaging without any reason to do so (they are not doing some long operation, they are not executing external async code, they do not even cross application boundary to be using message bus).</span></span> <span data-ttu-id="07be2-292">Proč se zavést tento nepotřebné složitost?</span><span class="sxs-lookup"><span data-stu-id="07be2-292">Why do they introduce this unnecessary complexity?</span></span> <span data-ttu-id="07be2-293">A ve skutečnosti, I nezaznamenali CQRS příklad kódu se blokování obslužné rutiny příkazů dosavadní práce, i když bude ve většině případů pracovat správně.</span><span class="sxs-lookup"><span data-stu-id="07be2-293">And actually, I haven't seen a CQRS code example with blocking command handlers so far, though it will work just fine in most cases.</span></span>

<span data-ttu-id="07be2-294">\[Gregu Young\] \[... \] příkaz asynchronní neexistuje, je ve skutečnosti jinou událost.</span><span class="sxs-lookup"><span data-stu-id="07be2-294">\[Greg Young\] \[...\] an asynchronous command doesn't exist; it's actually another event.</span></span> <span data-ttu-id="07be2-295">Pokud musí Souhlasím, co můžete poslat mi a vyvolat událost, pokud nesouhlasím, už jste zobrazuje oznámení něco udělat.</span><span class="sxs-lookup"><span data-stu-id="07be2-295">If I must accept what you send me and raise an event if I disagree, it's no longer you telling me to do something.</span></span> <span data-ttu-id="07be2-296">Je vám zobrazuje oznámení, které něco udělat.</span><span class="sxs-lookup"><span data-stu-id="07be2-296">It's you telling me something has been done.</span></span> <span data-ttu-id="07be2-297">Tohle vypadá jako malého rozdílu v první, ale má mnoho dopad.</span><span class="sxs-lookup"><span data-stu-id="07be2-297">This seems like a slight difference at first, but it has many implications.</span></span>

<span data-ttu-id="07be2-298">Asynchronní příkazy výrazně zvýšit složitost systému, protože neexistuje žádný jednoduchý způsob označující selhání.</span><span class="sxs-lookup"><span data-stu-id="07be2-298">Asynchronous commands greatly increase the complexity of a system, because there is no simple way to indicate failures.</span></span> <span data-ttu-id="07be2-299">Proto asynchronní příkazy nedoporučují jiné než potřeby škálování požadavky nebo ve zvláštních případech při komunikaci interní mikroslužeb pomocí zasílání zpráv.</span><span class="sxs-lookup"><span data-stu-id="07be2-299">Therefore, asynchronous commands are not recommended other than when scaling requirements are needed or in special cases when communicating the internal microservices through messaging.</span></span> <span data-ttu-id="07be2-300">V těchto případech je nutné vytvořit samostatné vytváření sestav a obnovení systému pro selhání.</span><span class="sxs-lookup"><span data-stu-id="07be2-300">In those cases, you must design a separate reporting and recovery system for failures.</span></span>

<span data-ttu-id="07be2-301">V původní verzi eShopOnContainers jsme se rozhodli použít příkaz synchronní zpracování, spuštěné z požadavků HTTP a řídí vzoru zprostředkovatel.</span><span class="sxs-lookup"><span data-stu-id="07be2-301">In the initial version of eShopOnContainers, we decided to use synchronous command processing, started from HTTP requests and driven by the Mediator pattern.</span></span> <span data-ttu-id="07be2-302">Který snadno umožňuje vrátit úspěch nebo selhání procesu, jako v [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementace.</span><span class="sxs-lookup"><span data-stu-id="07be2-302">That easily allows you to return the success or failure of the process, as in the [CreateOrderCommandHandler](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Commands/CreateOrderCommandHandler.cs) implementation.</span></span>

<span data-ttu-id="07be2-303">V každém případě to by měl být na základě požadavků vaší aplikace nebo na mikroslužbu obchodní rozhodnutí.</span><span class="sxs-lookup"><span data-stu-id="07be2-303">In any case, this should be a decision based on your application’s or microservice’s business requirements.</span></span>

## <a name="implementing-the-command-process-pipeline-with-a-mediator-pattern-mediatr"></a><span data-ttu-id="07be2-304">Implementace příkaz proces kanálu pomocí vzoru zprostředkovatel (MediatR)</span><span class="sxs-lookup"><span data-stu-id="07be2-304">Implementing the command process pipeline with a mediator pattern (MediatR)</span></span>

<span data-ttu-id="07be2-305">Jako ukázka provádění Tento průvodce navrhuje pomocí kanálu v procesu na základě vzoru zprostředkovatel k přijímání příkaz jednotky a směrování, v paměti, obslužné rutiny příkaz right.</span><span class="sxs-lookup"><span data-stu-id="07be2-305">As a sample implementation, this guide proposes using the in-process pipeline based on the Mediator pattern to drive command ingestion and routing them, in memory, to the right command handlers.</span></span> <span data-ttu-id="07be2-306">Průvodce také navrhne použití dekoratéry nebo [chování](https://github.com/jbogard/MediatR/wiki/Behaviors) k oddělení mezi vyjímání otázky.</span><span class="sxs-lookup"><span data-stu-id="07be2-306">The guide also proposes applying decorators or [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) in order to separate cross-cutting concerns.</span></span>

<span data-ttu-id="07be2-307">Pro implementaci v .NET Core jsou více knihovny open-source dostupné které implementují vzoru zprostředkovatel.</span><span class="sxs-lookup"><span data-stu-id="07be2-307">For implementation in .NET Core, there are multiple open-source libraries available that implement the Mediator pattern.</span></span> <span data-ttu-id="07be2-308">Knihovna používané v tomto průvodci se [MediatR](https://github.com/jbogard/MediatR) knihovny open-source (vytvořený Jimmy Bogard), ale může použít jiná možnost.</span><span class="sxs-lookup"><span data-stu-id="07be2-308">The library used in this guide is the [MediatR](https://github.com/jbogard/MediatR) open-source library (created by Jimmy Bogard), but you could use another approach.</span></span> <span data-ttu-id="07be2-309">MediatR je malý a jednoduchý knihovny, která umožňuje zpracování zpráv v paměti jako příkaz, při použití dekoratéry nebo chování.</span><span class="sxs-lookup"><span data-stu-id="07be2-309">MediatR is a small and simple library that allows you to process in-memory messages like a command, while applying decorators or behaviors.</span></span>

<span data-ttu-id="07be2-310">Použití vzoru zprostředkovatel vám pomůže snížit párování a izolovat si nemuseli dělat starosti požadovaný práce při automatické připojování k obslužná rutina, která provádí svou práci – v takovém případě do obslužné rutiny příkazů.</span><span class="sxs-lookup"><span data-stu-id="07be2-310">Using the Mediator pattern helps you to reduce coupling and to isolate the concerns of the requested work, while automatically connecting to the handler that performs that work—in this case, to command handlers.</span></span>

<span data-ttu-id="07be2-311">Dalším důvodem dobrý k použití vzoru zprostředkovatel byl vysvětlené Jimmy Bogard při revizi této příručce:</span><span class="sxs-lookup"><span data-stu-id="07be2-311">Another good reason to use the Mediator pattern was explained by Jimmy Bogard when reviewing this guide:</span></span>

<span data-ttu-id="07be2-312">Myslím, může být důležité zmínit, zde testování – poskytuje okno konzistentním změněnými do chování systému.</span><span class="sxs-lookup"><span data-stu-id="07be2-312">I think it might be worth mentioning testing here – it provides a nice consistent window into the behavior of your system.</span></span> <span data-ttu-id="07be2-313">V požadavku, odpověď na více systémů. Jsme zjistili tento aspekt velmi cenné v budově konzistentně chovají testy.</span><span class="sxs-lookup"><span data-stu-id="07be2-313">Request-in, response-out. We’ve found that aspect quite valuable in building consistently behaving tests.</span></span>

<span data-ttu-id="07be2-314">První dejte nám prohlédněte si kód řadiče ve skutečnosti použít objekt zprostředkovatel.</span><span class="sxs-lookup"><span data-stu-id="07be2-314">First, let us take a look to the controller code where you actually would use the mediator object.</span></span> <span data-ttu-id="07be2-315">Pokud nebyly používá zprostředkovatel objektu, musíte vložit všechny závislosti pro tento kontroler, třeba objekt protokolovacího nástroje a další.</span><span class="sxs-lookup"><span data-stu-id="07be2-315">If you were not using the mediator object, you would need to inject all the dependencies for that controller, things like a logger object and others.</span></span> <span data-ttu-id="07be2-316">Konstruktor proto může být poměrně složitá.</span><span class="sxs-lookup"><span data-stu-id="07be2-316">Therefore, the constructor would be quite complicated.</span></span> <span data-ttu-id="07be2-317">Na druhé straně Pokud chcete použít objekt zprostředkovatel, konstruktoru řadiče může být značnou měrou s několika závislosti místo velký počet závislostí, které byste měli Pokud jste měli jednu na operace vyjímání mezi, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="07be2-317">On the other hand, if you use the mediator object, the constructor of your controller can be a lot simpler, with just a few dependencies instead of many dependencies that you would have if you had one per cross-cutting operation, as in the following example:</span></span>

```csharp
public class OrdersController : Controller
{
    public OrdersController(IMediator mediator,
        IOrderQueries orderQueries)
    // ...
```

<span data-ttu-id="07be2-318">Uvidíte, že zprostředkovatel poskytuje vyčištění a štíhlého konstruktor kontroleru webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="07be2-318">You can see that the mediator provides a clean and lean Web API controller constructor.</span></span> <span data-ttu-id="07be2-319">Kromě toho v rámci metody kontroleru kód odeslat příkaz k objektu zprostředkovatel je téměř jeden řádek:</span><span class="sxs-lookup"><span data-stu-id="07be2-319">In addition, within the controller methods, the code to send a command to the mediator object is almost one line:</span></span>

```csharp
[Route("new")]
[HttpPost]
public async Task<IActionResult> CreateOrder([FromBody]CreateOrderCommand
    createOrderCommand)
{
    var commandResult = await _mediator.SendAsync(createOrderCommand);
    return commandResult ? (IActionResult)Ok() : (IActionResult)BadRequest();
}
```

<span data-ttu-id="07be2-320">Aby MediatR vědět třídy obslužná rutina příkazu budete muset registrovat zprostředkovatel třídy a třídy obslužné rutiny příkazů ve vašem kontejner IoC.</span><span class="sxs-lookup"><span data-stu-id="07be2-320">In order for MediatR to be aware of your command handler classes, you need to register the mediator classes and the command handler classes in your IoC container.</span></span> <span data-ttu-id="07be2-321">Ve výchozím nastavení MediatR používá Autofac jako kontejner IoC, ale můžete také použít integrované kontejner IoC jádro ASP.NET nebo jiných kontejneru, nepodporuje MediatR.</span><span class="sxs-lookup"><span data-stu-id="07be2-321">By default, MediatR uses Autofac as the IoC container, but you can also use the built-in ASP.NET Core IoC container or any other container supported by MediatR.</span></span>

<span data-ttu-id="07be2-322">Následující kód ukazuje, jak registrovat typy a příkazy pro zprostředkovatel při použití Autofac moduly.</span><span class="sxs-lookup"><span data-stu-id="07be2-322">The following code shows how to register Mediator’s types and commands when using Autofac modules.</span></span>

```csharp
public class MediatorModule : Autofac.Module
{
    protected override void Load(ContainerBuilder builder)
    {
        builder.RegisterAssemblyTypes(typeof(IMediator).GetTypeInfo().Assembly)
            .AsImplementedInterfaces();
        builder.RegisterAssemblyTypes(typeof(CreateOrderCommand)
            .GetTypeInfo().Assembly)
            .As(o => o.GetInterfaces()
            .Where(i => i.IsClosedTypeOf(typeof(IAsyncRequestHandler<,>)))
            .Select(i => new KeyedService("IAsyncRequestHandler", i)));
        builder.RegisterGenericDecorator(typeof(LogDecorator<,>),
            typeof(IAsyncRequestHandler<,>), "IAsyncRequestHandler");

        // Other types registration
    }
}
```

<span data-ttu-id="07be2-323">Protože každý obslužná rutina příkazu implementuje rozhraní s obecné IAsyncRequestHandler&lt;T&gt; a poté zkontroluje RegisteredAssemblyTypes objektu obslužná rutina je propojovat s jeho obslužná rutina příkazu každý příkaz, protože, relace je uvedeno v třídě commandhandler – jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="07be2-323">Because each command handler implements the interface with generic IAsyncRequestHandler&lt;T&gt; and then inspects the RegisteredAssemblyTypes object, the handler is able to relate each command with its command handler, because that relationship is stated in the CommandHandler class, as in the following example:</span></span>

```csharp
public class CreateOrderCommandHandler
  : IAsyncRequestHandler<CreateOrderCommand, bool>
{
```

<span data-ttu-id="07be2-324">Toto je kód, který příkazy koreluje s obslužné rutiny příkazů.</span><span class="sxs-lookup"><span data-stu-id="07be2-324">This is the code that correlates commands with command handlers.</span></span> <span data-ttu-id="07be2-325">Obslužná rutina je pouze jednoduchou třídu, ale dědí z RequestHandler&lt;T&gt;, a MediatR zajišťuje je volán s správné datové části.</span><span class="sxs-lookup"><span data-stu-id="07be2-325">The handler is just a simple class, but it inherits from RequestHandler&lt;T&gt;, and MediatR makes sure it gets invoked with the correct payload.</span></span>

## <a name="applying-cross-cutting-concerns-when-processing-commands-with-the-mediator-and-decorator-patterns"></a><span data-ttu-id="07be2-326">Při zpracování příkazů vzory zprostředkovatel a Dekoratéra použití mezi vyjímání otázky</span><span class="sxs-lookup"><span data-stu-id="07be2-326">Applying cross-cutting concerns when processing commands with the Mediator and Decorator patterns</span></span>

<span data-ttu-id="07be2-327">Neexistuje jeden krok: schopnost použít mezi vyjímání obavy zprostředkovatel kanálu.</span><span class="sxs-lookup"><span data-stu-id="07be2-327">There is one more thing: being able to apply cross-cutting concerns to the mediator pipeline.</span></span> <span data-ttu-id="07be2-328">Můžete také zjistit na konci kód Autofac registrace modulu jak se registrují dekoratéra, konkrétně zadejte vlastní třídu LogDecorator.</span><span class="sxs-lookup"><span data-stu-id="07be2-328">You can also see at the end of the Autofac registration module code how it is registering a decorator type, specifically, a custom LogDecorator class.</span></span>

<span data-ttu-id="07be2-329">Znovu si všimněte, že budoucí verzi systému eShopOnContainers se bude migrovat do [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) a přesunout do [chování](https://github.com/jbogard/MediatR/wiki/Behaviors) místo použití dekorátory.</span><span class="sxs-lookup"><span data-stu-id="07be2-329">Again, note that a future version of eShopOnContainers it will migrate to [MediatR 3](https://www.nuget.org/packages/MediatR/3.0.0) and move to [behaviors](https://github.com/jbogard/MediatR/wiki/Behaviors) instead of using decorators.</span></span>

<span data-ttu-id="07be2-330">Aby [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) třídy mohou být provedena jako následující kód, který ukládá do protokolu informace o obslužná rutina se spouští a bez ohledu na jeho, jestli byla úspěšná.</span><span class="sxs-lookup"><span data-stu-id="07be2-330">That [LogDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/LogDecorator.cs) class can be implemented as the following code, which logs information about the command handler being executed and whether it was successful or not.</span></span>

```csharp
public class LogDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly ILogger<LogDecorator<TRequest, TResponse>> _logger;

    public LogDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        ILogger<LogDecorator<TRequest, TResponse>> logger)
    {
        _inner = inner;
        _logger = logger;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        _logger.LogInformation($"Executing command {_inner.GetType().FullName}");
        var response = await _inner.Handle(message);
        _logger.LogInformation($"Succeeded executed command{_inner.GetType().FullName}");
        return response;
    }
}
```

<span data-ttu-id="07be2-331">Právě implementací této třídy dekoratéra a architekturu kanál s ním všechny příkazy, které jsou zpracované pomocí MediatR protokolování informace o provádění.</span><span class="sxs-lookup"><span data-stu-id="07be2-331">Just by implementing this decorator class and by decorating the pipeline with it, all the commands processed through MediatR will be logging information about the execution.</span></span>

<span data-ttu-id="07be2-332">EShopOnContainers řazení mikroslužbu platí také pro základní ověření, druhý dekoratéra [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) třídu, která závisí na [FluentValidation](https://github.com/JeremySkinner/FluentValidation) knihovny, jak je znázorněno Následující kód:</span><span class="sxs-lookup"><span data-stu-id="07be2-332">The eShopOnContainers ordering microservice also applies a second decorator for basic validations, the [ValidatorDecorator](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Decorators/ValidatorDecorator.cs) class that relies on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, as shown in the following code:</span></span>

```csharp
public class ValidatorDecorator<TRequest, TResponse>
    : IAsyncRequestHandler<TRequest, TResponse>
    where TRequest : IAsyncRequest<TResponse>
{
    private readonly IAsyncRequestHandler<TRequest, TResponse> _inner;
    private readonly IValidator<TRequest>[] _validators;

    public ValidatorDecorator(
        IAsyncRequestHandler<TRequest, TResponse> inner,
        IValidator<TRequest>[] validators)
    {
        _inner = inner;
        _validators = validators;
    }

    public async Task<TResponse> Handle(TRequest message)
    {
        var failures = _validators
            .Select(v => v.Validate(message))
            .SelectMany(result => result.Errors)
            .Where(error => error != null)
            .ToList();
            if (failures.Any())
            {
                throw new OrderingDomainException(
                $"Command Validation Errors for type {typeof(TRequest).Name}",
                new ValidationException("Validation exception", failures));
            }
            var response = await _inner.Handle(message);
        return response;
    }
}
```

<span data-ttu-id="07be2-333">Pak na základě [FluentValidation](https://github.com/JeremySkinner/FluentValidation) knihovna, kterou jsme vytvořili ověření dat předávaných s CreateOrderCommand, jako v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="07be2-333">Then, based on the [FluentValidation](https://github.com/JeremySkinner/FluentValidation) library, we created validation for the data passed with CreateOrderCommand, as in the following code:</span></span>

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
        RuleFor(command => command.CardExpiration).NotEmpty().Must(BeValidExpirationDate).
            WithMessage("Please specify a valid card expiration date");
        RuleFor(command => command.CardSecurityNumber).NotEmpty().Length(3);
        RuleFor(command => command.CardTypeId).NotEmpty();
        RuleFor(command => command.OrderItems).
            Must(ContainOrderItems).WithMessage("No order items found");
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

<span data-ttu-id="07be2-334">Můžete vytvořit další ověření.</span><span class="sxs-lookup"><span data-stu-id="07be2-334">You could create additional validations.</span></span> <span data-ttu-id="07be2-335">Toto je velmi vyčištění a elegantní způsob, jak implementovat vaše příkaz ověření.</span><span class="sxs-lookup"><span data-stu-id="07be2-335">This is a very clean and elegant way to implement your command validations.</span></span>

<span data-ttu-id="07be2-336">Podobným způsobem může implementovat jiné dekoratéry pro další aspekty nebo mezi vyjímání aspekty, které chcete použít k příkazům při jejich zpracování.</span><span class="sxs-lookup"><span data-stu-id="07be2-336">In a similar way, you could implement other decorators for additional aspects or cross-cutting concerns that you want to apply to commands when handling them.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="07be2-337">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="07be2-337">Additional resources</span></span>

##### <a name="the-mediator-pattern"></a><span data-ttu-id="07be2-338">Zprostředkovatel vzor</span><span class="sxs-lookup"><span data-stu-id="07be2-338">The mediator pattern</span></span>

-   <span data-ttu-id="07be2-339">**Zprostředkovatel vzor**
    [*https://en.wikipedia.org/wiki/Mediator\_vzor*](https://en.wikipedia.org/wiki/Mediator_pattern)</span><span class="sxs-lookup"><span data-stu-id="07be2-339">**Mediator pattern**
[*https://en.wikipedia.org/wiki/Mediator\_pattern*](https://en.wikipedia.org/wiki/Mediator_pattern)</span></span>

##### <a name="the-decorator-pattern"></a><span data-ttu-id="07be2-340">Vzor dekoratéra</span><span class="sxs-lookup"><span data-stu-id="07be2-340">The decorator pattern</span></span>

-   <span data-ttu-id="07be2-341">**Vzor dekoratéra**
    [*https://en.wikipedia.org/wiki/Decorator\_vzor*](https://en.wikipedia.org/wiki/Decorator_pattern)</span><span class="sxs-lookup"><span data-stu-id="07be2-341">**Decorator pattern**
[*https://en.wikipedia.org/wiki/Decorator\_pattern*](https://en.wikipedia.org/wiki/Decorator_pattern)</span></span>

##### <a name="mediatr-jimmy-bogard"></a><span data-ttu-id="07be2-342">MediatR (Jimmy Bogard)</span><span class="sxs-lookup"><span data-stu-id="07be2-342">MediatR (Jimmy Bogard)</span></span>

-   <span data-ttu-id="07be2-343">**MediatR.**</span><span class="sxs-lookup"><span data-stu-id="07be2-343">**MediatR.**</span></span> <span data-ttu-id="07be2-344">Úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="07be2-344">GitHub repo.</span></span>
    [<span data-ttu-id="07be2-345">*https://github.com/jbogard/MediatR*</span><span class="sxs-lookup"><span data-stu-id="07be2-345">*https://github.com/jbogard/MediatR*</span></span>](https://github.com/jbogard/MediatR)

-   <span data-ttu-id="07be2-346">**CQRS s MediatR a AutoMapper**
    [*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)</span><span class="sxs-lookup"><span data-stu-id="07be2-346">**CQRS with MediatR and AutoMapper**
[*https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/*](https://lostechies.com/jimmybogard/2015/05/05/cqrs-with-mediatr-and-automapper/)</span></span>

-   <span data-ttu-id="07be2-347">**Umístí řadičů vyváženosti: příspěvky a příkazy. ** 
     [ *https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)</span><span class="sxs-lookup"><span data-stu-id="07be2-347">**Put your controllers on a diet: POSTs and commands.**
[*https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/*](https://lostechies.com/jimmybogard/2013/12/19/put-your-controllers-on-a-diet-posts-and-commands/)</span></span>

-   <span data-ttu-id="07be2-348">**Boji se mezi vyjímání otázky se zřetězením příkazů zprostředkovatel**
    [*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)</span><span class="sxs-lookup"><span data-stu-id="07be2-348">**Tackling cross-cutting concerns with a mediator pipeline**
[*https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/*](https://lostechies.com/jimmybogard/2014/09/09/tackling-cross-cutting-concerns-with-a-mediator-pipeline/)</span></span>

-   <span data-ttu-id="07be2-349">**CQRS a REST: ideální doplněk**
    [*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)</span><span class="sxs-lookup"><span data-stu-id="07be2-349">**CQRS and REST: the perfect match**
[*https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/*](https://lostechies.com/jimmybogard/2016/06/01/cqrs-and-rest-the-perfect-match/)</span></span>

-   <span data-ttu-id="07be2-350">**Příklady MediatR kanálu**
    [*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)</span><span class="sxs-lookup"><span data-stu-id="07be2-350">**MediatR Pipeline Examples**
[*https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/*](https://lostechies.com/jimmybogard/2016/10/13/mediatr-pipeline-examples/)</span></span>

-   <span data-ttu-id="07be2-351">**Svislé řez testovací zařízení pro MediatR a ASP.NET Core**
    *<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/>*</span><span class="sxs-lookup"><span data-stu-id="07be2-351">**Vertical Slice Test Fixtures for MediatR and ASP.NET Core**
*<https://lostechies.com/jimmybogard/2016/10/24/vertical-slice-test-fixtures-for-mediatr-and-asp-net-core/> *</span></span>

-   <span data-ttu-id="07be2-352">**Rozšíření MediatR pro vkládání závislostí Microsoft vydané**
    [*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)</span><span class="sxs-lookup"><span data-stu-id="07be2-352">**MediatR Extensions for Microsoft Dependency Injection Released**
[*https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/*](https://lostechies.com/jimmybogard/2016/07/19/mediatr-extensions-for-microsoft-dependency-injection-released/)</span></span>

##### <a name="fluent-validation"></a><span data-ttu-id="07be2-353">Fluent ověření</span><span class="sxs-lookup"><span data-stu-id="07be2-353">Fluent validation</span></span>

-   <span data-ttu-id="07be2-354">**Jirka Skinner. FluentValidation.**</span><span class="sxs-lookup"><span data-stu-id="07be2-354">**Jeremy Skinner. FluentValidation.**</span></span> <span data-ttu-id="07be2-355">Úložiště GitHub.</span><span class="sxs-lookup"><span data-stu-id="07be2-355">GitHub repo.</span></span>
    [<span data-ttu-id="07be2-356">*https://github.com/JeremySkinner/FluentValidation*</span><span class="sxs-lookup"><span data-stu-id="07be2-356">*https://github.com/JeremySkinner/FluentValidation*</span></span>](https://github.com/JeremySkinner/FluentValidation)

>[!div class="step-by-step"]
<span data-ttu-id="07be2-357">[Předchozí] (microservice-application-layer-web-api-design.md) [Další] (.. /Implement-resilient-Applications/index.MD)</span><span class="sxs-lookup"><span data-stu-id="07be2-357">[Previous] (microservice-application-layer-web-api-design.md) [Next] (../implement-resilient-applications/index.md)</span></span>
