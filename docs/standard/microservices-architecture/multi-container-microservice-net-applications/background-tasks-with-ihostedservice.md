---
title: "Implementace úlohy na pozadí v mikroslužeb s IHostedService a BackgroundService – třída"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace úlohy na pozadí v mikroslužeb s IHostedService a BackgroundService – třída"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 12/11/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d60a4590682b79a9f8ac57afee09884b7edd1f98
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="implement-background-tasks-in-microservices-with-ihostedservice-and-the-backgroundservice-class"></a><span data-ttu-id="af9b3-104">Implementace úlohy na pozadí v mikroslužeb s IHostedService a BackgroundService – třída</span><span class="sxs-lookup"><span data-stu-id="af9b3-104">Implement background tasks in microservices with IHostedService and the BackgroundService class</span></span>

<span data-ttu-id="af9b3-105">Úlohy na pozadí a naplánované úlohy jsou něco, co může být nutné implementovat, nakonec v aplikaci mikroslužbu na základě nebo v jakékoliv aplikaci.</span><span class="sxs-lookup"><span data-stu-id="af9b3-105">Background tasks and scheduled jobs are something you might need to implement, eventually, in a microservice based application or in any kind of application.</span></span> <span data-ttu-id="af9b3-106">Při použití architektury mikroslužeb rozdílem je, že můžete implementovat jednu mikroslužbu proces nebo kontejner pro hostování tyto úlohy na pozadí, můžete ho dolů/nahoru škálovat, jako je třeba nebo můžete i zajistit, aby byl spouštěn jednu instanci mikroslužbu procesu nebo kontejneru.</span><span class="sxs-lookup"><span data-stu-id="af9b3-106">The difference when using a microservices architecture is that you can implement a single microservice process/container for hosting these background tasks so you can scale it down/up as you need or you can even make sure that it runs a single instance of that microservice process/container.</span></span>

<span data-ttu-id="af9b3-107">Z obecné hlediska v .NET Core volali jsme tyto typ úlohy hostované služby, protože jsou služby nebo logiky, která hostitele v rámci vaší hostitele/aplikace/mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="af9b3-107">From a generic point of view, in .NET Core we called these type of tasks Hosted Services, because they are services/logic that you host within your host/application/microservice.</span></span> <span data-ttu-id="af9b3-108">Všimněte si, že v tomto případě hostovanou službu jednoduše znamená třídu s logikou úloh na pozadí.</span><span class="sxs-lookup"><span data-stu-id="af9b3-108">Note that in this case, the hosted service simply means a class with the background task logic.</span></span>

<span data-ttu-id="af9b3-109">Od verze rozhraní .NET 2.0 jádra, rozhraní, poskytuje nové rozhraní s názvem <xref:Microsoft.Extensions.Hosting.IHostedService> pomáhá můžete snadno implementace hostované služby.</span><span class="sxs-lookup"><span data-stu-id="af9b3-109">Since .NET Core 2.0, the framework provides a new interface named <xref:Microsoft.Extensions.Hosting.IHostedService> helping you to easily implement hosted services.</span></span> <span data-ttu-id="af9b3-110">Základní myšlenkou je, že zaregistrujete několik úlohy na pozadí (hostované služby), které běží na pozadí při webového hostitele nebo hostiteli běží, jak je znázorněno na obrázku níže.</span><span class="sxs-lookup"><span data-stu-id="af9b3-110">The basic idea is that you can register multiple background tasks (hosted services), that run in the background while your web host or host is running, as shown in the image below.</span></span>

![](./media/image26.png)

<span data-ttu-id="af9b3-111">**Obrázek 8-25.**</span><span class="sxs-lookup"><span data-stu-id="af9b3-111">**Figure 8-25.**</span></span> <span data-ttu-id="af9b3-112">Použití IHostedService v webového hostitele a hostitele</span><span class="sxs-lookup"><span data-stu-id="af9b3-112">Using IHostedService in a WebHost vs. a Host</span></span>

