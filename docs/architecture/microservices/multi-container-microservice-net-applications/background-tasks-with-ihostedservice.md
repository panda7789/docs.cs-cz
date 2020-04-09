---
title: Implementace úloh na pozadí v mikroslužbách pomocí služby IHostedService a třídy BackgroundService
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Seznamte se s novými možnostmi použití služeb IHostedService a BackgroundService k implementaci úloh na pozadí v mikroslužbách .NET Core.
ms.date: 01/30/2020
ms.openlocfilehash: fd26d0444312d3525ad95b2273f28a6ceaa27911
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988333"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="9e33a-103">Implementace úloh na pozadí v mikroslužbách pomocí služby IHostedService a třídy BackgroundService</span><span class="sxs-lookup"><span data-stu-id="9e33a-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="9e33a-104">Úlohy na pozadí a naplánované úlohy jsou něco, co budete muset implementovat, nakonec v aplikaci založené na mikroslužbách nebo v jakémkoli druhu aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e33a-104">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="9e33a-105">Rozdíl při použití architektury mikroslužeb je, že můžete implementovat jeden proces mikroslužeb nebo kontejner pro hostování těchto úloh na pozadí, takže můžete škálovat dolů nebo nahoru podle potřeby, nebo můžete dokonce ujistěte se, že spustí jednu instanci tohoto procesu mikroslužeb/kontejneru.</span><span class="sxs-lookup"><span data-stu-id="9e33a-105">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="9e33a-106">Z obecného hlediska v .NET Core jsme nazvali tyto typy úkolů *hostované služby*, protože se jedná o služby nebo logiku, kterou hostujete v rámci hostitele/aplikace/mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="9e33a-106">From a generic point of view, in .NET Core we called these type of tasks *Hosted Services*, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="9e33a-107">Všimněte si, že v tomto případě hostované služby jednoduše znamená třídu s logikou úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="9e33a-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="9e33a-108">Vzhledem k tomu, že rozhraní .NET <xref:Microsoft.Extensions.Hosting.IHostedService> Core 2.0, rozhraní poskytuje nové rozhraní s názvem pomáhá snadno implementovat hostované služby.</span><span class="sxs-lookup"><span data-stu-id="9e33a-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="9e33a-109">Základní myšlenkou je, že můžete zaregistrovat více úloh na pozadí (hostované služby), které běží na pozadí, zatímco váš webový hostitel nebo hostitel běží, jak je znázorněno na obrázku 6-26.</span><span class="sxs-lookup"><span data-stu-id="9e33a-109">The basic idea is that you can register multiple background tasks (hosted services) that run in the background while your web host or host is running, as shown in the image 6-26.</span></span>

![Diagram porovnávající ASP.NET Core IWebHost a .NET Core IHost.](./media/background-tasks-with-ihostedservice/ihosted-service-webhost-vs-host.png)

<span data-ttu-id="9e33a-111">**Obrázek 6-26**.</span><span class="sxs-lookup"><span data-stu-id="9e33a-111">**Figure 6-26**.</span></span> <span data-ttu-id="9e33a-112">Použití služby IHostedService ve službě WebHost vs. hostitel</span><span class="sxs-lookup"><span data-stu-id="9e33a-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="9e33a-113">ASP.NET podpora core 1.x `IWebHost` a 2.x pro procesy na pozadí ve webových aplikacích.</span><span class="sxs-lookup"><span data-stu-id="9e33a-113">ASP.NET Core 1.x and 2.x support `IWebHost` for background processes in web apps.</span></span> <span data-ttu-id="9e33a-114">.NET Core 2.1 a `IHost` novější verze podporují procesy na pozadí s jednoduchými konzolovými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="9e33a-114">.NET Core 2.1 and later versions support `IHost` for background processes with plain console apps.</span></span> <span data-ttu-id="9e33a-115">Všimněte si `WebHost` rozdílu mezi a `Host`.</span><span class="sxs-lookup"><span data-stu-id="9e33a-115">Note the difference made between `WebHost` and `Host`.</span></span>

