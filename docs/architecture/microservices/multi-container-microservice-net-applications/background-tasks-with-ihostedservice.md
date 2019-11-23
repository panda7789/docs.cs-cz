---
title: Implementace úloh na pozadí v mikroslužbách pomocí IHostedService a třídy BackgroundService
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Seznamte se s novými možnostmi použití IHostedService a BackgroundService k implementaci úloh na pozadí v mikroslužbách .NET Core.
ms.date: 01/07/2019
ms.openlocfilehash: d289d8ccc737fa9fc13b95da44e4b617b431f96a
ms.sourcegitcommit: 22be09204266253d45ece46f51cc6f080f2b3fd6
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/07/2019
ms.locfileid: "73737193"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="e7cf4-103">Implementace úloh na pozadí v mikroslužbách pomocí IHostedService a třídy BackgroundService</span><span class="sxs-lookup"><span data-stu-id="e7cf4-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="e7cf4-104">Úlohy na pozadí a naplánované úlohy jsou něco, co možná budete muset implementovat, případně v aplikaci založené na mikroslužbách nebo v jakémkoli typu aplikace.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-104">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="e7cf4-105">Rozdíl při použití architektury mikroslužeb je, že můžete implementovat jeden proces nebo kontejner mikroslužeb pro hostování těchto úloh na pozadí, abyste ho mohli škálovat podle potřeby, nebo se můžete ujistit, že spouští jednu instanci tohoto procesu nebo kontejneru mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-105">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="e7cf4-106">Z obecného bodu zobrazení se v .NET Core říkáme tento typ úkolů *hostovaných službami*, protože se jedná o služby/logiku, které hostuje v rámci hostitele/aplikace nebo mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="e7cf4-107">Všimněte si, že v tomto případě hostovaná služba jednoduše znamená třídu s logikou úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="e7cf4-108">Vzhledem k tomu, že rozhraní .NET Core 2,0, rozhraní poskytuje nové rozhraní s názvem <xref:Microsoft.Extensions.Hosting.IHostedService>, které vám pomůže snadno implementovat hostované služby.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="e7cf4-109">Základní nápad je, že můžete registrovat více úloh na pozadí (hostované služby), které běží na pozadí, když je spuštěný webový hostitel nebo hostitel, jak je znázorněno na obrázku 6-26.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-109">The basic idea is that you can register multiple background tasks (hosted services) that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![Diagram porovnávání ASP.NET Core IWebHost a .NET Core IHost.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

<span data-ttu-id="e7cf4-111">**Obrázek 6-26**.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-111">**Figure 6-26**.</span></span> <span data-ttu-id="e7cf4-112">Použití IHostedService na Webhostu vs. hostiteli</span><span class="sxs-lookup"><span data-stu-id="e7cf4-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="e7cf4-113">ASP.NET Core 1. x a 2. x podporují IWebHost pro procesy na pozadí ve webových aplikacích.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-113">ASP.NET Core 1.x and 2.x support IWebHost for background processes in web apps.</span></span> <span data-ttu-id="e7cf4-114">.NET Core 2,1 podporuje IHost pro procesy na pozadí pomocí jednoduchých konzolových aplikací.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-114">.NET Core 2.1 supports IHost for background processes with plain console apps.</span></span> <span data-ttu-id="e7cf4-115">Všimněte si rozdílů mezi `WebHost` a `Host`.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-115">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="e7cf4-116">`WebHost` (základní třída implementující `IWebHost`) v ASP.NET Core 2,0 je artefakt infrastruktury, který používáte k poskytování funkcí serveru HTTP vašemu procesu, jako třeba při implementaci webové aplikace MVC nebo služby webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-116">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as if you are implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="e7cf4-117">Poskytuje veškerou novou užitečnost infrastruktury v ASP.NET Core, což vám umožní používat vkládání závislostí, vkládat middleware v kanálu požadavků atd. a přesné použití těchto `IHostedServices` pro úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-117">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, etc. and precisely use these `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="e7cf4-118">`Host` (implementace `IHost`základní třídy) byla představena v rozhraní .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-118">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="e7cf4-119">V podstatě vám `Host` umožňuje mít podobnou infrastrukturu, než jakou máte s `WebHost` (vkládání závislostí, hostované služby atd.), ale v takovém případě budete chtít mít jednoduchý a světlejší proces jako hostitel, a to bez ohledu na funkce MVC, webové rozhraní API nebo HTTP serveru.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-119">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="e7cf4-120">Proto si můžete vybrat a buď vytvořit specializovaný hostitelský proces s IHost pro zpracování hostovaných služeb a nic jiného, což je mikroslužba vytvořená pouze pro hostování `IHostedServices`, nebo můžete alternativně roztáhnout existující ASP.NET Core `WebHost`, jako je existující ASP.NET Core webového rozhraní API nebo aplikace MVC.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-120">Therefore, you can choose and either create a specialized host-process with IHost to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="e7cf4-121">Každý přístup má v závislosti na potřebách vaší firmy a škálovatelnosti své specialisty a nevýhody.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-121">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="e7cf4-122">Dolní řádek je v podstatě, aby v případě, že vaše úlohy na pozadí neobsahují žádné akce s protokolem HTTP (IWebHost), měli byste použít IHost.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-122">The bottom line is basically that if your background tasks have nothing to do with HTTP (IWebHost) you should use IHost.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="e7cf4-123">Registrace hostovaných služeb ve vašem Webhostu nebo hostiteli</span><span class="sxs-lookup"><span data-stu-id="e7cf4-123">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="e7cf4-124">Pojďme přejít podrobněji na rozhraní `IHostedService`, protože jeho použití je poměrně podobné v `WebHost` nebo v `Host`.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-124">Let’s drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="e7cf4-125">Návěstí je jedním z příkladů artefaktu, který používá hostované služby, ale můžete ho použít i mnohem jednodušším způsobem:</span><span class="sxs-lookup"><span data-stu-id="e7cf4-125">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="e7cf4-126">Úloha na pozadí s dotazem, který hledá změny v databázi</span><span class="sxs-lookup"><span data-stu-id="e7cf4-126">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="e7cf4-127">Naplánovaná aktualizace některých mezipamětí v pravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-127">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="e7cf4-128">Implementace QueueBackgroundWorkItem, která umožňuje spuštění úlohy ve vlákně na pozadí.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-128">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="e7cf4-129">Zpracování zpráv z fronty zpráv na pozadí webové aplikace při sdílení běžných služeb, jako je `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-129">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="e7cf4-130">Úloha na pozadí začala s `Task.Run()`.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-130">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="e7cf4-131">Všechny tyto akce můžete v zásadě přesměrovat na úlohu na pozadí na základě IHostedService.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-131">You can basically offload any of those actions to a background task based on IHostedService.</span></span>

<span data-ttu-id="e7cf4-132">Způsob, jakým do `Host` `WebHost` přidáte jeden nebo víc `IHostedServices`, je při jejich registraci prostřednictvím metody rozšíření <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> v ASP.NET Core `WebHost` (nebo v `Host` .NET Core 2,1 a vyšší).</span><span class="sxs-lookup"><span data-stu-id="e7cf4-132">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> extension method in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="e7cf4-133">V podstatě je nutné zaregistrovat hostované služby v rámci známé `ConfigureServices()` metody `Startup` třídy, jako v následujícím kódu z typického Webhostu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-133">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //Other DI registrations;

    // Register Hosted Services
    services.AddHostedService<GracePeriodManagerService>();
    services.AddHostedService<MyHostedServiceB>();
    services.AddHostedService<MyHostedServiceC>();
    //...
}
```

<span data-ttu-id="e7cf4-134">V tomto kódu `GracePeriodManagerService` hostovaná služba je skutečný kód z objednávání firemní mikroslužeb v eShopOnContainers, zatímco ostatní dva jsou jenom dvě další ukázky.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-134">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="e7cf4-135">`IHostedService` provádění úlohy na pozadí se koordinuje s životností aplikace (hostitel nebo mikroslužba pro tuto skutečnost).</span><span class="sxs-lookup"><span data-stu-id="e7cf4-135">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="e7cf4-136">Při spuštění aplikace zaregistrujete úlohy a máte příležitost provést některé řádné akce nebo vyčistit při vypínání aplikace.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-136">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="e7cf4-137">Bez použití `IHostedService`můžete vždy spustit vlákno na pozadí pro spuštění jakékoli úlohy.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-137">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="e7cf4-138">Rozdíl je přesně v době vypnutí aplikace, kdy by bylo vlákno jednoduše ukončeno, aniž by bylo možné spustit bezproblémové čisticí akce.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-138">The difference is precisely at the app’s shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="e7cf4-139">Rozhraní IHostedService</span><span class="sxs-lookup"><span data-stu-id="e7cf4-139">The IHostedService interface</span></span>

<span data-ttu-id="e7cf4-140">Když zaregistrujete `IHostedService`, .NET Core při spuštění a zastavení aplikace zavolá metody `StartAsync()` a `StopAsync()` daného `IHostedService` typu.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-140">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="e7cf4-141">Konkrétně je zavolána metoda Start po spuštění serveru a spuštění `IApplicationLifetime.ApplicationStarted`.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-141">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="e7cf4-142">`IHostedService` jak je definováno v .NET Core, vypadá následovně.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-142">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

```csharp
namespace Microsoft.Extensions.Hosting
{
    //
    // Summary:
    //     Defines methods for objects that are managed by the host.
    public interface IHostedService
    {
        //
        // Summary:
        // Triggered when the application host is ready to start the service.
        Task StartAsync(CancellationToken cancellationToken);
        //
        // Summary:
        // Triggered when the application host is performing a graceful shutdown.
        Task StopAsync(CancellationToken cancellationToken);
    }
}
```

<span data-ttu-id="e7cf4-143">Jak můžete předplatit, můžete vytvořit více implementací IHostedService a zaregistrovat je v metodě `ConfigureService()` do kontejneru DI, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-143">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="e7cf4-144">Všechny tyto hostované služby se spustí a zastaví společně s aplikací nebo mikroslužbou.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-144">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="e7cf4-145">Jako vývojář zodpovídáte za zpracování akce zastavení vašich služeb, když hostitel spustí metodu `StopAsync()`.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-145">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="e7cf4-146">Implementace IHostedService s vlastní třídou hostované služby odvozenou od základní třídy BackgroundService</span><span class="sxs-lookup"><span data-stu-id="e7cf4-146">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="e7cf4-147">Můžete pokračovat a vytvořit vlastní třídu hostované služby od začátku a implementovat `IHostedService`, jak potřebujete při použití .NET Core 2,0.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-147">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span>

<span data-ttu-id="e7cf4-148">Vzhledem k tomu, že většina úloh na pozadí bude mít podobné požadavky v souvislosti se správou tokenů zrušení a dalšími typickými operacemi, existuje praktická abstraktní základní třída, kterou můžete odvodit z, s názvem `BackgroundService` (k dispozici od rozhraní .NET Core 2,1).</span><span class="sxs-lookup"><span data-stu-id="e7cf4-148">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="e7cf4-149">Tato třída poskytuje hlavní práci potřebnou k nastavení úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-149">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="e7cf4-150">Dalším kódem je abstraktní základní třída BackgroundService, jak je implementováno v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-150">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

```csharp
// Copyright (c) .NET Foundation. Licensed under the Apache License, Version 2.0.
/// <summary>
/// Base class for implementing a long running <see cref="IHostedService"/>.
/// </summary>
public abstract class BackgroundService : IHostedService, IDisposable
{
    private Task _executingTask;
    private readonly CancellationTokenSource _stoppingCts =
                                                   new CancellationTokenSource();

