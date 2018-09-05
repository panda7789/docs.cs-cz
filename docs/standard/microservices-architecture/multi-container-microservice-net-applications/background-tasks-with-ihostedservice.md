---
title: Implementace úloh na pozadí v mikroslužbách s IHostedService a BackgroundService třídy
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Implementace úloh na pozadí v mikroslužbách s IHostedService a BackgroundService třídy
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.openlocfilehash: 6ce9e40334e80e8bd17ce2f3d2569a1e3c39d09e
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/05/2018
ms.locfileid: "43745772"
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="6fa3f-103">Implementace úloh na pozadí v mikroslužbách s IHostedService a BackgroundService třídy</span><span class="sxs-lookup"><span data-stu-id="6fa3f-103">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="6fa3f-104">Naplánované úlohy a úlohy na pozadí jsou něco, co možná budete muset implementovat, případně v aplikaci na základě mikroslužeb nebo v jakékoliv aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-104">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="6fa3f-105">Rozdíl při použití architektury mikroslužeb je, že můžete implementovat jednu mikroslužbu procesu/kontejner pro hostování tyto úlohy na pozadí, takže je možné ji dolů/nahoru škálovat podle musíte nebo dokonce zajistit, že běží jedna instance, která mikroslužby procesu nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-105">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="6fa3f-106">Z obecného pohledu v .NET Core jsme volat tyto typu úloh hostovaných služeb, protože jsou služby a logiku, která hostujete v rámci vašeho hostitele/aplikace/mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-106">From a generic point of view, in .NET Core we called these type of tasks Hosted Services, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="6fa3f-107">Všimněte si, že v tomto případě hostovanou službu jednoduše znamená, že třída s atributem logiky úloh na pozadí.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-107">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="6fa3f-108">Od verze rozhraní .NET Core 2.0, rozhraní poskytuje nové rozhraní s názvem <xref:Microsoft.Extensions.Hosting.IHostedService> vám pomáhá snadno implementovat hostované služby.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-108">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="6fa3f-109">Základní myšlenka je, že můžete registrovat několika úloh na pozadí (hostované služby), které běží na pozadí při webového hostitele nebo hostiteli běží, jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-109">The basic idea is that you can register multiple background tasks (hosted services), that run in the background while your web host or host is running, as shown in the image below.</span></span>

![](./media/image26.png)

<span data-ttu-id="6fa3f-110">**Obrázek 8-25.**</span><span class="sxs-lookup"><span data-stu-id="6fa3f-110">**Figure 8-25.**</span></span> <span data-ttu-id="6fa3f-111">Použití IHostedService v webového hostitele a hostitele</span><span class="sxs-lookup"><span data-stu-id="6fa3f-111">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="6fa3f-112">Všimněte si rozdílu mezi `WebHost` a `Host`.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-112">Note the difference made between `WebHost` and `Host`.</span></span> <span data-ttu-id="6fa3f-113">A `WebHost` (základní třídy implementující `IWebHost`) v ASP.NET Core 2.0 je artefaktů infrastruktury vám poskytují HTTP server s funkcí pro váš proces, třeba když implementujete MVC webové aplikace nebo služba webového rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-113">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as if you are implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="6fa3f-114">Poskytuje všechny nové infrastruktury přesnosti v ASP.NET Core, která vám umožní pomocí vkládání závislostí, vložit middlewares v kanálu protokolu HTTP, atd. a pomocí nich přesně `IHostedServices` pro úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-114">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the HTTP pipeline, etc. and precisely use these `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="6fa3f-115">A `Host` (základní třídy implementující `IHost`), ale něco nového v .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-115">A `Host` (base class implementing `IHost`), however, is something new in .NET Core 2.1.</span></span> <span data-ttu-id="6fa3f-116">V podstatě `Host` umožňuje mít podobné infrastruktury, než máte s `WebHost` (injektáž závislostí, hostovaných služeb atd.), ale v tomto případě chcete mít jednoduchou a lehčí proces jako hostitele, není nic související s MVC , Webové rozhraní API nebo HTTP funkce serveru.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-116">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="6fa3f-117">Proto můžete použít a buď vytvořte specializované hostitelský proces s IHost hostovaným službám a nic jiného, mikroslužby, vytvořená speciálně pro hostování `IHostedServices`, nebo můžete případně rozšířit stávající ASP.NET Core `WebHost` , jako je například existující aplikaci webového rozhraní API ASP.NET Core nebo MVC.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-117">Therefore, you can choose and either create a specialized host-process with IHost to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatively extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span> 

