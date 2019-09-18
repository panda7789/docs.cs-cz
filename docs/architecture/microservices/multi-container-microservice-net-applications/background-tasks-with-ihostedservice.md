---
title: Implementace úloh na pozadí v mikroslužbách pomocí IHostedService a třídy BackgroundService
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Seznamte se s novými možnostmi použití IHostedService a BackgroundService k implementaci úloh na pozadí v mikroslužbách .NET Core.
ms.date: 01/07/2019
ms.openlocfilehash: ff263212536233bef85e9517442b4d7ed9eff115
ms.sourcegitcommit: 289e06e904b72f34ac717dbcc5074239b977e707
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/17/2019
ms.locfileid: "71039876"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="d2474-103">Implementace úloh na pozadí v mikroslužbách pomocí IHostedService a třídy BackgroundService</span><span class="sxs-lookup"><span data-stu-id="d2474-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="d2474-104">Úlohy na pozadí a naplánované úlohy jsou něco, co možná budete muset implementovat, případně v aplikaci založené na mikroslužbách nebo v jakémkoli typu aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2474-104">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="d2474-105">Rozdíl při použití architektury mikroslužeb je, že můžete implementovat jeden proces nebo kontejner mikroslužeb pro hostování těchto úloh na pozadí, abyste ho mohli škálovat, jak budete potřebovat, nebo můžete zajistit, aby běžela jedna instance. proces/kontejner mikroslužeb</span><span class="sxs-lookup"><span data-stu-id="d2474-105">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="d2474-106">Z obecného bodu zobrazení se v .NET Core říkáme tento typ úkolů *hostovaných službami*, protože se jedná o služby/logiku, které hostuje v rámci hostitele/aplikace nebo mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="d2474-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="d2474-107">Všimněte si, že v tomto případě hostovaná služba jednoduše znamená třídu s logikou úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="d2474-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="d2474-108">Vzhledem k tomu, že rozhraní .NET Core 2,0, rozhraní poskytuje <xref:Microsoft.Extensions.Hosting.IHostedService> nové rozhraní s názvem, které vám pomůže snadno implementovat hostované služby.</span><span class="sxs-lookup"><span data-stu-id="d2474-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="d2474-109">Základní nápad je, že můžete registrovat více úloh na pozadí (hostované služby), které běží na pozadí, když je spuštěný webový hostitel nebo hostitel, jak je znázorněno na obrázku 6-26.</span><span class="sxs-lookup"><span data-stu-id="d2474-109">The basic idea is that you can register multiple background tasks (hosted services), that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![ASP.NET Core 1. x a 2. x podpora IWebHost pro procesy na pozadí ve webových aplikacích, .NET Core 2, 1 podporuje IHost pro procesy na pozadí pomocí jednoduchých konzolových aplikací.](./media/image26.png)