    protected abstract Task ExecuteAsync(CancellationToken stoppingToken);

    public virtual Task StartAsync(CancellationToken cancellationToken)
    {
        // Store the task we're executing
        _executingTask = ExecuteAsync(_stoppingCts.Token);

        // If the task is completed then return it,
        // this will bubble cancellation and failure to the caller
        if (_executingTask.IsCompleted)
        {
            return _executingTask;
        }

        // Otherwise it's running
        return Task.CompletedTask;
    }

    public virtual async Task StopAsync(CancellationToken cancellationToken)
    {
        // Stop called without start
        if (_executingTask == null)
        {
            return;
        }

        try
        {
            // Signal cancellation to the executing method
            _stoppingCts.Cancel();
        }
        finally
        {
            // Wait until the task completes or the stop token triggers
            await Task.WhenAny(_executingTask, Task.Delay(Timeout.Infinite,
                                                          cancellationToken));
        }

    }

    public virtual void Dispose()
    {
        _stoppingCts.Cancel();
    }
}
```

<span data-ttu-id="e7cf4-151">Při odvozování od předchozí abstraktní základní třídy díky této zděděné implementaci stačí implementovat metodu `ExecuteAsync()` ve vlastní třídě hostované služby, jako v následujícím zjednodušeném kódu z eShopOnContainers, který v případě potřeby dotazuje databázi a publikuje události integrace do sběrnice událostí.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-151">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

```csharp
public class GracePeriodManagerService : BackgroundService
{
    private readonly ILogger<GracePeriodManagerService> _logger;
    private readonly OrderingBackgroundSettings _settings;