<span data-ttu-id="6fa3f-118">Každý přístup má výhody a nevýhody v závislosti na potřebách vaší firmy a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-118">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="6fa3f-119">Dolní řádek je v podstatě, že pokud vaše úlohy na pozadí nemají co dělat s HTTP (IWebHost) byste měli používat a IHost, pokud je k dispozici v rozhraní .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-119">The bottom line is basically that if your background tasks have nothing to do with HTTP (IWebHost) you should use and IHost, when available in .NET Core 2.1.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="6fa3f-120">Registrace hostovaných služeb v webového hostitele nebo hostitele</span><span class="sxs-lookup"><span data-stu-id="6fa3f-120">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="6fa3f-121">Můžeme přejít na další nižší `IHostedService` rozhraní, protože jeho používání je hodně podobné jako u `WebHost` nebo v `Host`.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-121">Let’s drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span> 

<span data-ttu-id="6fa3f-122">SignalR je jeden příklad artefakt pomocí hostovaných služeb, ale můžete ho můžete použít pro jednodušší věci, jako je:</span><span class="sxs-lookup"><span data-stu-id="6fa3f-122">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

-   <span data-ttu-id="6fa3f-123">Dotazování databáze hledá změny úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-123">A background task polling a database looking for changes.</span></span>
-   <span data-ttu-id="6fa3f-124">Naplánované úlohy pravidelně aktualizuje některé mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-124">A scheduled task updating some cache periodically.</span></span>
-   <span data-ttu-id="6fa3f-125">Implementace QueueBackgroundWorkItem umožňující úkol má být proveden na vlákně na pozadí.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-125">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
-   <span data-ttu-id="6fa3f-126">Zpracování zpráv z fronty zpráv z webové aplikace na pozadí při sdílení běžné služby jako například `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-126">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
-   <span data-ttu-id="6fa3f-127">Spustit úlohu na pozadí s `Task.Run()`.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-127">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="6fa3f-128">V podstatě můžete přesměrovat některou z těchto akcí pro úlohu na pozadí podle IHostedService.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-128">You can basically offload any of those actions to a background task based on IHostedService.</span></span>

<span data-ttu-id="6fa3f-129">Způsob, jak přidat jeden nebo více `IHostedServices` do vaší `WebHost` nebo `Host` je tak, že je zaregistrujete si prostřednictvím standardních DI (injektáž závislostí) v ASP.NET Core `WebHost` (nebo `Host` v .NET Core 2.1).</span><span class="sxs-lookup"><span data-stu-id="6fa3f-129">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the standard DI (dependency injection) in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1).</span></span> <span data-ttu-id="6fa3f-130">V podstatě, je nutné provést registraci hostovaných služeb v rámci známé `ConfigureServices()` metodu `Startup` třídy, jako v následujícím kódu z typických tomuto webovému hostiteli technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-130">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span> 

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

<span data-ttu-id="6fa3f-131">V tomto kódu `GracePeriodManagerService` hostovanou službu je z mikroslužeb obchodní řazení v aplikaci eShopOnContainers skutečného kódu, ale jiné dva jsou jenom dvě další ukázky.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-131">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="6fa3f-132">`IHostedService` Provedení úlohy na pozadí se koordinují s životního cyklu aplikací (hostitele nebo mikroslužeb, k tomuto účelu).</span><span class="sxs-lookup"><span data-stu-id="6fa3f-132">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="6fa3f-133">Zaregistrujete úlohy při spuštění aplikace a budete mít příležitost provést určitou akci řádné nebo čištění po aplikaci se vypíná.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-133">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="6fa3f-134">Bez použití `IHostedService`, může vždy spustit vlákno na pozadí ke spuštění každého úkolu.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-134">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="6fa3f-135">Rozdíl je přesně v době vypnutí aplikace, kdy bylo vlákno by jednoduše ukončeny bez nutnosti příležitosti ke spouštění řádné akcí čištění.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-135">The difference is precisely at the app’s shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>


## <a name="the-ihostedservice-interface"></a><span data-ttu-id="6fa3f-136">Rozhraní IHostedService</span><span class="sxs-lookup"><span data-stu-id="6fa3f-136">The IHostedService interface</span></span>

<span data-ttu-id="6fa3f-137">Když se zaregistrujete `IHostedService`, zavolá .NET Core `StartAsync()` a `StopAsync()` metody vaše `IHostedService` zadejte při spuštění aplikace a zastavit v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-137">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="6fa3f-138">Konkrétně start se volá, když server spuštěn a `IApplicationLifetime.ApplicationStarted` se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-138">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="6fa3f-139">`IHostedService` Jak jsou definovány v .NET Core, vypadá podobně jako následující.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-139">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

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
<span data-ttu-id="6fa3f-140">Jak si dokážete představit, můžete vytvořit více implementací IHostedService a zaregistrujte je v `ConfigureService()` metoda do kontejnerů DI, jak bylo uvedeno výše.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-140">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="6fa3f-141">Všechny tyto hostované služby se a zastavování spolu s aplikací/mikroslužeb.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-141">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="6fa3f-142">Jako vývojář je zodpovědná za zpracování akce zastavení nebo služby při `StopAsync()` metoda aktivuje hostitele.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-142">As a developer, you are responsible for handling the stopping action or your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="6fa3f-143">Implementace IHostedService pomocí vlastní hostované služby třídu odvozenou z BackgroundService základní třídy</span><span class="sxs-lookup"><span data-stu-id="6fa3f-143">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="6fa3f-144">Můžete pokračovat a vytvořit vlastní hostovanou službu třídy úplně od začátku a implementovat `IHostedService`, jako je třeba provést při použití .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-144">You could go ahead and create you custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span> 

<span data-ttu-id="6fa3f-145">Ale protože většina úloh na pozadí mají podobné potřeby správy tokeny zrušení a další běžné operace, .NET Core 2.1 bude poskytovat velmi vhodné abstraktní základní třída, kterou lze odvodit z, s názvem BackgroundService.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-145">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other typical operations, .NET Core 2.1 will be providing a very convenient abstract base class you can derive from, named BackgroundService.</span></span>

<span data-ttu-id="6fa3f-146">Tuto třídu poskytuje hlavní práce potřebné k nastavení úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-146">That class provides the main work needed to set up the background task.</span></span> <span data-ttu-id="6fa3f-147">Všimněte si, že tato třída budou přicházet do knihovny .NET Core 2.1, takže není nutné k jejich zapsání.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-147">Note that this class will come in the .NET Core 2.1 library so you don’t need to write it.</span></span>

<span data-ttu-id="6fa3f-148">V době době psaní tohoto textu, nebyla však vydaná .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-148">However, as of the time of this writing, .NET Core 2.1 has not been released.</span></span> <span data-ttu-id="6fa3f-149">Proto v aplikaci eShopOnContainers, který je aktuálně pomocí .NET Core 2.0, jsme se právě časově začlenění tuto třídu v rozhraní .NET Core 2.1 úložiště open source (není nutné žádné speciální licence než licence open source) vzhledem k tomu, že je kompatibilní s aktuální IHostedService rozhraní v rozhraní .NET Core 2.0.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-149">Therefore, in eShopOnContainers which is currently using .NET Core 2.0, we are just temporally incorporating that class from the .NET Core 2.1 open-source repo (no need of any proprietary license other than the open-source license) because it is compatible with the current IHostedService interface in .NET Core 2.0.</span></span> <span data-ttu-id="6fa3f-150">Po vydání .NET Core 2.1, stejně musíte tak, aby odkazoval na správný balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-150">When .NET Core 2.1 is released, you’ll just need to point to the right NuGet package.</span></span>

<span data-ttu-id="6fa3f-151">Následující kód je abstraktní základní třída BackgroundService, jak je implementován v .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-151">The next code is the abstract BackgroundService base class as implemented in .NET Core 2.1.</span></span>

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

<span data-ttu-id="6fa3f-152">Při odvozování z předchozí abstraktní základní třída, díky zděděná implementace, stačí k implementaci `ExecuteAsync()` metoda ve vlastní hostované třídy služby, viz následující příklad zjednodušená kódu v aplikaci eShopOnContainers, což je interval dotazování databáze a publikování události integrace do sběrnice událostí v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-152">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

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
                // and publishing events into the Event Bus (RabbitMS / ServiceBus)
                CheckConfirmedGracePeriodOrders();

                await Task.Delay(_settings.CheckUpdateTime, stoppingToken);
            }
            
            _logger.LogDebug($"GracePeriod background task is stopping.");

        }

        protected override async Task StopAsync (CancellationToken stoppingToken)
        {
               // Run your graceful clean-up actions
        }
}
```