<span data-ttu-id="af9b3-113">Všimněte si rozdílu mezi `WebHost` a `Host`.</span><span class="sxs-lookup"><span data-stu-id="af9b3-113">Note the difference made between `WebHost` and `Host`.</span></span> <span data-ttu-id="af9b3-114">A `WebHost` (základní třída implementace `IWebHost`) v technologii ASP.NET 2.0 základní je artefaktů infrastruktury k poskytování HTTP server funkce procesu, jako třeba když používáte implementujete webové aplikace MVC nebo webového rozhraní API služby.</span><span class="sxs-lookup"><span data-stu-id="af9b3-114">A `WebHost` (base class implementing `IWebHost`) in ASP.NET Core 2.0 is the infrastructure artifact you use to provide HTTP server features to your process, such as if you are implementing an MVC web app or Web API service.</span></span> <span data-ttu-id="af9b3-115">Poskytuje všechny nové přesnosti infrastruktury v ASP.NET Core, umožňuje pomocí vkládání závislostí, vložte middlewares kanál protokolu HTTP, atd. a přesněji použít `IHostedServices` pro úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="af9b3-115">It provides all the new infrastructure goodness in ASP.NET Core, enabling you to use dependency injection, insert middlewares in the HTTP pipeline, etc. and precisely use these `IHostedServices` for background tasks.</span></span>

<span data-ttu-id="af9b3-116">A `Host` (základní třída implementace `IHost`), ale je něco v rozhraní .NET Core 2.1 nového.</span><span class="sxs-lookup"><span data-stu-id="af9b3-116">A `Host` (base class implementing `IHost`), however, is something new in .NET Core 2.1.</span></span> <span data-ttu-id="af9b3-117">V podstatě `Host` umožňuje mít podobné infrastrukturu než máte s `WebHost` (vkládání závislostí, hostovaných služeb atd.), ale v takovém případě stačí chcete mít jednoduché a světlejší proces jako hostitel, s nic související s MVC , Webové rozhraní API nebo HTTP funkce serveru.</span><span class="sxs-lookup"><span data-stu-id="af9b3-117">Basically, a `Host` allows you to have a similar infrastructure than what you have with `WebHost` (dependency injection, hosted services, etc.), but in this case, you just want to have a simple and lighter process as the host, with nothing related to MVC, Web API or HTTP server features.</span></span>

<span data-ttu-id="af9b3-118">Proto můžete vybrat a buď vytvořit specializované hostitelský proces s IHost pro zpracování hostované služby a nic jiného, takové mikroslužbu, jenom pro hostování `IHostedServices`, nebo můžete alternatevely rozšířit existující ASP.NET Core `WebHost` , jako je například stávající aplikace webového rozhraní API ASP.NET Core nebo MVC.</span><span class="sxs-lookup"><span data-stu-id="af9b3-118">Therefore, you can choose and either create a specialized host-process with IHost to handle the hosted services and nothing else, such a microservice made just for hosting the `IHostedServices`, or you can alternatevely extend an existing ASP.NET Core `WebHost`, such as an existing ASP.NET Core Web API or MVC app.</span></span> 

<span data-ttu-id="af9b3-119">Každý přístup má výhody a nevýhody podle potřeby firmy a škálovatelnost.</span><span class="sxs-lookup"><span data-stu-id="af9b3-119">Each approach has pros and cons depending on your business and scalability needs.</span></span> <span data-ttu-id="af9b3-120">Dolní řádek je v podstatě, pokud vaše úlohy na pozadí nemají co dělat s byste měli používat protokol HTTP (IWebHost) a IHost, pokud je k dispozici v rozhraní .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="af9b3-120">The bottom line is basically that if your background tasks have nothing to do with HTTP (IWebHost) you should use and IHost, when available in .NET Core 2.1.</span></span>

## <a name="registering-hosted-services-in-your-webhost-or-host"></a><span data-ttu-id="af9b3-121">Registrace hostovaných služeb v webového hostitele nebo hostitele</span><span class="sxs-lookup"><span data-stu-id="af9b3-121">Registering hosted services in your WebHost or Host</span></span>

<span data-ttu-id="af9b3-122">Umožňuje přejít k podrobnostem dolů na další `IHostedService` rozhraní vzhledem k tomu, že je poměrně podobně jako v jeho využití `WebHost` nebo v `Host`.</span><span class="sxs-lookup"><span data-stu-id="af9b3-122">Let’s drill down further on the `IHostedService` interface since its usage is pretty similar in a `WebHost` or in a `Host`.</span></span> 