    private readonly IEventBus _eventBus;

    public GracePeriodManagerService(IOptions<OrderingBackgroundSettings> settings,
                                     IEventBus eventBus,
                                     ILogger<GracePeriodManagerService> logger)
    {
        //Constructor’s parameters validations...
    }

    protected override async Task ExecuteAsync(CancellationToken stoppingToken)
    {
        _logger.LogDebug($"GracePeriodManagerService is starting.");

        stoppingToken.Register(() =>
            _logger.LogDebug($" GracePeriod background task is stopping."));

        while (!stoppingToken.IsCancellationRequested)
        {
            _logger.LogDebug($"GracePeriod task doing background work.");

            // This eShopOnContainers method is querying a database table
            // and publishing events into the Event Bus (RabbitMQ / ServiceBus)
            CheckConfirmedGracePeriodOrders();

            await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
        }

        _logger.LogDebug($"GracePeriod background task is stopping.");
    }

    .../...
}
```

<span data-ttu-id="e7cf4-152">V tomto konkrétním případě je pro eShopOnContainers spuštěná metoda aplikace, která se dotazuje databázové tabulky a hledá objednávky s určitým stavem a při použití změn publikuje události integrace prostřednictvím sběrnice událostí (pod ní může být použití RabbitMQ nebo Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="e7cf4-152">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="e7cf4-153">Samozřejmě můžete místo toho spustit jakoukoli jinou úlohu na pozadí firmy.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-153">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="e7cf4-154">Ve výchozím nastavení je token zrušení nastaven s časovým limitem 5 sekund, i když můžete tuto hodnotu změnit při sestavování `WebHost` pomocí rozšíření `UseShutdownTimeout` `IWebHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-154">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="e7cf4-155">To znamená, že se očekává, že se naše služba zruší do 5 sekund, jinak se ukončí.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-155">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="e7cf4-156">Následující kód se změní na tento čas na 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-156">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="e7cf4-157">Diagram třídy souhrnu</span><span class="sxs-lookup"><span data-stu-id="e7cf4-157">Summary class diagram</span></span>