<span data-ttu-id="9e33a-116">A `WebHost` (implementace základní `IWebHost`třídy ) v ASP.NET Core 2.0 je artefakt infrastruktury, který slouží k poskytování funkcí serveru HTTP pro váš proces, například při implementaci webové aplikace MVC nebo služby webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="9e33a-116">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as when you're implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="9e33a-117">Poskytuje všechny nové infrastruktury dobra v ASP.NET Core, což vám umožní používat vkládání závislostí, vložit middlewares v kanálu požadavku a podobně.</span><span class="sxs-lookup"><span data-stu-id="9e33a-117">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the request pipeline, and similar.</span></span> <span data-ttu-id="9e33a-118">Používá `WebHost` tyto velmi `IHostedServices` stejné pro úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="9e33a-118">The `WebHost` uses these very same `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="9e33a-119">A `Host` (implementace základní `IHost`třídy) byla zavedena v rozhraní .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="9e33a-119">A `Host` (base class implementing `IHost`) was introduced in .NET Core 2.1.</span></span> <span data-ttu-id="9e33a-120">V podstatě, `Host` a umožňuje mít podobnou infrastrukturu, než to, co máte s `WebHost` (vkládání závislostí, hostované služby, atd.), ale v tomto případě, stačí mít jednoduchý a lehčí proces jako hostitel, s ničím souvisejícím s MVC, Web API nebo HTTP server funkce.</span><span class="sxs-lookup"><span data-stu-id="9e33a-120">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="9e33a-121">Proto můžete zvolit a buď vytvořit specializovaný hostitelský proces s `IHost` pro zpracování hostované služby a nic `IHostedServices`jiného, jako mikroslužby `WebHost`vyrobené pouze pro hostování , nebo můžete alternativně rozšířit existující ASP.NET Core , jako je například existující ASP.NET Core Web API nebo MVC aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e33a-121">Therefore, you can choose and either create a specialized host-process with `IHost` to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span>

<span data-ttu-id="9e33a-122">Každý přístup má klady a zápory v závislosti na vaší firmě a potřebách škálovatelnosti.</span><span class="sxs-lookup"><span data-stu-id="9e33a-122">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="9e33a-123">Pointa je v podstatě, že pokud vaše pozadí`IWebHost`úkoly `IHost`nemají nic společného s HTTP ( ) měli byste použít .</span><span class="sxs-lookup"><span data-stu-id="9e33a-123">The bottom line is basically that if your background tasks have nothing to do with HTTP (`IWebHost`) you should use `IHost`.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="9e33a-124">Registrace hostovaných služeb ve vašem WebHost nebo Host</span><span class="sxs-lookup"><span data-stu-id="9e33a-124">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="9e33a-125">Pojďme přejít dále `IHostedService` na rozhraní, protože jeho `WebHost` použití je `Host`docela podobné v nebo v .</span><span class="sxs-lookup"><span data-stu-id="9e33a-125">Let's drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span>

<span data-ttu-id="9e33a-126">SignalR je jedním z příkladů artefaktu pomocí hostovaných služeb, ale můžete jej také použít pro mnohem jednodušší věci, jako jsou:</span><span class="sxs-lookup"><span data-stu-id="9e33a-126">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

- <span data-ttu-id="9e33a-127">Úloha na pozadí dotazování databáze hledá změny.</span><span class="sxs-lookup"><span data-stu-id="9e33a-127">A background task polling a database looking for changes.</span></span>
- <span data-ttu-id="9e33a-128">Naplánovaná úloha pravidelně aktualizuje některé mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="9e33a-128">A scheduled task updating some cache periodically.</span></span>
- <span data-ttu-id="9e33a-129">Implementace QueueBackgroundWorkItem, která umožňuje úlohu, která má být provedena na podprocesu na pozadí.</span><span class="sxs-lookup"><span data-stu-id="9e33a-129">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
- <span data-ttu-id="9e33a-130">Zpracování zpráv z fronty zpráv na pozadí webové aplikace při `ILogger`sdílení běžných služeb, jako je například .</span><span class="sxs-lookup"><span data-stu-id="9e33a-130">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
- <span data-ttu-id="9e33a-131">Úloha na `Task.Run()`pozadí byla zahájena pomocí souboru .</span><span class="sxs-lookup"><span data-stu-id="9e33a-131">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="9e33a-132">V podstatě můžete převést některé z těchto akcí `IHostedService`na úlohu na pozadí, která implementuje .</span><span class="sxs-lookup"><span data-stu-id="9e33a-132">You can basically offload any of those actions to a background task that implements `IHostedService`.</span></span>