<span data-ttu-id="af9b3-123">SignalR je příkladem artefakt pomocí hostované služby, ale můžete ji použít i pro mnohem jednodušší věcmi, jako jsou:</span><span class="sxs-lookup"><span data-stu-id="af9b3-123">SignalR is one example of an artifact using hosted services, but you can also use it for much simpler things like:</span></span>

-   <span data-ttu-id="af9b3-124">Úlohy na pozadí, dotazování databáze hledá změny.</span><span class="sxs-lookup"><span data-stu-id="af9b3-124">A background task polling a database looking for changes.</span></span>
-   <span data-ttu-id="af9b3-125">Naplánované úlohy pravidelně aktualizuje některé mezipaměti.</span><span class="sxs-lookup"><span data-stu-id="af9b3-125">A scheduled task updating some cache periodically.</span></span>
-   <span data-ttu-id="af9b3-126">Implementace QueueBackgroundWorkItem, která umožňuje úlohy ke spuštění na vlákna na pozadí.</span><span class="sxs-lookup"><span data-stu-id="af9b3-126">An implementation of QueueBackgroundWorkItem that allows a task to be executed on a background thread.</span></span>
-   <span data-ttu-id="af9b3-127">Zpracování zpráv z fronty zpráv na pozadí webové aplikace při sdílení společných služeb, jako `ILogger`.</span><span class="sxs-lookup"><span data-stu-id="af9b3-127">Processing messages from a message queue in the background of a web app while sharing common services such as `ILogger`.</span></span>
-   <span data-ttu-id="af9b3-128">Spuštění úlohy na pozadí s `Task.Run()`.</span><span class="sxs-lookup"><span data-stu-id="af9b3-128">A background task started with `Task.Run()`.</span></span>

<span data-ttu-id="af9b3-129">V podstatě můžete přesměrovat některou z těchto akcí pro úlohy na pozadí podle IHostedService.</span><span class="sxs-lookup"><span data-stu-id="af9b3-129">You can basically offload any of those actions to a background task based on IHostedService.</span></span>

<span data-ttu-id="af9b3-130">Způsob, jak můžete přidat jeden nebo více `IHostedServices` do vaší `WebHost` nebo `Host` je tak, že je zaregistrujete až prostřednictvím standardní DI (dependency injection) v ASP.NET Core `WebHost` (nebo v `Host` v rozhraní .NET Core 2.1).</span><span class="sxs-lookup"><span data-stu-id="af9b3-130">The way you add one or multiple `IHostedServices` into your `WebHost` or `Host` is by registering them up through the standard DI (dependency injection) in an ASP.NET Core `WebHost` (or in a `Host` in .NET Core 2.1).</span></span> <span data-ttu-id="af9b3-131">V podstatě, je nutné provést registraci hostovaných služeb v rámci známé `ConfigureServices()` metodu `Startup` třídy, jako v následujícím kódu z typických webového hostitele technologie ASP.NET.</span><span class="sxs-lookup"><span data-stu-id="af9b3-131">Basically, you have to register the hosted services within the familiar `ConfigureServices()` method of the `Startup` class, as in the following code from a typical ASP.NET WebHost.</span></span> 

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

<span data-ttu-id="af9b3-132">V kódu `GracePeriodManagerService` hostovaná služba je skutečné kód z mikroslužbu obchodní řazení v eShopOnContainers, při dalších dva jsou právě dva další ukázky.</span><span class="sxs-lookup"><span data-stu-id="af9b3-132">In that code, the `GracePeriodManagerService` hosted service is real code from the Ordering business microservice in eShopOnContainers, while the other two are just two additional samples.</span></span>

<span data-ttu-id="af9b3-133">`IHostedService` Provádění úkolů pozadí bude řízeno životního cyklu aplikace (hostitele nebo mikroslužbu k tomuto účelu).</span><span class="sxs-lookup"><span data-stu-id="af9b3-133">The `IHostedService` background task execution is coordinated with the lifetime of the application (host or microservice, for that matter).</span></span> <span data-ttu-id="af9b3-134">Při spuštění aplikace a máte možnost provést některé řádně akce nebo čištění když se aplikace vypíná, zaregistrovat úlohy.</span><span class="sxs-lookup"><span data-stu-id="af9b3-134">You register tasks when the application starts and you have the opportunity to do some graceful action or clean-up when the application is shutting down.</span></span>