<span data-ttu-id="d2474-111">**Obrázek 6-26**.</span><span class="sxs-lookup"><span data-stu-id="d2474-111">**Figure 6-26**.</span></span> <span data-ttu-id="d2474-112">Použití IHostedService na Webhostu vs. hostiteli</span><span class="sxs-lookup"><span data-stu-id="d2474-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="d2474-113">Všimněte si rozdílů mezi `WebHost` a `Host`.</span><span class="sxs-lookup"><span data-stu-id="d2474-113">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="d2474-114">A `WebHost` (implementace `IWebHost`základní třídy) v ASP.NET Core 2,0 je artefakt infrastruktury, který používáte k poskytování funkcí serveru http vašemu procesu, například Pokud implementujete webovou aplikaci MVC nebo službu webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="d2474-114">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as if you are implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="d2474-115">Poskytuje veškerou novou užitečnost infrastruktury v ASP.NET Core, takže můžete používat vkládání závislostí, vkládat middleware v kanálu požadavků atd. a přesně je použít `IHostedServices` pro úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="d2474-115">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, etc. and precisely use these `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="d2474-116">A `Host` (implementace `IHost`základní třídy) byla představena v rozhraní .NET Core 2,1.</span><span class="sxs-lookup"><span data-stu-id="d2474-116">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="d2474-117">V podstatě `WebHost` vám umožní mít podobnou infrastrukturu, než jakou máte (vkládání závislostí, hostované služby atd.), ale v takovém případě budete chtít mít jednoduchý a světlejší proces jako hostitel, ale nic nesouvisí s MVC. `Host` , Webové rozhraní API nebo funkce serveru HTTP.</span><span class="sxs-lookup"><span data-stu-id="d2474-117">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="d2474-118">Proto můžete zvolit a buď vytvořit specializovaný hostitelský proces s IHost pro zpracování hostovaných služeb a nic jiného, což je mikroslužba vytvořená pouze pro hostování `IHostedServices`portálu, nebo můžete alternativně zvětšit existující ASP.NET Core `WebHost` , jako je například existující ASP.NET Core webového rozhraní API nebo aplikace MVC.</span><span class="sxs-lookup"><span data-stu-id="d2474-118">Therefore, you can choose and either create a specialized host-process with IHost to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="d2474-119">Každý přístup má v závislosti na potřebách vaší firmy a škálovatelnosti své specialisty a nevýhody.</span><span class="sxs-lookup"><span data-stu-id="d2474-119">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="d2474-120">Dolní řádek je v podstatě, aby v případě, že vaše úlohy na pozadí neobsahují žádné akce s protokolem HTTP (IWebHost), měli byste použít IHost.</span><span class="sxs-lookup"><span data-stu-id="d2474-120">The bottom line is basically that if your background tasks have nothing to do with HTTP (IWebHost) you should use IHost.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="d2474-121">Registrace hostovaných služeb ve vašem Webhostu nebo hostiteli</span><span class="sxs-lookup"><span data-stu-id="d2474-121">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="d2474-122">Pojďme přejít podrobněji na `IHostedService` rozhraní, protože jeho použití je poměrně podobné `WebHost` v nebo v `Host`.</span><span class="sxs-lookup"><span data-stu-id="d2474-122">Let’s drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="d2474-123">Návěstí je jedním z příkladů artefaktu, který používá hostované služby, ale můžete ho použít i mnohem jednodušším způsobem:</span><span class="sxs-lookup"><span data-stu-id="d2474-123">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="d2474-124">Úloha na pozadí s dotazem, který hledá změny v databázi</span><span class="sxs-lookup"><span data-stu-id="d2474-124">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="d2474-125">Naplánovaná aktualizace některých mezipamětí v pravidelných intervalech.</span><span class="sxs-lookup"><span data-stu-id="d2474-125">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="d2474-126">Implementace QueueBackgroundWorkItem, která umožňuje spuštění úlohy ve vlákně na pozadí.</span><span class="sxs-lookup"><span data-stu-id="d2474-126">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="d2474-127">Zpracování zpráv z fronty zpráv na pozadí webové aplikace při sdílení běžných služeb, jako je `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="d2474-127">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="d2474-128">Úloha na pozadí začala s `Task.Run()`.</span><span class="sxs-lookup"><span data-stu-id="d2474-128">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="d2474-129">Všechny tyto akce můžete v zásadě přesměrovat na úlohu na pozadí na základě IHostedService.</span><span class="sxs-lookup"><span data-stu-id="d2474-129">You can basically offload any of those actions to a background task based on IHostedService.</span></span>

<span data-ttu-id="d2474-130">Způsob, jakým můžete přidat jeden `IHostedServices` nebo víc `WebHost` do `Host` svého nebo víc, se registruje pomocí standardu di (vkládání závislostí `Host` ) `WebHost` v ASP.NET Core (nebo v rozhraní .NET Core 2,1 a vyšší).</span><span class="sxs-lookup"><span data-stu-id="d2474-130">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the standard DI (dependency injection) in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="d2474-131">V podstatě je nutné zaregistrovat hostované služby v rámci známé `ConfigureServices()` metody `Startup` třídy, jako v následujícím kódu z typického Webhostu ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="d2474-131">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

```csharp
public IServiceProvider ConfigureServices(IServiceCollection services)
{
    //Other DI registrations;

    // Register Hosted Services
    services.AddSingleton<IHostedService, GracePeriodManagerService>();
    services.AddSingleton<IHostedService, MyHostedServiceB>();
    services.AddSingleton<IHostedService, MyHostedServiceC>();
    //...
}
```