<span data-ttu-id="9e33a-133">Způsob, jakým přidáte `IHostedServices` jeden `WebHost` nebo `Host` více do vašeho nebo <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A>  je jejich registrací prostřednictvím metody rozšíření v ASP.NET Core `WebHost` (nebo `Host` v rozhraní .NET Core 2.1 a vyšší).</span><span class="sxs-lookup"><span data-stu-id="9e33a-133">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the <xref:Microsoft.Extensions.DependencyInjection.ServiceCollectionHostedServiceExtensions.AddHostedService%2A> extension method in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1 and above).</span></span> <span data-ttu-id="9e33a-134">V podstatě musíte zaregistrovat hostované služby v rámci známé `ConfigureServices()` metody `Startup` třídy, jako v následujícím kódu z typického ASP.NET WebHost.</span><span class="sxs-lookup"><span data-stu-id="9e33a-134">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span>

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

<span data-ttu-id="9e33a-135">V tomto kódu `GracePeriodManagerService` hostované služby je skutečný kód z objednávání obchodní mikroslužby v eShopOnContainers, zatímco další dva jsou jen dva další ukázky.</span><span class="sxs-lookup"><span data-stu-id="9e33a-135">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="9e33a-136">Spuštění `IHostedService` úlohy na pozadí je koordinováno s životností aplikace (hostitele nebo mikroslužby, když na to přijde).</span><span class="sxs-lookup"><span data-stu-id="9e33a-136">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="9e33a-137">Zaregistrujete úkoly při spuštění aplikace a máte možnost provést některé řádné akce nebo vyčištění při ukončení aplikace.</span><span class="sxs-lookup"><span data-stu-id="9e33a-137">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="9e33a-138">Bez `IHostedService`použití můžete vždy spustit vlákno na pozadí pro spuštění libovolné úlohy.</span><span class="sxs-lookup"><span data-stu-id="9e33a-138">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="9e33a-139">Rozdíl je právě v době vypnutí aplikace, kdy by toto vlákno bylo jednoduše ukončeno, aniž by mělo možnost spustit řádné akce čištění.</span><span class="sxs-lookup"><span data-stu-id="9e33a-139">The difference is precisely at the app's shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>

## <a name="the-ihostedservice-interface"></a><span data-ttu-id="9e33a-140">Rozhraní IHostedService</span><span class="sxs-lookup"><span data-stu-id="9e33a-140">The IHostedService interface</span></span>

<span data-ttu-id="9e33a-141">Při registraci `IHostedService`, .NET Core `StartAsync()` `StopAsync()` bude volat `IHostedService` a metody vašeho typu během spuštění a zastavení aplikace v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="9e33a-141">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="9e33a-142">Konkrétně start je volána po `IApplicationLifetime.ApplicationStarted` spuštění serveru a je spuštěn.</span><span class="sxs-lookup"><span data-stu-id="9e33a-142">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="9e33a-143">Jak `IHostedService` je definováno v .NET Core, vypadá takto.</span><span class="sxs-lookup"><span data-stu-id="9e33a-143">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

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

<span data-ttu-id="9e33a-144">Jak si dokážete představit, můžete vytvořit více implementací IHostedService a zaregistrovat je metodou `ConfigureService()` do kontejneru DI, jak je znázorněno dříve.</span><span class="sxs-lookup"><span data-stu-id="9e33a-144">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="9e33a-145">Všechny tyto hostované služby budou spuštěny a zastaveny spolu s aplikací nebo mikroslužbou.</span><span class="sxs-lookup"><span data-stu-id="9e33a-145">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="9e33a-146">Jako vývojář jste zodpovědní za zpracování akce zastavení `StopAsync()` vašich služeb při spuštění metody hostitelem.</span><span class="sxs-lookup"><span data-stu-id="9e33a-146">As a developer, you are responsible for handling the stopping action of your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="9e33a-147">Implementace služby IHostedService s vlastní třídou hostované služby odvozenou ze základní třídy BackgroundService</span><span class="sxs-lookup"><span data-stu-id="9e33a-147">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="9e33a-148">Můžete pokračovat a vytvořit vlastní třídu hostované služby od začátku a implementovat `IHostedService`, jak je potřeba udělat při použití rozhraní .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="9e33a-148">You could go ahead and create your custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span>