<span data-ttu-id="af9b3-135">Bez použití `IHostedService`, můžete začít vždy vlákna na pozadí spustit všechny úlohy.</span><span class="sxs-lookup"><span data-stu-id="af9b3-135">Without using `IHostedService`, you could always start a background thread to run any task.</span></span> <span data-ttu-id="af9b3-136">Rozdílem je, přesněji v době vypnutí aplikace při daném vláknu by být ukončeny jednoduše bez nutnosti příležitostí ke spouštění řádně akcí čištění.</span><span class="sxs-lookup"><span data-stu-id="af9b3-136">The difference is precisely at the app’s shutdown time when that thread would simply be killed without having the opportunity to run graceful clean-up actions.</span></span>


## <a name="the-ihostedservice-interface"></a><span data-ttu-id="af9b3-137">Rozhraní IHostedService</span><span class="sxs-lookup"><span data-stu-id="af9b3-137">The IHostedService interface</span></span>

<span data-ttu-id="af9b3-138">Když se zaregistrujete `IHostedService`, .NET Core zavolá `StartAsync()` a `StopAsync()` metody vaší `IHostedService` zadejte při spuštění aplikace a zastavit v uvedeném pořadí.</span><span class="sxs-lookup"><span data-stu-id="af9b3-138">When you register an `IHostedService`, .NET Core will call the `StartAsync()` and `StopAsync()` methods of your `IHostedService` type during application start and stop respectively.</span></span> <span data-ttu-id="af9b3-139">Konkrétně je počáteční volána po spuštění serveru a `IApplicationLifetime.ApplicationStarted` se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="af9b3-139">Specifically, start is called after the server has started and `IApplicationLifetime.ApplicationStarted` is triggered.</span></span>

<span data-ttu-id="af9b3-140">`IHostedService` Definuje .NET Core, vypadá podobně jako následující.</span><span class="sxs-lookup"><span data-stu-id="af9b3-140">The `IHostedService` as defined in .NET Core, looks like the following.</span></span>

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
<span data-ttu-id="af9b3-141">Jak si lze představit, můžete vytvořit více implementace IHostedService a zaregistrujte je v `ConfigureService()` metoda do kontejneru DI, jak je uvedený výše.</span><span class="sxs-lookup"><span data-stu-id="af9b3-141">As you can imagine, you can create multiple implementations of IHostedService and register them at the `ConfigureService()` method into the DI container, as shown previously.</span></span> <span data-ttu-id="af9b3-142">Všechny tyto hostované služby se spuštění a zastavení spolu s aplikací nebo mikroslužby.</span><span class="sxs-lookup"><span data-stu-id="af9b3-142">All those hosted services will be started and stopped along with the application/microservice.</span></span>

<span data-ttu-id="af9b3-143">Jako vývojář je zodpovědná za zpracování akce zastavení nebo vašim službám při `StopAsync()` metoda se aktivuje hostitele.</span><span class="sxs-lookup"><span data-stu-id="af9b3-143">As a developer, you are responsible for handling the stopping action or your services when `StopAsync()` method is triggered by the host.</span></span>

## <a name="implementing-ihostedservice-with-a-custom-hosted-service-class-deriving-from-the-backgroundservice-base-class"></a><span data-ttu-id="af9b3-144">Implementace IHostedService s třídou vlastní hostovanou službu odvozování ze základní třídy BackgroundService</span><span class="sxs-lookup"><span data-stu-id="af9b3-144">Implementing IHostedService with a custom hosted service class deriving from the BackgroundService base class</span></span>

<span data-ttu-id="af9b3-145">Můžete ihned začít a vytvořit vlastní hostovanou službu třída od začátku a implementovat `IHostedService`, jako je třeba provést při použití rozhraní .NET 2.0 jádra.</span><span class="sxs-lookup"><span data-stu-id="af9b3-145">You could go ahead and create you custom hosted service class from scratch and implement the `IHostedService`, as you need to do when using .NET Core 2.0.</span></span> 