<span data-ttu-id="e7cf4-158">Následující obrázek ukazuje vizuální souhrn tříd a rozhraní zapojených při implementaci IHostedServices.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-158">The following image shows a visual summary of the classes and interfaces involved when implementing IHostedServices.</span></span>

![Diagram znázorňující, že IWebHost a IHost můžou hostovat spoustu služeb.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

<span data-ttu-id="e7cf4-160">**Obrázek 6-27**.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-160">**Figure 6-27**.</span></span> <span data-ttu-id="e7cf4-161">Diagram tříd znázorňující více tříd a rozhraní souvisejících s IHostedService</span><span class="sxs-lookup"><span data-stu-id="e7cf4-161">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

<span data-ttu-id="e7cf4-162">Diagram tříd: IWebHost a IHost mohou hostovat mnoho služeb, které dědí z BackgroundService, které implementuje IHostedService.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-162">Class diagram: IWebHost and IHost can host many services, which inherit from BackgroundService, which implements IHostedService.</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="e7cf4-163">Požadavky na nasazení a poznatky</span><span class="sxs-lookup"><span data-stu-id="e7cf4-163">Deployment considerations and takeaways</span></span>

<span data-ttu-id="e7cf4-164">Je důležité si uvědomit, že způsob nasazení ASP.NET Core `WebHost` nebo .NET Core `Host` může mít dopad na konečné řešení.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-164">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="e7cf4-165">Pokud například nasadíte `WebHost` ve službě IIS nebo v běžném Azure App Service, může být hostitel vypnutý kvůli recyklaci fondu aplikací.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-165">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="e7cf4-166">Pokud ale hostitele nasazujete jako kontejner do nástroje Orchestrator, jako je Kubernetes nebo Service Fabric, můžete řídit zaručený počet živých instancí hostitele.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-166">But if you are deploying your host as a container into an orchestrator like Kubernetes or Service Fabric, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="e7cf4-167">Kromě toho můžete zvážit další přístupy v cloudu, zejména pro tyto scénáře, například Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-167">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="e7cf4-168">Nakonec, pokud potřebujete, aby služba běžela po celou dobu a nasadila na Windows Server, můžete použít službu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-168">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="e7cf4-169">I když `WebHost` nasazený do fondu aplikací, existují scénáře, jako je přeplnění nebo vyprázdnění mezipaměti v paměti aplikace, kterou by bylo možné dál použít.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-169">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application’s in-memory cache that would be still applicable.</span></span>

<span data-ttu-id="e7cf4-170">Rozhraní `IHostedService` poskytuje pohodlný způsob, jak spustit úlohy na pozadí ve webové aplikaci ASP.NET Core (v .NET Core 2,0) nebo v jakémkoli procesu nebo hostiteli (počínaje rozhraním .NET Core 2,1 s `IHost`).</span><span class="sxs-lookup"><span data-stu-id="e7cf4-170">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="e7cf4-171">Hlavní výhodou je příležitost, kterou obdržíte s řádným zrušením pro vyčištění kódu úloh na pozadí při vypnutí samotného hostitele.</span><span class="sxs-lookup"><span data-stu-id="e7cf4-171">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="e7cf4-172">Další materiály a zdroje informací</span><span class="sxs-lookup"><span data-stu-id="e7cf4-172">Additional resources</span></span>

- <span data-ttu-id="e7cf4-173">**Vytvoření naplánované úlohy v ASP.NET Core/Standard 2,0**
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html></span><span class="sxs-lookup"><span data-stu-id="e7cf4-173">**Building a scheduled task in ASP.NET Core/Standard 2.0**
<https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html></span></span>

- <span data-ttu-id="e7cf4-174">**Implementace IHostedService v
  ASP.NET Core 2,0** <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice></span><span class="sxs-lookup"><span data-stu-id="e7cf4-174">**Implementing IHostedService in ASP.NET Core 2.0**
<https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice></span></span>

- <span data-ttu-id="e7cf4-175">**Ukázka GenericHost s využitím
  ASP.NET Core 2,1** <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample></span><span class="sxs-lookup"><span data-stu-id="e7cf4-175">**GenericHost Sample using ASP.NET Core 2.1**
<https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample></span></span>

>[!div class="step-by-step"]
><span data-ttu-id="e7cf4-176">[Předchozí](test-aspnet-core-services-web-apps.md)
>[Další](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="e7cf4-176">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