<span data-ttu-id="9e33a-149">Však vzhledem k tomu, že většina úloh na pozadí bude mít podobné potřeby s ohledem na `BackgroundService` správu tokenů zrušení a další typické operace, je pohodlné abstraktní základní třídy můžete odvodit z, pojmenovaný (k dispozici od .NET Core 2.1).</span><span class="sxs-lookup"><span data-stu-id="9e33a-149">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, there is a convenient abstract base class you can derive from, named `BackgroundService` (available since .NET Core 2.1).</span></span>

<span data-ttu-id="9e33a-150">Tato třída poskytuje hlavní práci potřebnou k nastavení úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="9e33a-150">That class provides the main work needed to set up the background task.</span></span>

<span data-ttu-id="9e33a-151">Další kód je abstraktní Základní třída BackgroundService, jak je implementována v .NET Core.</span><span class="sxs-lookup"><span data-stu-id="9e33a-151">The next code is the abstract BackgroundService base class as implemented in .NET Core.</span></span>

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

<span data-ttu-id="9e33a-152">Při odvození z předchozí abstraktní základní třídy, díky této zděděné `ExecuteAsync()` implementaci, stačí implementovat metodu ve vlastní třídě hostované služby, jako v následujícím zjednodušeném kódu z eShopOnContainers, který je dotazování databáze a publikování integračních událostí do sběrnice událostí v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="9e33a-152">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

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
        // Constructor's parameters validations...
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