<span data-ttu-id="af9b3-146">Ale vzhledem k tomu, že většina úlohy na pozadí bude mít podobné potřeby správy zrušení tokenů a dalších tipical operací, .NET Core 2.1 bude poskytovat velmi praktické abstraktní základní třída, kterou můžete odvozena od, s názvem BackgroundService.</span><span class="sxs-lookup"><span data-stu-id="af9b3-146">However, since most background tasks will have similar needs in regard to the cancellation tokens management and other tipical operations, .NET Core 2.1 will be providing a very convenient abstract base class you can derive from, named BackgroundService.</span></span>

<span data-ttu-id="af9b3-147">Třídy poskytuje hlavní práce potřebné k nastavení úlohy na pozadí.</span><span class="sxs-lookup"><span data-stu-id="af9b3-147">That class provides the main work needed to set up the background task.</span></span> <span data-ttu-id="af9b3-148">Všimněte si, že tato třída, vrátí se v knihovně .NET Core 2.1, nemusíte ho zapsat.</span><span class="sxs-lookup"><span data-stu-id="af9b3-148">Note that this class will come in the .NET Core 2.1 library so you don’t need to write it.</span></span>

<span data-ttu-id="af9b3-149">Však od době psaní tohoto textu .NET Core 2.1 ještě neuvolnil.</span><span class="sxs-lookup"><span data-stu-id="af9b3-149">However, as of the time of this writing, .NET Core 2.1 has not been released.</span></span> <span data-ttu-id="af9b3-150">Proto v eShopOnContainers, který je aktuálně používá rozhraní .NET 2.0 jádra, jsme se právě dočasně zařadit třídy z úložiště .NET Core 2.1 open-source (není třeba žádné vlastní licence než licence open-source) vzhledem k tomu, že je kompatibilní s aktuální IHostedService rozhraní v rozhraní .NET 2.0 jádra.</span><span class="sxs-lookup"><span data-stu-id="af9b3-150">Therefore, in eShopOnContainers which is currently using .NET Core 2.0, we are just temporally incorporating that class from the .NET Core 2.1 open-source repo (no need of any proprietary license other than the open-source license) because it is compatible with the current IHostedService interface in .NET Core 2.0.</span></span> <span data-ttu-id="af9b3-151">Po vydání .NET Core 2.1, budete potřebovat pouze tak, aby odkazovaly na správné balíček NuGet.</span><span class="sxs-lookup"><span data-stu-id="af9b3-151">When .NET Core 2.1 is released, you’ll just need to point to the right NuGet package.</span></span>

<span data-ttu-id="af9b3-152">Další kód je abstraktní základní třída BackgroundService, jak jsou implementované v rozhraní .NET Core 2.1.</span><span class="sxs-lookup"><span data-stu-id="af9b3-152">The next code is the abstract BackgroundService base class as implemented in .NET Core 2.1.</span></span>

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

<span data-ttu-id="af9b3-153">Při jeho odvozování z předchozí abstraktní základní třída, díky této zděděné implementace, stačí k implementaci `ExecuteAsync()` metoda ve vlastní vlastní hostované třídy služeb, jako v následujícím příkladu zjednodušené kód z eShopOnContainers, který se dotazuje databáze a publikování události integrace do sběrnici událost v případě potřeby.</span><span class="sxs-lookup"><span data-stu-id="af9b3-153">When deriving from the previous abstract base class, thanks to that inherited implementation, you just need to implement the `ExecuteAsync()` method in your own custom hosted service class, as in the following simplified code from eShopOnContainers which is polling a database and publishing integration events into the Event Bus when needed.</span></span>

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

                // This eShopOnContainers method is quering a database table 
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

<span data-ttu-id="af9b3-154">V tomto konkrétním případě pro eShopOnContainers je prováděna metodu aplikace, která je quering databázové tabulky hledá řadí s konkrétním stavem a při použití změn, publikování události integrace přes sběrnici událostí (dole, může to být pomocí RabbitMQ nebo Azure Service Bus).</span><span class="sxs-lookup"><span data-stu-id="af9b3-154">In this specific case for eShopOnContainers, it is executing an application method which is quering a database table looking for orders with a specific state and when applying changes, it is publishing integration events through the event bus (underneath it can be using RabbitMQ or Azure Service Bus).</span></span> 