<span data-ttu-id="d2474-132">V tomto kódu `GracePeriodManagerService` je hostovaná služba skutečný kód z objednávání firemní mikroslužeb v eShopOnContainers, zatímco ostatní dva jsou jenom dvě další ukázky.</span><span class="sxs-lookup"><span data-stu-id="d2474-132">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="d2474-133">Provádění `IHostedService` úlohy na pozadí je koordinováno s životností aplikace (hostitel nebo mikroslužba pro tuto skutečnost).</span><span class="sxs-lookup"><span data-stu-id="d2474-133">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="d2474-134">Při spuštění aplikace zaregistrujete úlohy a máte příležitost provést některé řádné akce nebo vyčistit při vypínání aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2474-134">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="d2474-135">Bez použití `IHostedService`můžete vlákno na pozadí vždy spustit, aby se spouštěla libovolná úloha.</span><span class="sxs-lookup"><span data-stu-id="d2474-135">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="d2474-136">Rozdíl je přesně v době vypnutí aplikace, kdy by bylo vlákno jednoduše ukončeno, aniž by bylo možné spustit bezproblémové čisticí akce.</span><span class="sxs-lookup"><span data-stu-id="d2474-136">The difference is precisely at the app’s shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="d2474-137">Rozhraní IHostedService</span><span class="sxs-lookup"><span data-stu-id="d2474-137">The IHostedService interface</span></span>

<span data-ttu-id="d2474-138">Při registraci `IHostedService`rozhraní .NET Core `StartAsync()` zavolá metody a `StopAsync()` vašeho `IHostedService` typu během spuštění a zastavení aplikace.</span><span class="sxs-lookup"><span data-stu-id="d2474-138">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="d2474-139">Konkrétně je volána metoda Start po spuštění serveru a `IApplicationLifetime.ApplicationStarted` aktivaci.</span><span class="sxs-lookup"><span data-stu-id="d2474-139">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="d2474-140">`IHostedService` Jak je definováno v .NET Core, vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="d2474-140">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

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

<span data-ttu-id="d2474-141">Jak můžete předplatit, můžete vytvořit více implementací IHostedService a zaregistrovat je v `ConfigureService()` metodě do kontejneru di, jak je uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="d2474-141">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="d2474-142">Všechny tyto hostované služby se spustí a zastaví společně s aplikací nebo mikroslužbou.</span><span class="sxs-lookup"><span data-stu-id="d2474-142">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="d2474-143">Jako vývojář zodpovídáte za zpracování akce zastavení vašich služeb, když `StopAsync()` hostitel spustí metodu.</span><span class="sxs-lookup"><span data-stu-id="d2474-143">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="d2474-144">Implementace IHostedService s vlastní třídou hostované služby odvozenou od základní třídy BackgroundService</span><span class="sxs-lookup"><span data-stu-id="d2474-144">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="d2474-145">Můžete pokračovat a vytvořit vlastní třídu hostované služby od začátku a implementovat `IHostedService`, jak potřebujete při použití .NET Core 2,0.</span><span class="sxs-lookup"><span data-stu-id="d2474-145">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span>

<span data-ttu-id="d2474-146">Vzhledem k tomu, že většina úloh na pozadí bude mít podobné požadavky v souvislosti se správou tokenů zrušení a dalšími typickými operacemi, existuje praktická abstraktní základní třída, `BackgroundService` kterou můžete odvodit z, s názvem (k dispozici od rozhraní .NET Core 2,1).</span><span class="sxs-lookup"><span data-stu-id="d2474-146">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="d2474-147">Tato třída poskytuje hlavní práci potřebnou k nastavení úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="d2474-147">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="d2474-148">Dalším kódem je abstraktní základní třída BackgroundService, jak je implementováno v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="d2474-148">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

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

<span data-ttu-id="d2474-149">Při odvozování od předchozí abstraktní základní třídy díky této zděděné implementaci stačí implementovat `ExecuteAsync()` metodu ve vlastní třídě hostované služby, jako v následujícím zjednodušeném kódu z eShopOnContainers, který se dotazuje. databáze a publikování integračních událostí do sběrnice událostí v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="d2474-149">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

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