<span data-ttu-id="9e33a-153">V tomto konkrétním případě pro eShopOnContainers je provádění aplikační metody, která je dotazování databázové tabulky hledá objednávky s určitým stavem a při použití změn, je publikování událostí integrace prostřednictvím sběrnice událostí (pod ním může být pomocí RabbitMQ nebo Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="9e33a-153">In this specific case for eShopOnContainers, it's executing an application method that's querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span>

<span data-ttu-id="9e33a-154">Samozřejmě, můžete spustit jakýkoli jiný obchodní pozadí úkol, místo toho.</span><span class="sxs-lookup"><span data-stu-id="9e33a-154">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="9e33a-155">Ve výchozím nastavení je token zrušení nastaven s časovým limitem 5 `WebHost` sekund, `UseShutdownTimeout` i `IWebHostBuilder`když tuto hodnotu můžete změnit při vytváření rozšíření .</span><span class="sxs-lookup"><span data-stu-id="9e33a-155">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="9e33a-156">To znamená, že naše služba by měla být zrušena do 5 sekund, jinak bude náhle zabita.</span><span class="sxs-lookup"><span data-stu-id="9e33a-156">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="9e33a-157">Následující kód by se mění, že čas na 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="9e33a-157">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="9e33a-158">Souhrnný diagram třídy</span><span class="sxs-lookup"><span data-stu-id="9e33a-158">Summary class diagram</span></span>

<span data-ttu-id="9e33a-159">Následující obrázek znázorňuje vizuální souhrn tříd a rozhraní zapojených při implementaci IHostedServices.</span><span class="sxs-lookup"><span data-stu-id="9e33a-159">The following image shows a visual summary of the classes and interfaces involved when implementing IHostedServices.</span></span>

![Diagram znázorňující, že IWebHost a IHost mohou hostit mnoho služeb.](./media/background-tasks-with-ihostedservice/class-diagram-custom-ihostedservice.png)

<span data-ttu-id="9e33a-161">**Obrázek 6-27**.</span><span class="sxs-lookup"><span data-stu-id="9e33a-161">**Figure 6-27**.</span></span> <span data-ttu-id="9e33a-162">Diagram tříd znázorňující více tříd a rozhraní souvisejících se službou IHostedService</span><span class="sxs-lookup"><span data-stu-id="9e33a-162">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

<span data-ttu-id="9e33a-163">Diagram tříd: IWebHost a IHost mohou hostovat mnoho služeb, které dědí z BackgroundService, která implementuje IHostedService.</span><span class="sxs-lookup"><span data-stu-id="9e33a-163">Class diagram: IWebHost and IHost can host many services, which inherit from BackgroundService, which implements IHostedService.</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="9e33a-164">Důležité informace o nasazení a s sebou</span><span class="sxs-lookup"><span data-stu-id="9e33a-164">Deployment considerations and takeaways</span></span>

<span data-ttu-id="9e33a-165">Je důležité si uvědomit, že způsob `WebHost` nasazení ASP.NET `Host` core nebo .NET Core může mít vliv na konečné řešení.</span><span class="sxs-lookup"><span data-stu-id="9e33a-165">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="9e33a-166">Pokud například nasadíte službu `WebHost` IIS nebo běžnou službu Azure App Service, můžete hostitele vypnout z důvodu recyklace fondu aplikací.</span><span class="sxs-lookup"><span data-stu-id="9e33a-166">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="9e33a-167">Ale pokud nasazujete hostitele jako kontejner do orchestrátoru, jako je Kubernetes, můžete řídit jistý počet živých instancí hostitele.</span><span class="sxs-lookup"><span data-stu-id="9e33a-167">But if you are deploying your host as a container into an orchestrator like Kubernetes, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="9e33a-168">Kromě toho můžete zvážit další přístupy v cloudu speciálně pro tyto scénáře, jako jsou funkce Azure.</span><span class="sxs-lookup"><span data-stu-id="9e33a-168">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> <span data-ttu-id="9e33a-169">A konečně, pokud potřebujete službu, která má být spuštěna po celou dobu a nasazuje te na systém Windows Server, můžete použít službu Systému Windows.</span><span class="sxs-lookup"><span data-stu-id="9e33a-169">Finally, if you need the service to be running all the time and are deploying on a Windows Server you could use a Windows Service.</span></span>

<span data-ttu-id="9e33a-170">Ale i `WebHost` pro nasazené do fondu aplikací existují scénáře, jako je repopulating nebo vyprázdnění mezipaměti aplikace v paměti, které by byly stále použitelné.</span><span class="sxs-lookup"><span data-stu-id="9e33a-170">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application's in-memory cache that would be still applicable.</span></span>

<span data-ttu-id="9e33a-171">Rozhraní `IHostedService` poskytuje pohodlný způsob, jak spustit úlohy na pozadí ve webové aplikaci ASP.NET Core (v rozhraní .NET Core 2.0 `IHost`a novějších verzích) nebo v libovolném procesu/hostiteli (počínaje rozhraním .NET Core 2.1 s).</span><span class="sxs-lookup"><span data-stu-id="9e33a-171">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0 and later versions) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="9e33a-172">Jeho hlavní výhodou je příležitost, kterou získáte s elegantním zrušením k vyčištění kódu vašich úloh na pozadí, když se hostitel sám vypíná.</span><span class="sxs-lookup"><span data-stu-id="9e33a-172">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="9e33a-173">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="9e33a-173">Additional resources</span></span>

- <span data-ttu-id="9e33a-174">**Vytvoření naplánované úlohy v ASP.NET Jádrem/Standardem 2.0** </span><span class="sxs-lookup"><span data-stu-id="9e33a-174">**Building a scheduled task in ASP.NET Core/Standard 2.0** </span></span>\
  <https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html>

- <span data-ttu-id="9e33a-175">**Implementace služby IHostedService v ASP.NET Jádra 2.0** </span><span class="sxs-lookup"><span data-stu-id="9e33a-175">**Implementing IHostedService in ASP.NET Core 2.0** </span></span>\
  <https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice>

- <span data-ttu-id="9e33a-176">**Ukázka generického hostitele pomocí ASP.NET Core 2.1** </span><span class="sxs-lookup"><span data-stu-id="9e33a-176">**GenericHost Sample using ASP.NET Core 2.1** </span></span>\
  <https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample>

> [!div class="step-by-step"]
> <span data-ttu-id="9e33a-177">[Předchozí](test-aspnet-core-services-web-apps.md)
> [další](implement-api-gateways-with-ocelot.md)</span><span class="sxs-lookup"><span data-stu-id="9e33a-177">[Previous](test-aspnet-core-services-web-apps.md)
[Next](implement-api-gateways-with-ocelot.md)</span></span>