<span data-ttu-id="af9b3-155">Samozřejmě může spustit jakékoli jiné obchodní úlohy na pozadí, místo toho.</span><span class="sxs-lookup"><span data-stu-id="af9b3-155">Of course, you could run any other business background task, instead.</span></span>

<span data-ttu-id="af9b3-156">Ve výchozím nastavení, token zrušení nastavena 5 druhý vypršel časový limit, i když tuto hodnotu můžete změnit při vytváření vašeho `WebHost` pomocí `UseShutdownTimeout` rozšíření `IWebHostBuilder`.</span><span class="sxs-lookup"><span data-stu-id="af9b3-156">By default, the cancellation token is set with a 5 second timeout, although you can change that value when building your `WebHost` using the `UseShutdownTimeout` extension of the `IWebHostBuilder`.</span></span> <span data-ttu-id="af9b3-157">To znamená, že naše služby je očekávaná zrušit po dobu pěti sekund jinak bude mít více náhle ukončeny.</span><span class="sxs-lookup"><span data-stu-id="af9b3-157">This means that our service is expected to cancel within 5 seconds otherwise it will be more abruptly killed.</span></span>

<span data-ttu-id="af9b3-158">Následující kód by změna této doby na 10 sekund.</span><span class="sxs-lookup"><span data-stu-id="af9b3-158">The following code would be changing that time to 10 seconds.</span></span>

```csharp
WebHost.CreateDefaultBuilder(args)
    .UseShutdownTimeout(TimeSpan.FromSeconds(10))
    ...
```

### <a name="summary-class-diagram"></a><span data-ttu-id="af9b3-159">Třída shrnutí diagram</span><span class="sxs-lookup"><span data-stu-id="af9b3-159">Summary class diagram</span></span>

<span data-ttu-id="af9b3-160">Následující obrázek 8-26 zobrazuje souhrn třídy vizuál a propojen související se situací, při implementaci IHostedServices.</span><span class="sxs-lookup"><span data-stu-id="af9b3-160">The following image 8-26 shows a visual summary of the classes and interfaced involved when implementing IHostedServices.</span></span>
 
![](./media/image27.png)

<span data-ttu-id="af9b3-161">**Obrázek 8-26.**</span><span class="sxs-lookup"><span data-stu-id="af9b3-161">**Figure 8-26.**</span></span> <span data-ttu-id="af9b3-162">Třída diagram znázorňující násobek třídy a rozhraní související s IHostedService</span><span class="sxs-lookup"><span data-stu-id="af9b3-162">Class diagram showing the multiple classes and interfaces related to IHostedService</span></span>

### <a name="deployment-considerations-and-takeaways"></a><span data-ttu-id="af9b3-163">Důležité informace o nasazení a takeaways</span><span class="sxs-lookup"><span data-stu-id="af9b3-163">Deployment considerations and takeaways</span></span>

<span data-ttu-id="af9b3-164">Je důležité si uvědomit, že způsob nasazení ASP.NET Core `WebHost` nebo .NET Core `Host` může mít vliv na konečné řešení.</span><span class="sxs-lookup"><span data-stu-id="af9b3-164">It is important to note that the way you deploy your ASP.NET Core `WebHost` or .NET Core `Host` might impact the final solution.</span></span> <span data-ttu-id="af9b3-165">Například pokud nasadíte vaší `WebHost` služby IIS nebo regulární Azure App Service, může být váš hostitel vypnut z důvodu recykluje fond aplikací.</span><span class="sxs-lookup"><span data-stu-id="af9b3-165">For instance, if you deploy your `WebHost` on IIS or a regular Azure App Service, your host can be shut down because of app pool recycles.</span></span> <span data-ttu-id="af9b3-166">Ale pokud nasazujete váš hostitel jako kontejner do produktu orchestrator jako Kubernetes nebo Service Fabric, můžete řídit pojištěných počet instancí za provozu vaše hostitele.</span><span class="sxs-lookup"><span data-stu-id="af9b3-166">But if you are deploying your host as a container into an orchestrator like Kubernetes or Service Fabric, you can control the assured number of live instances of your host.</span></span> <span data-ttu-id="af9b3-167">Kromě toho zvažte další postupy v cloudu, zejména provedené pro tyto scénáře, jako je Azure Functions.</span><span class="sxs-lookup"><span data-stu-id="af9b3-167">In addition, you could consider other approaches in the cloud especially made for these scenarios, like Azure Functions.</span></span> 