<span data-ttu-id="d2474-150">V tomto konkrétním případě je pro eShopOnContainers spuštěná metoda aplikace, která se dotazuje databázové tabulky a hledá objednávky s určitým stavem a při použití změn publikuje události integrace prostřednictvím sběrnice událostí (pod ní může být použití RabbitMQ nebo Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="d2474-150">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="d2474-151">Samozřejmě můžete místo toho spustit jakoukoli jinou úlohu na pozadí firmy.</span><span class="sxs-lookup"><span data-stu-id="d2474-151">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="d2474-152">Ve výchozím nastavení je token zrušení nastaven s časovým limitem 5 sekund, i když můžete tuto hodnotu změnit při `WebHost` sestavování `UseShutdownTimeout` pomocí rozšíření `IWebHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="d2474-152">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="d2474-153">To znamená, že se očekává, že se naše služba zruší do 5 sekund, jinak se ukončí.</span><span class="sxs-lookup"><span data-stu-id="d2474-153">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="d2474-154">Následující kód se změní na tento čas na 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="d2474-154">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="d2474-155">Diagram třídy souhrnu</span><span class="sxs-lookup"><span data-stu-id="d2474-155">Summary class diagram</span></span>

<span data-ttu-id="d2474-156">Následující obrázek ukazuje vizuální Shrnutí tříd a rozhraní zapojených při implementaci IHostedServices.</span><span class="sxs-lookup"><span data-stu-id="d2474-156">The following image shows a visual summary of the classes and interfaced involved when implementing IHostedServices.</span></span>

![Diagram tříd: IWebHost a IHost můžou hostovat spoustu služeb, které dědí z BackgroundService, které implementuje IHostedService.](./media/image27.png)

<span data-ttu-id="d2474-158">**Obrázek 6-27**.</span><span class="sxs-lookup"><span data-stu-id="d2474-158">**Figure 6-27**.</span></span> <span data-ttu-id="d2474-159">Diagram tříd znázorňující více tříd a rozhraní souvisejících s IHostedService</span><span class="sxs-lookup"><span data-stu-id="d2474-159">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="d2474-160">Požadavky na nasazení a poznatky</span><span class="sxs-lookup"><span data-stu-id="d2474-160">Deployment considerations and takeaways</span></span>

<span data-ttu-id="d2474-161">Je důležité si uvědomit, že způsob nasazení ASP.NET Core `WebHost` nebo .NET Core `Host` může mít dopad na konečné řešení.</span><span class="sxs-lookup"><span data-stu-id="d2474-161">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="d2474-162">Pokud například nasadíte `WebHost` službu do služby IIS nebo běžný Azure App Service, může být hostitel vypnutý kvůli recyklaci fondu aplikací.</span><span class="sxs-lookup"><span data-stu-id="d2474-162">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="d2474-163">Pokud ale hostitele nasazujete jako kontejner do nástroje Orchestrator, jako je Kubernetes nebo Service Fabric, můžete řídit zaručený počet živých instancí hostitele.</span><span class="sxs-lookup"><span data-stu-id="d2474-163">But if you are deploying your host as a container into an orchestrator like Kubernetes or Service Fabric, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="d2474-164">Kromě toho můžete zvážit další přístupy v cloudu, zejména pro tyto scénáře, například Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="d2474-164">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="d2474-165">Nakonec, pokud potřebujete, aby služba běžela po celou dobu a nasadila na Windows Server, můžete použít službu systému Windows.</span><span class="sxs-lookup"><span data-stu-id="d2474-165">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="d2474-166">Ale i pro `WebHost` nasazení do fondu aplikací existují scénáře, jako je přeplnění nebo vyprázdnění mezipaměti v paměti aplikace, které by byly stále použitelné.</span><span class="sxs-lookup"><span data-stu-id="d2474-166">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application’s in-memory cache, that would be still applicable.</span></span>

<span data-ttu-id="d2474-167">Rozhraní poskytuje pohodlný způsob, jak spustit úlohy na pozadí ve webové aplikaci ASP.NET Core (v .NET Core 2,0) nebo v jakémkoli procesu nebo hostiteli (počínaje rozhraním .NET Core 2,1 s `IHost`). `IHostedService`</span><span class="sxs-lookup"><span data-stu-id="d2474-167">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="d2474-168">Hlavní výhodou je příležitost, kterou obdržíte s řádným zrušením pro vyčištění kódu úloh na pozadí při vypnutí samotného hostitele.</span><span class="sxs-lookup"><span data-stu-id="d2474-168">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="d2474-169">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="d2474-169">Additional resources</span></span>

- <span data-ttu-id="d2474-170">**Sestavení naplánované úlohy v ASP.NET Core/Standard 2,0**</span><span class="sxs-lookup"><span data-stu-id="d2474-170">**Building a scheduled task in ASP.NET Core/Standard 2.0**</span></span>  
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- <span data-ttu-id="d2474-171">**Implementace IHostedService v ASP.NET Core 2,0**</span><span class="sxs-lookup"><span data-stu-id="d2474-171">**Implementing IHostedService in ASP.NET Core 2.0**</span></span>  
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- <span data-ttu-id="d2474-172">**Ukázka GenericHost s využitím ASP.NET Core 2,1**</span><span class="sxs-lookup"><span data-stu-id="d2474-172">**GenericHost Sample using ASP.NET Core 2.1**</span></span>  
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

>[!div class="step-by-step"]
><span data-ttu-id="d2474-173">[Předchozí](test-aspnet-core-services-web-apps.md)Další
>[](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="d2474-173">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