<span data-ttu-id="6fa3f-153">V tomto konkrétním případě pro aplikaci eShopOnContainers je prováděna metodu aplikace, který se dotazuje tabulku databáze hledá objednávky se specifickým stavem, a při použití změn, je publikování události integrace přes Service bus událostí (pod tím může být s použitím RabbitMQ nebo Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="6fa3f-153">In this specific case for eShopOnContainers, it is executing an application method which is querying a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span> 

<span data-ttu-id="6fa3f-154">Samozřejmě můžete spustit žádné jiné obchodní úlohy na pozadí, místo toho.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-154">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="6fa3f-155">Ve výchozím nastavení, token rušení, který je nastavena s 5 druhý časový limit, i když tuto hodnotu můžete změnit při sestavování vašich `WebHost` pomocí `UseShutdownTimeout` rozšíření `IWebHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-155">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="6fa3f-156">To znamená, že naše služby má zrušit v rámci jinak 5 sekund více náhlé ukončení dojde.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-156">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="6fa3f-157">Následující kód by změna této doby na 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-157">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="6fa3f-158">Třída shrnutí diagramu</span><span class="sxs-lookup"><span data-stu-id="6fa3f-158">Summary class diagram</span></span>

<span data-ttu-id="6fa3f-159">Na následujícím obrázku 8-26 zobrazuje souhrn třídy vizuálu a propojen používané při implementaci IHostedServices.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-159">The following image 8-26 shows a visual summary of the classes and interfaced involved when implementing IHostedServices.</span></span>
 
![](./media/image27.png)

<span data-ttu-id="6fa3f-160">**Obrázek 8 – 26.**</span><span class="sxs-lookup"><span data-stu-id="6fa3f-160">**Figure 8-26.**</span></span> <span data-ttu-id="6fa3f-161">Diagram tříd zobrazující více tříd a rozhraní související s IHostedService</span><span class="sxs-lookup"><span data-stu-id="6fa3f-161">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="6fa3f-162">Důležité informace o nasazení a takeaways</span><span class="sxs-lookup"><span data-stu-id="6fa3f-162">Deployment considerations and takeaways</span></span>

<span data-ttu-id="6fa3f-163">Je důležité si uvědomit, že způsob nasazení ASP.NET Core `WebHost` nebo .NET Core `Host` může mít vliv na konečné řešení.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-163">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="6fa3f-164">Například při nasazení vaší `WebHost` na serveru IIS nebo pravidelné službě Azure App Service, může být vypnut hostitele kvůli recyklace fondu aplikací.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-164">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="6fa3f-165">Ale pokud nasazujete hostitele jako kontejner do orchestrátoru, jako je Kubernetes nebo Service Fabric, můžete řídit pojištěných počet instancí za provozu z hostitele.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-165">But if you are deploying your host as a container into an orchestrator like Kubernetes or Service Fabric, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="6fa3f-166">Kromě toho zvažte další přístupy v cloudu, zejména provedené pro tyto scénáře, jako je Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-166">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> 

<span data-ttu-id="6fa3f-167">Ale i pro `WebHost` nasazené do fondu aplikací, jsou scénáře, jako jsou opětovného vyplnění nebo vyprazdňování mezipaměti v paměti aplikace, která bude i nadále použitelná.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-167">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application’s in-memory cache, that would be still applicable.</span></span>

<span data-ttu-id="6fa3f-168">`IHostedService` Rozhraní poskytuje pohodlný způsob, jak spustit úlohy na pozadí v ASP.NET Core webovou aplikaci (v .NET Core 2.0) nebo v procesu/hostitele (počínaje verzí .NET Core 2.1 s `IHost`).</span><span class="sxs-lookup"><span data-stu-id="6fa3f-168">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="6fa3f-169">Jeho hlavní výhodou je příležitost, kterou dostanete s řádné zrušení na kód pro vyčištění vaše úlohy na pozadí, když se vypíná samotného hostitele.</span><span class="sxs-lookup"><span data-stu-id="6fa3f-169">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>


#### <a name="additional-resources"></a><span data-ttu-id="6fa3f-170">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="6fa3f-170">Additional resources</span></span>

-   <span data-ttu-id="6fa3f-171">**Vytvoření naplánované úlohy v technologii ASP.NET Core/Standard 2.0**</span><span class="sxs-lookup"><span data-stu-id="6fa3f-171">**Building a scheduled task in ASP.NET Core/Standard 2.0**</span></span> 

    [*https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html*](https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html)

-   <span data-ttu-id="6fa3f-172">**Implementace IHostedService v ASP.NET Core 2.0**</span><span class="sxs-lookup"><span data-stu-id="6fa3f-172">**Implementing IHostedService in ASP.NET Core 2.0**</span></span> 

    [*https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice*](https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice)

-   <span data-ttu-id="6fa3f-173">**ASP.NET Core 2.1 hostování ukázky**</span><span class="sxs-lookup"><span data-stu-id="6fa3f-173">**ASP.NET Core 2.1 Hosting samples**</span></span> 

    [*https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample*](https://github.com/aspnet/Hosting/tree/release/2.1/samples/GenericHostSample)

>[!div class="step-by-step"]
<span data-ttu-id="6fa3f-174">[Předchozí](test-aspnet-core-services-web-apps.md)
[další](../microservice-ddd-cqrs-patterns/index.md)</span><span class="sxs-lookup"><span data-stu-id="6fa3f-174">[Previous](test-aspnet-core-services-web-apps.md)
[Next](../microservice-ddd-cqrs-patterns/index.md)</span></span>