<span data-ttu-id="af9b3-168">Ale i pro `WebHost` nasadí do fondu aplikací, existují scénáře, jako je opětovného vyplnění nebo abyste vyprázdnili mezipaměť v paměti aplikace, která by byla stále platná.</span><span class="sxs-lookup"><span data-stu-id="af9b3-168">But even for a `WebHost` deployed into an app pool, there are scenarios like repopulating or flushing application’s in-memory cache, that would be still applicable.</span></span>

<span data-ttu-id="af9b3-169">`IHostedService` Rozhraní představuje pohodlný způsob pro spuštění úlohy na pozadí v ASP.NET Core webovou aplikaci (v rozhraní .NET 2.0 jádra) nebo v jakékoli proces hostitele (počínaje .NET Core 2.1 s `IHost`).</span><span class="sxs-lookup"><span data-stu-id="af9b3-169">The `IHostedService` interface provides a convenient way to start background tasks in an ASP.NET Core web application (in .NET Core 2.0) or in any process/host (starting in .NET Core 2.1 with `IHost`).</span></span> <span data-ttu-id="af9b3-170">Jeho hlavní výhodou je příležitost, kterou dostanete s řádně zrušení čištění kódu úlohy na pozadí, když se vypíná hostitele sám sebe.</span><span class="sxs-lookup"><span data-stu-id="af9b3-170">Its main benefit is the opportunity you get with the graceful cancellation to clean-up code of your background tasks when the host itself is shutting down.</span></span>


#### <a name="additional-resources"></a><span data-ttu-id="af9b3-171">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="af9b3-171">Additional resources</span></span>

-   <span data-ttu-id="af9b3-172">**Vytváření naplánované úlohy v technologii ASP.NET 2.0 základní nebo standardní**</span><span class="sxs-lookup"><span data-stu-id="af9b3-172">**Building a scheduled task in ASP.NET Core/Standard 2.0**</span></span> 

    [<span data-ttu-id="af9b3-173">*https://blog.maartenballiauw.be/POST/2017/08/01/Building-a-Scheduled-Cache-Updater-in-ASPNET-Core-2.HTML*</span><span class="sxs-lookup"><span data-stu-id="af9b3-173">*https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html*</span></span>](https://blog.maartenballiauw.be/post/2017/08/01/building-a-scheduled-cache-updater-in-aspnet-core-2.html)

-   <span data-ttu-id="af9b3-174">**Implementace IHostedService v základní technologie ASP.NET 2.0**</span><span class="sxs-lookup"><span data-stu-id="af9b3-174">**Implementing IHostedService in ASP.NET Core 2.0**</span></span> 

    [<span data-ttu-id="af9b3-175">*https://www.stevejgordon.co.uk/ASP-NET-Core-2-ihostedservice*</span><span class="sxs-lookup"><span data-stu-id="af9b3-175">*https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice*</span></span>](https://www.stevejgordon.co.uk/asp-net-core-2-ihostedservice)

-   <span data-ttu-id="af9b3-176">**Ukázky hostování 2.1 jádro ASP.NET**</span><span class="sxs-lookup"><span data-stu-id="af9b3-176">**ASP.NET Core 2.1 Hosting samples**</span></span> 

    [<span data-ttu-id="af9b3-177">*https://github.com/ASPNET/Hosting/Tree/dev/Samples/GenericHostSample*</span><span class="sxs-lookup"><span data-stu-id="af9b3-177">*https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample*</span></span>](https://github.com/aspnet/Hosting/tree/dev/samples/GenericHostSample)



>[!div class="step-by-step"]
<span data-ttu-id="af9b3-178">[Předchozí] (test-aspnet-core-services-web-apps.md) [Další] (.. /microservice-ddd-cqrs-Patterns/index.MD)</span><span class="sxs-lookup"><span data-stu-id="af9b3-178">[Previous] (test-aspnet-core-services-web-apps.md) [Next] (../microservice-ddd-cqrs-patterns/index.md)</span></span>
